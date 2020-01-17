---
title: Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 547c23509096b66c1fdbd46117a10f4de1692387
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212047"
---
# <a name="message-security-with-a-user-name-client"></a>Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
Na poniższej ilustracji przedstawiono usługę Windows Communication Foundation (WCF) i klienta zabezpieczoną przy użyciu zabezpieczeń na poziomie komunikatów. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509. Klient jest uwierzytelniany przy użyciu nazwy użytkownika i hasła.  
  
 Aby zapoznać się z przykładową aplikacją, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Zabezpieczenia komunikatów przy użyciu uwierzytelniania nazwy użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tylko Windows Communication Foundation (WCF)|  
|Uwierzytelnianie (serwer)|Początkowe negocjowanie wymaga uwierzytelniania serwera|  
|Uwierzytelnianie (klient)|Nazwa użytkownika/hasło|  
|Integralność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionych|  
|Poufność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionych|  
|Transport|HTTP|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>NDES  
 Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:  
  
- Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.  
  
- Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń komunikatów.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Konfiguracja  
 Zamiast kodu można użyć następującej konfiguracji:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy klienta. Powiązanie jest zabezpieczeniami trybu komunikatów, a typ poświadczeń klienta ma wartość `UserName`. Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go konfigurować). Kod, który ma zwrócić nazwę użytkownika i hasło, nie jest tutaj wyświetlany, ponieważ należy go wykonać na poziomie aplikacji. Na przykład użyj okna dialogowego Windows Forms, aby wysłać zapytanie do użytkownika o dane.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta. Powiązanie jest zabezpieczeniami trybu komunikatów, a typ poświadczeń klienta ma wartość `UserName`. Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go konfigurować).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<tożsamość >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
