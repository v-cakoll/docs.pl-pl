### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad nie należy używać w niestandardowych możliwości pliku, ponieważ jest on obecnie możliwości przeglądarki

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, iPad jest identyfikatorem w pliku możliwości przeglądarki ASP.NET domyślne, z dzięki nie powinny być one używane w pliku możliwości niestandardowych|
|Sugestia|Jeśli wymagane są możliwości specyficznych dla urządzeń iPad, należy zmodyfikować zachowanie iPad przez ustawienie możliwości refID wstępnie zdefiniowane bramy &quot;IPad&quot; zamiast generując nowy &quot;IPad&quot; identyfikator przez agenta użytkownika dopasowanie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

