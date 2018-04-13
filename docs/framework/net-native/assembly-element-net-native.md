---
title: Element &lt;Assembly&gt; (architektura .NET Native)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34e49e4d11f442f15db2f06b330b8b84a165a08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="ltassemblygt-element-net-native"></a>Element &lt;Assembly&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania odbicia do wszystkich typów w określonym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting" />  
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
|`Name`|Ogólne|Atrybut wymagany. Określa prostą nazwę zestawu.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa, czy wyszukiwanie informacji o wyliczania typów w zestawie, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.|  
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
|*assembly_name*|Prosta nazwa zestawu, bez jego rozszerzenie pliku. Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwa zestawu o nazwie Extensions.dll jest "Rozszerzenia".<br /><br /> Można również określić literał `*Application*` zastosować zasady do wszystkich zestawów do pakietu aplikacji, czy te zestawy są załadowane, czy nie. `*Application*` nigdy nie stosuje zasady do zestawów platformy .NET Framework.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad dla wszystkich typów w zestawie. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw podrzędnych.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) element może mieć wartość zero, co najmniej jeden `<Assembly>` elementów.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element może mieć wartość zero lub jeden `<Assembly>` elementu.|  
  
## <a name="remarks"></a>Uwagi  
 `<Assembly>` Element definiuje zasad wykonywania dla wszystkich typów w zestawie. Różni się od [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element, który określa bibliotekę, ale zależy od jego elementów podrzędnych do definiowania zasad wykonywania odbicia. `<Assembly>` Element ma zastosowanie do wszystkich typów w zestawie, chyba że zostaną one zastąpione przez element podrzędny.  
  
 W poniższym przykładzie pokazano, jak można stosować zasad wykonywania dla wszystkich typów w zestawach w ramach pakietu aplikacji, przypisując `Name` wartość atrybutu "* Application\*". `<Assembly>` Element musi być elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, I `Serialize` atrybuty są wszystkie opcjonalne. Jednak `<Assembly>` element musi zawierać co najmniej jeden z tych atrybutów.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
