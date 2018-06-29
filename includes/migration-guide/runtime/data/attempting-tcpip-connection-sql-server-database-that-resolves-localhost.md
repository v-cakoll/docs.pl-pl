### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Próba połączenia TCP/IP do bazy danych programu SQL Server, który jest rozpoznawany jako `localhost` nie powiedzie się

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.6 i 4.6.1 nawiązać połączenie TCP/IP z bazy danych programu SQL Server, który jest rozpoznawany jako <code>localhost</code> zakończy się niepowodzeniem z powodu błędu, &quot;wystąpił błąd związany z siecią lub wystąpieniem podczas ustanawiania połączenia z programem SQL Server. Serwer nie został znaleziony lub był niedostępny. Sprawdź, czy nazwa wystąpienia jest poprawna i czy programu SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: interfejsy sieciowe programu SQL, błąd: 26 - błąd podczas lokalizowania określonego serwera/wystąpienia)&quot;|
|Sugestia|Ten problem został rozwiązany i poprzednie przywrócić w programie .NET Framework 4.6.2. Aby nawiązać połączenie rozwiązań programu SQL Server, który jest rozpoznawany jako <code>localhost</code>, przeprowadź uaktualnienie do programu .NET Framework 4.6.2.|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|środowisko uruchomieniowe|

