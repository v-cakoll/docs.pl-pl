---
title: <MethodInstantiation> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae15e6d61267feb0388170ee27dcd939035329b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121696"
---
# <a name="methodinstantiation-element-net-native"></a>\<MethodInstantiation > (architektura .NET Native)
Ma zastosowanie zasad odbicia środowiska uruchomieniowego do skonstruowanego metody rodzajowej.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę metody.|  
|`Signature`|Ogólne|Atrybut opcjonalny. Określa nazwane parametry metody. Wiele parametry nazwane są oddzielone przecinkami. `Signature` Atrybut jest używany do odróżnienia przeciążonych metod.|  
|`Arguments`|Ogólne|Atrybut wymagany. Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa wykonanie zapytania dotyczącego informacji o wyliczanie metody, ale nie uwzględnia żadnych wywołanie dynamiczne w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Dostęp do środowiska uruchomieniowego formanty do konstruktora lub metody, aby włączyć dynamiczne programowania. Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Określa nazwane parametry metody. Jeśli podano wiele parametrów są oddzielone przecinkami.|  
  
## <a name="arguments-attribute"></a>Argumenty atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_arguments*|Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami. Każdy argument musi zawierać w pełni kwalifikowana nazwa typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad dla metody. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 `<MethodInstantiation>` Element zastąpienia zasad odbicia środowiska uruchomieniowego odpowiedniego Otwórz metody rodzajowej.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [\<Metoda > Element](../../../docs/framework/net-native/method-element-net-native.md)
