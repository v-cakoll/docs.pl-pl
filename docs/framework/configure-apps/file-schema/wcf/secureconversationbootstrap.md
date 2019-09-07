---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: b3187cb51b6fd32797c9ad401c704d5f16c6f7e8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399912"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationBootstrap >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
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
|`allowSerializedSigningTokenOnReply`|Opcjonalna. Wartość logiczna określająca, czy serializowany token może być używany w odpowiedzi. Wartość domyślna to `false`. W przypadku korzystania z podwójnego powiązania ustawienie domyślnie `true` zostanie zignorowane.|  
|`authenticationMode`|Określa tryb uwierzytelniania SOAP używany między inicjatorem a obiektem odpowiadającym.<br /><br /> Wartość domyślna to sspiNegotiated.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Pakiet algorytmów zabezpieczeń definiuje różne algorytmy, takie jak kanonizacja, skróty, zawijanie, sygnatura, szyfrowanie i algorytmy wyznaczania wartości. Każdy pakiet algorytmów zabezpieczeń definiuje wartości dla tych różnych parametrów. Zabezpieczenia oparte na komunikatach są osiągane przy użyciu tych algorytmów.<br /><br /> Ten atrybut jest używany podczas pracy z inną platformą, która powoduje, że zestaw algorytmów różni się od wartości domyślnej. Podczas wprowadzania modyfikacji tego ustawienia należy mieć świadomość siły i słabości odpowiednich algorytmów. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Wartość domyślna to `Basic256`.|  
|`includeTimestamp`|Wartość logiczna określająca, czy sygnatury czasowe są uwzględniane w poszczególnych wiadomościach. Wartość domyślna to `true`.|  
|`keyEntropyMode`|Określa sposób, w jaki są obliczane klucze służące do zabezpieczania komunikatów. Klucze mogą opierać się tylko na materiale klucza klienta, tylko w materiale klucza usługi lub kombinacji obu tych elementów. Prawidłowe wartości to:<br /><br /> - ClientEntropy: Klucz sesji jest oparty na kluczowym materiale dostarczonym przez klienta.<br />- ServerEntropy: Klucz sesji znajduje się na podstawie dostarczonego materiału klucza usługi.<br />- CombinedEntropy: Klucz sesji jest oparty na danych klienta i usługi dostarczonej przez usługę.<br /><br /> Wartość domyślna to CombinedEntropy.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Ustawia kolejność, w jakiej algorytmy zabezpieczeń na poziomie komunikatów są stosowane do wiadomości. Prawidłowe wartości to:<br /><br /> - SignBeforeEncrypt: Najpierw Podpisz, a następnie Szyfruj.<br />- SignBeforeEncryptAndEncryptSignature: Podpisywanie, szyfrowanie i szyfrowanie sygnatury.<br />- EncryptBeforeSign: Szyfruj najpierw, a następnie podpisz.<br /><br /> SignBeforeEncryptAndEncryptSignature jest wartością domyślną w przypadku korzystania z certyfikatów obustronnych z obsługą protokołu WS-Security 1,1.  SignBeforeEncrypt jest wartością domyślną przy użyciu protokołu WS-Security 1,0.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Ustawia wersję WS-Security, która jest używana. Prawidłowe wartości to:<br /><br /> - WSSecurityJan2004<br />- WSSecurityXXX2005<br /><br /> Wartość domyślna to WSSecurityXXX2005. Ten atrybut jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Wartość logiczna określająca, czy klucze mogą być uzyskane z oryginalnych kluczy dowodu. Wartość domyślna to `true`.|  
|`requireSecurityContextCancellation`|Wartość logiczna określająca, czy kontekst zabezpieczeń powinien być anulowany i zakończony, gdy nie jest już wymagany. Wartość domyślna to `true`.|  
|`requireSignatureConfirmation`|Wartość logiczna określająca, czy włączone jest potwierdzenie podpisu WS-Security. Po ustawieniu na `true`sygnatury komunikatów są potwierdzane przez obiekt odpowiadający. Wartość domyślna to `false`.<br /><br /> Potwierdzenie podpisu służy do potwierdzenia, że usługa reaguje na pełną świadomość żądania.|  
|`securityHeaderLayout`|Określa kolejność elementów w nagłówku zabezpieczeń. Prawidłowe wartości to:<br /><br /> Surowszych. Elementy są dodawane do nagłówka Security zgodnie z ogólną zasadą "DECLARE przed użyciem".<br />Swobodny. Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP.<br />- LaxWithTimestampFirst. Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP, z tą różnicą, że pierwszy element w nagłówku zabezpieczeń musi być elementem wsse: timestamp.<br />- LaxWithTimestampLast. Elementy są dodawane do nagłówka zabezpieczenia w dowolnej kolejności, która jest poprawna do programu WSS: Zabezpieczenia komunikatów protokołu SOAP, z tą różnicą, że ostatni element w nagłówku zabezpieczeń musi być elementem wsse: timestamp.<br /><br /> Wartość domyślna to Strict.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Określa bieżący token wystawiony. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Określa ustawienia zabezpieczeń lokalnego klienta dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Określa ustawienia zabezpieczeń usługi lokalnej dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
