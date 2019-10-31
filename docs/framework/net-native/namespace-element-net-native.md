---
title: Element <Namespace> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: b6d7a45de14d0fb8eb2e27a02c86510f630be9e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128264"
---
# <a name="namespace-element-net-native"></a>\<> elementu przestrzeni nazw (.NET Native)
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania struktur w kodzie natywnym.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*namespace_name*|Nazwa przestrzeni nazw. Jeśli element > \<przestrzeń nazw jest elementem podrzędnym [\<aplikacji >](application-element-net-native.md), [\<biblioteki](library-element-net-native.md)> lub [\<zestawu](assembly-element-net-native.md) >, *namespace_name* musi być w pełni kwalifikowaną nazwą przestrzeni nazw. Jeśli \<przestrzeni nazw > element jest elementem podrzędnym innego \<przestrzeni nazw > elementu, *namespace_name* musi być względną nazwą przestrzeni nazw.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla wszystkich typów w przestrzeni nazw. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<Namespace>`|Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w nadrzędnej przestrzeni nazw.|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> aplikacji](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. Element [\<> aplikacji](application-element-net-native.md) może mieć zero, jeden lub więcej\<elementów [> zestawu](assembly-element-net-native.md) .|  
|[\<zestawu >](assembly-element-net-native.md)|Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym zestawie.|  
|[Biblioteka \<](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [Biblioteka\<](library-element-net-native.md) element może mieć zero lub jeden element [> zestawu\<](assembly-element-net-native.md) .|  
|`<Namespace>`|Stosuje zasady odbicia do wszystkich typów w nadrzędnej przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybuty `Activate`, `Browse`, `Dynamic`i `Serialize` są opcjonalne. Jeśli żaden nie istnieje, element `<Namespace>` służy tylko jako kontener dla elementów podrzędnych. Jeśli są obecne, element `<Namespace>` stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonej przestrzeni nazw.  
  
 Gdy jest elementem podrzędnym [\<zestawu >](assembly-element-net-native.md) , element `<Namespace>` zastępuje zasady odbicia środowiska uruchomieniowego zdefiniowane przez [\<zestawu >](assembly-element-net-native.md) .  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
