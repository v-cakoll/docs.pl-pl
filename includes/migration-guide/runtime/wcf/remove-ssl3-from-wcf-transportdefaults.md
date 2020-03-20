---
ms.openlocfilehash: d75eff2d2a43ab4488577014ec43a9826b2b2924
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237847"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Usuń Ssl3 z WCF TransportDefaults

|   |   |
|---|---|
|Szczegóły|W przypadku korzystania z protokołu NetTcp z zabezpieczeniami transportu i certyfikatem typu poświadczeń protokół SSL 3 nie jest już domyślnym protokołem używanym do negocjowania bezpiecznego połączenia. W większości przypadków nie powinno być żadnego wpływu na istniejące aplikacje, ponieważ protokół TLS 1.0 zawsze był uwzględniony na liście protokołów dla protokołu NetTcp. Wszyscy istniejący klienci powinni mieć możliwość negocjowania połączenia przy użyciu co najmniej protokołu TLS1.0.|
|Sugestia|Jeśli wymagany jest protokół Ssl3, użyj jednego z następujących mechanizmów konfiguracji, aby dodać Ssl3 do listy wynegocjowanych protokołów.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; &lt;sekcji customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
