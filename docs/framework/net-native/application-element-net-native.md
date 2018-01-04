---
title: Element &lt;Application&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c486faf43a1109b0391f40072ab267b72e1d07d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationgt-element-net-native"></a>Element &lt;Application&gt; (architektura .NET Native)
Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, których metadanych jest dostępny w celu odbicia w czasie wykonywania i zastosowanie zasad wykonywania odbicia do wszystkich elementów programu w aplikacji.  
  
 \<Dyrektywy > — Element  
\<Aplikacja > elementu (rd.xml)  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne. W tabeli elementów podrzędnych zasad odwołuje się do typu metadanych, który ma zostać udostępnione dla elementów określonego programu w czasie wykonywania.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Activate`|Odbicie|Atrybut opcjonalny. Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa, czy wyszukiwanie informacji o wyliczanie typów, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Współdziałanie|Atrybut opcjonalny. Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.|  
|`MarshalDelegate`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie struktur do kodu natywnego.|  
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie dla tej zasady do zastosowania do typów w aplikacji. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje zasady do określonego typu, takich jak klasy lub struktury.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do zdefiniowania zasad dla `List<String>` typu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Stosuje zasady do metody dla określonego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego metody rodzajowej.|  
|[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady do właściwości dla określonego typu.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Stosuje zasady do pola dla określonego typu.|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Stosuje zasady do zdarzenia określonego typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)|Element główny pliku dyrektyw środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero lub jeden `<Application>` elementu. Wiele `<Application>` elementów w pliku dyrektywy odbicia jednego nie są obsługiwane.  
  
 `<Application>` Element może być użyty w jednym z dwóch sposobów:  
  
-   Jako kontener do zdefiniowania elementów program, którego metadanych jest wymagany w czasie wykonywania. W takim przypadku `<Application>` elementu nie wymagają żadnych atrybutów. W czasie kompilacji narzędzia kompilatora wyszukiwać wszystkie biblioteki, łącznie z .NET Framework podstawowe biblioteki dla elementów programu identyfikowane przez elementy podrzędne `<Application>` elementu. Z kolei narzędzia kompilatora wyszukiwania biblioteki wskazywany przez [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementu dla elementów programu identyfikowane przez elementy podrzędne [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md).  
  
-   Jako element, który ustawia zasady dla całej aplikacji odbicia, serializacji i interop. Atrybuty `<Application>` element definiować całej aplikacji zasad, które mogą zostać zastąpione przez elementy podrzędne zdefiniowane przez `<Application>` lub [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Biblioteka > — Element](../../../docs/framework/net-native/library-element-net-native.md)  
 [\<Dyrektywy > — Element](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
