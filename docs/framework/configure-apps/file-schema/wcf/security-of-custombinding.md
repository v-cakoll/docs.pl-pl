---
title: '&lt;security&gt; w &lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
caps.latest.revision: "24"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1130c6f91f8f55e539e85b6deda535e92258165c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;security&gt; w &lt;customBinding&gt;
Określa opcje zabezpieczeń dla niestandardowego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security   
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
      defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
      requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
      messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean"  
      securityHeaderLayout=  
              "Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean">  
   <issuedTokenParameters />  
   <localClientSettings />  
   <localServiceSettings />  
   <secureConversationBootstrap />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Opcjonalny. Wartość logiczna, która określa, czy szeregowanego tokenu można używać w odpowiedzi. Wartość domyślna to `false`. Korzystając z podwójną powiązanie, ustawienie domyślnie `true` i wszystkie wprowadzone ustawienia zostaną zignorowane.|  
|authenticationMode|Opcjonalny. Określa tryb uwierzytelniania używany podczas komunikacji między Inicjator i obiekt odpowiadający. Poniżej znajduje się wszystkie wartości.<br /><br /> Wartość domyślna to `sspiNegotiated`.|  
|DefaultAlgorithmSuite|Opcjonalny. Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Poniżej przedstawiono możliwe wartości. Wartość domyślna to `Basic256`.<br /><br /> Ten atrybut jest używany podczas pracy z innej platformie, która zdecyduje się na zestawem algorytmów innych niż domyślne. Należy pamiętać o słabych algorytmów odpowiednich i po zmodyfikowaniu tego ustawienia. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|IncludeTimestamp|Wartość logiczna określająca czy sygnatury czasowe są umieszczane w każdej wiadomości. Wartość domyślna to `true`.|  
|KeyEntropyMode|Określa sposób, że są obliczane klucze dla zabezpieczenia wiadomości. Klucze może być oparta na klienta klucza materiałów, usługa materiału klucza tylko lub obie te grupy. Prawidłowe wartości to<br /><br /> -   `ClientEntropy`: Klucz sesji jest oparty na danych dostarczonych przez klienta.<br />-   `ServerEntropy`: Klucz sesji jest oparta na klucza dane dostarczone przez serwer.<br />-   `CombinedEntropy`Klucz sesji jest oparty na danych klucza dostarczonych przez klienta i usługi.<br /><br /> Wartość domyślna to `CombinedEntropy`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Ustawia kolejność, w jaki komunikat algorytmy poziomu zabezpieczenia są stosowane do wiadomości. Prawidłowe wartości są następujące:<br /><br /> -   `SignBeforeEncrypt`: Zaloguj się najpierw, a następnie szyfrować.<br />-   `SignBeforeEncryptAndEncryptSignature`: Zaloguj się najpierw, szyfrowania, a następnie szyfrować podpisu.<br />-   `EncryptBeforeSign`: Szyfrowanie, następnie logowania.<br /><br /> Wartość domyślna zależy od wersji WS-Security używane. Wartość domyślna to `SignBeforeEncryptAndEncryptSignature` przy użyciu 1.1 WS-Security. Wartość domyślna to `SignBeforeEncrypt` używając WS-Security 1.0.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|Właściwości MessageSecurityVersion|Opcjonalny. Ustawia wersję WS-Security, która jest używana. Prawidłowe wartości są następujące:<br /><br /> -WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Wartość domyślna jest WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 i mogą być wyrażone w kodzie XML tylko `Default`. Ten atrybut jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Wartość logiczna określająca, czy klucze mogą być uzyskane z oryginalnych kluczy dowodu. Wartość domyślna to `true`.|  
|requireSecurityContextCancellation|Opcjonalny. Wartość logiczna określająca, jeśli kontekstu zabezpieczeń powinny być anulowany i zakończony, kiedy nie jest już potrzebne. Wartość domyślna to `true`.|  
|requireSignatureConfirmation|Opcjonalny. Wartość logiczna określająca, czy włączone jest potwierdzenie podpisu WS-Security. Jeśli wartość `true`, odpowiadający potwierdzają sygnatury komunikatów.  Gdy niestandardowego powiązania jest skonfigurowany dla wzajemnymi certyfikatami lub jest ona skonfigurowana do użycia wystawiony tokeny (powiązania 1.1 programu WSS) domyślna tego atrybutu `true`. W przeciwnym razie wartość domyślna to `false`.<br /><br /> Potwierdzenie podpisu jest używana do upewnij się, czy usługa odpowiada w pełną świadomość żądania.|  
|SecurityHeaderLayout|Opcjonalny. Określa kolejność elementów w nagłówku zabezpieczeń. Prawidłowe wartości to<br /><br /> -   `Strict`: Elementy są dodawane do nagłówka zabezpieczeń zgodnie z ogólną zasadę "deklaruje przed użyciem".<br />-   `Lax`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP.<br />-   `LaxWithTimestampFirst`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP z tą różnicą, że pierwszym elementem w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br />-   `LaxWithTimestampLast`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP z tą różnicą, że ostatnim elementem w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br /><br /> Wartość domyślna to `Strict`.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Aes128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.|  
|Basic192|Użyj szyfrowania Aes192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256|Użyj szyfrowania Aes256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Rsa15|Aes256 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Rsa15|Aes192 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDes|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Rsa15|Aes128 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic128Sha256|Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic192Sha256|Aes192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Sha256|Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|TripleDesSha256|TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Sha256Rsa15|Aes128 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Sha256Rsa15|Aes192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic256Sha256Rsa15|Aes256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesSha256Rsa15|TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa bieżący wystawionego tokenu. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]przy użyciu tego elementu, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) i [porady: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania zabezpieczeń przy użyciu niestandardowego powiązania. Widoczny jest sposób umożliwiają niestandardowego powiązania zabezpieczeń na poziomie komunikatu wraz z bezpiecznego transportu. Jest to przydatne, gdy do przesyłania wiadomości między klientem a usługą jest wymagane bezpieczne transportu i jednocześnie wiadomości musi być bezpieczny na poziomie wiadomości. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.  
  
 Konfiguracja usługi definiuje niestandardowe powiązanie, które obsługuje komunikację TCP chronione przy użyciu protokołu TLS/SSL i zabezpieczenia komunikatów systemu Windows. Wiązanie niestandardowe używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz chronić przed komunikaty podczas transmisji między klientem a usługą. Jest to osiągane przez [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu powiązania. Certyfikat usługi jest skonfigurowany przy użyciu zachowanie usługi.  
  
 Ponadto niestandardowego powiązania używa zabezpieczenia komunikatów z typu poświadczeń systemu Windows — jest to domyślny typ poświadczeń. Jest to osiągane przez [zabezpieczeń](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu powiązania. Zarówno klient, jak i usługa są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizmu uwierzytelniania Kerberos jest dostępne. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępna, jest używane uwierzytelnianie NTLM. NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnia usługi do klienta. [Zabezpieczeń](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania jest skonfigurowana do używania `SecureConversation` authenticationType, co prowadzi do utworzenia sesji zabezpieczeń zarówno klient, jak i usługi. Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy. Aby uzyskać więcej informacji dotyczących uruchamiania tego przykładu, zobacz [niestandardowego powiązania zabezpieczeń](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- use following base address -->  
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                    binding="customBinding"  
                    bindingConfiguration="Binding1"   
                    contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <sslStreamSecurity requireClientCertificate="false"/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.SecurityElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
