---
title: Element &lt;Type&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2569ac2ec170e5ac137751d790d41c2ab6cf0262
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttypegt-element-net-native"></a>Element &lt;Type&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania do określonego typu, takich jak klasy lub struktury.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Współdziałanie|Atrybut opcjonalny. Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.|  
|`MarshalDelegate`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów wartości do kodu natywnego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_name*|Nazwa typu. Jeśli `<Type>` element jest elementem podrzędnym albo [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md) element lub innym `<Type>` elementu *type_name* mogą obejmować nazwę typu bez jego przestrzeń nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Jeśli typ zawierający jest atrybut, definiuje zasad wykonywania dla elementów kodu, do których zastosowano ten atrybut.|  
|[\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)|Stosuje zasady odbicia na zdarzenie należących do tego typu.|  
|[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|Stosuje zasady odbicia do pola należących do tego typu.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, o ile tej zasady zostały zastosowane do typu reprezentowanego przez zawierający `<Type>` elementu.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Stosuje zasady odbicia do metody należących do tego typu.|  
|[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego metody rodzajowej należących do tego typu.|  
|[\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)|Stosuje zasady odbicia właściwości należących do tego typu.|  
|[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|Zastosowanie zasad wykonywania dla wszystkich klas dziedziczony z typu zawierającego.|  
|`<Type>`|Stosuje odbicia zasady do typu zagnieżdżonego.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w określonym zestawie.|  
|[\<Biblioteka >](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw.|  
|`<Type>`|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Odbicie serializacji i atrybutów międzyoperacyjności są wszystkie opcjonalne. Jeśli nie są obecne, `<Type>` elementu służy jako kontener, których typy podrzędne zdefiniowania zasad dla poszczególnych członków.  
  
 Jeśli `<Type>` element jest elementem podrzędnym [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>`, lub [ \< TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu zastępuje ustawienia zasad zdefiniowanych w elemencie nadrzędnym.  
  
 A `<Type>` elementu typu ogólnego dotyczy wszystkich wystąpień, które nie mają własnych zasad polityki. Zasady utworzone typy ogólne jest definiowana za pomocą [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
 Jeśli typ jest typem ogólnym, jego nazwa jest oznaczone symbolem akcent (\`) następuje ich liczba parametrów ogólnych. Na przykład `Name` atrybutu `<Type>` elementu <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy jest wyświetlany jako `Name="System.Collections.Generic.List`1"".  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia, aby wyświetlić informacje o polach, właściwości i metody <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy. Zmienna `b` w tym przykładzie jest [blok tekstu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu. Ponieważ przykładzie po prostu pobiera informacje o typie, dostępność metadanych jest kontrolowane przez `Browse` ustawienie zasad.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Ponieważ metadanych dla <xref:System.Collections.Generic.List%601> klasy nie jest automatycznie włączone przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi przykładzie nie są wyświetlane żądane informacje w czasie wykonywania. Aby zapewnić metadane potrzebne, Dodaj następujący `<Type>` elementu do pliku dyrektyw środowiska uruchomieniowego. Należy zauważyć, że ponieważ przygotowaliśmy nadrzędne [< Namespace\> ](../../../docs/framework/net-native/namespace-element-net-native.md) elementu, nie trzeba było Podaj w pełni kwalifikowana nazwa typu w `<Type>` elementu.  
  
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
 W poniższym przykładzie użyto odbicia pobrać <xref:System.Reflection.PropertyInfo> obiekt, który reprezentuje <xref:System.String.Chars%2A?displayProperty=nameWithType> właściwości. Następnie używa <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody do pobierania wartości siódmego znaku w ciągu, aby wyświetlić wszystkie znaki w ciągu. Zmienna `b` w tym przykładzie jest [blok tekstu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) formantu.  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Ponieważ metadanych dla <xref:System.String> obiektu nie jest dostępna, wywołanie <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metoda zgłasza <xref:System.NullReferenceException> wyjątek wykonywania czasu, gdy skompilowano z [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Aby wyeliminować wyjątek i udostępnienia metadanych niezbędne, Dodaj następujący `<Type>` elementu do pliku dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
