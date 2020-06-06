---
title: <Application>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: e26826b3d8674b536ab0897182da58bc02cfd00b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128518"
---
# <a name="application-element-net-native"></a>\<Application>— Element (.NET Native)
Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania, i stosuje zasady odbicia środowiska uruchomieniowego do wszystkich elementów programu w aplikacji.  
  
 \<Directives> Element  
\<Application>— Element (RD. xml)  
  
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
|`DataContractSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Opcjonalny atrybut. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Interop|Opcjonalny atrybut. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Opcjonalny atrybut. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Opcjonalny atrybut. Steruje zasadami organizowania struktur w kodzie natywnym.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie tych zasad, które mają być stosowane do typów w aplikacji. Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace>](namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w konkretnym obszarze nazw.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady do określonego typu, na przykład klasy lub struktury.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element może służyć do definiowania zasad dla `List<String>` typu.|  
|[\<Method>](method-element-net-native.md)|Stosuje zasady do metody dla określonego typu.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanej metody ogólnej.|  
|[\<Property>](property-element-net-native.md)|Stosuje zasady do właściwości określonego typu.|  
|[\<Field>](field-element-net-native.md)|Stosuje zasady do pola określonego typu.|  
|[\<Event>](event-element-net-native.md)|Stosuje zasady do zdarzenia w określonym typie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Element główny pliku dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [\<Directives>](directives-element-net-native.md)Element może zawierać zero lub jeden `<Application>` element. Wiele `<Application>` elementów w jednym pliku dyrektywy odbicia nie jest obsługiwane.  
  
 `<Application>`Element może być używany na jeden z dwóch sposobów:  
  
- Jako kontener do definiowania elementów programu, których metadane są konieczne w czasie wykonywania. W takim przypadku `<Application>` element nie musi mieć żadnych atrybutów. W czasie kompilacji narzędzia kompilatora przeszukują wszystkie biblioteki, w tym .NET Framework biblioteki podstawowe, dla elementów programu identyfikowanych przez elementy podrzędne `<Application>` elementu. W przeciwieństwie do narzędzia kompilatora przeszukiwana jest tylko biblioteka wyznaczony przez [\<Library>](library-element-net-native.md) element dla elementów programu identyfikowanych przez elementy podrzędne [\<Library>](library-element-net-native.md) .  
  
- Jako element, który ustawia zasady dla całej aplikacji na potrzeby odbicia, serializacji i międzyoperacyjności. Atrybuty `<Application>` elementu definiują zasady na poziomie aplikacji, które mogą zostać zastąpione przez elementy podrzędne zdefiniowane przez `<Application>` [\<Library>](library-element-net-native.md) element lub.  
  
## <a name="see-also"></a>Zobacz także

- [\<Library>Postaci](library-element-net-native.md)
- [\<Directives>Postaci](directives-element-net-native.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
