---
title: <AttributeImplies> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d59f1f48be19a21ccc7ee5bb73cebfffc387fec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165064"
---
# <a name="attributeimplies-element-net-native"></a>\<AttributeImplies > (architektura .NET Native)
Definiuje zasady dla elementów kodu, który zawierającego atrybut jest stosowany do.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Usługa międzyoperacyjna|Atrybut opcjonalny. Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.|  
|`MarshalDelegate`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.|  
|`MarshalStructure`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady dla marshaling typów wartości do kodu natywnego.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 `<AttributeImplies>` Element jest używany, jeśli jej typ zawierający jest atrybutem (to znaczy, klasę pochodną <xref:System.Attribute?displayProperty=nameWithType>). Jeśli ten atrybut jest stosowany do elementu określonego programu, zasady zdefiniowane przez `<AttributeImplies>` element ma zastosowanie do tego elementu programu.  
  
 Odbicia, serializacja i atrybutów międzyoperacyjności są wszystkie opcjonalne, ale co najmniej jeden powinien być obecny.  
  
## <a name="see-also"></a>Zobacz także

- [\<Typ > Element](../../../docs/framework/net-native/type-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
