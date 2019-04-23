---
title: <Assembly> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0788c05edace2142d348c679c73aa1b4404ce75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137855"
---
# <a name="assembly-element-net-native"></a>\<Zestaw > (architektura .NET Native)
Dotyczy wszystkich typów w określonym zestawie zasad odbicia środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa prostą nazwę zestawu.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa wykonanie zapytania dotyczącego informacji o wyliczania typów w zestawie, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.|  
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
|*assembly_name*|Prosta nazwa zestawu, bez jego rozszerzenia pliku. Ten atrybut odnosi się do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwę zestawu o nazwie Extensions.dll jest "Rozszerzenia".<br /><br /> Można również określić ciąg literału `*Application*` zastosować zasady do wszystkich zestawów do pakietu aplikacji, czy te zestawy są ładowane, czy nie. `*Application*` nigdy nie stosuje zasady do zestawów .NET Framework.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad dla wszystkich typów w zestawie. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Ma zastosowanie zasad odbicia do wszystkich typów w podrzędnej przestrzeni nazw.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Zastosowanie zasad odbicia do typu.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) element może mieć zero, co najmniej jeden `<Assembly>` elementów.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. [ \<Biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element może mieć zero lub jeden `<Assembly>` elementu.|  
  
## <a name="remarks"></a>Uwagi  
 `<Assembly>` Element definiuje zasad środowiska uruchomieniowego dla wszystkich typów w zestawie. Różni się od [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) element, który określa bibliotekę, ale zależy od jego elementów podrzędnych do definiowania zasad odbicia środowiska uruchomieniowego. `<Assembly>` Element ma zastosowanie do wszystkich typów w zestawie, chyba że zostaną zastąpione przez element podrzędny.  
  
 W poniższym przykładzie pokazano, jak można stosować zasad środowiska uruchomieniowego dla wszystkich typów w zestawach w ramach pakietu aplikacji, przypisując `Name` wartość atrybutu "* aplikacji\*". `<Assembly>` Element musi być elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate`, `Browse`, `Dynamic`, I `Serialize` atrybuty są wszystkie opcjonalne. Jednak `<Assembly>` musi zawierać co najmniej jeden z tych atrybutów.  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
