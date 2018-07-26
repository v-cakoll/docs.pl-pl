### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad nie należy używać w pliku niestandardowego możliwości, ponieważ jest on obecnie możliwości przeglądarki

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, iPad jest identyfikatora w pliku możliwości uzyskiwania informacji na temat przeglądarki ASP.NET domyślne z więc nie powinien on używany w pliku niestandardowego możliwości|
|Sugestia|Jeżeli wymagane są funkcje właściwe dla tabletu iPad, należy zmodyfikować zachowanie dla urządzenia iPad, ustawiając możliwości na refID wstępnie zdefiniowanych bram &quot;IPad&quot; zamiast, generując nowy &quot;IPad&quot; identyfikator według agenta użytkownika dopasowanie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

