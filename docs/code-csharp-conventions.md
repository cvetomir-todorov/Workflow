# Naming

Most naming rules and conventions should be enforced by the code style tools used

## Acronym casing

* 2, 3, 4 (and more) -letter acronyms in source code should be:
  - **`PascalCase`**:
    - `namespace System.Db`, `namespace System.Xml`, `namespace System.Http`
    - `class DbContext`, `class TestXmlReader`, `class HttpClient`
    - `field inputDbReader`, `field testHttpClient`,
    - `var testXmlWriter`, `var testDbWriter`
  - **`lowercase`** when in the beginning of variables and fields:
    - `field dbWriter`, `field httpClient`
    - `var dbReader`, `var xmlReader`
* All acronyms should be **UPPERCASE** in documentation, comments and any free text
  - Example: IO, XML, HTTP

## Type names

* Classes should not have `Service` suffix just because they are registered in a dependency injection container
  - Example: `Authenticator` should be preferred over ~~`AuthenticationService`~~

## Async suffix

* Add suffix when the method has both async and sync versions: `Extract`, `ExtractAsync`
* Avoid suffix when the method has just 1 version: `Extract`, `Transform`, `Load`

# Project-dependent settings

* `<Nullable>enable</Nullable>`
* `<ImplicitUsings>enable</ImplicitUsings>`
  - Namespaces that are **too** specific should not be added to the custom list of implicit usings

# Style

* Use **file-scoped** namespaces
  - Reduced indentation allows more code to be fitted into screen
* **Explicit types over `var`**
  - Use C# 10 `new()` feature
  - Readability improves when type is explicit
    - No need for mouse hovering in IDE to discover it
    - No need to remember return types of all methods to know it
    - Works for non-IDE environment
  - For generics more complex than `List<string>` or `IDictionary<string, int>` strongly consider creating a custom data model
  - Example at the bottom
* **Method ordering**
  - We **do not** place public methods on top and non-public below them
  - If a non-public method is used **only once**, then it is placed right below the method that is using it
  - Result is that code is read from top to the bottom **linearly**
  - If a non-public method is used **more than once** then it could be placed at the very bottom
  - Rule could be applied recursively, but hopefully there is no need to form deeper hierarchies
    - This could also indicate class is too complex
  - Example at the bottom
* **Parameter ordering**
  - Start with ones that are strictly input
  - Put in the middle the ones that are changed
  - End with ones that are strictly output
  - Example at the bottom
* **Records** - TODO

# Code examples

<details><summary>Explicit types over var custom data model</summary>

```csharp
class InvertedIndex
{
    // the dictionary keeps a list of postings for each term
    // a posting is a pair of document and number of occurrences of the respective term in the respective document
    private readonly Dictionary<string, List<KeyValuePair<string, int>>> _index = new();

    public void AddPosting(string term, string document, int occurrences)
    {
        if (!_index.TryGetValue(term, out List<KeyValuePair<string, int>> postings))
        {
            postings = new();
            _index.Add(term, postings);
        }

        postings.Add(new KeyValuePair<string, int>(document, occurrences));
    }

    public IReadOnlyCollection<string> GetDocuments(string term)
    {
        if (!_index.TryGetValue(term, out List<KeyValuePair<string, int>> postings))
        {
            return new List<string>(capacity: 0);
        }

        List<string> documents = new(capacity: postings.Count);
        foreach (KeyValuePair<string, int> posting in postings)
        {
            documents.Add(posting.Key);
        }

        return documents;
    }
}
```
</details>
<details><summary>Method ordering hierarchy example using YAML</summary>

```yaml
class SessionController:
  # log-in sub-tree
  LogIn public method:
    Authenticate private method:
    CreateSession private method:
  # log out sub-tree
  LogOut public method:
    DeleteSession private method:
  # common
  PrepareClient private method:
```
</details>
<details><summary>Method ordering code example</summary>

```csharp
public class SessionController
{
    // log-in sub-tree

    public ISession LogIn(ICredentials credentials)
    {
        IAuthClient client = PrepareClient();
        Authenticate(client, credentials);
        return CreateSession(client, credentials);
    }

    private void Authenticate(IAuthClient client, ICredentials credentials) {}

    private ISession CreateSession(IAuthClient client, ICredentials credentials) {}

    // log-out subtree

    public void LogOut()
    {
        IAuthClient client = PrepareClient();
        DeleteSession(client, Context.CurrentCredentials);
    }

    private void DeleteSession(IAuthClient client, ICredentials credentials) {}

    // common

    private IAuthClient PrepareClient() {}
}
```

</details>
<details><summary>Parameter ordering code example</summary>

```csharp
// input is strictly an input parameter, so it is in the beginning
// log gets changed in the implementation
// result is an out parameter, so it is at the end
public bool TryDoSomething(int input, List<string> log, out int result)
{}
```

</details>
