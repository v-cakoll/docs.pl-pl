---
ms.openlocfilehash: 9e8fdb54bddc32c08adbe114e2d46e2508585bc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858515"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Usługi WCF korzystające z protokołu NETTCP z zabezpieczeniami SSL i uwierzytelnianiem certyfikatów MD5

|   |   |
|---|---|
|Szczegóły|Program .NET Framework 4.6 dodaje protokoły TLS 1.1 i TLS 1.2 do listy domyślnych protokołów SSL WCF. Gdy maszyny klienckie i serwerowe mają zainstalowany program .NET Framework 4.6 lub nowszy, do negocjacji jest używany tls 1.2. TLS 1.2 nie obsługuje uwierzytelniania certyfikatu MD5. W rezultacie jeśli klient używa certyfikatu MD5, klient WCF nie połączy się z usługą WCF.|
|Sugestia|Można obejść ten problem, tak aby klient WCF można połączyć się z serwerem WCF wykonując dowolną z następujących czynności:<ul><li>Zaktualizuj certyfikat, aby nie używać algorytmu MD5. Jest to zalecane rozwiązanie.</li><li>Jeśli powiązanie nie jest dynamicznie skonfigurowane w kodzie źródłowym, zaktualizuj plik konfiguracyjny aplikacji, aby używał protokołu TLS 1.1 lub starszej wersji protokołu. Dzięki temu można nadal używać certyfikatu z algorytmem mieszania MD5.</li></ul> <blockquote> [!WARNING] To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.</blockquote> Następujący plik konfiguracyjny robi to:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>Jeśli powiązanie jest dynamicznie skonfigurowane w <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> kodzie źródłowym, zaktualizuj właściwość, aby użyć protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> lub wcześniejszej wersji protokołu w kodzie źródłowym.</li></ul> <blockquote> [!WARNING] To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.</blockquote> |
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
