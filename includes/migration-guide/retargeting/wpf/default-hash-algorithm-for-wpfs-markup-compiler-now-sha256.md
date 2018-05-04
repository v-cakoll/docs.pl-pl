### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Domyślny algorytm skrótu dla kompilatora znaczników w WPF jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|WPF MarkupCompiler udostępnia usługi kompilacji dla plików XAML znaczników.  W .NET Framework 4.7.1 i starszych wersjach domyślny algorytm skrótu używany dla sum kontrolnych było SHA1. Ze względów bezpieczeństwa ostatnie z SHA1, SHA256 została zmieniona to ustawienie domyślne w programie .NET Framework 4.7.2.  Ta zmiana wpływa na wszystkie generowania sumy kontrolnej plików znaczników podczas kompilacji.|
|Sugestia|Deweloper, który jest przeznaczony dla platformy .NET Framework 4.7.2 lub nowszej i chce, aby powrócić do zachowania wyznaczania wartości skrótu SHA1 musi być ustawione następujące flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Deweloper, który chce korzystać z skrótu SHA256 podczas określania wartości docelowej wersji struktury poniżej .NET 4.7.2 należy ustawić poniżej flagi AppContext.  Należy pamiętać, że zainstalowana wersja programu .NET Framework musi być 4.7.2 lub nowszej.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.7.2|
|Typ|Przekierowania|

