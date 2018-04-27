### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializacja obiektów MailMessage serializowany w .NET Framework 4.5 może zakończyć się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 <xref:System.Web.Mail.MailMessage> obiektów może zawierać znaki inne niż ASCII. W .NET Framework 4 obsługiwane są tylko znaki ASCII. <xref:System.Web.Mail.MailMessage> w obszarze programu .NET Framework 4 nie można rozszeregować obiektów, które zawierają znaki spoza zestawu ASCII i które są serializowane w .NET Framework 4.5 lub nowszej.|
|Sugestia|Upewnij się, że kod zawiera Obsługa wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

