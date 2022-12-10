---
layout: post
title: C++ GAME AUDIO ENGINE PART 2 - FACTORIES AND POOLS
date: 2017-03-20 12:49:00
description: A useful optimization technique for systems that generate many small objects.
---

In any large scale system, especially one driven by a variety of commands and resources, heap allocations (via `malloc`/`free` or `new`/`delete`) can become serious performance bottlenecks as well as liabilities in memory management due to their unbounded execution time and fragmentation. One effective way to mitigate these issues is to replace your raw allocations with factories that pool your resources for you. You can potentially avoid hundreds of allocations when creating timeline commands, playlists, voices, by only calling new when your pool of inactive objects is empty.

The nice thing about this approach is that it can become almost formulaic, with only situational tweaks when you need to be properly reset and reconfigure recycled resources. As an example, here is a header for a Play Command factory:

{% highlight c++ %}
class PlayCommandFactory

{

    public:
    //...

    // Only allocates a new Play Command 
    // if the inactive pool is empty.
    // We pass it a sound to give the command context.
    snd_err Create(PlayCommand*& out, Sound* playlist);

    // Adds an otherwise deleted object to the recycled pool
    snd_err Return(PlayCommand* toReturn);

    private:

    // Keeps track of the active allocations
    std::list<PlayCommand*> activePool;

    // Saves inactive objects for recycling
    std::stack<PlayCommand*> inactivePool;
};
{% endhighlight %}

As per the comments, the Create method of the factory replaces any raw new you would use for getting Play commands; same for Return and delete. Since audio commands in particular are rampant in this audio engine, this approach is essential; there could easily be dozens of commands for each instance of a playlist, multiplied by many sound calls on the game thread.

{% highlight c++ %}
snd_err PlayCommandFactory::Create( PlayCommand*& out,
                                        Sound* toPlay)
{

    snd_err err = snd_err::OK;
    if(!toPlay)
    {
        err = snd_err::NULLPTR;
    }
    PlayCommand* cmd = nullptr;
    if (inactivePool.empty())
    {
        // Can't recycle -- allocate!
        cmd = new PlayCommand();
    }
    else
    {
        // Avoid allocation, take a dead one!
        cmd = inactivePool.top();
        inactivePool.pop();

    }
    // Set the context (the case specific part)
    cmd->AttachSound(toPlay);

    // The command is now active!
    activePool.push_front(cmd);

    // set the output
    out = cmd;

    // side note-- return error codes!
    return err;
}
{% endhighlight %}

{% highlight c++ %}
void PlayCommandFactory::Return(PlayCommand* toReturn)
{
    snd_err err = snd_err::OK;
    if(!toReturn)
    {
        err = snd_err::NULLPTR;
    }
    // put the pointer back on the stack
    activePool.remove(toReturn);
    inactivePool.push(toReturn);

    return err;
}
{% endhighlight %}


# CONCLUSION

Resource pooling via factories is a very effective way to minimize the footprint caused by a large amount of small allocations and allows you to elegantly request resources without manually pooling memory by hand. Next up in this series (Part 3) is a discussion about designing a central timeline for your engine.

