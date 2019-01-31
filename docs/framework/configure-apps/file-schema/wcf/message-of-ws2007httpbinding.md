---
title: <message> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 7447c41d991561bc98540b6fb8ea3ad93a42192b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281856"
---
# <a name="message-of-ws2007httpbinding"></a>\<komunikat > z \<ws2007HttpBinding >
Definiuje ustawienia zabezpieczeń na poziomie komunikatu z [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<ws2007HttpBinding>  
\<Powiązanie >  
\<security>  
\<message>  
  
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
|`algorithmSuite`|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Te algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).<br /><br /> Wartość domyślna to Basic256.|  
|`clientCredentialType`|Opcjonalna. Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu trybu zabezpieczeń `Message` lub `TransportWithMessageCredentials`. Zobacz wartości wyliczenia w poniższej tabeli. Wartość domyślna to Windows.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Wartość, która określa, czy kanał zabezpieczeń ustanawia bezpiecznej sesji. Bezpiecznej sesji ustanawia tokenu kontekstu zabezpieczeń (SCT) przed rozpoczęciem wymiany komunikatów aplikacji. Po ustanowieniu SCT kanału zabezpieczeń oferuje <xref:System.ServiceModel.Channels.ISession> interfejsu do górnej kanałów. Aby uzyskać więcej informacji na temat przy użyciu bezpiecznej sesji zobacz [jak: Tworzenie bezpiecznej sesji](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Wartość domyślna to `true`.|  
|`negotiateServiceCredential`|Opcjonalna. Wartość, która określa, czy poświadczenia usługi jest zainicjowana klientem poza pasmem lub uzyskany z usługi do klienta w procesie negocjacji. Takie negocjacji jest wstępnym i niezbędnym warunkiem do programu exchange zwykle wiadomości.<br /><br /> Jeśli `clientCredentialType` atrybutu jest równa None, nazwa użytkownika lub certyfikatu, ustawienie tego atrybutu na `false` oznacza, że certyfikat usługi jest dostępny po stronie klienta poza pasmem i czy klienta należy określić certyfikat usługi (za pomocą [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) w [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) usługi zachowanie. Ten tryb jest współpracujący z stosów protokołu SOAP, które implementują WS-Trust i WS-SecureConversation.<br /><br /> Jeśli `ClientCredentialType` ma ustawioną wartość atrybutu `Windows`, ustawienie tego atrybutu na `false` Określa uwierzytelnianie oparte na protokołu Kerberos. Oznacza to, że klient i usługa musi należeć do tej samej domeny protokołu Kerberos. Ten tryb jest współpracujący z stosów protokołu SOAP, które implementują profilu tokenu protokołu Kerberos (zgodnie z definicją w OASIS WSS TC) oraz WS-Trust i WS-SecureConversation.<br /><br /> Jeśli ten atrybut jest `true`, sprawia, że negocjacji protokołu SOAP .NET, która tuneli <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange za pośrednictwem protokołu SOAP wiadomości.<br /><br /> Wartość domyślna to `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite Attribute  
  
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
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Dzięki usłudze na współdziałanie z anonimowych klientów. W usłudze oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, że klient nie zawiera żadnych poświadczeń klienta.|  
|`Certificate`|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli `message` używany jest tryb zabezpieczeń i `negotiateServiceCredential` ma ustawioną wartość atrybutu `false`, klient musi być obsługiwana za pomocą certyfikatu usługi.|  
|`IssuedToken`|Określa niestandardowy token, zwykle wydany przez Usługa tokenu zabezpieczającego (STS).|  
|`UserName`|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą `UserName` poświadczeń. Usługi WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia wiadomości. W efekcie WCF wymusza, czy transport jest zabezpieczony, korzystając z `UserName` poświadczeń. W tym trybie poświadczeń skutkuje międzyoperacyjnych programu exchange lub negocjacji międzyoperacyjnych, na podstawie `negotiateServiceCredential` atrybutu.|  
|`Windows`|Umożliwia wymianę SOAP się pod uwierzytelnionego kontekście `Windows` poświadczeń. Jeśli `negotiateServiceCredential` ma ustawioną wartość atrybutu `true`, to albo wykonuje negocjacji interfejsu SSPI protokołu Kerberos (standard interoperacyjne).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń dla [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
