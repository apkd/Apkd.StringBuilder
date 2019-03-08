# Apkd.StringBuilder

An alternative to the [StringBuilder](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder) class, with minimal memory allocation.

The default StringBuilder implementation in Mono/.NET 4.0+/.NET Core is optimized for the common case of multiple calls to `Append` by storing strings in a linked-list of chunks.*[1]* This can lead to non-obvious performance issues, for example allocations when using `Clear()` on a builder with multiple chunks.

This implementation is more similar to the one in .NET 2.0, in the way that it is optimized for better performance in the case of frequent `Insert`/`Remove` operations.

You can get zero allocations (other than the `ToString()` call) by re-using the same `StringBuilder` instance.

*[1]* https://codingsight.com/stringbuilder-the-past-and-the-future/

## Implemented interfaces

- `IList<char>`
- `ICollection<char>`
- `IReadOnlyList<char>`
- `IReadOnlyCollection<char>`
- `IEnumerable<char>`
- `IEnumerable`

## Supported methods

```csharp
/// <summary> Return the string result </summary>
public override string ToString();

/// <summary> Clears the StringBuilder instance (preserving allocated capacity) </summary>
public StringBuilder Clear();

/// <summary> Insert string at given index </summary>
public StringBuilder Insert(int index, string text);

/// <summary> Insert character at given index </summary>
public StringBuilder Insert(int index, char character);

/// <summary> Remove characters starting from specified index </summary>
public StringBuilder Remove(int index, int count);

/// <summary> Append the content of another StringBuilder instance </summary>
public StringBuilder Append(StringBuilder other);

/// <summary> Append a string </summary>
public StringBuilder Append(string value);

/// <summary> Append a substring of a string </summary>
public StringBuilder Append(string value, int valueStartIndex = 0, int? valueLength = default);

/// <summary> Append a character </summary>
public StringBuilder Append(char c);

/// <summary> Append a character </summary>
public StringBuilder Append(char c, int repeat);

/// <summary> Append an object (calls .ToString()) </summary>
public StringBuilder Append(object value);

/// <summary> Append an int without memory allocation </summary>
public StringBuilder Append(int value);

/// <summary> Append a float without memory allocation. </summary>
public StringBuilder Append(float valueF);

/// <summary> Replace all occurences of a character </summary>
public StringBuilder Replace(char a, char b);

/// <summary> Replace all occurences of a string by another one </summary>
public StringBuilder Replace(string oldStr, string newStr);

public bool StartsWith(string value);

public bool StartsWith(string value, bool ignoreCase);

public bool StartsWith(string value, int startIndex = 0, bool ignoreCase = false);

public int IndexOf(char value);

public int IndexOf(char value, int startIndex);

public int IndexOf(string value);

public int IndexOf(string value, int startIndex);

public int IndexOf(string value, bool ignoreCase);

public int IndexOf(string value, int startIndex, bool ignoreCase);

int ICollection<char>.Count;

int IReadOnlyCollection<char>.Count;

bool ICollection<char>.IsReadOnly;

void IList<char>.RemoveAt(int index);

void IList<char>.Insert(int index, char item);

void ICollection<char>.Clear();

void ICollection<char>.Add(char character);

bool ICollection<char>.Contains(char item);

public void CopyTo(char[] array, int arrayIndex);

bool ICollection<char>.Remove(char item);

public List<char>.Enumerator GetEnumerator();

IEnumerator IEnumerable.GetEnumerator();

IEnumerator<char> IEnumerable<char>.GetEnumerator();

public static implicit operator string(StringBuilder builder);
```
