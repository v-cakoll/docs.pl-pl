---
title: <AttributeImplies>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181066"
---
# <a name="attributeimplies-element-net-native"></a>\<Atrybut implikuje element> (natywny.NET)
Definiuje zasady dla elementów kodu, do których jest stosowany atrybut zawierający.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów wartości do kodu macierzystego.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad. Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<AttributeImplies>` jest używany, jeśli jego typ zawierający jest atrybutem (czyli klasą pochodną <xref:System.Attribute?displayProperty=nameWithType>). Jeśli atrybut jest stosowany do określonego elementu programu, zasady `<AttributeImplies>` zdefiniowane przez element stosuje się do tego elementu programu.  
  
 Atrybuty odbicia, serializacji i międzyoperacyjne są opcjonalne, chociaż co najmniej jeden powinien być obecny.  
  
## <a name="see-also"></a>Zobacz też

- [\<Wpisz element>](type-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
