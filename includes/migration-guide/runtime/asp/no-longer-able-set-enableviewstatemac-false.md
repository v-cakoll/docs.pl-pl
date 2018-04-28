### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Nie może ustawić EnableViewStateMac false

|   |   |
|---|---|
|Szczegóły|Program ASP.NET nie jest już umożliwia deweloperom określ <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Widok stanu kod uwierzytelniania wiadomości (MAC) obecnie jest wymuszany dla wszystkich żądań o stan widoku osadzonych. Tylko te aplikacje, które jawnie ustaw dla właściwości EnableViewStateMac <code>false</code> dotyczy problem.|
|Sugestia|EnableViewStateMac musi być założono, że to PRAWDA, a wynikowy błędy MAC należy usunąć (zgodnie z objaśnieniem w [w tych wskazówkach](https://support.microsoft.com/kb/2915218), który zawiera wiele rozdzielczości w zależności od tego, co jest przyczyną błędów MAC specyfice).|
|Zakres|Główne|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

