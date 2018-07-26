### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogi MEF implementować interfejs IEnumerable i w związku z tym może już służyć do tworzenia serializatora

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, implementować interfejs IEnumerable katalogach MEF i dlatego nie będzie można utworzyć programu szeregującego (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu). Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.|
|Sugestia|Nie można korzystać MEF do tworzenia serializatora|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

