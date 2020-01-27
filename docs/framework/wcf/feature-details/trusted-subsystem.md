---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 4f3166b8f1e59a100f54574ab548f5dae88eb5cd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742640"
---
# <a name="trusted-subsystem"></a>Zaufany podsystem
Klient uzyskuje dostęp do co najmniej jednej usługi sieci Web, która jest dystrybuowana przez sieć. Usługi sieci Web są zaprojektowane tak, aby dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web) był hermetyzowany w logice biznesowej usługi sieci Web. Te zasoby muszą być chronione przed nieautoryzowanym dostępem. Poniższa ilustracja przedstawia proces zaufanego podsystemu.  
  
 ![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 W poniższych krokach opisano proces zaufanego podsystemu, jak pokazano poniżej:  
  
1. Klient przesyła żądanie do zaufanego podsystemu wraz z poświadczeniami.  
  
2. Zaufany podsystem uwierzytelnia użytkownika i autoryzuje go.  
  
3. Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego. Do tego żądania dołączane są poświadczenia dla zaufanego podsystemu (lub konta usługi, w ramach którego jest wykonywany proces zaufanego podsystemu).  
  
4. Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem. Następnie przetwarza żądanie i wystawia odpowiedź na zaufany podsystem.  
  
5. Zaufany podsystem przetwarza odpowiedź i emituje własną odpowiedź do klienta programu.  
  
|Charakterystyk|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Tylko Windows Communication Foundation (WCF).|  
|Uwierzytelnianie (usługa)|Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.|  
|Uwierzytelnianie (klient)|Zaufany podsystem uwierzytelnia klienta, a zasób uwierzytelnia usługę zaufanego podsystemu.|  
|Spójn|Tak|  
|Poufne|Tak|  
|Transportu|Protokół HTTP między klientem a usługą zaufanego podsystemu.<br /><br /> Waga. TCP między usługą zaufanego podsystemu a zasobem (usługa zaplecza).|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Zasób (usługa zaplecza)  
  
### <a name="code"></a>Kod  
 Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zasobu, który używa zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a>Zaufany podsystem  
  
### <a name="code"></a>Kod  
 Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zaufanego podsystemu, który używa zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Poniższy kod przedstawia usługę w zaufanym podsystemie, który komunikuje się z usługą zaplecza przy użyciu zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji. Zwróć uwagę na dwa powiązania: jeden zabezpiecza usługę hostowaną w zaufanym podsystemie, a druga komunikuje się między zaufanym podsystemem a usługą zaplecza.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufanym podsystemem przy użyciu zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod służy do konfigurowania klienta do korzystania z zabezpieczeń komunikatów za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła na potrzeby uwierzytelniania. Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go konfigurować).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
