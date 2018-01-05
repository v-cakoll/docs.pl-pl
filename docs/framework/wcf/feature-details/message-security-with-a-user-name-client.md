---
title: "Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: dfda34c6bf165ebcecfd6d9a3710e785586d6cb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-user-name-client"></a>Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
Na poniższej ilustracji pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługa i klient zabezpieczone przy użyciu zabezpieczeń na poziomie wiadomości. Usługa jest uwierzytelniane za pomocą certyfikatu X.509. Klient jest uwierzytelniany przy użyciu nazwy użytkownika i hasła.  
  
 Przykładową aplikację, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Zabezpieczenia komunikatów przy użyciu uwierzytelniania nazwa użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]tylko|  
|Uwierzytelnianie (serwer)|Początkowa negocjacji wymaga uwierzytelniania serwera|  
|Uwierzytelnianie (klient)|Nazwa użytkownika/hasło|  
|Integralność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionego|  
|Poufność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionego|  
|Transportu|HTTP|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń wiadomości.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Konfiguracja  
 Zamiast kodu mogą być używane następującej konfiguracji:  
  
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
 Poniższy kod tworzy klienta. Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `UserName`. Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne). Kod, aby zwrócić nazwę użytkownika i hasło nie jest wyświetlane w tym miejscu, ponieważ musi zostać wykonana na poziomie aplikacji. Na przykład okno formularzy systemu Windows do badania użytkownika dla danych.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta. Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `UserName`. Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).  
  
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
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
