### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF, windows mają być renderowane bez przycinania, rozszerzając poza pojedynczy monitor

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 jest uruchomiona w systemie Windows 8 lub nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza jednym wyświetlana w przypadku wielu monitorów. To różni się od poprzednich wersji programu .NET Framework, która będzie obcina okna WPF, które wykracza poza pojedynczy ekran.|
|Sugestia|To zachowanie, (, kiedy należy przyciąć, czy nie) może być jawnie ustawione, za pomocą <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element <code>&lt;appSettings&gt;</code> w pliku konfiguracji aplikacji lub poprzez skonfigurowanie <code>EnableMultiMonitorDisplayClipping</code> właściwość przy uruchamianiu aplikacji.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

