# Crosscutter - [Available on nuget](https://www.nuget.org/packages/Crosscutter/)
.NET extensions, safety &amp; convenience methods for known types.  This project is esssentially me "scratching my own itch", and writing a library of extension methods that make known .NET types safer and easier to use.  This reduces my rate of friction in all projects, and I've always wished to have a globally-available toolkit for anything and everything.  To this end, all .csproj files in this project are published to [nuget](https://www.nuget.org/packages?q=crosscutter) via continuous deployment, and open-sourced at [github](https://github.com/dbenzel/Crosscutter).  Enjoy!

# Installation
Using Package Manager Console:
```
PM> Install-Package Crosscutter
```

# Usage
Most all of Crosscutter's functionality is found in the Crosscutter.Extensions namespace.
```c#
using Crosscutter.Extensions;
```

### String Extensions
```c#
"".IsPopulated();               //  false
"".IsNullOrWhitespace();        //  true
"".IsNullOrEmpty();             //  true

"abc".IsIn("ABC", "DEF");       //  true (case-insensitive)

"abc".Matches("abc", "def");    //  true (case-sensitive)
"ABC".Matches("abc", "def");    //  false (case-sensitive)

"12345-6789".GetSafeSubstring(0, 5);	//	"12345"
"1234".GetSafeSubstring(0, 5);			//	"1234"

"Just  Read  The  Instructions".CollapseSpaces();	//	"Just Read The Instructions"
```

### Regex Extensions
```c#
"12345-6789".MatchesRegex(@"^\d{5}\-\d{4}$");   //  true

"AA AB AC".GetFirstMatch(@"A\w\b");		//	"AA"

"AA AB AC".GetAllMatches(@"A\w\b");		// Matches == ["AA", "AB", "AC"]
```