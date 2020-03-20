---
title: <Namespace>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180955"
---
# <a name="namespace-element-net-native"></a>\<Obszar nazw> element (natywny.NET)
Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym obszarze nazw.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
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
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę przestrzeni nazw.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania struktur do kodu macierzystego.|  
  
## <a name="name-attribute"></a>Atrybut Nazwa  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*namespace_name*|Nazwa obszaru nazw. \<Jeśli element> obszaru nazw jest elementem podrzędnym [ \<>aplikacji, ](application-element-net-native.md) [ \<biblioteki>](library-element-net-native.md)lub *namespace_name* [ \<](assembly-element-net-native.md) elementu>zestawu, namespace_name musi być w pełni kwalifikowaną nazwą obszaru nazw. \<Jeśli element> obszaru nazw jest elementem \<podrzędnym innego elementu> obszaru nazw, *namespace_name* musi być nazwą względnego obszaru nazw.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad dla wszystkich typów w obszarze nazw. Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<Namespace>`|Stosuje zasady odbicie środowiska uruchomieniowego do wszystkich typów w nadrzędnej przestrzeni nazw.|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<>typu>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>aplikacji](application-element-net-native.md)|Służy jako kontener dla typów całej aplikacji i członków typu, których metadane są dostępne do odbicia w czasie wykonywania. [ \<Element>aplikacji](application-element-net-native.md) może mieć zero, jeden lub więcej [ \<elementów>zestawu.](assembly-element-net-native.md)|  
|[\<>montażowe](assembly-element-net-native.md)|Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym zestawie.|  
|[\<>biblioteczna](library-element-net-native.md)|Definiuje zestaw, który zawiera typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [ \<Element>biblioteki](library-element-net-native.md) może mieć zero lub jeden [ \<](assembly-element-net-native.md) element zestawu>.|  
|`<Namespace>`|Stosuje zasady odbicia do wszystkich typów w nadrzędnej przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `Activate`Atrybuty `Browse` `Dynamic`, `Serialize` i atrybuty są opcjonalne. Jeśli żaden z `<Namespace>` nich nie są obecne, element służy tylko jako kontener dla elementów podrzędnych. Jeśli są one `<Namespace>` obecne, element stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym obszarze nazw.  
  
 Gdy jest elementem podrzędnym [ \<elementu Assembly>,](assembly-element-net-native.md) `<Namespace>` element zastępuje zasady odbicia środowiska wykonawczego zdefiniowane [ \<](assembly-element-net-native.md) przez element Zestawu>.  
  
## <a name="see-also"></a>Zobacz też

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
