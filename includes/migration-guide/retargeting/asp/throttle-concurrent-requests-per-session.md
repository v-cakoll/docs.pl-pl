### <a name="throttle-concurrent-requests-per-session"></a>Ograniczenie przepustowości równoczesnych żądań na sesję

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 wcześniej, ASP.NET sekwencyjnie wykonuje żądania z tego samego identyfikatora sesji i ASP.NET zawsze wystawia Sessionid za pomocą plików cookie domyślnie. Jeśli strona zajmuje dużo czasu na odpowiedź, znacznie zmniejszy to wydajność serwera tylko przez naciśnięcie klawisza F5 w przeglądarce. Ta poprawka dodaliśmy licznik do śledzenia żądań w kolejce i kończenia żądania przekroczeniu określonego limitu. Wartością domyślną jest 50. Po osiągnięciu limitu ostrzeżenie jest rejestrowane w przypadku dziennika i odpowiedzi HTTP 500 mogą być rejestrowane w dzienniku usług IIS.|
|Sugestia|Aby przywrócić poprzednie działanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowe zachowanie.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowania|

