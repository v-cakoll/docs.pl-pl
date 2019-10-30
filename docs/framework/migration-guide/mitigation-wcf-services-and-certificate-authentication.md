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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Środki zaradcze: usługi WCF i uwierzytelnianie certyfikatów

.NET Framework 4,6 dodaje protokoły TLS 1,1 i TLS 1,2 do listy domyślnych protokołu SSL WCF. Gdy komputery klienckie i serwery mają zainstalowany .NET Framework 4,6 lub nowszy, protokół TLS 1,2 jest używany do negocjacji.

## <a name="impact"></a>Wpływ

Protokół TLS 1,2 nie obsługuje uwierzytelniania certyfikatów MD5. W związku z tym, jeśli klient korzysta z certyfikatu SSL, który używa algorytmu MD5 do mieszania, klient programu WCF nie będzie mógł nawiązać połączenia z usługą WCF. Aby uzyskać więcej informacji, zobacz [ograniczanie: usługi WCF i uwierzytelnianie certyfikatów](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Ograniczenie

Ten problem można obejść, aby klient programu WCF mógł połączyć się z serwerem WCF, wykonując jedną z następujących czynności:

- Zaktualizuj certyfikat, aby nie używał algorytmu MD5. Jest to zalecane rozwiązanie.

- Jeśli powiązanie nie jest konfigurowane dynamicznie w kodzie źródłowym, zaktualizuj plik konfiguracji aplikacji tak, aby korzystał z protokołu TLS 1,1 lub starszej wersji. Dzięki temu można nadal używać certyfikatu z algorytmem wyznaczania wartości skrótu MD5.

  > [!CAUTION]
  > To obejście nie jest zalecane, ponieważ certyfikat z algorytmem wyznaczania wartości skrótu MD5 jest uznawany za niezabezpieczony.

  Następujący plik konfiguracji wykonuje następujące czynności:

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

- Jeśli powiązanie jest konfigurowane dynamicznie w kodzie źródłowym, zaktualizuj właściwość <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> tak, aby używała protokołu TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub starszej wersji protokołu w kodzie źródłowym.

  > [!CAUTION]
  > To obejście nie jest zalecane, ponieważ certyfikat z algorytmem wyznaczania wartości skrótu MD5 jest uznawany za niezabezpieczony.

## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](runtime-changes-in-the-net-framework-4-6.md)
