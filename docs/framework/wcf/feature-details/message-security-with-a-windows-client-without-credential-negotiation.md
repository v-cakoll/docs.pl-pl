---
title: Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 05ffe731a578f8b8d2cdbdf5e3c9229e2b03821c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń
Poniższy scenariusz przedstawia klienta usługi Windows Communication Foundation (WCF) i usługi zabezpieczonej przez protokół Kerberos.  
  
 Zarówno usługa, jak i klienta znajdują się w tej samej domenie lub domenach zaufanych.  
  
> [!NOTE]
>  Różnica między tym scenariuszu i [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) jest, że w tym scenariuszu nie negocjuje poświadczenie usługi z usługą przed wysłaniem wiadomości aplikacji. Ponadto ponieważ wymaga to protokół Kerberos, ten scenariusz wymaga środowiska domeny systemu Windows.  
  
 ![Zabezpieczenia bez negocjowania poświadczeń wiadomości](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tak, WS-Security klientom zgodne profilu token protokołu Kerberos|  
|Uwierzytelnianie (serwer)|Wzajemne uwierzytelnianie serwera i klienta|  
|Uwierzytelnianie (klient)|Wzajemne uwierzytelnianie serwera i klienta|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transportu|HTTP|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy punkt końcowy usługi, który korzysta z zabezpieczeń wiadomości. Kod wyłącza negocjowania poświadczeń usługi i ustanowienia token kontekstu zabezpieczeń (SCT).  
  
> [!NOTE]
>  Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy głównej usługi (SPN), która jest zarejestrowana do domeny usługi Active Directory. Można to zrobić na dwa sposoby:  
  
1.  Użyj `NetworkService` lub `LocalSystem` konto uruchamiania usługi. Ponieważ te konta dostępu do komputera, nazwę SPN, który zostanie nawiązane, gdy komputer jest dołączany do domeny usługi Active Directory, usługi WCF automatycznie generuje prawidłowego elementu SPN w punkt końcowy usługi w metadanych usługi (Web Services Description Język lub WSDL).  
  
2.  Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi. W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny. Jednym ze sposobów realizacji tego jest narzędzie Narzędzie Setspn.exe. Po utworzeniu nazwy SPN dla konta usługi należy skonfigurować usług WCF do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL). Odbywa się przez ustawienie tożsamość punktu końcowego dla dostępnego punktu końcowego, albo jeśli pliku konfiguracji aplikacji lub kodu. Poniższy przykład publikuje tożsamość programowo.  
  
 Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330). Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następującej konfiguracji można zamiast kodu.  
  
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
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).  
  
-   Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod konfiguruje klienta. Tryb zabezpieczeń jest ustawiony na komunikat, a ustawiono typ poświadczeń klienta Windows. Należy pamiętać, że <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości są ustawione na `false`.  
  
> [!NOTE]
>  Aby użyć typu poświadczeń systemu Windows bez negocjowania, klient musi być skonfigurowany przed rozpoczęciem komunikacji z usługą nazwa SPN konta usługi. Klient używa nazwy SPN, aby uzyskać token protokołu Kerberos do uwierzytelniania i zabezpieczania komunikacji z usługą. Poniższy przykład przedstawia sposób konfigurowania klienta z usługi SPN. Jeśli używasz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klienta, nazwę usługi SPN będzie automatycznie propagowane do klienta z metadanych usługi (WSDL), jeśli zawiera metadanych usługi te informacje. Aby uzyskać więcej informacji o sposobie konfigurowania usługi do uwzględnienia w metadanych usługi jego głównej nazwy usługi zobacz sekcję "Usługa" w dalszej części tego tematu.  
>   
>  Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330). Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tematu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta. Należy pamiętać, że [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element musi mieć ustawiony odpowiadające usługi SPN w zarejestrowany dla konta usługi w domenie usługi Active Directory.  
  
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
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
