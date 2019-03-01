# Apkd.StringBuilder

An alternative to the [StringBuilder class](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder), with minimal memory allocation.

The default Mono/.NET4+/.NET Core StringBuilder implementation is optimized for the common case of multiple calls to `StringBuilder.Append` by storing strings in a linked-list of chunks.[1] This implementation is more similar to the .NET2.0 one, in the way it is optimized for better performance in the case of frequent `Insert`/`Remove` operations.

You can get zero allocations (other than the `ToString()` call) by re-using the same `StringBuilder` instance.

[1] https://codingsight.com/stringbuilder-the-past-and-the-future/