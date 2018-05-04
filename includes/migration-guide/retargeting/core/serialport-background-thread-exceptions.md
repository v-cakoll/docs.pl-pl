### <a name="serialport-background-thread-exceptions"></a>Wyjątki wątku tła portu SerialPort

|   |   |
|---|---|
|Szczegóły|Utworzone z wątki w tle <xref:System.IO.Ports.SerialPort> strumieni nie jest już zakończenie procesu, gdy wyjątek systemu operacyjnego. <br/>W aplikacjach przeznaczonych dla platformy .NET Framework 4.7 i wcześniejsze wersje, proces jest zakończony, gdy system operacyjny jest zwracany wyjątek w wątku w tle utworzonych za pomocą <xref:System.IO.Ports.SerialPort> strumienia. <br/>W aplikacjach czy docelowej platformy .NET Framework 4.7.1 lub nowszej wersji, wątki w tle poczekaj zdarzeń systemu operacyjnego dotyczące active portu szeregowego i może ulec awarii w niektórych przypadkach, takich jak nagłym usunięcie z portu szeregowego.|
|Sugestia|W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 możesz zrezygnować z obsługą wyjątków, jeśli nie jest pożądane, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojego <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji, które odnoszą się do wcześniejszych wersji programu .NET Framework, ale Uruchom w programie .NET Framework 4.7.1 lub później, można włączyć do obsługi, dodając następujące polecenie, aby wyjątków <code>&lt;runtime&gt;</code> części Twojego <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

