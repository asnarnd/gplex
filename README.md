# Project Description
GPLEX is a scanner generator which produces lexical scanners written in C#.  The input language is similar to the original LEX specification language, but allows full 21-bit Unicode scanners to be specified.

This repository now includes the full documentation for the scanner-generator.

## This Fork
The repo is a fork of the original maintained by [@k-john-gough](https://github.com/k-john-gough/gplex). The generator produced here requires a .NET runtime compatible with .NET6 or .NETFramework 4.72. The MSBuild targets contained in the NuGet package produced by the repo support .NET SDK "multi-targeting" projects (minimum .NETStandard 2.0). Targets have been modified, with improvements in incremental compilation and use in modern IDEs.

## Features
_GPLEX_ generates scanners based around finite state automata.  The generated automata have the number of states minimized by default, and have a large number of options for table compression.  The default compression scheme is chosen depending on the input alphabet cardinality, and almost always gives a reasonable result.  However a large number of options are available for the user to tune the behavior if necessary.

The tool implements many of the _FLEX_ extensions, including such things as start-state stacks.

The generated scanners are designed to interface cleanly with bottom-up parsers generated by _Gardens_ _Point_ _Parser_ _Generator_.  However, gplex-generated scanners have been successfully used with both handwritten parsers and with parsers generated by _COCO/R_. 

## Examples Of Use

There are a small number of examples of use included in the download package, and these are fully discussed in the documentation.  For a more complex example _GPLEX_ and the companion _GPPG_ tool each themselves use scanners and parsers generated by _GPLEX_ and _GPPG_. The examples described in the documentation for GPPG and GPLEX have now been added to the distribution as file GP-Examples.zip.

There is a separate documentation file that deals with the special issues that arise with scanners that use the Unicode character set.

## Is GPLEX What You Need?

_GPLEX_ is a scanner generator.  It is intended to be used to generate scanners for compilers or other tools that process text. It picks out non-overlapping substrings from within a continuing input stream, and returns an integer token identification. It may also be used for other simple regular expression recognition tasks, but is not a replacement for the _System.Text.RegularExpressions_ classes. It does not have built-in mechanisms for multiple substring capture or anything similar.

_GPLEX_ has historically had an approximately 2-per-year release cycle.  If there is some feature that fits within the broad intention of the tool and which you feel is missing ... raise an issue.  If what you really want is a C# version of AWK then _GPLEX_ isn't it, and the copyright notice explains the conditions under which you may use code of _GPLEX_ to help you implement AWK.NET yourself.
