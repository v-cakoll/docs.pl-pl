---
title: <message> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 3396f74f76d790759f4c32de2907607486701b1a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738946"
---
# <a name="message-of-ws2007httpbinding"></a>\<komunikat > \<ws2007HttpBinding >
Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla elementu [\<ws2007HttpBinding >](ws2007httpbinding.md) .  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WS2007HttpBinding**](ws2007httpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-ws2007httpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ws2007HttpBinding>
  <binding>
    <security>
      <message clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Enumeration. See algorithmSuite Attribute below."
               defaultProtectionLevel="None/Sign/EncryptionAndSign" />
    </security>
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`algorithmSuite`|Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy. Algorytmy i rozmiary kluczy są określane przez klasę <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Wartość domyślna to Basic256.|  
|`clientCredentialType`|Opcjonalny. Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu trybu zabezpieczeń `Message` lub `TransportWithMessageCredentials`. Zobacz wartości wyliczenia w poniższej tabeli. Wartość domyślna to Windows.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Wartość określająca, czy kanał zabezpieczeń ustanawia bezpieczną sesję. Bezpieczna sesja ustanawia token kontekstu zabezpieczeń (SCT) przed wymianą komunikatów aplikacji. Po ustanowieniu tego SCT kanał zabezpieczeń oferuje interfejs <xref:System.ServiceModel.Channels.ISession> do górnych kanałów. Aby uzyskać więcej informacji o korzystaniu z bezpiecznych sesji, zobacz [How to: Create a Secure Session](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Wartość domyślna to `true`.|  
|`negotiateServiceCredential`|Opcjonalny. Wartość określająca, czy poświadczenie usługi jest inicjowane na kliencie poza pasmem, czy jest uzyskiwane z usługi do klienta przez proces negocjacji. Takie negocjowanie jest prekursorem do zwykłej wymiany komunikatów.<br /><br /> Jeśli atrybut `clientCredentialType` ma wartość None, username lub Certificate, ustawienie tego atrybutu na `false` oznacza, że certyfikat usługi jest dostępny na kliencie poza pasmem, a klient musi określić certyfikat usługi (przy użyciu [\<> serviceCertificate](servicecertificate-of-servicecredentials.md)) w [\<servicecredentials >](servicecredentials.md) zachowanie usługi. Ten tryb jest interoperacyjny z stosami protokołu SOAP, które implementują WS-Trust i WS-SecureConversation.<br /><br /> Jeśli atrybut `ClientCredentialType` jest ustawiony na `Windows`, ustawienie tego atrybutu na `false` Określa uwierzytelnianie oparte na protokole Kerberos. Oznacza to, że klient i usługa muszą być częścią tej samej domeny Kerberos. Ten tryb jest współdziałania z stosami protokołu SOAP, które implementują profil tokenu Kerberos (zgodnie z definicją języka Oasis WSS TC) oraz WS-Trust i WS-SecureConversation.<br /><br /> Gdy ten atrybut jest `true`, powoduje negocjowanie protokołu SOAP platformy .NET, który tuneluje <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> Exchange przez komunikaty protokołu SOAP.<br /><br /> Wartość domyślna to `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite — atrybut  
  
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
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Dzięki temu usługa może korzystać z anonimowych klientów. W usłudze oznacza to, że usługa nie wymaga poświadczeń klienta. Na kliencie wskazuje, że klient nie dostarcza poświadczeń klienta.|  
|`Certificate`|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu certyfikatu. Jeśli jest używany tryb zabezpieczeń `message` i atrybut `negotiateServiceCredential` jest ustawiony na `false`, klient musi być zainicjowany przy użyciu certyfikatu usługi.|  
|`IssuedToken`|Określa niestandardowy token, zazwyczaj wystawiony przez usługę tokenu zabezpieczającego (STS).|  
|`UserName`|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu poświadczeń `UserName`. Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów. W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń `UserName`. Ten tryb poświadczeń służy do samodzielnej wymiany lub negocjowania niewspółpracującego na podstawie atrybutu `negotiateServiceCredential`.|  
|`Windows`|Umożliwia wymianę SOAP w ramach uwierzytelnionego kontekstu poświadczenia `Windows`. Jeśli atrybut `negotiateServiceCredential` jest ustawiony na `true`, to wykonuje negocjowanie interfejsu SSPI lub Kerberos (standard interoperacyjny).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> zabezpieczeń \<](security-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń dla [\<> WS2007HttpBinding](ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
