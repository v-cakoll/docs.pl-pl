---
title: '&lt;message&gt; w &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae44c80f99b2753b4914ff0844fd9538f3ac3f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>&lt;message&gt; w &lt;netTcpBinding&gt;
Określa typ zabezpieczenia na poziomie komunikatu wymagania dotyczące punkt końcowy skonfigurowany [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<System. ServiceModel >  
\<powiązania >  
\<netTcpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<komunikat >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`algorithmSuite`|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Algorytmy i klucza rozmiary są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> W poniższej tabeli przedstawiono możliwe wartości. Wartość domyślna to `Basic256`.<br /><br /> Jeśli powiązanie usługi Określa `algorithmSuite` wartość, która nie jest równa domyślne, a Generowanie pliku konfiguracji, przy użyciu Svcutil.exe, a następnie nie jest poprawnie wygenerowany i musi ręcznie edytować plik konfiguracji, aby ustawić wartość tego atrybutu żądaną wartość.|  
|`clientCredentialType`|Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta za pomocą zabezpieczenia na poziomie wiadomości. W poniższej tabeli przedstawiono możliwe wartości. Wartość domyślna to `UserName`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
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
|Brak|Dzięki usłudze na współdziałanie z anonimowego klientów. W usłudze oznacza to, że usługa nie wymaga żadnych poświadczeń klienta. Na komputerze klienckim oznacza to, klient nie ma żadnych poświadczeń klienta.|  
|Windows|Umożliwia wymianę SOAP się pod uwierzytelnionego kontekstu poświadczenia systemu Windows.|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń UserName. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości. W efekcie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczone przy użyciu poświadczeń UserName. W tym trybie poświadczenia powoduje wymianę interoperacyjne lub -interoperacyjne negocjacji, na podstawie `negotiateServiceCredential` atrybutu.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu. Jeśli używany jest tryb zabezpieczeń komunikatów i `negotiateServiceCredential` atrybut ma ustawioną `false`, klient musi zostać zainicjowana obsługa certyfikatu usługi.|  
|IssuedToken|Określa niestandardowy token, zwykle wydany przez zabezpieczenia tokenu usługi (STS).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definiuje funkcje zabezpieczeń dla <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikat używa zabezpieczenia na poziomie komunikatu, integralności i poufności komunikatu protokołu SOAP, a także do wzajemnego uwierzytelniania komunikacji elementów równorzędnych. Zaznaczenie tego trybu zabezpieczeń dla powiązania stosu kanał jest skonfigurowany z elementami powiązanie zabezpieczeń komunikatów i zabezpieczonych wiadomości SOAP z zasadami usługi WS-Security * standardów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
