---
title: Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
ms.openlocfilehash: 8ca3a3e44386c1576610fe3d42f8697c66bee9ab
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205083"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń
Następujący scenariusz pokazuje klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych przez protokół Kerberos.  
  
 Usługi i klienta znajdują się w tej samej domenie lub domenach zaufanych.  
  
> [!NOTE]
>  Różnią się w tym scenariuszu i [zabezpieczenia komunikatów z klientem Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) jest w tym scenariuszu nie negocjuje poświadczenia usługi z usługą przed wysłaniem komunikatów aplikacji. Ponadto ponieważ wymaga to protokołu Kerberos, ten scenariusz wymaga środowiska domeny Windows.  
  
 ![Zabezpieczenia bez negocjowania poświadczeń wiadomości](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tak, WS-Security-Kerberos tokenu profilu zgodnych klientów|  
|Uwierzytelnianie (serwer)|Wzajemne uwierzytelnianie serwera i klienta|  
|Uwierzytelnianie (klient)|Wzajemne uwierzytelnianie serwera i klienta|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transportu|HTTP|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy punkt końcowy usługi, która używa zabezpieczenia wiadomości. Ten kod powoduje wyłączenie negocjowania poświadczeń usługi i utworzenie tokenu kontekstu zabezpieczeń (SCT).  
  
> [!NOTE]
>  Aby użyć typu poświadczeń Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy głównej usługi (SPN), który jest zarejestrowany w domenie usługi Active Directory. Można to zrobić na dwa sposoby:  
  
1.  Użyj `NetworkService` lub `LocalSystem` konta, aby uruchomić usługę. Ponieważ te konta dostępu do komputera, nazwę SPN, który jest ustanawiane, jeśli komputer jest przyłączony do domeny usługi Active Directory, usługi WCF automatycznie generuje prawidłowego elementu SPN wewnątrz punktu końcowego usługi w metadanych usługi (Web Services Description Język lub WSDL).  
  
2.  Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny. Jest jednym ze sposobów w ten sposób korzystania z narzędzia narzędzia Setspn.exe. Po utworzeniu nazwy SPN dla konta usługi należy skonfigurować usługi WCF do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL). Jest to realizowane przez ustawienie tożsamość punktu końcowego dla narażonych punktu końcowego, albo że plik konfiguracyjny aplikacji lub kodu. Poniższy przykład publikuje tożsamości programowo.  
  
 Aby uzyskać więcej informacji na temat nazw głównych usług, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos technicznego dodatku dla Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Aby uzyskać więcej informacji o tożsamościach punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja można używać zamiast kodu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
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
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).  
  
-   Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod konfiguruje klienta. Tryb zabezpieczeń jest ustawiony na komunikat, a typ poświadczeń klienta jest ustawiona na Windows. Należy pamiętać, że <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości są ustawione na `false`.  
  
> [!NOTE]
>  Aby użyć typu poświadczeń Windows bez negocjowania, klient musi mieć skonfigurowaną nazwa SPN konta usługi przed rozpoczęciem komunikacji z usługą. Klient używa nazwy SPN, można pobrać tokenu protokołu Kerberos do uwierzytelniania i zabezpieczania komunikacji z usługą. Poniższy przykład pokazuje sposób konfigurowania klienta przy użyciu usługi SPN. Jeśli używasz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wygenerować klienta, nazwę usługi SPN będzie automatycznie propagowane do klienta z usługi metadanych (WSDL), jeśli zawiera metadanych usługi te informacje. Aby uzyskać więcej informacji o sposobie konfigurowania usługi do uwzględnienia jej nazwę SPN w metadanych usługi zobacz sekcję "Usługa" w dalszej części tego tematu.  
>   
>  Aby uzyskać więcej informacji na temat nazw głównych usług, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos technicznego dodatku dla Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Aby uzyskać więcej informacji o tożsamościach punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tematu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta. Należy pamiętać, że [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element musi być ustawiony na odpowiadać usługi SPN zarejestrowanych dla konta usługi w domenie usługi Active Directory.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
