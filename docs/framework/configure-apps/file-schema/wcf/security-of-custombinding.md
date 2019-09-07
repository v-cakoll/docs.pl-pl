---
title: <security> dla <customBinding>
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: 165d1f2b9b770fd7c3f05143c1d85955c6008463
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399879"
---
# <a name="security-of-custombinding"></a>\<> \<zabezpieczeń niestandardowegobinding >
Określa opcje zabezpieczeń dla niestandardowego powiązania.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Opcjonalna. Wartość logiczna określająca, czy serializowany token może być używany w odpowiedzi. Wartość domyślna to `false`. W przypadku korzystania z podwójnego powiązania ustawienie domyślnie `true` zostanie zignorowane.|  
|Parametru AuthenticationMode|Opcjonalny. Określa tryb uwierzytelniania używany między inicjatorem a obiektem odpowiadającym. Poniżej znajdują się wszystkie wartości.<br /><br /> Wartość domyślna to `sspiNegotiated`.|  
|defaultAlgorithmSuite|Opcjonalna. Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy. Algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasę. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Możliwe wartości przedstawiono poniżej. Wartość domyślna to `Basic256`.<br /><br /> Ten atrybut jest używany podczas pracy z inną platformą, która powoduje, że zestaw algorytmów różni się od wartości domyślnej. Podczas wprowadzania modyfikacji tego ustawienia należy mieć świadomość siły i słabości odpowiednich algorytmów. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Wartość logiczna określająca, czy sygnatury czasowe są uwzględniane w poszczególnych wiadomościach. Wartość domyślna to `true`.|  
|keyEntropyMode|Określa sposób, w jaki są obliczane klucze służące do zabezpieczania komunikatów. Klucze mogą opierać się tylko na materiale klucza klienta, tylko w materiale klucza usługi lub kombinacji obu tych elementów. Prawidłowe wartości to<br /><br /> -   `ClientEntropy`: Klucz sesji jest oparty na danych klucza dostarczonych przez klienta.<br />-   `ServerEntropy`: Klucz sesji jest oparty na danych klucza dostarczonych przez serwer.<br />-   `CombinedEntropy`: Klucz sesji jest oparty na kluczowych danych dostarczonych przez klienta i usługę.<br /><br /> Wartość domyślna to `CombinedEntropy`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Ustawia kolejność, w jakiej algorytmy zabezpieczeń na poziomie komunikatów są stosowane do wiadomości. Prawidłowe wartości to:<br /><br /> -   `SignBeforeEncrypt`: Najpierw Podpisz, a następnie Szyfruj.<br />-   `SignBeforeEncryptAndEncryptSignature`: Najpierw Podpisz, Szyfruj, a następnie Szyfruj podpis.<br />-   `EncryptBeforeSign`: Szyfruj najpierw, a następnie podpisz.<br /><br /> Wartość domyślna zależy od używanej wersji usługi WS-Security. Wartość domyślna to `SignBeforeEncryptAndEncryptSignature` w przypadku korzystania z protokołu WS-Security 1,1. Wartość domyślna to `SignBeforeEncrypt` w przypadku korzystania z protokołu WS-Security 1,0.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Opcjonalny. Ustawia wersję WS-Security, która jest używana. Prawidłowe wartości to:<br /><br /> - WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />- WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />- WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Wartość domyślna to WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 i może być wyrażona w kodzie XML jako `Default`po prostu. Ten atrybut jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Wartość logiczna określająca, czy klucze mogą być uzyskane z oryginalnych kluczy dowodu. Wartość domyślna to `true`.|  
|requireSecurityContextCancellation|Opcjonalna. Wartość logiczna określająca, czy kontekst zabezpieczeń powinien być anulowany i zakończony, gdy nie jest już wymagany. Wartość domyślna to `true`.|  
|requireSignatureConfirmation|Opcjonalny. Wartość logiczna określająca, czy włączone jest potwierdzenie podpisu WS-Security. Po ustawieniu na `true`sygnatury komunikatów są potwierdzane przez obiekt odpowiadający.  W przypadku skonfigurowania niestandardowego powiązania dla certyfikatów obustronnych lub skonfigurowania do używania wystawionych tokenów (powiązania usług WSS 1,1) `true`ten atrybut jest domyślnie ustawiony na. W przeciwnym razie wartość domyślna `false`to.<br /><br /> Potwierdzenie podpisu służy do potwierdzenia, że usługa reaguje na pełną świadomość żądania.|  
|securityHeaderLayout|Opcjonalny. Określa kolejność elementów w nagłówku zabezpieczeń. Prawidłowe wartości to<br /><br /> -   `Strict`: Elementy są dodawane do nagłówka Security zgodnie z ogólną zasadą "DECLARE przed użyciem".<br />-   `Lax`: Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP.<br />-   `LaxWithTimestampFirst`: Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP, z tą różnicą, że pierwszy element w nagłówku zabezpieczeń musi być elementem wsse: timestamp.<br />-   `LaxWithTimestampLast`: Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP, z tą różnicą, że ostatni element w nagłówku zabezpieczeń musi być elementem wsse: timestamp.<br /><br /> Wartość domyślna to `Strict`.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>AuthenticationMode — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Aes128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic192|Użyj szyfrowania Aes192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256|Użyj szyfrowania AES256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256Rsa15|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|Basic192Rsa15|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|TripleDes|Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic128Rsa15|Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.|  
|Basic128Sha256|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic192Sha256|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic256Sha256|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|TripleDesSha256|Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.|  
|Basic128Sha256Rsa15|Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|Basic192Sha256Rsa15|Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|Basic256Sha256Rsa15|Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
|TripleDesSha256Rsa15|Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Określa bieżący token wystawiony. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Określa ustawienia zabezpieczeń lokalnego klienta dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Określa ustawienia zabezpieczeń usługi lokalnej dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat używania tego elementu, zobacz [elementu SecurityBindingElement Authentication Modes](../../../wcf/feature-details/securitybindingelement-authentication-modes.md) and [How to: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób konfigurowania zabezpieczeń przy użyciu niestandardowego powiązania. Pokazuje, jak użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie wiadomości razem z bezpiecznym transportem. Jest to przydatne, gdy do przesyłania komunikatów między klientem i usługą jest wymagany bezpieczny transport, a jednocześnie komunikaty muszą być bezpieczne na poziomie wiadomości. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczone przez system.  
  
 Konfiguracja usługi definiuje niestandardowe powiązanie obsługujące komunikację TCP zabezpieczone przy użyciu protokołu TLS/SSL i zabezpieczenia komunikatów systemu Windows. Niestandardowe powiązanie używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz do ochrony komunikatów podczas przesyłania między klientem i usługą. Jest to realizowane przez [ \<element powiązania > sslStreamSecurity](sslstreamsecurity.md) . Certyfikat usługi jest konfigurowany przy użyciu zachowania usługi.  
  
 Ponadto niestandardowe powiązanie używa zabezpieczeń komunikatów z typem poświadczeń systemu Windows — jest to domyślny typ poświadczeń. Jest to realizowane przez element powiązania [zabezpieczeń](security-of-custombinding.md) . Klient i usługa są uwierzytelniani przy użyciu zabezpieczeń na poziomie wiadomości, jeśli jest dostępny mechanizm uwierzytelniania Kerberos. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, jest używane uwierzytelnianie NTLM. Protokół NTLM uwierzytelnia klienta w usłudze, ale nie uwierzytelnia usługi dla klienta. Element powiązania [zabezpieczeń](security-of-custombinding.md) jest skonfigurowany do korzystania `SecureConversation` z typu AuthenticationType, co powoduje utworzenie sesji zabezpieczeń zarówno na kliencie, jak i w usłudze. Jest to wymagane, aby umożliwić pracę kontraktu dupleksowego usługi. Aby uzyskać więcej informacji na temat uruchamiania tego przykładu, zobacz [niestandardowe powiązania zabezpieczeń](../../../wcf/samples/custom-binding-security.md).  
  
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
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
