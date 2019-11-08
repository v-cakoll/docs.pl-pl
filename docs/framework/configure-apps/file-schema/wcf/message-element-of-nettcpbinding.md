---
title: <message> element <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 76c4a0a30b637bc168855b091029a959b858401e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739009"
---
# <a name="message-element-of-nettcpbinding"></a>\<komunikat > elementu \<netTcpBinding >
Definiuje typ wymagań dotyczących zabezpieczeń na poziomie wiadomości dla punktu końcowego skonfigurowanego przy użyciu [\<netTcpBinding >](nettcpbinding.md).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetTcpBinding**](nettcpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-nettcpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`algorithmSuite`|Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy. Algorytmy i rozmiary kluczy są określane przez klasę <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Możliwe wartości przedstawiono w poniższej tabeli. Wartość domyślna to `Basic256`.<br /><br /> Jeśli powiązanie usługi określa wartość `algorithmSuite`, która nie jest równa wartości domyślnej, a plik konfiguracji zostanie wygenerowany przy użyciu Svcutil. exe, wówczas nie zostanie prawidłowo wygenerowany i trzeba ręcznie edytować plik konfiguracji, aby ustawić żądany atrybut wartościami.|  
|`clientCredentialType`|Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikatach. Możliwe wartości przedstawiono w poniższej tabeli. Wartość domyślna to `UserName`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
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
|Brak|Dzięki temu usługa może korzystać z anonimowych klientów. W usłudze oznacza to, że usługa nie wymaga poświadczeń klienta. Na kliencie wskazuje, że klient nie dostarcza poświadczeń klienta.|  
|Windows|Zezwala, aby wymiany SOAP były w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows.|  
|UserName|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu poświadczeń nazwy użytkownika. Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów. W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika. Ten tryb poświadczeń służy do samodzielnej wymiany lub negocjowania niewspółpracującego na podstawie atrybutu `negotiateServiceCredential`.|  
|Certyfikatu|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu certyfikatu. Jeśli jest używany tryb zabezpieczeń wiadomości, a atrybut `negotiateServiceCredential` jest ustawiony na `false`, klient musi być zainicjowany przy użyciu certyfikatu usługi.|  
|IssuedToken|Określa niestandardowy token, zazwyczaj wystawiony przez usługę tokenu zabezpieczającego (STS).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> zabezpieczeń \<](security-of-nettcpbinding.md)|Definiuje możliwości zabezpieczeń dla <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikat używa zabezpieczeń na poziomie komunikatów dla integralności i poufności komunikatu protokołu SOAP oraz do wzajemnego uwierzytelniania elementów równorzędnych komunikacji. Jeśli w powiązaniu wybrano ten tryb zabezpieczeń, stos kanału jest konfigurowany z elementami powiązania zabezpieczeń wiadomości, a komunikaty protokołu SOAP są zabezpieczone zgodnie ze standardami WS-Security *.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
