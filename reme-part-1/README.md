# Write Up
Using dnSpy to inspect ReMe.dll file.  Exporting to Visual Studio 2017 project. When inspecting this part of the code stands out as it holds the encrypted password/flag.
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
Making a new Csharp project and copying the String.Encryption Class into it. Making a new main class:
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
