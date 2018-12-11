### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Domyślny algorytm skrótu dla WPF przez kompilator znaczników jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|WPF MarkupCompiler udostępnia usługi kompilacji dla plików znaczników XAML.  W .NET Framework 4.7.1 i wcześniejszych wersjach domyślny algorytm skrótu używany dla sum kontrolnych było SHA1. Ze względu na ostatnie obawy związane z bezpieczeństwem z SHA1, to ustawienie domyślne zostało zmienione na SHA256 począwszy od programu .NET Framework 4.7.2.  Ta zmiana ma wpływ na wszystkie generowanie sum kontrolnych dla plików znaczników podczas kompilacji.|
|Sugestia|Deweloper, który jest przeznaczony dla .NET Framework 4.7.2 lub nowszej oraz profesjonalistą przywrócić zachowanie wyznaczania wartości skrótu SHA1, należy ustawić następujące flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Dla deweloperów, który chce korzystać z SHA256 wyznaczania wartości skrótu, podczas określania wartości docelowej framework w wersji starszej niż .NET 4.7.2 należy ustawić poniżej AppContext flagi.  Należy pamiętać, że zainstalowana wersja programu .NET Framework, musi być 4.7.2 lub nowszej.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.7.2|
|Typ|Przekierowanie|

