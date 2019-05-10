---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 5cbe6ce6e8e36fc9460295c454014d6f3fbf3983
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635117"
---
# <a name="transport-security-with-basic-authentication"></a>Zabezpieczenia transportu z uwierzytelnianiem podstawowym
Na poniższej ilustracji przedstawiono usługi Windows Communication Foundation (WCF) i klienta. Serwer musi mieć prawidłowy certyfikat X.509, który może służyć do Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatowi serwera. Ponadto usługa sieci Web już implementacją protokołu SSL, który może służyć. Aby uzyskać więcej informacji dotyczących włączania uwierzytelniania podstawowego w Internet Information Services (IIS), zobacz <https://go.microsoft.com/fwlink/?LinkId=83822>.  
  
 ![Zrzut ekranu przedstawia zabezpieczenia transportu z uwierzytelnianiem podstawowym.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transport|  
|Współdziałanie|Za pomocą istniejących klientów usługi sieci Web i usług|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (za pomocą protokołu HTTPS)<br /><br /> Tak (za pomocą nazwy użytkownika i hasła)|  
|Integralność|Yes|  
|Poufność|Yes|  
|Transport|HTTPS|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
- Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.  
  
- Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z Windows domena nazwa użytkownika i hasło dla bezpieczeństwie transferu. Należy pamiętać, że usługa wymaga certyfikatu X.509 do uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Konfiguracja  
 Następujące konfiguruje usługę do używania uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia kod klienta, który zawiera nazwę użytkownika i hasło. Należy pamiętać, że użytkownik musi podać prawidłowe Windows nazwy użytkownika i hasła. Kod, aby zwrócić nazwę użytkownika i hasło nie jest wyświetlane w tym miejscu. Zapytanie użytkownika o informacje, należy użyć okno dialogowe lub innego interfejsu.  
  
> [!NOTE]
>  Nazwa użytkownika i hasło można ustawić tylko przy użyciu kodu.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod pokazuje konfigurację klienta.  
  
> [!NOTE]
>  Nie można użyć konfiguracji, aby ustawić nazwę użytkownika i hasło. Konfiguracji przedstawionej w tym miejscu musi zostać rozszerzony przy użyciu kodu, aby ustawić nazwę użytkownika i hasło.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
