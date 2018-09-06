---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: ac789ba81d728c067be515479e749440bb5809d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779396"
---
# <a name="trusted-subsystem"></a>Zaufany podsystem
Klient uzyskuje dostęp do usług sieci Web, które są rozpowszechniane w sieci. Usługi sieci Web zostały zaprojektowane, tak że dostęp do dodatkowych zasobów (np. baz danych lub inne usługi sieci Web) są hermetyzowane w logice biznesowej usługi sieci Web. Te zasoby muszą być chronione przed nieautoryzowanym dostępem. Poniższa ilustracja przedstawia proces zaufany podsystem.  
  
 ![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 W poniższych krokach opisano proces zaufany podsystem, jak pokazano:  
  
1.  Klient przesyła żądanie do zaufany podsystem, wraz z poświadczeniami.  
  
2.  Zaufany podsystem uwierzytelnia i autoryzuje użytkownika.  
  
3.  Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego. To żądanie towarzyszy poświadczenia zaufany podsystem (lub konta usługi, w którym jest wykonywana procesu zaufany podsystem).  
  
4.  Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem. Następnie przetwarza żądanie i wysyła odpowiedź do zaufany podsystem.  
  
5.  Zaufany podsystem przetwarza odpowiedź i generuje odpowiedzi do klienta.  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Komunikat|  
|Współdziałanie|Windows Communication Foundation (WCF) tylko.|  
|Uwierzytelniania (usługa)|Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.|  
|Uwierzytelnianie (klient)|Zaufany podsystem uwierzytelnia klienta i zasobów uwierzytelnia usługi zaufany podsystem.|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transportu|Protokół HTTP między klientem a usługą zaufany podsystem.<br /><br /> NET. TCP między usługą zaufany podsystem i zasobów (usłudze zaplecza).|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Zasób (usługa zaplecza)  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi dla zasobu, która używa zabezpieczenia transportu za pośrednictwem protokołu transportu TCP.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja konfiguruje ten sam punkt końcowy, za pomocą konfiguracji.  
  
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
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi dla zaufany podsystem, który używa Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Poniższy kod przedstawia usługę w zaufany podsystem, który komunikuje się za pomocą usługi zaplecza za pośrednictwem protokołu transportu TCP za pomocą zabezpieczeń transportu.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja konfiguruje ten sam punkt końcowy, za pomocą konfiguracji. Należy zauważyć dwa powiązania: zabezpiecza jedną usługę hostowaną w zaufany podsystem, a druga komunikuje się między zaufany podsystem i usługi zaplecza.  
  
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
 Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufany podsystem przy użyciu Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje klienta w celu użycia Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania. Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
