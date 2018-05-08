### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Karty strumienia WinRT nie długie wywołania FlushAsync automatycznie przy zamknięciu

|   |   |
|---|---|
|Szczegóły|Aplikacje ze Sklepu Windows kart strumienia środowiska wykonawczego systemu Windows nie jest już wywołać metodę FlushAsync z metody Dispose.|
|Sugestia|Ta zmiana powinny być przezroczyste. Deweloperzy można przywrócić poprzednie pisanie kodu w następujący sposób:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

