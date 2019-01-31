---
title: <TypeInstantiation> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 928d3c528bef6d319f50464a0648e61de2603eb2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256631"
---
# <a name="typeinstantiation-element-net-native"></a>\<TypeInstantiation > (architektura .NET Native)
Skonstruowany typ rodzajowy dotyczy zasad odbicia środowiska uruchomieniowego.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.|  
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
|*type_name*|Nazwa typu. Jeśli ten `<TypeInstantiation>` element jest elementem podrzędnym elementu [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) elementu [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element lub innego `<TypeInstantiation>` elementu *type_ Nazwa* można określić nazwę typu bez jego przestrzeń nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowana nazwa typu. Nazwa typu nie jest oznaczone. Na przykład w przypadku <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu `<TypeInstantiation>` element mogą wyglądać następująco:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Argumenty atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_argument*|Określa argumenty typu ogólnego. Jeśli podano wiele argumentów są oddzielone przecinkami. Każdy argument musi zawierać w pełni kwalifikowana nazwa typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad, aby uzyskać zbudowany typ ogólny. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Ma zastosowanie zasad odbicia do zdarzenia należące do tego typu.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Ma zastosowanie zasad odbicia do pola należących do tego typu.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały doliczone do typu reprezentowanego przez zawierający `<TypeInstantiation>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Ma zastosowanie zasad odbicia do metody należących do tego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowanego należących do tego typu metody ogólnej.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady odbicia właściwości należących do tego typu.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu zagnieżdżonego.|  
|`<TypeInstantiation>`|Ma zastosowanie zasad odbicia do zagnieżdżonych zbudowany typ ogólny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zastosowanie zasad odbicia do wszystkich typów w określonym zestawie.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Zastosowanie zasad odbicia do wszystkich typów w przestrzeni nazw.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|`<TypeInstantiation>`|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Odbicia, serializacja i atrybutów międzyoperacyjności są wszystkie opcjonalne. Jednak co najmniej jedna musi być obecny.  
  
 Jeśli `<TypeInstantiation>` element jest elementem podrzędnym elementu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), lub [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), element Ustawienie to zastępuje ustawienia zasad zdefiniowanych w elemencie nadrzędnym. Jeśli [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element definiuje odpowiedniej definicji typu ogólnego, `<TypeInstantiation>` element zastąpienia zasad odbicia środowiska uruchomieniowego tylko w przypadku wystąpień określonego zbudowany typ ogólny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia do pobierania definicji typu ogólnego z skonstruowany <xref:System.Collections.Generic.Dictionary%602> obiektu. Również używa odbicia do wyświetlania informacji o <xref:System.Type> obiekty reprezentujące skonstruowany typy ogólne i definicji typu ogólnego. Zmienna `b` w tym przykładzie jest <xref:Windows.UI.Xaml.Controls.TextBlock> kontroli.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po kompilacji za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi, przykład generuje [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek w wierszu, który wywołuje <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metody. Możesz wyeliminować wyjątek i dostarczyć potrzebnych metadanych przez dodanie poniższego `<TypeInstantiation>` element do pliku dyrektyw środowiska uruchomieniowego:  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
