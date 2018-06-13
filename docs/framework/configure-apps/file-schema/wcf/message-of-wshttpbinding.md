---
title: '&lt;message&gt; w &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 29cef7aa215b29ac5c7a986b456e5e5e06ba135f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364628"
---
# <a name="ltmessagegt-of-ltwshttpbindinggt"></a>&lt;message&gt; w &lt;wsHttpBinding&gt;
Definiuje ustawienia zabezpieczeń na poziomie komunikatu z [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsHttpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<message>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
   establishSecurityContext="Boolean"  
   negotiateServiceCredential="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Wartość domyślna to `Basic256`.|  
|clientCredentialType|Opcjonalna. Określa typ poświadczenia, które będą używane podczas wykonywania uwierzytelniania klienta za pomocą trybu zabezpieczeń jest `Message` lub `TransportWithMessageCredentials`. Zobacz poniższe wartości wyliczenia. Wartość domyślna to `Windows`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Wartość logiczna określająca, czy kanał zabezpieczeń ustanawia bezpiecznej sesji. Bezpieczna sesja ustanawia narzędzia zabezpieczeń kontekstu tokenu (SCT) przed rozpoczęciem wymiany komunikatów aplikacji. Po nawiązaniu SCT kanału zabezpieczeń oferuje <xref:System.ServiceModel.Channels.ISession> interfejs do górnej kanałów. Aby uzyskać więcej informacji o korzystaniu z bezpiecznej sesji, zobacz [porady: tworzenie bezpiecznej sesji](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Wartość domyślna to `true`.|  
|negotiateServiceCredential|Opcjonalna. Wartość logiczna, która określa, czy poświadczenia usługi jest udostępniane po stronie klienta poza pasmem lub są uzyskiwane z usługi do klienta w procesie negocjacji. Takie negocjacji jest macierzystych do programu exchange zwykle wiadomości.<br /><br /> Jeśli `clientCredentialType` atrybut ma wartość None, nazwa użytkownika lub certyfikatu, ustawienie tego atrybutu na `false` oznacza, że certyfikat usługi jest dostępny po stronie klienta poza pasmem i że klienta należy określić certyfikat usługi (za pomocą [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) w [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zachowania usługi. Ten tryb jest współpraca z stosy SOAP, które implementują WS-Trust i WS-SecureConversation.<br /><br /> Jeśli `ClientCredentialType` atrybut ma ustawioną `Windows`, ustawienie tego atrybutu na `false` określa uwierzytelniania opartego na protokołu Kerberos. Oznacza to, że klient i usługa muszą być częścią tej samej domeny protokołu Kerberos. Ten tryb jest współpraca z stosy SOAP, implementujące profilu token protokołu Kerberos (zgodnie z definicją w OASIS TC programu WSS) oraz protokołu WS-Trust i WS-SecureConversation.<br /><br /> Jeśli ten atrybut jest `true`, powoduje negocjacji .NET SOAP, który tuneli SPNego exchange za pośrednictwem wiadomości SOAP.<br /><br /> Wartość domyślna to `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite Attribute  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Basic128|Użyj szyfrowania Basic128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.|  
|Basic192|Użyj szyfrowania Basic192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256|Użyj szyfrowania Basic256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Rsa15|Basic256 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Rsa15|Basic192 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDes|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Rsa15|Basic128 używany do szyfrowania wiadomości, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesRsa15|Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic128Sha256|Basic256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic192Sha256|Basic192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic256Sha256|Basic256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|TripleDesSha256|TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.|  
|Basic128Sha256Rsa15|Basic128 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic192Sha256Rsa15|Basic192 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|Basic256Sha256Rsa15|Basic256 używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
|TripleDesSha256Rsa15|TripleDes używany do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Dzięki usłudze na współdziałanie z anonimowego klientów. Na stronie usługi oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, klient nie ma żadnych poświadczeń klienta.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli używany jest tryb zabezpieczeń komunikatów i `negotiateServiceCredential` atrybut ma ustawioną `false`, klient musi zostać zainicjowana obsługa certyfikatu usługi.|  
|IssuedToken|Określa niestandardowy token, zwykle wystawiane przez usługę tokenu zabezpieczającego.|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń UserName. Usługi WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości. Usługi WCF wymusza tak, czy transport jest zabezpieczone przy użyciu poświadczeń UserName. W tym trybie poświadczenia powoduje wymianę interoperacyjne lub -interoperacyjne negocjacji, na podstawie `negotiateServiceCredential` atrybutu.|  
|Windows|Umożliwia wymianę SOAP się pod uwierzytelnionego kontekstu poświadczenia systemu Windows. Jeśli `negotiateServiceCredential` atrybut ma ustawioną `true`, to albo przeprowadza negocjowanie interfejsu SSPI protokołu Kerberos (interoperacyjne standard).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definiuje ustawienia zabezpieczeń dla [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
