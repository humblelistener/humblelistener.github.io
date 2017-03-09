---
layout: post
title: "Understanding async keyword in c#"
date: 2012-12-16
categories:
  - programming
  - c#
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
---

Understanding how async keyword works in c#

So, c# 5 introduced a new keyword to simplify asynchronous programming
by the introduction of await keyword. Functionally this keyword will
wait for the completion of asynchronous operation that was started.


Technically though it has a complex contract, take a look at the same
code below

```
internal class Class3
{
    public async Task<PersonDetails[]> GetPersonDetails(string personName)
    {
      var personGoogleDetails = CollectPersonDetailFromGoogle(personName);
      DoSomeComplexWork();
      PersonDetails[] personDetails = await personGoogleDetails;
      CallSomeSimpleWork();

      return personDetails;
    }

    private CustomAwaitable CollectPersonDetailFromGoogle(string personName)
    {
      return null;
    }

    private void CallSomeSimpleWork()
    {
      throw new NotImplementedException();
    }

    private void DoSomeComplexWork()
    {
      throw new NotImplementedException();
    }    
}

internal class CustomAwaitable
{
  public CustomAwaiter<PersonDetails[]> GetAwaiter()
  {
    return new CustomAwaiter<PersonDetails[]>();
  }
}

internal class CustomAwaiter<T> : System.Runtime.CompilerServices.INotifyCompletion
{
  public bool IsCompleted { get; set; }
  public void OnCompleted(Action continuation)
  {
    throw new NotImplementedException();
  }

  public T GetResult()
  {
    return default(T);
  }
}

internal class PersonDetails
{
}

```


There are few things, that I want to bring it up,
1.  `GetPersonDetails()` method’s signature says it will return `Task<PersonDetails>`
    however the return statement just returns PersonDetails[] and the
    compiler is happy about it.
2.  Look at the dis assembler screen shot
    and see `<GetPersonDetails>d_0` which is an anonymous
    class created. Any idea why?</span>
3.  Look at use of “await” keyword, though
    my method `CollectPersonDetailFromGoogle` is not a `Task<T>` or
    `Task`, the compiler is still happy with that.
