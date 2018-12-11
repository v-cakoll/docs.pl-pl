---
title: Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 76accbccc1f65bb44b7e710f3f24dc2bae17eeda
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155002"
---
# <a name="message-security-with-a-user-name-client"></a>Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
Na poniższej ilustracji przedstawiono usługi Windows Communication Foundation (WCF) i klient zabezpieczone przy użyciu zabezpieczeń na poziomie komunikatu. Usługa jest uwierzytelniana przy użyciu certyfikatu X.509. Klient jest uwierzytelniany przy użyciu nazwy użytkownika i hasła.  
  
 Dla przykładowej aplikacji, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Zabezpieczenia komunikatów przy użyciu uwierzytelniania nazwy użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Windows Communication Foundation (WCF) tylko|  
|Uwierzytelnianie (serwer)|Początkowego negocjowania wymaga uwierzytelniania przez serwer|  
|Uwierzytelnianie (klient)|Nazwa użytkownika/hasło|  
|Integralność|Tak, za pomocą kontekstu zabezpieczeń udostępnionego|  
|Poufność|Tak, za pomocą kontekstu zabezpieczeń udostępnionego|  
|Transportu|HTTP|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia wiadomości.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja można używać zamiast kodu:  
  
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
 Poniższy kod tworzy klienta. Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `UserName`. Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne). Kod, aby zwrócić nazwę użytkownika i hasło nie został tutaj pokazany, ponieważ muszą być wykonane na poziomie aplikacji. Na przykład okno formularzy Windows do wykonywania zapytań użytkownika na potrzeby danych.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta. Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `UserName`. Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<tożsamość >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
