---
title: 'Środki zaradcze: Usługi WCF i uwierzytelnianie certyfikatu'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f94cabb482a237395854fcdc91df476c567069c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599507"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="beacb-102">Środki zaradcze: Usługi WCF i uwierzytelnianie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="beacb-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="beacb-103">.NET Framework 4.6 dodaje protokołu TLS 1.1 i TLS 1.2, do listy domyślnych protokołu SSL usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="beacb-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="beacb-104">Gdy zarówno klienta, jak i serwera zainstalować program .NET Framework 4.6 lub nowszy, protokołu TLS 1.2 jest używana do negocjacji.</span><span class="sxs-lookup"><span data-stu-id="beacb-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="beacb-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="beacb-105">Impact</span></span>  
 <span data-ttu-id="beacb-106">Protokół TLS 1.2 nie obsługuje uwierzytelnianie certyfikatu MD5.</span><span class="sxs-lookup"><span data-stu-id="beacb-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="beacb-107">W rezultacie jeśli klient używa certyfikatu SSL, który używa algorytmu wyznaczania wartości skrótu MD5, klient WCF nie uda się nawiązać usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="beacb-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="beacb-108">Aby uzyskać więcej informacji, zobacz [środki zaradcze: Usługi WCF i uwierzytelnianie certyfikatu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="beacb-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="beacb-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="beacb-109">Mitigation</span></span>  
 <span data-ttu-id="beacb-110">Ten problem można obejść, czemu klienta programu WCF można nawiązywać połączenia z serwerem usługi WCF, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="beacb-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
- <span data-ttu-id="beacb-111">Zaktualizuj certyfikat, aby nie używać algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="beacb-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="beacb-112">Jest to zalecane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="beacb-112">This is the recommended solution.</span></span>  
  
- <span data-ttu-id="beacb-113">Jeśli dynamicznie powiązanie nie jest skonfigurowany w kodzie źródłowym, należy zaktualizować plik konfiguracji aplikacji do używania protokołu TLS 1.1 lub wcześniejszej wersji protokołu.</span><span class="sxs-lookup"><span data-stu-id="beacb-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="beacb-114">Dzięki temu można w dalszym ciągu używać certyfikatu przy użyciu algorytmu wyznaczania wartości skrótu MD5.</span><span class="sxs-lookup"><span data-stu-id="beacb-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="beacb-115">To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="beacb-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="beacb-116">Następujący plik konfiguracji ma następujące efekty:</span><span class="sxs-lookup"><span data-stu-id="beacb-116">The following configuration file does this:</span></span>  
  
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
  
- <span data-ttu-id="beacb-117">Jeśli wiązanie dynamiczne jest skonfigurowany w kodzie źródłowym, należy zaktualizować <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> właściwości, aby korzystała z protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub starszej wersji protokołu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="beacb-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="beacb-118">To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="beacb-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beacb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beacb-119">See also</span></span>

- [<span data-ttu-id="beacb-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="beacb-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
