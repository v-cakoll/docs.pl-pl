---
title: Element &lt;Namespace&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108c27747e0b823f2315a914f8db3c8711fbb698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltnamespacegt-element-net-native"></a>Element &lt;Namespace&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania odbicia do wszystkich typów w określonej przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type" />  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Współdziałanie|Atrybut opcjonalny. Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.|  
|`MarshalDelegate`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie struktur do kodu natywnego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*namespace_name*|Nazwa przestrzeni nazw. Jeśli \<Namespace > element jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md), [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md), lub [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu *namespace_name* musi być nazwą przestrzeni nazw FQDN. Jeśli \<Namespace > element jest elementem podrzędnym innego \<Namespace > elementu *namespace_name* musi być nazwą względną przestrzeni nazw.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad dla wszystkich typów w przestrzeni nazw. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<Namespace>`|Zastosowanie zasad wykonywania odbicia dla wszystkich typów w nadrzędną przestrzeń nazw.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) element może mieć wartość zero, co najmniej jeden [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementów.|  
|[\<zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zastosowanie zasad wykonywania odbicia do wszystkich typów w określonym zestawie.|  
|[\<Biblioteka >](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element może mieć wartość zero lub jeden [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.|  
|`<Namespace>`|Stosuje zasady odbicia do wszystkich typów w nadrzędną przestrzeń nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `Activate`, `Browse`, `Dynamic`, I `Serialize` atrybuty są wszystkie opcjonalne. Jeśli nie są obecne, `<Namespace>` elementu służy tylko jako kontener dla elementów podrzędnych. Jeśli są obecne, `<Namespace>` elementu dotyczy wszystkich typów w określonej przestrzeni nazw zasad wykonywania odbicia.  
  
 Gdy jest elementem podrzędnym [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu `<Namespace>` element zastąpienia zdefiniowane przez zasady odbicia środowiska uruchomieniowego [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
