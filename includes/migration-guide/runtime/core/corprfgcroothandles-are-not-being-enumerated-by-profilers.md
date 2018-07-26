### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>Nie są wyliczane COR_PRF_GC_ROOT_HANDLEs przez profilery

|   |   |
|---|---|
|Szczegóły|W v4.5.1 .NET Framework, interfejsie API profilowania <code>RootReferences2()</code> niepoprawnie nigdy nie zwraca <code>COR_PRF_GC_ROOT_HANDLE</code> (są zwracane w postaci <code>COR_PRF_GC_ROOT_OTHER</code> zamiast). Ten problem jest rozwiązany, począwszy od programu .NET Framework 4.6.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

