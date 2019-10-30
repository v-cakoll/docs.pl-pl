---
title: 'Środki zaradcze: usługi WCF i uwierzytelnianie certyfikatów'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14fafa68e55ae7c1f3b6672b150cd0b149a3ffcd
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039551"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="7f346-102">Środki zaradcze: usługi WCF i uwierzytelnianie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="7f346-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="7f346-103">.NET Framework 4,6 dodaje protokoły TLS 1,1 i TLS 1,2 do listy domyślnych protokołu SSL WCF.</span><span class="sxs-lookup"><span data-stu-id="7f346-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="7f346-104">Gdy komputery klienckie i serwery mają zainstalowany .NET Framework 4,6 lub nowszy, protokół TLS 1,2 jest używany do negocjacji.</span><span class="sxs-lookup"><span data-stu-id="7f346-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="7f346-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="7f346-105">Impact</span></span>

<span data-ttu-id="7f346-106">Protokół TLS 1,2 nie obsługuje uwierzytelniania certyfikatów MD5.</span><span class="sxs-lookup"><span data-stu-id="7f346-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="7f346-107">W związku z tym, jeśli klient korzysta z certyfikatu SSL, który używa algorytmu MD5 do mieszania, klient programu WCF nie będzie mógł nawiązać połączenia z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="7f346-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="7f346-108">Aby uzyskać więcej informacji, zobacz [ograniczanie: usługi WCF i uwierzytelnianie certyfikatów](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7f346-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="7f346-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="7f346-109">Mitigation</span></span>

<span data-ttu-id="7f346-110">Ten problem można obejść, aby klient programu WCF mógł połączyć się z serwerem WCF, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7f346-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="7f346-111">Zaktualizuj certyfikat, aby nie używał algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="7f346-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="7f346-112">Jest to zalecane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="7f346-112">This is the recommended solution.</span></span>

- <span data-ttu-id="7f346-113">Jeśli powiązanie nie jest konfigurowane dynamicznie w kodzie źródłowym, zaktualizuj plik konfiguracji aplikacji tak, aby korzystał z protokołu TLS 1,1 lub starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="7f346-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="7f346-114">Dzięki temu można nadal używać certyfikatu z algorytmem wyznaczania wartości skrótu MD5.</span><span class="sxs-lookup"><span data-stu-id="7f346-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="7f346-115">To obejście nie jest zalecane, ponieważ certyfikat z algorytmem wyznaczania wartości skrótu MD5 jest uznawany za niezabezpieczony.</span><span class="sxs-lookup"><span data-stu-id="7f346-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="7f346-116">Następujący plik konfiguracji wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7f346-116">The following configuration file does this:</span></span>

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

- <span data-ttu-id="7f346-117">Jeśli powiązanie jest konfigurowane dynamicznie w kodzie źródłowym, zaktualizuj właściwość <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> tak, aby używała protokołu TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub starszej wersji protokołu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="7f346-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="7f346-118">To obejście nie jest zalecane, ponieważ certyfikat z algorytmem wyznaczania wartości skrótu MD5 jest uznawany za niezabezpieczony.</span><span class="sxs-lookup"><span data-stu-id="7f346-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f346-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f346-119">See also</span></span>

- [<span data-ttu-id="7f346-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7f346-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
