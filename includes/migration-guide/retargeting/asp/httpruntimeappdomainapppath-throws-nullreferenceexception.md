### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath zgłasza NullReferenceException

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2, zgłasza wyjątek środowiska uruchomieniowego <code>T:System.NullReferenceException</code> podczas pobierania <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> wartość zawierającą znaki null. W programie .NET Framework 4.6.1 i wcześniejszych wersjach, zgłasza wyjątek środowiska uruchomieniowego <code>T:System.ArgumentNullException</code>.|
|Sugestia|Należy albo wykonaj odpowiedzieć na tej zmiany:<ul><li>Obsługa <code>T:System.NullReferenceException</code> Jeśli aplikacja jest uruchomiona na .NET Framework 4.6.2.</li><li>Uaktualnij do 4.7 Framework .NET, która przywraca poprzednie i zgłasza <code>T:System.ArgumentNullException</code>.</li></ul>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

