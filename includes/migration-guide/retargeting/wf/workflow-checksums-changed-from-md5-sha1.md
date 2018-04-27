### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Sum kontrolnych przepływu pracy zmienione od MD5, SHA1

|   |   |
|---|---|
|Szczegóły|Aby zapewnić obsługę debugowania za pomocą programu Visual Studio, środowiska uruchomieniowego przepływu pracy generuje sumy kontrolnej dla wystąpienia przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu. .NET Framework 4.6.2 i starszych wersjach mieszania sum kontrolnych przepływu pracy używane algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS. Począwszy od .NET Framework 4.7, algorytm jest SHA1. Jeśli kod ma utrwalone tych sum kontrolnych, będą niezgodne.|
|Sugestia|Jeśli kod nie mógł załadować wystąpienia przepływu pracy z powodu błędu sumy kontrolnej, spróbuj ustawienie <code>AppContext</code> przełącznika &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; na wartość true. W kodzie:<pre><code class="language-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Lub w konfiguracji:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7|
|Typ|Przekierowania|

