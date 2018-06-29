### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows mają być renderowane bez przycinania, rozszerzając poza jednego monitora

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.6 uruchomione w systemie Windows 8 lub nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza pojedynczy wyświetlana w przypadku wielu monitora. To różni się od poprzedniej wersji programu .NET Framework, który będzie obcina WPF systemu windows, które wykracza poza jednym wyświetlania.|
|Sugestia|To zachowanie (kiedy należy przyciąć lub nie) może być wyraźnie ustawione, za pomocą <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element <code>&lt;appSettings&gt;</code> w pliku konfiguracji aplikacji lub przez ustawienie <code>EnableMultiMonitorDisplayClipping</code> właściwości podczas uruchamiania aplikacji.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|środowisko uruchomieniowe|

