---
layout: post
title: C++ GAME AUDIO ENGINE PART 4 - HASHING OBJECTS
date: 2017-04-16 10:13:00
description: How to encode an identifier for an object as a unique hash to avoid expensive string compares throughout an engine.
---

All the articles in this series so far have been about components of software architecture and design, and this is a little more nitty gritty -- I want to talk about data hashing. This is a useful technique in a variety of contexts. 

You can allow users to enter strings on a high level API but represent them internally with their associated hashes; you can hash an entire loaded resource like an audio file while loading to make sure you have not loaded the same audio file by another name; you can hash metadata about audio file format to quickly find a Voice Factory that outputs the correct type of voices.

Unsigned ints make great keys, and you can be sure that your hashes will remain unique and consistent with an encryption algorithm such as MD5. The algorithm in that link can be distilled into a single function, and whenever you need to hash data, just include your Hash Function.

{% highlight c++ %}

// find a buffer by string name
Buffer* BufferManager::Find(const char* id_string)
{
    unsigned int buffer_id = HashThis(id_string);
    //... iterate through your list and use buffer_id
    //... to find the correct node
}
{% endhighlight %}


Once you have a hashing algorithm, there may be some tweaking that you contain inside the HashThis function. For example, I set a maximum length for string names (32 bytes) and copy the input into this container, to keep consistency. Then the final output is a binary-or of the four dwords that the md5 algorithm outputs.

{% highlight c++ %}
unsigned int HashThis(const char* input)
{
    // usually hash inupt to MD5, create tuples

    unsigned char hashThis[MAX_NAME_SIZE] = { 0 };
    unsigned char i = input[0];
    unsigned int iterator = 0;
    while (i != '\0')
    {
        hashThis[iterator] = input[iterator];
        i = input[iterator];
        iterator++;
    }

    MD5Output out;
    MD5Buffer(hashThis, MAX_NAME_SIZE, out);

    // create a reduced hash:
    unsigned int md5;
    md5 = out.dWord_0 ^ out.dWord_1 ^ 
          out.dWord_2 ^ out.dWord_3;
    return md5;
}
{% endhighlight %}

You can take this approach for any time of data, though to keep my head straight I convert objects to raw bytes to send through the algorithm. For example, I overloaded this function to submit WAVEFORMATEX objects when using XAudio2 so that whenever I load a new file, I check if there exists a factory yet to output voices tailored to that file's particular attributes such as channels, sample rate, and filetype (contained in the WAVEFORMATEX object.) For interest, here is that overloaded function:

{% highlight c++ %}
unsigned int HashThis(WAVEFORMATEXTENSIBLE& wfx)
{
    // turn the object into a raw array of bytes
    unsigned char hashThis[sizeof(wfx)] = { 0 };
    unsigned char* i = reinterpret_cast<unsigned char*>(&wfx);

    unsigned int iterator = 0;
    while (iterator < sizeof(wfx))
    {
        hashThis[iterator] = *i;
        i++;
        iterator++;
    }

    MD5Output out;
    MD5Buffer(hashThis, MAX_NAME_SIZE, out);

    // create a reduced hash:
    unsigned int md5;
    md5 = out.dWord_0 ^ out.dWord_1 ^ 
          out.dWord_2 ^ out.dWord_3;

    return md5;
}
{% endhighlight %}


# CONCLUSION

You can apply this technique anywhere that an unsigned int representation of a hunk of data would be useful; another cool one is hashing audio data for uniqueness so you can check whether a load request should actually load a file or just assign an alias to an already loaded file. Utilizing this technique can speed up searches via unsigned int compares and allow an intuitive way to assign keys to resources in your management.