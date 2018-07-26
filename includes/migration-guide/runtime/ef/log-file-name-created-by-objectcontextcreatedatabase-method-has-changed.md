### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Nazwa pliku dziennika, tworzone przez metodę ObjectContext.CreateDatabase został zmieniony na zgodne ze specyfikacjami programu SQL Server

|   |   |
|---|---|
|Szczegóły|Gdy <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda jest wywoływana albo bezpośrednio lub przy użyciu najpierw kod dzięki dostawcy SqlClient i wartość AttachDBFilename w ciągu połączenia, tworzy plik dziennika o nazwie filename_log.ldf zamiast filename.ldf (gdzie nazwa_pliku to nazwa Plik określony przez wartość AttachDBFilename). Ta zmiana usprawnia proces debugowania, dostarczając plik dziennika o nazwie zgodnej ze specyfikacjami programu SQL Server.|
|Sugestia|Jeśli nazwa pliku dziennika jest ważne w przypadku aplikacji, aplikacji powinny zostać uaktualnione w oczekiwany format nazwy pliku _log.ldf standardowych.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

