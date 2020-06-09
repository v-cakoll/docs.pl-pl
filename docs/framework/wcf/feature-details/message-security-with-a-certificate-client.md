---
title: Zabezpieczenia komunikatów z klientem dysponującym certyfikatem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 2b2717bc68da9f07cd38e10a5d75b2a7df9add45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602638"
---
# <a name="message-security-with-a-certificate-client"></a>Zabezpieczenia komunikatów z klientem dysponującym certyfikatem
W poniższym scenariuszu przedstawiono klienta i usługę Windows Communication Foundation (WCF) zabezpieczony przy użyciu trybu zabezpieczeń wiadomości. Zarówno klient, jak i usługa są uwierzytelniani przy użyciu certyfikatów. Aby uzyskać więcej informacji, zobacz [rozproszone zabezpieczenia aplikacji](distributed-application-security.md).

 ![Zrzut ekranu pokazujący klienta z certyfikatem.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 Aby zapoznać się z przykładową aplikacją, zobacz [certyfikat zabezpieczeń wiadomości](../samples/message-security-certificate.md).  

|Charakterystyka|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tylko WCF|  
|Uwierzytelnianie (serwer)|Korzystanie z certyfikatu usługi|  
|Uwierzytelnianie (klient)|Korzystanie z certyfikatu klienta|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transport|HTTP|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:  
  
- Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.  
  
- Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który używa zabezpieczeń komunikatów do ustanowienia bezpiecznego kontekstu.  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a>Konfigurowanie  
 Można użyć poniższej konfiguracji zamiast kodu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
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
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:  
  
- Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).  
  
- Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy klienta. Powiązanie jest zabezpieczeniami trybu komunikatów, a typ poświadczeń klienta jest ustawiony na `Certificate` .  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a>Konfigurowanie  
 Poniższa konfiguracja określa certyfikat klienta przy użyciu zachowania punktu końcowego. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](working-with-certificates.md). Kod używa również `identity` elementu> <, aby określić system nazw domen (DNS) oczekiwanej tożsamości serwera. Aby uzyskać więcej informacji na temat tożsamości, zobacz [tożsamość usługi i uwierzytelnianie](service-identity-and-authentication.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd zabezpieczeń](security-overview.md)
- [Uwierzytelnianie i tożsamość usług](service-identity-and-authentication.md)
- [Praca z certyfikatami](working-with-certificates.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
