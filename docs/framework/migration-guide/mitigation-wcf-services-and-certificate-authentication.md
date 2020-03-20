---
title: 'Łagodzenie: Usługi WCF i uwierzytelnianie certyfikatów'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: 8c8493efa2c3223809ad87e01e3faddaea859ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457795"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="84b58-102">Łagodzenie: Usługi WCF i uwierzytelnianie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="84b58-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="84b58-103">Program .NET Framework 4.6 dodaje protokoły TLS 1.1 i TLS 1.2 do domyślnej listy protokołu SSL WCF.</span><span class="sxs-lookup"><span data-stu-id="84b58-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="84b58-104">Gdy maszyny klienckie i serwerowe mają zainstalowany program .NET Framework 4.6 lub nowszy, do negocjacji jest używany tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="84b58-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="84b58-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="84b58-105">Impact</span></span>

<span data-ttu-id="84b58-106">TLS 1.2 nie obsługuje uwierzytelniania certyfikatu MD5.</span><span class="sxs-lookup"><span data-stu-id="84b58-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="84b58-107">W rezultacie jeśli klient używa certyfikatu SSL, który używa MD5 dla algorytmu mieszania, klient WCF nie może połączyć się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="84b58-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="84b58-108">Aby uzyskać więcej informacji, zobacz [Łagodzenie: Usługi WCF i uwierzytelnianie certyfikatów](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="84b58-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="84b58-109">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="84b58-109">Mitigation</span></span>

<span data-ttu-id="84b58-110">Można obejść ten problem, tak aby klient WCF można połączyć się z serwerem WCF wykonując dowolną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="84b58-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="84b58-111">Zaktualizuj certyfikat, aby nie używać algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="84b58-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="84b58-112">Jest to zalecane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="84b58-112">This is the recommended solution.</span></span>

- <span data-ttu-id="84b58-113">Jeśli powiązanie nie jest dynamicznie skonfigurowane w kodzie źródłowym, zaktualizuj plik konfiguracyjny aplikacji, aby używał protokołu TLS 1.1 lub starszej wersji protokołu.</span><span class="sxs-lookup"><span data-stu-id="84b58-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="84b58-114">Dzięki temu można nadal używać certyfikatu z algorytmem mieszania MD5.</span><span class="sxs-lookup"><span data-stu-id="84b58-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="84b58-115">To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="84b58-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="84b58-116">Następujący plik konfiguracyjny robi to:</span><span class="sxs-lookup"><span data-stu-id="84b58-116">The following configuration file does this:</span></span>

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
      </system.serviceModel>
  </configuration>
  ```

- <span data-ttu-id="84b58-117">Jeśli powiązanie jest dynamicznie skonfigurowane w <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> kodzie źródłowym, zaktualizuj właściwość, aby użyć protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub wcześniejszej wersji protokołu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="84b58-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="84b58-118">To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="84b58-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="84b58-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84b58-119">See also</span></span>

- [<span data-ttu-id="84b58-120">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="84b58-120">Application compatibility</span></span>](application-compatibility.md)
