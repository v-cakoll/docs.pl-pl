---
title: <Application> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b858b9daad22cdda6df30be7b28cdecfd275b8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228305"
---
# <a name="application-element-net-native"></a>\<Aplikacja > (architektura .NET Native)
Służy jako kontener dla całej aplikacji, typy i składowe typu, którego metadanych dotyczących odbicia w czasie wykonywania oraz będzie miało zastosowanie zasad odbicia środowiska uruchomieniowego do wszystkich elementów programu w aplikacji.  
  
 \<Dyrektywy > Element  
\<Aplikacja > — Element (rd.xml)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne. W tabeli elementów podrzędnych zasad odwołuje się do rodzaju metadanych, który ma zostać udostępnione dla elementów konkretnego programu w czasie wykonywania.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa wykonanie zapytania dotyczącego informacji o wyliczanie typów, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Usługa międzyoperacyjna|Atrybut opcjonalny. Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.|  
|`MarshalDelegate`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.|  
|`MarshalStructure`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady marshalingu struktur do kodu macierzystego.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie dla tej zasady mają zastosowanie do typów w aplikacji. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje zasady do określonego typu, takie jak klasy lub struktury.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do definiowania zasad dla `List<String>` typu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Stosuje zasady do metody dla określonego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego metody rodzajowej.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady do właściwości dla określonego typu.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Stosuje zasady do pola dla określonego typu.|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Stosuje zasady do zdarzenia określonego typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)|Element główny plik dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero lub jeden `<Application>` elementu. Wiele `<Application>` elementy w pliku dyrektywy pojedynczego odbicia nie są obsługiwane.  
  
 `<Application>` Elementu mogą być używane w jeden z dwóch sposobów:  
  
-   Jako kontener, aby zdefiniować elementy programu, w których metadanych jest potrzebnych w czasie wykonywania. W tym przypadku `<Application>` elementu nie wymagają żadnych atrybutów. W czasie kompilacji narzędzia kompilatora wyszukiwać wszystkie biblioteki, w tym podstawowe biblioteki .NET Framework, dla elementów programu identyfikowane przez elementy podrzędne `<Application>` elementu. Z kolei narzędzia kompilatora wyszukiwanie tylko w bibliotece, które są oznaczane [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element dla elementów programu identyfikowane przez elementy podrzędne [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Jako element, który ustawia zasady dla całej aplikacji odbicia, serializacja i współdziałania. Atrybuty `<Application>` element Definiowanie zasad całej aplikacji, które mogą zostać zastąpione przez elementy podrzędne, zdefiniowane przez `<Application>` lub [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Zobacz także

- [\<Biblioteka > Element](../../../docs/framework/net-native/library-element-net-native.md)
- [\<Dyrektywy > Element](../../../docs/framework/net-native/directives-element-net-native.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
