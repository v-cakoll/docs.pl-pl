### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Usuń Ssl3 z WCF TransportDefaults

|   |   |
|---|---|
|Szczegóły|Używając NetTcp z zabezpieczeniami transportu i typu poświadczeń certyfikatu protokołu SSL 3 nie jest już domyślnym protokołem używane do negocjowania bezpiecznego połączenia. W większości przypadków należy bez wpływu na istniejące aplikacje jako protokołu TLS 1.0 ma zawsze uwzględnionych na liście protokół dla NetTcp. Wszyscy istniejący klienci powinno być możliwe do negocjowania połączenia przy użyciu na co najmniej TLS1.0.|
|Sugestia|Jeśli wymagana jest Ssl3, użyj jednej z następujących mechanizmów konfiguracji do dodania do listy protokołów wynegocjowanym Ssl3.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; sekcji &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

