### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Nazwa pliku dziennika utworzone przez metodę ObjectContext.CreateDatabase zmieniła się na odpowiada specyfikacji programu SQL Server

|   |   |
|---|---|
|Szczegóły|Gdy <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda jest wywoływana albo bezpośrednio lub za pomocą kodu pierwszy dostawca SqlClient oraz wartości AttachDBFilename w parametrach połączenia, tworzy plik dziennika o nazwie filename_log.ldf zamiast filename.ldf (gdzie filename jest nazwą Plik określony przez wartość AttachDBFilename). Ta zmiana usprawnia proces debugowania, dostarczając plik dziennika o nazwie zgodnej ze specyfikacjami programu SQL Server.|
|Sugestia|Jeśli nazwa pliku dziennika jest ważne dla aplikacji, aplikacji powinny zostać uaktualnione oczekiwać _log.ldf standardowy format nazwy pliku.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

