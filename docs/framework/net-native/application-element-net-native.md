---
title: Element <Application> (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: e26826b3d8674b536ab0897182da58bc02cfd00b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128518"
---
# <a name="application-element-net-native"></a>\<> aplikacji (.NET Native)
Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania, i stosuje zasady odbicia środowiska uruchomieniowego do wszystkich elementów programu w aplikacji.  
  
 Dyrektywy \<> element  
\<> aplikacji (RD. xml)  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne. W tabeli elementy podrzędne zasady odnoszą się do rodzaju metadanych, które są udostępniane dla określonych elementów programu w czasie wykonywania.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie typów, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Opcjonalny atrybut. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Opcjonalny atrybut. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Opcjonalny atrybut. Steruje zasadami organizowania struktur w kodzie natywnym.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie tych zasad, które mają być stosowane do typów w aplikacji. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zestawu >](assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<przestrzeni nazw >](namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w konkretnym obszarze nazw.|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady do określonego typu, na przykład klasy lub struktury.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład element [\<TypeInstantiation >](typeinstantiation-element-net-native.md) może służyć do definiowania zasad dla typu `List<String>`.|  
|[> metody\<](method-element-net-native.md)|Stosuje zasady do metody dla określonego typu.|  
|[\<MethodInstantiation >](methodinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanej metody ogólnej.|  
|[\<Właściwość >](property-element-net-native.md)|Stosuje zasady do właściwości określonego typu.|  
|[\<pole >](field-element-net-native.md)|Stosuje zasady do pola określonego typu.|  
|[> zdarzeń \<](event-element-net-native.md)|Stosuje zasady do zdarzenia w określonym typie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Dyrektywy \<](directives-element-net-native.md)|Element główny pliku dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [Dyrektywy\<](directives-element-net-native.md) element może zawierać zero lub jeden element `<Application>`. Wiele elementów `<Application>` w jednym pliku dyrektywy odbicia nie jest obsługiwane.  
  
 Elementu `<Application>` można użyć na jeden z dwóch sposobów:  
  
- Jako kontener do definiowania elementów programu, których metadane są konieczne w czasie wykonywania. W takim przypadku element `<Application>` nie musi mieć żadnych atrybutów. W czasie kompilacji narzędzia kompilatora przeszukują wszystkie biblioteki, w tym .NET Framework biblioteki podstawowe, dla elementów programu identyfikowanych przez elementy podrzędne elementu `<Application>`. W przeciwieństwie do narzędzia kompilatora przeszukiwana jest tylko biblioteka wyznaczony przez [bibliotekę\<](library-element-net-native.md) element dla elementów programu identyfikowanych przez elementy podrzędne [biblioteki\<](library-element-net-native.md).  
  
- Jako element, który ustawia zasady dla całej aplikacji na potrzeby odbicia, serializacji i międzyoperacyjności. Atrybuty elementu `<Application>` definiują zasady na poziomie aplikacji, które mogą zostać zastąpione przez elementy podrzędne zdefiniowane przez `<Application>` lub [\<](library-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Zobacz także

- [\<Biblioteka > element](library-element-net-native.md)
- [Dyrektywy \<> element](directives-element-net-native.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
