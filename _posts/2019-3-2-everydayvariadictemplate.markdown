---
layout: post
title: A USE OF VARIADIC TEMPLATES THAT I CAN STILL UNDERSTAND NEXT WEEK
date: 2019-03-2 21:01:00
description: This post discusses a case in which a dash of variadic templates resulted in more elegant library code.
---

In college I was told that behind any easy-to-use API is a tangled web of complicated code spaghetti. While I don't necessarily agree with this in many cases, it is in line with the common sentiment that C++ template meta-programming is best used in libraries that prioritize elegant or expressive usage over clear internal code, especially when those libraries emphasize complicated mathematics.
 
From a C++ nerd perspective, I love the idea of template meta-programming. It's sort of a pipe-dream for me to be able to fully understand Eigen or STL source code and be able to write libraries that, in spite of their incomprehensible complexity, allow for simple and easy to understand abstractions in the library's usage.

But I'd like to talk about a case in which I found a common template meta-programming construct to be useful in more everyday code. Variadic templates tend to be fairly "coupled" with template meta-programming, as they are a key component in creating many fancy, recursive types that are written by a compiler. For this reason, it caught me by surprise that I found a more "common" usage the other day that isn't really template meta-programming... more in line with [template "normal"-programming](https://www.youtube.com/watch?v=vwrXHznaYLA).

I was dealing with a class that took a stream of bytes  (between 2 and 8 bytes in length) and parsed/stored them in its own special way.

{% highlight c++ %}
struct Dog
{
    // A legacy constructor whose semantics we have to maintain
    // for the outside world
    Dog(uint8_t byte0, 
        uint8_t byte1 = 0,
        uint8_t byte2 = 0,
        uint8_t byte3 = 0,
        uint8_t byte4 = 0,
        uint8_t byte5 = 0,
        uint8_t byte6 = 0,
        uint8_t byte7 = 0)
    {
        SetDogBytes({byte0, byte1, byte2, byte3, byte4, byte5, byte6, byte7});
    }    

    template<size_t N>
    void SetDogBytes(const uint8_t(&inBytes)[N])
    {
        for(auto byte : inBytes)
        {
            printf("Yum!\n");
        }
    }
};
{% endhighlight %}

The problem was, `null` bytes were totally valid in this data stream (as were all other byte values), so we couldn't just use `0x0` as default arguments and pass them to this function that took an array. We could just change the constructor to take an array-of-bytes reference/`std::array` or use a `numBytes` argument or something, but we were working with an API that people were used to and didn't want to rock the boat in that way. So, my first "let's just get this to work in the ugliest way possible and stay externally the same" solution looked like this:

{% highlight c++ %}
struct Dog
{
    Dog(uint8_t byte0)
    {
        SetDogBytes({byte0});
    }
       
    Dog(uint8_t byte0, 
        uint8_t byte1)
    {
        SetDogBytes({byte0, byte1});
    }   

    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2)
    {
        SetDogBytes({byte0, byte1, byte2});
    }   
    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2,
        uint8_t byte3)
    {
        SetDogBytes({byte0, byte1, byte2, byte3});
    }   
    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2,
        uint8_t byte3,
        uint8_t byte4)
    {
        SetDogBytes({byte0, byte1, byte2, byte3, byte4});
    }   
    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2,
        uint8_t byte3,
        uint8_t byte4,
        uint8_t byte5)
    {
        SetDogBytes({byte0, byte1, byte2, byte3, byte4, byte5});
    }   
    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2,
        uint8_t byte3,
        uint8_t byte4,
        uint8_t byte5,
        uint8_t byte6)
    {
        SetDogBytes({byte0, byte1, byte2, byte3, byte4, byte5, byte6});
    }       

    Dog(uint8_t byte0, 
        uint8_t byte1,
        uint8_t byte2,
        uint8_t byte3,
        uint8_t byte4,
        uint8_t byte5,
        uint8_t byte6,
        uint8_t byte7)
    {
        SetDogBytes({byte0, byte1, byte2, byte3, byte4, byte5, byte6, byte7});
    }    

    template<size_t N>
    void SetDogBytes(const uint8_t(&inBytes)[N])
    {
        for(auto byte : inBytes)
        {
            printf("Yum!\n");
        }
    }
};
{% endhighlight %}

No more default arguments muddying our byte stream! So we know the length of our byte-stream without any `numBytes` argument or passing an array reference or `std::array<uint8_t, N>`, etc. But it sure is ugly...

This is a case where we want the same code, but we just want the compiler to "copy and paste" it **for** us rather than us leaving all this redundant code explicitly written out, which is exactly what variadic templates can easily do. The equivalent code using a variadic template looks like this:
{% highlight c++ %}
struct Dog
{   
    // Ta-Da!
    // Expands to the constructors we saw above.
    template<typename... Ts>
    Dog(Ts... args)
    {
        // This is one way we could ask the compiler to disallow 
        // too many arguments in the parameter pack
        static_assert(sizeof...(args) <= kMaxByteStreamSize, 
        "You're trying to construct with too large a byte stream!");
        
        SetDogBytes({static_cast<uint8_t>(args)...});
    }    

    template<size_t N>
    void SetDogBytes(const uint8_t(&inBytes)[N])
    {
        for(auto byte : inBytes)
        {
            printf("Yum!\n");
        }
    }

    static constexpr int kMaxByteStreamSize = 8;
};
{% endhighlight %}
Regarding the `static_assert`: yes, you could use SFINAE here, but looking at variadic templates for the first time is enough to make one's eyes cross on its own!

My point here is that using a simple variadic template in this case made some very redundant, unwieldy code into a short snippet that can be at least reasoned about -- and may serve as a gateway drug into using variadic templates for more nefarious deeds!