---
ms.openlocfilehash: 77d4978df76735d11f63c7118c1b4708b5b85502
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236075"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Usuwanie Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Szczegóły|Używając NetTcp za pomocą zabezpieczeń transportu i poświadczeń typu certyfikatu protokołu SSL 3 nie jest już domyślny protokół używany do negocjowania bezpiecznego połączenia. W większości przypadków należy bez wpływu na istniejące aplikacje jako protokół TLS 1.0 zawsze została uwzględniona na liście protokół dla NetTcp. Wszyscy istniejący klienci powinno być możliwe negocjowania połączenia przy użyciu w co najmniej TLS1.0.|
|Sugestia|Jeśli wymagana jest Ssl3, umożliwia jedną z następujących mechanizmów konfiguracji Dodawanie Ssl3 do listy wynegocjowanym protokołów.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[\<transport > z \<netTcpBinding >](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; części &lt;customBinding&gt;](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
