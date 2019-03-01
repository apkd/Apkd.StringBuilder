# Apkd.StringBuilder

An alternative to the [StringBuilder](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder) class, with minimal memory allocation.

The default StringBuilder implementation in Mono/.NET 4.0+/.NET Core is optimized for the common case of multiple calls to `Append` by storing strings in a linked-list of chunks.*[1]* This can lead to non-obvious performance issues, for example allocations when using `Clear()` on a builder with multiple chunks.

This implementation is more similar to the one in .NET 2.0, in the way that it is optimized for better performance in the case of frequent `Insert`/`Remove` operations.

You can get zero allocations (other than the `ToString()` call) by re-using the same `StringBuilder` instance.

*[1]* https://codingsight.com/stringbuilder-the-past-and-the-future/
