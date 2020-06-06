---
title: <Namespace>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180955"
---
# <a name="namespace-element-net-native"></a>\<Namespace>— Element (.NET Native)
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
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania struktur w kodzie natywnym.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*namespace_name*|Nazwa przestrzeni nazw. Jeśli \<Namespace> element jest elementem podrzędnym [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) elementu,, lub [\<Assembly>](assembly-element-net-native.md) , *namespace_name* musi być w pełni kwalifikowaną nazwą przestrzeni nazw. Jeśli \<Namespace> element jest elementem podrzędnym innego \<Namespace> elementu, *namespace_name* musi być względną nazwą przestrzeni nazw.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla wszystkich typów w przestrzeni nazw. Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<Namespace>`|Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w nadrzędnej przestrzeni nazw.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. [\<Application>](application-element-net-native.md)Element może mieć zero, jeden lub więcej [\<Assembly>](assembly-element-net-native.md) elementów.|  
|[\<Assembly>](assembly-element-net-native.md)|Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym zestawie.|  
|[\<Library>](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [\<Library>](library-element-net-native.md)Element może mieć zero lub jeden [\<Assembly>](assembly-element-net-native.md) element.|  
|`<Namespace>`|Stosuje zasady odbicia do wszystkich typów w nadrzędnej przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `Activate`Atrybuty, `Browse` , `Dynamic` i `Serialize` są opcjonalne. Jeśli żaden nie jest obecny, `<Namespace>` element służy tylko jako kontener dla elementów podrzędnych. Jeśli są obecne, `<Namespace>` element stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym obszarze nazw.  
  
 Gdy jest elementem podrzędnym [\<Assembly>](assembly-element-net-native.md) elementu, `<Namespace>` element zastępuje zasady odbicia środowiska uruchomieniowego zdefiniowane przez [\<Assembly>](assembly-element-net-native.md) element.  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
