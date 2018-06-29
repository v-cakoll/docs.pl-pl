### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Przepływ pracy SQL trwałości dodaje klucz podstawowy klastrów i nie zezwala na wartości null w niektórych kolumnach

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7, tabele utworzone dla SQL magazynu wystąpienia przepływu pracy (SWIS) za pomocą skryptu SqlWorkflowInstanceStoreSchema.sql użyć klastrowanego kluczy podstawowych. W związku z tym nie obsługują tożsamości <code>null</code> wartości. Operacja SWIS nie ma wpływu na tę zmianę. Aktualizacje zostały wprowadzone do obsługi replikacji transakcyjnej programu SQL Server.|
|Sugestia|Pliku SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql musi zostać zastosowana do istniejących instalacji, aby to zmienić. Nowe instalacje bazy danych ma automatycznie zmiany.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|środowisko uruchomieniowe|

