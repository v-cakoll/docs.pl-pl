### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Próba nawiązania połączenia protokołu TCP/IP w bazie danych SQL Server, który jest rozpoznawany jako `localhost` kończy się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 i 4.6.1 nawiązać połączenie TCP/IP z bazy danych programu SQL Server, który jest rozpoznawany jako <code>localhost</code> zakończy się niepowodzeniem z powodu błędu, &quot;wystąpił błąd związany z siecią lub wystąpieniem podczas nawiązywania połączenia z programem SQL Server. Serwer nie został znaleziony lub jest on niedostępny. Sprawdź, czy nazwa wystąpienia jest prawidłowa i że program SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: interfejsy sieciowe programu SQL, błąd: 26 — Błąd lokalizowania określonego Server/wystąpienie)&quot;|
|Sugestia|Ten problem został rozwiązany i przywrócić poprzednie zachowanie w programie .NET Framework 4.6.2. Połączyć się z opcjami programu SQL Server, który jest rozpoznawany jako <code>localhost</code>Przeprowadź uaktualnienie do programu .NET Framework 4.6.2.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

