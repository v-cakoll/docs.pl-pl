### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogi MEF implementować interfejs IEnumerable i dlatego nie można utworzyć serializatora

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, wykazy MEF implementować interfejs IEnumerable i dlatego nie można utworzyć serializatora (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu). Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.|
|Sugestia|Aby utworzyć element serializujący dalszego korzystania MEF|
|Zakres|Główne|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|

