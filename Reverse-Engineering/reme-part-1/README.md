# Writeup
I used dnSpy to inspect the ***ReMe.dll*** file and exported the file into a Visual Studio 2017 project. When inspecting, the following part of the code stands out:
```csharp
bool flag5 = args[0] != StringEncryption.Decrypt("D/T9XRgUcKDjgXEldEzeEsVjIcqUTl7047pPaw7DZ9I=");
			if (flag5)
			{
				Console.WriteLine("Nope");
				Environment.Exit(-1);
			}
			else
			{
				Console.WriteLine("There you go. Thats the first of the two flags! CSCG{{{0}}}", args[0]);
			}
```
After a short look at it, it becomes obvious, that the encrypted password is in the code and the code also includes the decryption algorithm.
To make use of that method, I made a new Csharp project and copied the String.Encryption Class into it and created a new main class:
```csharp
using System;

namespace Exploit
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(StringEncryption.Decrypt("D/T9XRgUcKDjgXEldEzeEsVjIcqUTl7047pPaw7DZ9I="));
        }
    }
}
```
This can now be executed and prints the password, which can be used to get the flag.
# Prevention
The real password should be stored as a hash. It should not be possible to reverse the encryption/hash function. The entered password should be hashed / encrypted and than be compared to the real password and not the other way round.
