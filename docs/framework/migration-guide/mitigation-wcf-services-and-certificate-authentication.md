---
title: "Ograniczenie: Usługi WCF i uwierzytelnianie certyfikatu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b106dd7a6853e5af6aa53bcc8a66ae1d949f0f0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="9cfdf-102">Ograniczenie: Usługi WCF i uwierzytelnianie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="9cfdf-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="9cfdf-103">.NET Framework 4.6 dodaje protokołu TLS 1.1 i TLS 1.2, do listy domyślnych protokołu SSL usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="9cfdf-104">Jeśli klienta i na serwerze zainstalować program .NET Framework 4.6 lub nowszy, protokołu TLS 1.2 jest używany dla negocjacji.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9cfdf-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="9cfdf-105">Impact</span></span>  
 <span data-ttu-id="9cfdf-106">Protokołu TLS 1.2 nie obsługuje uwierzytelnianie certyfikatu MD5.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="9cfdf-107">W związku z tym jeśli klient używa certyfikatu SSL, który używa algorytmu wyznaczania wartości skrótu MD5, klient WCF nie może się połączyć z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="9cfdf-108">Aby uzyskać więcej informacji, zobacz [środki zaradcze: usługi WCF i uwierzytelnianie certyfikatu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9cfdf-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9cfdf-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="9cfdf-109">Mitigation</span></span>  
 <span data-ttu-id="9cfdf-110">Można obejść ten problem, tak aby klienta WCF można połączenie z serwerem usługi WCF, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9cfdf-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="9cfdf-111">Zaktualizuj certyfikat, aby nie używać algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="9cfdf-112">Jest to zalecane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="9cfdf-113">Jeśli w kodzie źródłowym nie skonfigurowano dynamicznie powiązanie, należy zaktualizować pliku konfiguracji aplikacji do użycia protokołu TLS 1.1 lub starszej wersji protokołu.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="9cfdf-114">Dzięki temu można nadal używać certyfikatu przy użyciu algorytmu wyznaczania wartości skrótu MD5.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="9cfdf-115">To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="9cfdf-116">Następujący plik konfiguracji robi to:</span><span class="sxs-lookup"><span data-stu-id="9cfdf-116">The following configuration file does this:</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="9cfdf-117">Jeśli powiązanie jest skonfigurowane dynamicznie w kodzie źródłowym, należy zaktualizować <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> właściwości do użycia protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub starsza wersja protokołu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="9cfdf-118">To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="9cfdf-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfdf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cfdf-119">See Also</span></span>  
 [<span data-ttu-id="9cfdf-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9cfdf-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
