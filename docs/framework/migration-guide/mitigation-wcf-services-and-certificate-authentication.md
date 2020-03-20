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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Łagodzenie: Usługi WCF i uwierzytelnianie certyfikatów

Program .NET Framework 4.6 dodaje protokoły TLS 1.1 i TLS 1.2 do domyślnej listy protokołu SSL WCF. Gdy maszyny klienckie i serwerowe mają zainstalowany program .NET Framework 4.6 lub nowszy, do negocjacji jest używany tls 1.2.

## <a name="impact"></a>Wpływ

TLS 1.2 nie obsługuje uwierzytelniania certyfikatu MD5. W rezultacie jeśli klient używa certyfikatu SSL, który używa MD5 dla algorytmu mieszania, klient WCF nie może połączyć się z usługą WCF. Aby uzyskać więcej informacji, zobacz [Łagodzenie: Usługi WCF i uwierzytelnianie certyfikatów](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Środki zaradcze

Można obejść ten problem, tak aby klient WCF można połączyć się z serwerem WCF wykonując dowolną z następujących czynności:

- Zaktualizuj certyfikat, aby nie używać algorytmu MD5. Jest to zalecane rozwiązanie.

- Jeśli powiązanie nie jest dynamicznie skonfigurowane w kodzie źródłowym, zaktualizuj plik konfiguracyjny aplikacji, aby używał protokołu TLS 1.1 lub starszej wersji protokołu. Dzięki temu można nadal używać certyfikatu z algorytmem mieszania MD5.

  > [!CAUTION]
  > To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.

  Następujący plik konfiguracyjny robi to:

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

- Jeśli powiązanie jest dynamicznie skonfigurowane w <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> kodzie źródłowym, zaktualizuj właściwość, aby użyć protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub wcześniejszej wersji protokołu w kodzie źródłowym.

  > [!CAUTION]
  > To obejście nie jest zalecane, ponieważ certyfikat z algorytmem mieszania MD5 jest uważany za niebezpieczny.

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
