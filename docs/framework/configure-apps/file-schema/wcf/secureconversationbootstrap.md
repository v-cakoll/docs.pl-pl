---
title: '&lt;secureConversationBootstrap&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8b29b9b4253e51f8cc1d0625fb27998a2d10b3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<secureConversationBootstrap >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|Opcjonalny. Wartość logiczna, która określa, czy szeregowanego tokenu można używać w odpowiedzi. Wartość domyślna to `false`. Korzystając z podwójną powiązanie, ustawienie domyślnie `true` każdego ustawienia wprowadzone zostaną zignorowane.|  
|`authenticationMode`|Określa tryb uwierzytelniania SOAP między inicjatorem i obiekt odpowiadający.<br /><br /> Wartość domyślna to sspiNegotiated.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Definiuje pakiet algorytmów zabezpieczeń z różnych algorytmów, takich jak zapewniania kanoniczności, Digest, KeyWrap, podpisu, szyfrowanie oraz keyderivation. Każdy z mechanizmów zabezpieczeń algorytmu definiuje wartości dla różnych parametrów. Zabezpieczenia na poziomie komunikatu jest osiągane przy użyciu tych algorytmów.<br /><br /> Ten atrybut jest używany podczas pracy z innej platformie, która zdecyduje się na zestawem algorytmów innych niż domyślne. Należy pamiętać o słabych algorytmów odpowiednich i po zmodyfikowaniu tego ustawienia. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Wartość domyślna to `Basic256`.|  
|`includeTimestamp`|Wartość logiczna określająca czy sygnatury czasowe są umieszczane w każdej wiadomości. Wartość domyślna to `true`.|  
|`keyEntropyMode`|Określa sposób, że są obliczane klucze dla zabezpieczenia wiadomości. Klucze może być oparta na klienta klucza materiałów, usługa materiału klucza tylko lub obie te grupy. Prawidłowe wartości to:<br /><br /> -ClientEntropy: Klucz sesji na podstawie klienta pod warunkiem materiału klucza.<br />-ServerEntropy: Klucz sesji na podstawie usług materiału klucza.<br />-CombinedEntropy: Klucz sesji opiera się poza klienta i usługi dostępne materiału klucza.<br /><br /> Wartość domyślna to CombinedEntropy.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Ustawia kolejność, w jaki komunikat algorytmy poziomu zabezpieczenia są stosowane do wiadomości. Prawidłowe wartości są następujące:<br /><br /> -SignBeforeEncrypt: Zaloguj się najpierw, a następnie szyfrować.<br />-SignBeforeEncryptAndEncryptSignature: Podpisywania, szyfrowania i szyfrowania podpisu.<br />-EncryptBeforeSign: Najpierw szyfrowania, a następnie zaloguj się.<br /><br /> SignBeforeEncryptAndEncryptSignature jest wartością domyślną, używając wzajemnymi certyfikatami 1.1 WS-Security.  SignBeforeEncrypt jest wartością domyślną z WS-Security w wersji 1.0.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Ustawia wersję WS-Security, która jest używana. Prawidłowe wartości są następujące:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> Wartość domyślna to WSSecurityXXX2005. Ten atrybut jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Wartość logiczna określająca, czy klucze mogą być uzyskane z oryginalnych kluczy dowodu. Wartość domyślna to `true`.|  
|`requireSecurityContextCancellation`|Wartość logiczna określająca, czy kontekstu zabezpieczeń powinny być anulowany i zakończony, kiedy nie jest już wymagane. Wartość domyślna to `true`.|  
|`requireSignatureConfirmation`|Wartość logiczna określająca, czy włączone jest potwierdzenie podpisu WS-Security. Jeśli wartość `true`, odpowiadający potwierdzają sygnatury komunikatów. Wartość domyślna to `false`.<br /><br /> Potwierdzenie podpisu jest używana do upewnij się, czy usługa odpowiada w pełną świadomość żądania.|  
|`securityHeaderLayout`|Określa kolejność elementów w nagłówku zabezpieczeń. Prawidłowe wartości to:<br /><br /> -Strict. Elementy są dodawane do nagłówka zabezpieczeń zgodnie z ogólną zasadę "deklaruje przed użyciem".<br />-Swobodny. Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP.<br />-LaxWithTimestampFirst. Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP z tą różnicą, że pierwszym elementem w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br />-LaxWithTimestampLast. Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który potwierdza WSS: zabezpieczeń wiadomości protokołu SOAP z tą różnicą, że ostatnim elementem w nagłówku zabezpieczeń musi być elementem wsse:Timestamp.<br /><br /> Wartość domyślna to Strict.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa bieżący wystawionego tokenu. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
