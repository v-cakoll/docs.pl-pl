---
title: Element &lt;TypeInstantiation&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5dc19038af220cca63417a331a37d4a7d3b9f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttypeinstantiationgt-element-net-native"></a>Element &lt;TypeInstantiation&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania odbicia do skonstruowanego typu ogólnego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
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
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę typu.|  
|`Arguments`|Ogólne|Atrybut wymagany. Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami.|  
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
|*type_name*|Nazwa typu. Jeśli `<TypeInstantiation>` element jest elementem podrzędnym [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) elementu [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) element lub innej `<TypeInstantiation>` elementu *type_ Nazwa* można określić nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu. Nazwa typu nie jest przypisany. Na przykład w przypadku <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu `<TypeInstantiation>` element może wyglądać następująco:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Argumentów atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_argument*|Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami. Każdy argument musi zawierać nazwę FQDN typu.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad dla skonstruowanego typu ogólnego. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Stosuje zasady odbicia na zdarzenie należących do tego typu.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Stosuje zasady odbicia do pola należących do tego typu.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, o ile tej zasady zostały zastosowane do typu reprezentowanego przez zawierający `<TypeInstantiation>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Stosuje zasady odbicia do metody należących do tego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego metody rodzajowej należących do tego typu.|  
|[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady odbicia właściwości należących do tego typu.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu zagnieżdżonego.|  
|`<TypeInstantiation>`|Stosuje zasady odbicia do skonstruowanego typu zagnieżdżonego ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w określonym zestawie.|  
|[\<Biblioteka >](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|`<TypeInstantiation>`|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Odbicie serializacji i atrybutów międzyoperacyjności są wszystkie opcjonalne. Jednak co najmniej jeden musi być obecny.  
  
 Jeśli `<TypeInstantiation>` element jest elementem podrzędnym [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), lub [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md), element zastępuje on zdefiniowany w elemencie nadrzędnym ustawienia zasad. Jeśli [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) element definiuje odpowiedniej definicji typu ogólnego, `<TypeInstantiation>` element zastąpienia zasad wykonywania odbicia tylko dla operacji tworzenia wystąpień określonego skonstruowanego typu ogólnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia pobrać definicji typu ogólnego skonstruowane <xref:System.Collections.Generic.Dictionary%602> obiektu. Zastosowano odbicia do wyświetlania informacji o <xref:System.Type> obiekty reprezentujące utworzone typy ogólne i definicje typu ogólnego. Zmienna `b` w tym przykładzie jest [blok tekstu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po kompilacji z [!INCLUDE[net_native](../../../includes/net-native-md.md)] zgłasza przykładzie łańcucha narzędzi [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek w wierszu, który wywołuje <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metody. Można wyeliminować wyjątek i udostępniać niezbędne metadanych przez dodanie poniższego `<TypeInstantiation>` elementu do pliku dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
