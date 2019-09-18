---
title: <Type>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ffe37540fe089bfd1e0eca1958498e725eb9b5b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049156"
---
# <a name="type-element-net-native"></a>\<Typ > element (.NET Native)

Stosuje zasady środowiska uruchomieniowego do określonego typu, takiego jak Klasa lub struktura.

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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.|
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.|
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.|
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.|

## <a name="name-attribute"></a>Atrybut nazwy

|Wartość|Opis|
|-----------|-----------------|
|*type_name*|Nazwa typu. Jeśli ten `<Type>` element jest elementem podrzędnym [ \<przestrzeni nazw >](namespace-element-net-native.md) elementu lub innego `<Type>` elementu, *TYPE_NAME* może zawierać nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *TYPE_NAME* musi zawierać w pełni kwalifikowaną nazwę typu.|

## <a name="all-other-attributes"></a>Wszystkie inne atrybuty

|Wartość|Opis|
|-----------|-----------------|
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `All`, `Auto` `Excluded` ,,`Public` ,,`Required All`, i. `PublicAndInternal` `Required Public` `Required PublicAndInternal` Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<AttributeImplies >](attributeimplies-element-net-native.md)|Jeśli typ zawierający jest atrybutem, definiuje zasady środowiska uruchomieniowego dla elementów kodu, do których zastosowano atrybut.|
|[\<> Zdarzeń](event-element-net-native.md)|Stosuje zasady odbicia do zdarzenia należącego do tego typu.|
|[\<> Pola](field-element-net-native.md)|Stosuje zasady odbicia do pola należącego do tego typu.|
|[\<GenericParameter >](genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego.|
|[\<ImpliesType >](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały zastosowane do typu reprezentowanego przez element zawierający `<Type>` .|
|[\<> Metody](method-element-net-native.md)|Stosuje zasady odbicia do metody należącej do tego typu.|
|[\<MethodInstantiation >](methodinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanej metody ogólnej należącej do tego typu.|
|[\<> Właściwości](property-element-net-native.md)|Stosuje zasady odbicia do właściwości należącej do tego typu.|
|[\<Podtypy >](subtypes-element-net-native.md)|Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.|
|`<Type>`|Stosuje zasady odbicia do typu zagnieżdżonego.|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<> Aplikacji](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.|
|[\<> Zestawu](assembly-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w określonym zestawie.|
|[\<> Biblioteki](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.|
|[\<Namespace>](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw.|
|`<Type>`|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|

## <a name="remarks"></a>Uwagi

Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne. Jeśli nie są obecne, `<Type>` element służy jako kontener, którego typy podrzędne definiują zasady dla poszczególnych członków.

[ \<](typeinstantiation-element-net-native.md) `<Type>` [ \<](assembly-element-net-native.md) [ \<](namespace-element-net-native.md)Jeśli element jest elementem podrzędnym > zestawu, przestrzeni nazw >, lub TypeInstantiation > element, zastępuje ustawienia zasad zdefiniowane przez `<Type>` element nadrzędny.

`<Type>` Element typu ogólnego stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad. Zasady skonstruowanych typów ogólnych są zdefiniowane przez [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) .

Jeśli typ jest typem ogólnym, jego nazwa jest uzupełniona symbolem akcentu słabego\`(), po którym następuje liczba parametrów ogólnych. Na przykład `Name` ``Name="System.Collections.Generic.List`1"``atrybut `<Type>` elementu<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy jest wyświetlany jako.

## <a name="example"></a>Przykład

Poniższy przykład używa odbicia, aby wyświetlić informacje dotyczące pól, właściwości i metod <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy. Zmienna `b` w przykładzie <xref:Windows.UI.Xaml.Controls.TextBlock> jest kontrolką. Ponieważ przykład po prostu pobiera informacje o typie, dostępność metadanych jest kontrolowana przez `Browse` ustawienie zasad.

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 Ponieważ metadane <xref:System.Collections.Generic.List%601> klasy nie są automatycznie dołączane do łańcucha narzędzi .NET Native, w przykładzie nie można wyświetlić żądanych informacji o elementach członkowskich w czasie wykonywania. Aby zapewnić niezbędne metadane, Dodaj następujący `<Type>` element do pliku dyrektywy środowiska uruchomieniowego. Należy pamiętać, że ze względu na to, że podano nadrzędny element [\> przestrzeni nazw <](namespace-element-net-native.md) , nie musimy podawać w `<Type>` elemencie w pełni kwalifikowanej nazwy typu.

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
 Poniższy przykład używa odbicia, aby pobrać <xref:System.Reflection.PropertyInfo> obiekt, który <xref:System.String.Chars%2A?displayProperty=nameWithType> reprezentuje właściwość. Następnie używa metody, <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> aby pobrać wartość siódmego znaku w ciągu i wyświetlić wszystkie znaki w ciągu. Zmienna `b` w przykładzie <xref:Windows.UI.Xaml.Controls.TextBlock> jest kontrolką.

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 Ponieważ metadane dla <xref:System.String> obiektu nie są dostępne, wywołanie <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody zgłasza <xref:System.NullReferenceException> wyjątek w czasie wykonywania, gdy jest kompilowany za pomocą łańcucha narzędzi .NET Native. Aby wyeliminować wyjątek i podać niezbędne metadane, Dodaj następujący `<Type>` element do pliku dyrektywy środowiska uruchomieniowego:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
