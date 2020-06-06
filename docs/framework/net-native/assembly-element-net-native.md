---
title: <Assembly>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: f3cf65b185b1db3289a0dbb785c2b91431951cc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181077"
---
# <a name="assembly-element-net-native"></a>\<Assembly>— Element (.NET Native)
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
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania struktur w kodzie natywnym.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*assembly_name*|Prosta nazwa zestawu bez rozszerzenia pliku. Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwa zestawu o nazwie Extensions. dll ma wartość "Extensions".<br /><br /> Możesz również określić ciąg literału, `*Application*` Aby zastosować zasady do wszystkich zestawów w pakiecie aplikacji, niezależnie od tego, czy te zestawy zostały załadowane. `*Application*`nie stosuje zasad do .NET Framework zestawów.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla wszystkich typów w zestawie. Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w podrzędnej przestrzeni nazw.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. [\<Application>](application-element-net-native.md)Element może mieć zero, jeden lub więcej `<Assembly>` elementów.|  
|[\<Library>](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania. [\<Library>](library-element-net-native.md)Element może mieć zero lub jeden `<Assembly>` element.|  
  
## <a name="remarks"></a>Uwagi  
 `<Assembly>`Element definiuje zasady środowiska uruchomieniowego dla wszystkich typów w zestawie. Różni się od [\<Library>](library-element-net-native.md) elementu, który określa bibliotekę, ale zależy od elementów podrzędnych, aby zdefiniować zasady odbicia środowiska uruchomieniowego. `<Assembly>`Element ma zastosowanie do wszystkich typów w zestawie, chyba że zostaną zastąpione przez element podrzędny.  
  
 Poniższy przykład pokazuje, jak można zastosować zasady środowiska uruchomieniowego do wszystkich typów w zestawach w pakiecie aplikacji, przypisując `Name` atrybutowi wartość "* aplikacja \* ". `<Assembly>`Element musi być elementem podrzędnym [\<Application>](application-element-net-native.md) elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 `Activate`Atrybuty, `Browse` , `Dynamic` i `Serialize` są opcjonalne. Jednak `<Assembly>` element musi zawierać co najmniej jeden z tych atrybutów.  
  
## <a name="see-also"></a>Zobacz także

- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
