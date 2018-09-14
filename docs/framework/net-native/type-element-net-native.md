---
title: Element &lt;Type&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaf5103dfee366466ff701ce3669bbabb97233ac
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516108"
---
# <a name="lttypegt-element-net-native"></a>Element &lt;Type&gt; (architektura .NET Native)
Ma zastosowanie zasad środowiska uruchomieniowego do określonego typu, takie jak klasy lub struktury.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Type Name="type_name"  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Usługa międzyoperacyjna|Atrybut opcjonalny. Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.|  
|`MarshalDelegate`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.|  
|`MarshalStructure`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady dla marshaling typów wartości do kodu natywnego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_name*|Nazwa typu. Jeśli ten `<Type>` element jest elementem podrzędnym jednej [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) element lub innym `<Type>` elementu *type_name* można uwzględnić nazwę typu bez jego przestrzeń nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowana nazwa typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Jeśli typ zawierający jest atrybut, zdefiniowano zasad wykonywania dla elementów kodu, do których zastosowano ten atrybut.|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Ma zastosowanie zasad odbicia do zdarzenia należące do tego typu.|  
|[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|Ma zastosowanie zasad odbicia do pola należących do tego typu.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały doliczone do typu reprezentowanego przez zawierający `<Type>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Ma zastosowanie zasad odbicia do metody należących do tego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowanego należących do tego typu metody ogólnej.|  
|[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady odbicia właściwości należących do tego typu.|  
|[\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Stosuje zasady środowiska uruchomieniowego dla wszystkich klas dziedziczone z typu zawierającego.|  
|`<Type>`|Ma zastosowanie zasad odbicia do typu zagnieżdżonego.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Zastosowanie zasad odbicia do wszystkich typów w określonym zestawie.|  
|[\<Biblioteki >](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Zastosowanie zasad odbicia do wszystkich typów w przestrzeni nazw.|  
|`<Type>`|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Odbicia, serializacja i atrybutów międzyoperacyjności są wszystkie opcjonalne. Jeśli żaden nie jest obecny, `<Type>` element służy jako kontener, w których typy podrzędne Definiowanie zasad dla poszczególnych członków.  
  
 Jeśli `<Type>` element jest elementem podrzędnym elementu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, lub [ \< TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu zastępuje ustawienia zasad zdefiniowanych w elemencie nadrzędnym.  
  
 Element `<Type>` elementu typu ogólnego stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad. Zasady skonstruowany typów ogólnych jest definiowany przez [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
 Jeśli typ jest typem ogólnym, jego nazwa zostanie nadany przez symbol akcent (\`) i jego numer parametrów ogólnych. Na przykład `Name` atrybutu `<Type>` elementu <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasa jest wyświetlany jako `Name="System.Collections.Generic.List`1"".  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia, aby wyświetlić informacje dotyczące pola, właściwości i metod <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy. Zmienna `b` w tym przykładzie jest [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) kontroli. Ponieważ w tym przykładzie po prostu pobiera informacje o typie, dostępność metadanych jest kontrolowany przez `Browse` ustawienie zasad.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Ponieważ metadane <xref:System.Collections.Generic.List%601> klasy nie jest automatycznie dołączany przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi przykładzie nie są wyświetlane żądane informacje w czasie wykonywania. Aby zapewnić potrzebnych metadanych, Dodaj następujący kod `<Type>` element do pliku dyrektyw środowiska uruchomieniowego. Należy zauważyć, że ponieważ udostępniliśmy nadrzędnego [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) elementu, firma Microsoft nie muszą podawać nazwę w pełni kwalifikowany typ `<Type>` elementu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia w celu pobrania <xref:System.Reflection.PropertyInfo> obiekt, który reprezentuje <xref:System.String.Chars%2A?displayProperty=nameWithType> właściwości. Następnie używa <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody można pobrać wartość siódmego znaku w ciągu, aby wyświetlić wszystkie znaki w ciągu. Zmienna `b` w tym przykładzie jest [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) kontroli.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Ponieważ metadane dla <xref:System.String> obiekt nie jest dostępna, wywołanie <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda zgłasza wyjątek <xref:System.NullReferenceException> wyjątek wykonywania czasu, gdy skompilowano z opcją [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi. Aby wyeliminować wyjątek, a następnie podaj wymagane metadane, Dodaj następujący element `<Type>` elementu plik dyrektywy środowiska uruchomieniowego:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
