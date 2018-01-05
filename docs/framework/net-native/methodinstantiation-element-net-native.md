---
title: Element &lt;MethodInstantiation&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c888bf806744c5c62d130ec00b89838c52f67d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a>Element &lt;MethodInstantiation&gt; (architektura .NET Native)
Stosuje zasad wykonywania odbicia do skonstruowanego metody rodzajowej.  
  
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
|`Signature`|Ogólne|Atrybut opcjonalny. Określa nazwane parametry metody. Wiele nazwanych parametrów są oddzielone przecinkami. `Signature` Atrybut służy do rozróżnienia przeciążonej metody.|  
|`Arguments`|Ogólne|Atrybut wymagany. Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania. Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Określa nazwane parametry metody. Jeśli podano wiele parametrów są oddzielone przecinkami.|  
  
## <a name="arguments-attribute"></a>Argumentów atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_arguments*|Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami. Każdy argument musi zawierać nazwę FQDN typu.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|To ustawienie, aby zastosować do tego typu w metodzie. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 `<MethodInstantiation>` Element zastępuje zasad odbicia wykonywania odpowiednich Otwórz metody ogólnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<Metoda > — Element](../../../docs/framework/net-native/method-element-net-native.md)
