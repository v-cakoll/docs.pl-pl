---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 1b2b451eb1ea6a1a49ce1ba8cc1edef1fe72d01b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184355"
---
# <a name="transport-security-with-basic-authentication"></a>Zabezpieczenia transportu z uwierzytelnianiem podstawowym
Na poniższej ilustracji przedstawiono usługę i klienta programu Windows Communication Foundation (WCF). Serwer potrzebuje prawidłowego certyfikatu X.509, który może być używany dla secure sockets layer (SSL), a klienci muszą ufać certyfikatowi serwera. Ponadto usługa sieci Web ma już implementację SSL, która może być używana. Aby uzyskać więcej informacji na temat włączania uwierzytelniania <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>podstawowego w internetowych usługach informacyjnych (IIS), zobacz .  
  
 ![Zrzut ekranu przedstawiający zabezpieczenia transportu z uwierzytelnianiem podstawowym.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Charakterystyka|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transport|  
|Współdziałanie|Z istniejącymi klientami i usługami usługi sieci Web|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (przy użyciu protokołu HTTPS)<br /><br /> Tak (za pomocą nazwy użytkownika/hasła)|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transport|HTTPS|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
- Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.  
  
- Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.  
  
### <a name="code"></a>Code  
 Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa nazwy użytkownika domeny systemu Windows i hasła do zabezpieczeń transferu. Należy zauważyć, że usługa wymaga certyfikatu X.509 do uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [Jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Konfigurowanie  
 Poniżej przedstawiono skonfigurowanie usługi do używania uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:  
  
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
  
### <a name="code"></a>Code  
 Poniższy kod przedstawia kod klienta, który zawiera nazwę użytkownika i hasło. Należy pamiętać, że użytkownik musi podać prawidłową nazwę użytkownika i hasło systemu Windows. Kod do zwrócenia nazwy użytkownika i hasła nie jest wyświetlany w tym miejscu. Użyj okna dialogowego lub innego interfejsu, aby zbadać użytkownika w poszukiwaniu informacji.  
  
> [!NOTE]
> Nazwę użytkownika i hasło można ustawić tylko przy użyciu kodu.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurowanie  
 Poniższy kod przedstawia konfigurację klienta.  
  
> [!NOTE]
> Nie można użyć konfiguracji, aby ustawić nazwę użytkownika i hasło. Konfiguracja pokazana w tym miejscu musi zostać rozszerzona za pomocą kodu, aby ustawić nazwę użytkownika i hasło.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [\<>clientCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
