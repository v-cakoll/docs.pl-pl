### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Karty strumienia WinRT nie są już wywoływać FlushAsync automatycznie przy zamykaniu

|   |   |
|---|---|
|Szczegóły|W aplikacjach Windows Store kart strumienia środowiska wykonawczego Windows nie jest już wywołać metodę FlushAsync z metody Dispose.|
|Sugestia|Ta zmiana powinny być przezroczyste. Deweloperzy mogą przywrócić poprzednie zachowanie przez pisanie kodu w następujący sposób:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

