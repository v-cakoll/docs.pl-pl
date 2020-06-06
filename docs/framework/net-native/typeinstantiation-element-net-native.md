---
title: <TypeInstantiation>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: 9069856b3d8739724d148b5eea5d4188c8b8b9e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128682"
---
# <a name="typeinstantiation-element-net-native"></a>\<TypeInstantiation>— Element (.NET Native)
Stosuje zasady odbicia środowiska uruchomieniowego do skonstruowanego typu ogólnego.  
  
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
|`Arguments`|Ogólne|Atrybut wymagany. Określa argumenty typu ogólnego. Jeśli istnieją wiele argumentów, są one oddzielone przecinkami.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.|  
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
|*type_name*|Nazwa typu. Jeśli ten `<TypeInstantiation>` element jest elementem podrzędnym [\<Namespace>](namespace-element-net-native.md) elementu, [\<Type>](type-element-net-native.md) elementu lub innego `<TypeInstantiation>` elementu, *TYPE_NAME* może określić nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *TYPE_NAME* musi zawierać w pełni kwalifikowaną nazwę typu. Nazwa typu nie jest poprzednia. Na przykład dla <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu `<TypeInstantiation>` element może wyglądać w następujący sposób:<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Arguments — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_argument*|Określa argumenty typu ogólnego. Jeśli istnieją wiele argumentów, są one oddzielone przecinkami. Każdy argument musi składać się z w pełni kwalifikowanej nazwy typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla konstruowanego typu ogólnego. Możliwe wartości to `All` , `Auto` ,,,,, `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` i `Required All` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|Stosuje zasady odbicia do zdarzenia należącego do tego typu.|  
|[\<Field>](field-element-net-native.md)|Stosuje zasady odbicia do pola należącego do tego typu.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały zastosowane do typu reprezentowanego przez `<TypeInstantiation>` element zawierający.|  
|[\<Method>](method-element-net-native.md)|Stosuje zasady odbicia do metody należącej do tego typu.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanej metody ogólnej należącej do tego typu.|  
|[\<Property>](property-element-net-native.md)|Stosuje zasady odbicia do właściwości należącej do tego typu.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu zagnieżdżonego.|  
|`<TypeInstantiation>`|Stosuje zasady odbicia do zagnieżdżonego konstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.|  
|[\<Assembly>](assembly-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w określonym zestawie.|  
|[\<Library>](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.|  
|[\<Namespace>](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|`<TypeInstantiation>`|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne. Jednak musi być obecny co najmniej jeden.  
  
 Jeśli `<TypeInstantiation>` element jest elementem podrzędnym [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) elementu,, lub [\<Type>](type-element-net-native.md) , zastępuje ustawienia zasad zdefiniowane przez element nadrzędny. Jeśli [\<Type>](type-element-net-native.md) element definiuje odpowiadającą definicję typu ogólnego, `<TypeInstantiation>` element zastępuje zasady odbicia w czasie wykonywania tylko dla wystąpień określonego konstruowanego typu ogólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa odbicia w celu pobrania definicji typu ogólnego z konstruowanego <xref:System.Collections.Generic.Dictionary%602> obiektu. Używa również odbicia do wyświetlania informacji o <xref:System.Type> obiektach, które reprezentują skonstruowane typy ogólne i definicje typów ogólnych. Zmienna `b` w przykładzie jest <xref:Windows.UI.Xaml.Controls.TextBlock> kontrolką.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Po kompilacji z łańcuchem narzędzi .NET Native, przykład zgłasza wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) w wierszu, który wywołuje <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> metodę. Można wyeliminować wyjątek i dostarczyć niezbędnych metadanych, dodając następujący `<TypeInstantiation>` element do pliku dyrektywy środowiska uruchomieniowego:  
  
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

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
