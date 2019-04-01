---
ms.openlocfilehash: ae3766e2045b5834fbf6ea20415942413b1590c0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761412"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Usługi WCF NETTCP za pomocą zabezpieczeń SSL i uwierzytelniania certyfikatu MD5

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.6 dodaje protokołu TLS 1.1 i TLS 1.2 do domyślnej listy protokołu SSL usługi WCF. Gdy zarówno klienta, jak i serwera zainstalować program .NET Framework 4.6 lub nowszy, protokołu TLS 1.2 jest używana do negocjacji. Protokół TLS 1.2 nie obsługuje uwierzytelnianie certyfikatu MD5. W rezultacie jeśli klient używa certyfikatu MD5, klient WCF zakończy się niepowodzeniem połączyć się z usługą WCF.|
|Sugestia|Ten problem można obejść, czemu klienta programu WCF można nawiązywać połączenia z serwerem usługi WCF, wykonując następujące czynności:<ul><li>Zaktualizuj certyfikat, aby nie używać algorytmu MD5. Jest to zalecane rozwiązanie.</li><li>Jeśli dynamicznie powiązanie nie jest skonfigurowany w kodzie źródłowym, należy zaktualizować plik konfiguracji aplikacji do używania protokołu TLS 1.1 lub wcześniejszej wersji protokołu. Dzięki temu można w dalszym ciągu używać certyfikatu przy użyciu algorytmu wyznaczania wartości skrótu MD5.</li></ul> <blockquote> [!WARNING] To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</blockquote> Następujący plik konfiguracji ma następujące efekty:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Jeśli wiązanie dynamiczne jest skonfigurowany w kodzie źródłowym, należy zaktualizować <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> właściwości, aby korzystała z protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> lub starszej wersji protokołu w kodzie źródłowym.</li></ul> <blockquote> [!WARNING] To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</blockquote> |
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

