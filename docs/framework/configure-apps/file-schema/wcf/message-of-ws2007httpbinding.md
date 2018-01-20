---
title: '&lt;message&gt; w &lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88f9a766c85ec0fd6cb3379be239db33dc6ebb20
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltws2007httpbindinggt"></a>&lt;message&gt; w &lt;ws2007HttpBinding&gt;
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
 <binding >  
  <security>  
   <message clientCredentialType =  
    "None/Windows/UserName/Certificate/IssuedToken"  
    establishSecurityContext="Boolean"  
    negotiateServiceCredential="Boolean"  
    algorithmSuite= Enumeration. See algorithmSuite Attribute below.  
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
|`algorithmSuite`|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Wartość domyślna to Basic256.|  
|`clientCredentialType`|Opcjonalny. Określa typ poświadczenia, który będzie używany podczas uwierzytelniania klienta przy użyciu trybu zabezpieczeń `Message` lub `TransportWithMessageCredentials`. Zobacz wartości wyliczenia w poniższej tabeli. Wartość domyślna to Windows.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Wartość, która określa, czy kanał zabezpieczeń ustanawia bezpiecznej sesji. Bezpieczna sesja ustanawia token kontekstu zabezpieczeń (SCT) przed rozpoczęciem wymiany komunikatów aplikacji. Po nawiązaniu SCT kanału zabezpieczeń oferuje <xref:System.ServiceModel.Channels.ISession> interfejs do górnej kanałów. Aby uzyskać więcej informacji o korzystaniu z bezpiecznej sesji, zobacz [porady: tworzenie bezpiecznej sesji](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Wartość domyślna to `true`.|  
|`negotiateServiceCredential`|Opcjonalny. Wartość, która określa, czy poświadczenia usługi jest udostępniane po stronie klienta poza pasmem lub są uzyskiwane z usługi do klienta w procesie negocjacji. Takie negocjacji jest macierzystych do programu exchange zwykle wiadomości.<br /><br /> Jeśli `clientCredentialType` atrybut ma wartość None, nazwa użytkownika lub certyfikatu, ustawienie tego atrybutu na `false` oznacza to, że certyfikat usługi jest dostępny na kliencie poza pasmem klienta należy określić certyfikat usługi (za pomocą [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) w [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zachowania usługi. Ten tryb jest współpraca z implementacji protokołu WS-Trust i WS-SecureConversation stosy protokołu SOAP.<br /><br /> Jeśli `ClientCredentialType` atrybut ma ustawioną `Windows`, ustawienie tego atrybutu na `false` określa uwierzytelniania opartego na protokołu Kerberos. Oznacza to, że klient i usługa muszą być częścią tej samej domeny protokołu Kerberos. Ten tryb jest współpraca z wdrożenia profilu token protokołu Kerberos (zgodnie z definicją w OASIS TC programu WSS) oraz protokołu WS-Trust i WS-SecureConversation stosy protokołu SOAP.<br /><br /> Jeśli ten atrybut jest `true`, powoduje negocjacji protokołu SOAP .NET, który tuneli <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange za pośrednictwem wiadomości SOAP.<br /><br /> Wartość domyślna to `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite Attribute  
  
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
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Dzięki usłudze na współdziałanie z anonimowego klientów. W usłudze oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, klient nie ma żadnych poświadczeń klienta.|  
|`Certificate`|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli `message` używany jest tryb zabezpieczeń i `negotiateServiceCredential` atrybut ma ustawioną `false`, klient musi zostać zainicjowana obsługa certyfikatu usługi.|  
|`IssuedToken`|Określa niestandardowy token, zwykle wydany przez zabezpieczenia tokenu usługi (STS).|  
|`UserName`|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą `UserName` poświadczeń. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości. W efekcie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczone przy użyciu `UserName` poświadczeń. W tym trybie poświadczenia powoduje wymianę interoperacyjne lub -interoperacyjne negocjacji, na podstawie `negotiateServiceCredential` atrybutu.|  
|`Windows`|Umożliwia wymianę SOAP się pod uwierzytelnionego kontekście `Windows` poświadczeń. Jeśli `negotiateServiceCredential` atrybut ma ustawioną `true`, to albo przeprowadza negocjowanie interfejsu SSPI protokołu Kerberos (interoperacyjne standard).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń dla [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
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
