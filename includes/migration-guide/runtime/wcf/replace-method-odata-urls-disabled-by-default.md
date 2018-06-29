### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Metoda Zamień w adresach URL OData jest domyślnie wyłączona

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, Zastąp metody w adresach URL OData jest domyślnie wyłączona. Wyłączenie Zamień OData (teraz domyślnie), wszystkie żądania użytkowników, łącznie z funkcjami Zamień, (które są rzadko) zakończy się niepowodzeniem.|
|Sugestia|Jeśli wymagana jest metoda Zamień (czyli rzadko), można ją ponownie włączyć za pomocą ustawień konfiguracji (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Jednak metoda włączone Zamień można otworzyć luk w zabezpieczeniach i powinien być używany tylko po dokładne przeglądu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

