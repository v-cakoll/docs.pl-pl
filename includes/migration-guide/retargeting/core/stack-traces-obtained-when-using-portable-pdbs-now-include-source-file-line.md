### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Śladów stosu uzyskać, korzystając z plików przenośnych PDB teraz zawierają informacje plików i wierszy źródła, jeśli jest to wymagane

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7.2, śladów stosu uzyskane w przypadku korzystania z plików przenośnych PDB zawierają źródła plików i wierszy informacje na żądanie. W wersjach wcześniejszych niż .NET Framework 4.7.2, plik źródłowy i wiersza informacji byłyby niedostępne podczas korzystania z plików przenośnych PDB nawet wtedy, gdy jawnie żądanie.|
|Sugestia|Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.2, możesz zrezygnować z informacji źródłowych plików i wierszy podczas przy użyciu plików przenośnych PDB, jeśli nie jest pożądane, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojego <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji, które odnoszą się do wcześniejszych wersji programu .NET Framework, ale Uruchom w programie .NET Framework 4.7.2 lub później, musisz zgodzić się na informacji źródłowych plików i wierszy podczas korzystania z plików przenośnych PDB, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> sekcji Twojego<code>app.config</code>pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

