### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath zgłasza obiektu NullReferenceException

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2, środowisko wykonawcze zgłasza <code>T:System.NullReferenceException</code> podczas pobierania <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> wartość, która zawiera znaki null. W .NET Framework 4.6.1 i wcześniejszych wersjach, środowisko wykonawcze zgłasza <code>T:System.ArgumentNullException</code>.|
|Sugestia|Możesz wykonać jedną z działaniami, aby odpowiedzieć na tę zmianę:<ul><li>Obsługa <code>T:System.NullReferenceException</code> Jeśli aplikacja jest uruchomiona w środowisku .NET Framework 4.6.2.</li><li>Uaktualnianie do programu .NET Framework 4.7, który przywraca poprzednie zachowanie i zgłasza <code>T:System.ArgumentNullException</code>.</li></ul>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

