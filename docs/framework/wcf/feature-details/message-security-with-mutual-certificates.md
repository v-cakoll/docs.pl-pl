---
title: Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1407593bf90b28a1890a8c18564b31d0aa67e0cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494179"
---
# <a name="message-security-with-mutual-certificates"></a>Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
Poniższy scenariusz zawiera usługi Windows Communication Foundation (WCF) i klienta zabezpieczony używających trybu zabezpieczenia wiadomości. Klient i usługa są uwierzytelniane za pomocą certyfikatów.  
  
 Ten scenariusz jest współdziałanie, ponieważ używa WS-Security z profilem tokenu certyfikatu X.509.  
  
> [!NOTE]
>  W tym scenariuszu nie przeprowadza negocjowanie certyfikatu usługi. Należy podać certyfikat usługi do klienta z wyprzedzeniem wszelkie komunikacji klienta. Certyfikat serwera można rozpowszechnianej za pomocą aplikacji lub podane w komunikacie poza pasmem.  
  
 ![Zabezpieczenia ze wzajemnymi certyfikatami wiadomości](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tak, z WS-Security i klientów zgodne tokenu profilu certyfikatu X.509 i usług.|  
|Uwierzytelnianie|Wzajemne uwierzytelnianie serwera i klienta.|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transportu|HTTP|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 W poniższym kodzie tworzy punkt końcowy usługi, który korzysta z zabezpieczeń wiadomości. Usługa wymaga certyfikatu do samodzielnego uwierzytelnienia.  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następującej konfiguracji można zamiast kodu do utworzenia tej samej usługi.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
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
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).  
  
-   Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy klienta. Tryb zabezpieczeń jest ustawiony na komunikat, a typ poświadczeń klienta ma wartość Certificate.  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższa konfiguracja klienta. Certyfikat klienta musi być podana przy użyciu [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md). Ponadto certyfikat usługi zostanie określona przy użyciu [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)  
 [Porady: tworzenie i zainstalować certyfikaty tymczasowe w programie WCF dla zabezpieczeń transportu podczas tworzenia](http://go.microsoft.com/fwlink/?LinkId=244264)
