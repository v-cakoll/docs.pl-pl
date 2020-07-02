---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621214"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Usuń Ssl3 z TransportDefaults WCF

#### <a name="details"></a>Szczegóły

W przypadku korzystania z programu NetTcp z zabezpieczeniami transportu i typem poświadczeń certyfikatu protokół SSL 3 nie jest już domyślnym protokołem używanym do negocjowania bezpiecznego połączenia. W większości przypadków nie powinno się mieć wpływu na istniejące aplikacje, ponieważ protokół TLS 1,0 został zawsze uwzględniony na liście protokołów dla NetTcp. Wszyscy istniejący klienci powinni mieć możliwość negocjowania połączenia przy użyciu co najmniej protokołu TLS 1.0.

#### <a name="suggestion"></a>Sugestia

Jeśli Ssl3 jest wymagany, użyj jednego z poniższych mechanizmów konfiguracyjnych, aby dodać Ssl3 do listy protokołów negocjowanych.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[ &lt; sslStreamSecurity &gt; sekcja elementu &lt; CustomBinding &gt; ] ~/docs/Framework/Configure-Apps/File-Schema/WCF/sslStreamSecurity.MD)</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
