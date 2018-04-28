### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom zwraca nieprawidłowy wynik ogólny zmiennych z ograniczeniami

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 <xref:System.Type.IsAssignableFrom(System.Type)> niepoprawnie zwróci <code>false</code> we wszystkich przypadkach dla niektórych typów ogólnych z ograniczeniami.|
|Sugestia|Ten problem został rozwiązany w ramach obsługi aktualizacji. Zaktualizuj .NET Framework 4.5, lub uaktualnienia programu .NET Framework 4.5.1 lub nowszej, aby rozwiązać ten problem. Alternatywnie należy unikać IsAssignableFrom z typów ogólnych, które mają ograniczenia dotyczące parametrów ogólnych. Interfejsy API odbicia może służyć jako obejścia.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|Analizatory|<ul><li>CD0089</li></ul>|

