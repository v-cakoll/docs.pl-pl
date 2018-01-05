---
title: '&lt;message&gt; w &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e336d96b89c073c4ba7de6a746ba60d829013f25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a>&lt;message&gt; w &lt;wsDualHttpBinding&gt;
Definiuje zabezpieczenia na poziomie komunikatu [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<System. ServiceModel >  
\<powiązania >  
\<wsDualHttpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<komunikat >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Opcjonalny. Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Poniżej znajduje się możliwe wartości. Wartość domyślna to `Basic256`.|  
|Właściwość clientCredentialType|Opcjonalny. Określa typ poświadczenia, które będą używane podczas wykonywania uwierzytelniania klienta za pomocą trybu zabezpieczeń jest `Message`. Poniżej znajduje się możliwe wartości. Wartość domyślna to `Windows`.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Opcjonalny. Wartość logiczna określająca, czy poświadczenie usługi jest udostępniane po stronie klienta poza pasmem lub są uzyskiwane z usługi do klienta w procesie negocjacji. Takie negocjacji jest macierzystych do programu exchange zwykle wiadomości.<br /><br /> Jeśli `clientCredentialType` atrybut ma wartość None, nazwa użytkownika lub certyfikatu, ustawienie tego atrybutu na `false` oznacza, że certyfikat usługi jest dostępny po stronie klienta poza pasmem i że klienta należy określić certyfikat usługi (za pomocą [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) w [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zachowania usługi. Ten tryb jest współpraca z stosy SOAP, które implementują WS-Trust i WS-SecureConversation.<br /><br /> Jeśli `ClientCredentialType` atrybut ma ustawioną `Windows`, ustawienie tego atrybutu na `false` określa uwierzytelniania opartego na protokołu Kerberos. Oznacza to, że klient i usługa muszą być częścią tej samej domeny protokołu Kerberos. Ten tryb jest współpraca z stosy SOAP, implementujące profilu token protokołu Kerberos (zgodnie z definicją w OASIS TC programu WSS) oraz protokołu WS-Trust i WS-SecureConversation. Jeśli ten atrybut jest `true`, powoduje negocjacji .NET SOAP, który tuneli SPNego exchange za pośrednictwem wiadomości SOAP.<br /><br /> Wartość domyślna to `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atrybutu  
  
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
|Brak|Dzięki usłudze na współdziałanie z anonimowego klientów. Na stronie usługi oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, klient nie ma żadnych poświadczeń klienta.|  
|Windows|Umożliwia wymianę SOAP się pod uwierzytelnionego kontekstu poświadczenia systemu Windows. Jeśli `negotiateServiceCredential` atrybut ma ustawioną `true`, to albo przeprowadza negocjowanie interfejsu SSPI protokołu Kerberos (interoperacyjne standard).|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń UserName. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości. W efekcie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczone przy użyciu poświadczeń UserName. W tym trybie poświadczenia powoduje wymianę interoperacyjne lub -interoperacyjne negocjacji, na podstawie `negotiateServiceCredential` atrybutu.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli używany jest tryb zabezpieczeń komunikatów i `negotiateServiceCredential` atrybut ma ustawioną `false`, klient musi zostać zainicjowana obsługa certyfikatu usługi.|  
|IssuedToken|Określa niestandardowy token, zwykle wystawiane przez usługę tokenu zabezpieczającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Możliwości zabezpieczeń definiuje [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
