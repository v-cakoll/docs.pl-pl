---
title: Element &lt;Namespace&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89c9edf47edcb5089e094529b8e8108271518d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590581"
---
# <a name="ltnamespacegt-element-net-native"></a>Element &lt;Namespace&gt; (architektura .NET Native)
Zastosowanie zasad odbicia środowiska uruchomieniowego dla wszystkich typów w określonej przestrzeni nazw.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Usługa międzyoperacyjna|Atrybut opcjonalny. Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.|  
|`MarshalDelegate`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.|  
|`MarshalStructure`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady marshalingu struktur do kodu macierzystego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*namespace_name*|Nazwa przestrzeni nazw. Jeśli \<Namespace > element jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md), [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md), lub [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu *namespace_name* musi być w pełni kwalifikowanej nazwy obszaru nazw. Jeśli \<Namespace > element jest elementem podrzędnym innego \<Namespace > elementu *namespace_name* musi być nazwą względną przestrzeni nazw.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad dla wszystkich typów w przestrzeni nazw. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<Namespace>`|Dotyczy wszystkich typów w przestrzeni nazw nadrzędnego zasad odbicia środowiska uruchomieniowego.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Zastosowanie zasad odbicia do typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) element może mieć zero, co najmniej jeden [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementów.|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Dotyczy wszystkich typów w określonym zestawie zasad odbicia środowiska uruchomieniowego.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element może mieć zero lub jeden [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.|  
|`<Namespace>`|Ma zastosowanie zasad odbicia do wszystkich typów w nadrzędna przestrzeń nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `Activate`, `Browse`, `Dynamic`, I `Serialize` atrybuty są wszystkie opcjonalne. Jeśli żaden nie jest obecny, `<Namespace>` element służy tylko jako kontener dla elementów podrzędnych. Jeśli są obecne, `<Namespace>` element dotyczy wszystkich typów w określonej przestrzeni nazw zasad odbicia środowiska uruchomieniowego.  
  
 Gdy jest elementem podrzędnym [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu `<Namespace>` element zastąpienia zasad odbicia środowiska uruchomieniowego, które są definiowane przez [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Zobacz także
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
