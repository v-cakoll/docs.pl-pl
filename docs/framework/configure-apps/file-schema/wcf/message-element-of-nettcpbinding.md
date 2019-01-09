---
title: '&lt;message&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 7af8cd9d36b56093eee2b53873c0fe0775a33430
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146163"
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>&lt;message&gt; w &lt;netTcpBinding&gt;
Określa typ zabezpieczenia na poziomie wiadomości dotyczące punkty końcowe skonfigurowane za pomocą [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netTcpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<message>  
  
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
|`algorithmSuite`|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Te algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).<br /><br /> Możliwe wartości zostały przedstawione w poniższej tabeli. Wartość domyślna to `Basic256`.<br /><br /> Jeśli powiązanie usługi Określa `algorithmSuite` wartość, która nie jest równa domyślne, a Generowanie pliku konfiguracji, za pomocą Svcutil.exe, a następnie nie jest poprawnie generowane i należy ręcznie zmodyfikować plik konfiguracji, aby ustawić ten atrybut żądaną wartość.|  
|`clientCredentialType`|Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikat. Możliwe wartości zostały przedstawione w poniższej tabeli. Wartość domyślna to `UserName`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
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
|Brak|Dzięki usłudze na współdziałanie z anonimowych klientów. W usłudze oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, że klient nie zawiera żadnych poświadczeń klienta.|  
|Windows|Umożliwia wymianę SOAP się być pod kontekst uwierzytelniania poświadczeń Windows.|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń UserName. Usługi WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia wiadomości. W efekcie WCF wymusza, czy transport jest zabezpieczony, korzystając z poświadczeń UserName. W tym trybie poświadczeń skutkuje międzyoperacyjnych programu exchange lub negocjacji międzyoperacyjnych, na podstawie `negotiateServiceCredential` atrybutu.|  
|Certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli używany jest tryb zabezpieczeń wiadomości i `negotiateServiceCredential` ma ustawioną wartość atrybutu `false`, klient musi być obsługiwana za pomocą certyfikatu usługi.|  
|IssuedToken|Określa niestandardowy token, zwykle wydany przez Usługa tokenu zabezpieczającego (STS).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definiuje funkcje bezpieczeństwa umożliwiające <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikat używa zabezpieczenia na poziomie komunikatu, integralności i poufności komunikatu protokołu SOAP, a także do wzajemnego uwierzytelniania komunikacji elementów równorzędnych. Zaznaczenie tego trybu zabezpieczeń w powiązaniu stosu kanał jest skonfigurowany przy użyciu elementów powiązanie zabezpieczeń komunikatów i komunikaty protokołu SOAP są zabezpieczone zgodnie z protokołu WS-Security * standardy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
