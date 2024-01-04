# Common Errors
When developing with Azure SDK, we often encounter repeatedly errors, let's catch those, so we dont repeat ourselves 
on looking for solutions. 

## Can't find xxx under namespace "Microsoft.xxxx"
```C#
namespace Microsoft.Example.Services
{
    using Azure.Identity;
    ....
}
```
The above code would fail and would complain CS0234 with The Type or namespace "Identity" does not exist in "Microsoft.Azure". This is a common know issue for Azure libraries if they are being used under namespace "Microsoft.xxxx". "Microsoft" should be a reserved keyword to avoid unwanted failures. 
To fix the problem above, we need to change the namespace to remove "Microsoft". It would work as follow: 
 ```C#
namespace Example.Services
{
    using Azure.Identity;
    ....
}
```
Alternatively, you can use the "global" keyword in front of the namespace, this would avoid the conflict between parent namespace scope, for instance, the "Azure.Identity" will not be treated under "Microsoft.Azure.Identity". 
```C#
namespace Example.Services
{
    global::using Azure.Identity;
    ....
}
```
