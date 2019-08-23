---
title: <message> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 4a7606c0ebc9fc1bbd34aef619dcb4b8a1d63fa5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931546"
---
# <a name="message-of-nethttpbinding"></a>\<> \<komunikatu > protokołu HttpBinding
Definiuje ustawienia zabezpieczeń [ \<](basichttpbinding.md)na poziomie wiadomości BasicHttpBinding >.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<> protokołu HttpBinding  
\<> powiązania  
\<> zabezpieczeń  
\<message>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Wartość domyślna to `Basic256`.|  
|clientCredentialType|Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikatach. Wartość domyślna to `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|UserName|-Wymaga uwierzytelnienia klienta na serwerze przy użyciu poświadczeń nazwy użytkownika. To poświadczenie należy określić przy użyciu elementu >`clientCredentials`<.<br />— Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu haseł i używania tych kluczy do zabezpieczenia komunikatów. W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika. W przypadku `basicHttpBinding`programu wymagane jest skonfigurowanie kanału SSL.|  
|Certyfikatu|Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu. Poświadczenia klienta w tym przypadku należy określić przy użyciu <`clientCredentials`> i <`clientCertificate`>. Ponadto w przypadku korzystania z trybu zabezpieczeń wiadomości klient musi być zainicjowany przy użyciu certyfikatu usługi. Poświadczenia usługi w tym przypadku należy określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` zachowań, a \<także określić certyfikat usługi przy użyciu serviceCertificate > elementu ServiceCredentials.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|<`security`> element <`netHttpBinding`>|Definiuje możliwości zabezpieczeń dla elementu > <`netHttpBinding`.|  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje sposób implementacji aplikacji, która korzysta z basicHttpBinding i zabezpieczenia komunikatów. W poniższym przykładzie konfiguracji dla usługi definicja punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`. Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w `behaviors` sekcji pliku konfiguracji `serviceCredentials` w obszarze elementu. Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również `behaviors` ustawiany w sekcji `clientCertificate` w obszarze elementu.  
  
 W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
