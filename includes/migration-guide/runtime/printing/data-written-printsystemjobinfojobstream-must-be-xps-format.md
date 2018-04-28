### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Dane zapisywane w PrintSystemJobInfo.JobStream musi być w formacie XPS

|   |   |
|---|---|
|Szczegóły|<xref:System.Printing.PrintSystemJobInfo.JobStream> Właściwość udostępnia strumienia zadania drukowania. Użytkownik może wysyłać dane pierwotne drukowania komponentów systemu operacyjnego przez zapisywanie do tego strumienia. W programie .NET Framework 4.5 w systemie Windows 8 i nowszych wersjach systemu operacyjnego Windows, w tym strumieniu danych musi być w formacie XPS jako strumień pakietu.|
|Sugestia|Do wyjściowego drukowania zawartości, wykonaj następujące czynności:<ul><li>Użyj <xref:System.Windows.Xps.XpsDocumentWriter> klasy do drukowania zawartości wyjściowej. Jest to zalecane alternatywnej.</li><li>Upewnij się, że dane wysłane do strumienia zwrócone przez <xref:System.Printing.PrintSystemJobInfo.JobStream> właściwość jest w formacie XPS jako strumień pakietu.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|

