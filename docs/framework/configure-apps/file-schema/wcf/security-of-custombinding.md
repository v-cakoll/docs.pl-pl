---
title: '&lt;security&gt; w &lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: c80a4a34d5315dbc5a22d3953fee437ebe2e938f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573455"
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;security&gt; w &lt;customBinding&gt;
Określa opcje zabezpieczeń dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<security>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
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
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Opcjonalna. Wartość logiczna określająca, jeśli szeregowanego tokenu można użyć w przypadku odpowiedzi. Wartość domyślna to `false`. Korzystając z podwójną powiązania, ustawienie domyślnie `true` i wszystkie ustawienia wprowadzone zostaną zignorowane.|  
|authenticationMode|Opcjonalna. Określa tryb uwierzytelniania używany między inicjatorem i obiekt odpowiadający. Poniżej znajdują się wszystkie wartości.<br /><br /> Wartość domyślna to `sspiNegotiated`.|  
|defaultAlgorithmSuite|Opcjonalna. Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Te algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).<br /><br /> Poniżej przedstawiono możliwe wartości. Wartość domyślna to `Basic256`.<br /><br /> Ten atrybut jest używany podczas pracy z różnych platform, który zdecyduje się na zestaw algorytmów innych niż domyślne. Należy pamiętać o słabych algorytmów odpowiednie i, po zmodyfikowaniu tego ustawienia. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Wartość logiczna określająca czy sygnatury czasowe są umieszczane w każdej wiadomości. Wartość domyślna to `true`.|  
|keyEntropyMode|Określa sposób, że są obliczane klucze dla zabezpieczenia wiadomości. Klucze mogą opierać się na klienta materiału klucza tylko usługa materiału klucza tylko lub jako kombinację obu tych. Prawidłowe wartości to:<br /><br /> -   `ClientEntropy`: Klucz sesji opiera się na kluczowych danych dostarczonych przez klienta.<br />-   `ServerEntropy`: Klucz sesji opiera się na kluczowych danych dostarczanych przez serwer.<br />-   `CombinedEntropy`: Klucz sesji opiera się na kluczowych danych dostarczanych przez klienta i usługi.<br /><br /> Wartość domyślna to `CombinedEntropy`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Ustawia kolejność, w jaki komunikat algorytmy poziomu zabezpieczenia są stosowane do wiadomości. Prawidłowe wartości są następujące:<br /><br /> -   `SignBeforeEncrypt`: Zaloguj się najpierw, a następnie szyfrować.<br />-   `SignBeforeEncryptAndEncryptSignature`: Najpierw zaloguj się, szyfrowania, a następnie szyfrować podpis.<br />-   `EncryptBeforeSign`: Szyfrowanie po pierwsze, następnie logowania.<br /><br /> Wartość domyślna zależy od wersji WS-Security używane. Wartość domyślna to `SignBeforeEncryptAndEncryptSignature` podczas korzystania z protokołu WS-Security 1.1. Wartość domyślna to `SignBeforeEncrypt` podczas korzystania z wersji 1.0 WS-Security.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Opcjonalna. Ustawia wersję WS-Security, która jest używana. Prawidłowe wartości są następujące:<br /><br /> -   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-   WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Wartość domyślna jest WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 i mogą być wyrażone w kodzie XML jako po prostu `Default`. Ten atrybut jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Wartość logiczna określająca, jeśli klucze mogą być uzyskane z oryginalnych kluczy dowodu. Wartość domyślna to `true`.|  
|requireSecurityContextCancellation|Opcjonalna. Wartość logiczna określająca, jeśli kontekstu zabezpieczeń powinien być anulowany i zakończony, kiedy nie jest już potrzebne. Wartość domyślna to `true`.|  
|requireSignatureConfirmation|Opcjonalna. Wartość logiczna określająca, czy włączone jest potwierdzenie podpisu WS-Security. Po ustawieniu `true`, sygnatury komunikatów zostało potwierdzone przez obiekt odpowiadający.  Gdy niestandardowe powiązanie jest skonfigurowane dla wzajemnymi certyfikatami lub jest ona skonfigurowana do użycia wystawione tokeny (powiązań 1.1 programu WSS) tego atrybutu, wartość domyślna to `true`. W przeciwnym razie wartość domyślna to `false`.<br /><br /> Potwierdzenie podpisu jest używany do upewnij się, usługa odpowiada w pełną świadomość żądania.|  
|securityHeaderLayout|Opcjonalna. Określa kolejność elementów w nagłówku zabezpieczenia. Prawidłowe wartości to:<br /><br /> -   `Strict`: Elementy są dodawane do nagłówka zabezpieczeń, zgodnie z zasadą ogólne "zadeklarować przed użyciem".<br />-   `Lax`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: Zabezpieczenia komunikatów protokołu SOAP.<br />-   `LaxWithTimestampFirst`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: Zabezpieczenia komunikatów SOAP, z tą różnicą, że pierwszy element w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br />-   `LaxWithTimestampLast`: Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: Zabezpieczenia komunikatów SOAP, z tą różnicą, że po ostatnim elemencie w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br /><br /> Wartość domyślna to `Strict`.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Aes128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.|  
|Basic192|Należy używać szyfrowania Aes192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256|Użyj szyfrowania Aes256 Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Rsa15|Użyj Aes256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Rsa15|Użyj Aes192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDes|Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Rsa15|Użyj Aes128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic128Sha256|Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic192Sha256|Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Sha256|Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|TripleDesSha256|TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Sha256Rsa15|Użyj Aes128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Sha256Rsa15|Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic256Sha256Rsa15|Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesSha256Rsa15|TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa bieżący wystawiony token. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o korzystaniu z tego elementu, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) i [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować zabezpieczenia przy użyciu niestandardowego powiązania. Widoczny jest sposób użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie komunikatu wraz z bezpiecznym transportem. Jest to przydatne, gdy bezpiecznym transportem jest wymagana do przesyłania komunikatów między klientem a usługą i jednocześnie komunikaty muszą być bezpieczne na poziomie komunikatu. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.  
  
 Konfiguracja usługi definiuje niestandardowego powiązania, który obsługuje komunikację TCP chronione przy użyciu protokołu TLS/SSL i zabezpieczenia komunikatów Windows. Niestandardowego powiązania z certyfikatem usługi do uwierzytelniania usługi na poziomie transportu i do ochrony komunikatów podczas transmisji między klientem a usługą. Jest to osiągane przez [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element powiązania. Certyfikat usługi jest skonfigurowany za pomocą zachowania usługi.  
  
 Ponadto niestandardowego powiązania za pomocą zabezpieczeń wiadomości typ poświadczeń Windows — jest to domyślny typ poświadczeń. Jest to osiągane przez [zabezpieczeń](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania. Zarówno klient, jak i usługi są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizm uwierzytelniania Kerberos jest dostępna. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, zostanie użyte uwierzytelnianie NTLM. NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnia usługi dla klienta. [Zabezpieczeń](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania jest skonfigurowany do używania `SecureConversation` authenticationType, co powoduje utworzenie sesji zabezpieczeń zarówno klient, jak i usługi. Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy. Aby uzyskać więcej informacji na temat uruchamiania tego przykładu, zobacz [zabezpieczeń powiązań niestandardowych](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
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
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
