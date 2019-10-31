---
title: Element <Assembly> (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: bad2286c5306b9f8a8955ebef12e5e99aec5bb89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128507"
---
# <a name="assembly-element-net-native"></a>Element > zestawu \<(.NET Native)
Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów w określonym zestawie.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie typów w zestawie, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.|  
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
|*assembly_name*|Prosta nazwa zestawu bez rozszerzenia pliku. Ten atrybut odpowiada właściwości <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Na przykład nazwa zestawu o nazwie Extensions. dll ma wartość "Extensions".<br /><br /> Możesz również określić ciąg literału `*Application*`, aby zastosować zasady do wszystkich zestawów w pakiecie aplikacji, niezależnie od tego, czy te zestawy zostały załadowane. `*Application*` nigdy nie stosuje zasad do .NET Framework zestawów.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla wszystkich typów w zestawie. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<przestrzeni nazw >](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w podrzędnej przestrzeni nazw.|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> aplikacji](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. Element [\<> aplikacji](application-element-net-native.md) może mieć zero, jeden lub więcej elementów `<Assembly>`.|  
|[Biblioteka \<](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [\<biblioteki >](library-element-net-native.md) element może mieć zero lub jeden element `<Assembly>`.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<Assembly>` definiuje zasady środowiska uruchomieniowego dla wszystkich typów w zestawie. Różni się od elementu [\<library >](library-element-net-native.md) , który określa bibliotekę, ale zależy od jej elementów podrzędnych, aby zdefiniować zasady odbicia środowiska uruchomieniowego. Element `<Assembly>` ma zastosowanie do wszystkich typów w zestawie, chyba że zostaną zastąpione przez element podrzędny.  
  
 Poniższy przykład pokazuje, jak można zastosować zasady środowiska uruchomieniowego do wszystkich typów w zestawach w pakiecie aplikacji, przypisując atrybut `Name` wartość "* Application\*". Element `<Assembly>` musi być elementem podrzędnym elementu [\<aplikacji >](application-element-net-native.md) .  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 Atrybuty `Activate`, `Browse`, `Dynamic`i `Serialize` są opcjonalne. Jednak element `<Assembly>` musi zawierać co najmniej jeden z tych atrybutów.  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
