### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kody błędów maxRequestLength lub maxReceivedMessageSize różnią się

|   |   |
|---|---|
|Szczegóły|Wiadomości w usłudze WCF web usług hostowanych w Internet Information Services (IIS) lub programem ASP.NET Development Server, które przekraczają maxRequestLength (w programie ASP.NET) lub maxReceivedMessageSize (w usłudze WCF) mają inny błąd kod stanu codeThe HTTP został zmieniony z 400 (nieprawidłowe żądanie ) na 413 (żądanie podmiotu zbyt duże) i komunikaty, które przekraczają maxRequestLength lub ustawienie maxReceivedMessageSize throw <xref:System.ServiceModel.ProtocolException?displayProperty=name> wyjątku. Obejmuje to przypadki, w których tryb transferu jest przesyłany strumieniowo.|
|Sugestia|Ta zmiana ułatwia debugowanie w przypadkach, gdy długość komunikatu przekracza dozwolone limity programu ASP.NET lub usługi WCF. Należy zmodyfikować każdy kod wykonujący przetwarzanie na podstawie kodu stanu HTTP 400.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

