---
title: <Assembly>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: f3cf65b185b1db3289a0dbb785c2b91431951cc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181077"
---
# <a name="assembly-element-net-native"></a>\<Element> zestawu (.NET native)
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
|`Name`|Ogólne|Atrybut wymagany. Określa prostą nazwę złożenia.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje dotyczące typów w zestawie lub wyliczaniem ich, ale nie włącza dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania struktur do kodu macierzystego.|  
  
## <a name="name-attribute"></a>Atrybut Nazwa  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*assembly_name*|Prosta nazwa zestawu, bez jego rozszerzenia pliku. Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwa zestawu o nazwie Extensions.dll jest "Rozszerzenia".<br /><br /> Można również określić ciąg `*Application*` literału, aby zastosować zasady do wszystkich zestawów w pakiecie aplikacji, czy te zestawy są ładowane, czy nie. `*Application*`nigdy nie stosuje zasad do zestawów .NET Framework.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, aby zastosować do tego typu zasad dla wszystkich typów w zestawie. Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>przestrzeni nazw](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w podrzędnym obszarze nazw.|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<>typu>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>aplikacji](application-element-net-native.md)|Służy jako kontener dla typów całej aplikacji i członków typu, których metadane są dostępne do odbicia w czasie wykonywania. [ \<Element>aplikacji](application-element-net-native.md) może mieć zero, jeden lub więcej `<Assembly>` elementów.|  
|[\<>biblioteczna](library-element-net-native.md)|Definiuje zestaw, który zawiera typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [ \<Element>biblioteki](library-element-net-native.md) może mieć zero `<Assembly>` lub jeden element.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<Assembly>` definiuje zasady środowiska uruchomieniowego dla wszystkich typów w zestawie. Różni się od [ \<Library>](library-element-net-native.md) element, który określa bibliotekę, ale zależy od jego elementów podrzędnych do definiowania zasad odbicia środowiska uruchomieniowego. Element `<Assembly>` stosuje się do wszystkich typów w zestawie, chyba że są one zastąpione przez element podrzędny.  
  
 Poniższy przykład pokazuje, jak można zastosować zasady środowiska uruchomieniowego do wszystkich `Name` typów w zestawach w\*pakiecie aplikacji, przypisując atrybut o wartości "*Application". Element `<Assembly>` musi być elementem [ \<](application-element-net-native.md) podrzędnym application>element.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 `Activate`Atrybuty `Browse` `Dynamic`, `Serialize` i atrybuty są opcjonalne. Jednak `<Assembly>` element musi zawierać co najmniej jeden z tych atrybutów.  
  
## <a name="see-also"></a>Zobacz też

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
