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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Ograniczenie: Usługi WCF i uwierzytelnianie certyfikatu
.NET Framework 4.6 dodaje protokołu TLS 1.1 i TLS 1.2, do listy domyślnych protokołu SSL usługi WCF. Jeśli klienta i na serwerze zainstalować program .NET Framework 4.6 lub nowszy, protokołu TLS 1.2 jest używany dla negocjacji.  
  
## <a name="impact"></a>Wpływ  
 Protokołu TLS 1.2 nie obsługuje uwierzytelnianie certyfikatu MD5. W związku z tym jeśli klient używa certyfikatu SSL, który używa algorytmu wyznaczania wartości skrótu MD5, klient WCF nie może się połączyć z usługą WCF. Aby uzyskać więcej informacji, zobacz [środki zaradcze: usługi WCF i uwierzytelnianie certyfikatu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
## <a name="mitigation"></a>Ograniczenie  
 Można obejść ten problem, tak aby klienta WCF można połączenie z serwerem usługi WCF, wykonując jedną z następujących czynności:  
  
-   Zaktualizuj certyfikat, aby nie używać algorytmu MD5. Jest to zalecane rozwiązanie.  
  
-   Jeśli w kodzie źródłowym nie skonfigurowano dynamicznie powiązanie, należy zaktualizować pliku konfiguracji aplikacji do użycia protokołu TLS 1.1 lub starszej wersji protokołu. Dzięki temu można nadal używać certyfikatu przy użyciu algorytmu wyznaczania wartości skrótu MD5.  
  
    > [!CAUTION]
    >  To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.  
  
     Następujący plik konfiguracji robi to:  
  
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
  
-   Jeśli powiązanie jest skonfigurowane dynamicznie w kodzie źródłowym, należy zaktualizować <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> właściwości do użycia protokołu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) lub starsza wersja protokołu w kodzie źródłowym.  
  
    > [!CAUTION]
    >  To rozwiązanie nie jest zalecane, ponieważ certyfikat przy użyciu algorytmu wyznaczania wartości skrótu MD5 jest uznawany za niebezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
