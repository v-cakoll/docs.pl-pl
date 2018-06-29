### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kody błędów maxRequestLength lub maxReceivedMessageSize są różne

|   |   |
|---|---|
|Szczegóły|Wiadomości w programie WCF web usług hostowanych usług Internet Information Services (IIS) lub ASP.NET Development Server, które przekraczają maxRequestLength (w programie ASP.NET) lub maxReceivedMessageSize (w programie WCF) ma inny błąd kod stanu codeThe HTTP zmienił się od 400 (nieprawidłowe żądanie ) 413 (żądania jednostki zbyt duża liczba godzin) i komunikaty, które przekraczają maxRequestLength lub ustawienie maxReceivedMessageSize throw <xref:System.ServiceModel.ProtocolException?displayProperty=name> wyjątku. Dotyczy to przypadków, w których jest przesyłane strumieniowo tryb transferu.|
|Sugestia|Ta zmiana umożliwia debugowanie w przypadkach, gdy długość komunikatu przekracza limity dozwolone przez ASP.NET lub usługi WCF. Należy zmodyfikować każdy kod przetwarza oparte na kod stanu HTTP 400.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|

