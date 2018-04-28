### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nie są wyliczenia przez profilowania

|   |   |
|---|---|
|Szczegóły|W v4.5.1 .NET Framework, interfejsu API profilowania <code>RootReferences2()</code> niepoprawnie nigdy nie zwraca <code>COR_PRF_GC_ROOT_HANDLE</code> (są one zwracane jako <code>COR_PRF_GC_ROOT_OTHER</code> zamiast niego). Tego problemu w programie .NET Framework 4.6.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

