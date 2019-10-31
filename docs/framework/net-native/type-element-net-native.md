---
title: Element <Type> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091851"
---
# <a name="type-element-net-native"></a>Typ \<> element (.NET Native)

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
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.|

## <a name="name-attribute"></a>Atrybut nazwy

|Wartość|Opis|
|-----------|-----------------|
|*type_name*|Nazwa typu. Jeśli ten `<Type>` element jest elementem podrzędnym [\<przestrzeni nazw >](namespace-element-net-native.md) elementu lub innego elementu `<Type>`, *TYPE_NAME* może zawierać nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *TYPE_NAME* musi zawierać w pełni kwalifikowaną nazwę typu.|

## <a name="all-other-attributes"></a>Wszystkie inne atrybuty

|Wartość|Opis|
|-----------|-----------------|
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<AttributeImplies >](attributeimplies-element-net-native.md)|Jeśli typ zawierający jest atrybutem, definiuje zasady środowiska uruchomieniowego dla elementów kodu, do których zastosowano atrybut.|
|[> zdarzeń \<](event-element-net-native.md)|Stosuje zasady odbicia do zdarzenia należącego do tego typu.|
|[\<pole >](field-element-net-native.md)|Stosuje zasady odbicia do pola należącego do tego typu.|
|[\<GenericParameter >](genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego.|
|[\<ImpliesType >](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały zastosowane do typu reprezentowanego przez zawierający element `<Type>`.|
|[> metody\<](method-element-net-native.md)|Stosuje zasady odbicia do metody należącej do tego typu.|
|[\<MethodInstantiation >](methodinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanej metody ogólnej należącej do tego typu.|
|[\<Właściwość >](property-element-net-native.md)|Stosuje zasady odbicia do właściwości należącej do tego typu.|
|[podtypy \<](subtypes-element-net-native.md)|Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.|
|`<Type>`|Stosuje zasady odbicia do typu zagnieżdżonego.|
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<> aplikacji](application-element-net-native.md)|Służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.|
|[\<zestawu >](assembly-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w określonym zestawie.|
|[Biblioteka \<](library-element-net-native.md)|Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.|
|[\<przestrzeni nazw >](namespace-element-net-native.md)|Stosuje zasady odbicia do wszystkich typów w przestrzeni nazw.|
|`<Type>`|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|

## <a name="remarks"></a>Uwagi

Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne. Jeśli żaden nie istnieje, element `<Type>` służy jako kontener, którego typy podrzędne definiują zasady dla poszczególnych członków.

Jeśli element `<Type>` jest elementem podrzędnym [zestawu\<](assembly-element-net-native.md), [\<przestrzeń nazw >](namespace-element-net-native.md), `<Type>`lub [\<TypeInstantiation >](typeinstantiation-element-net-native.md) , zastępuje ustawienia zasad zdefiniowane przez element nadrzędny.

Element `<Type>` typu ogólnego stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad. Zasady skonstruowanych typów ogólnych są zdefiniowane przez\<elementu [> TypeInstantiation](typeinstantiation-element-net-native.md) .

Jeśli typ jest typem ogólnym, jego nazwa jest uzupełniona symbolem akcentu słabego (\`), po którym następuje liczba parametrów ogólnych. Na przykład atrybut `Name` elementu `<Type>` dla klasy <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> jest wyświetlany jako ``Name="System.Collections.Generic.List`1"``.

## <a name="example"></a>Przykład

Poniższy przykład używa odbicia, aby wyświetlić informacje dotyczące pól, właściwości i metod klasy <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Zmienna `b` w przykładzie jest formantem <xref:Windows.UI.Xaml.Controls.TextBlock>. Ponieważ przykład po prostu pobiera informacje o typie, dostępność metadanych jest kontrolowana przez ustawienie zasad `Browse`.

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 Ponieważ metadane klasy <xref:System.Collections.Generic.List%601> nie są automatycznie dołączane przez łańcuch narzędzi .NET Native, w przykładzie nie można wyświetlić żądanych informacji o członkach w czasie wykonywania. Aby zapewnić niezbędne metadane, Dodaj następujący element `<Type>` do pliku dyrektywy środowiska uruchomieniowego. Należy pamiętać, że ze względu na to, że podano nadrzędny [< przestrzeni nazw\>](namespace-element-net-native.md) element, nie musimy podawać w pełni kwalifikowanej nazwy typu w elemencie `<Type>`.

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
 Poniższy przykład używa odbicia w celu pobrania obiektu <xref:System.Reflection.PropertyInfo>, który reprezentuje właściwość <xref:System.String.Chars%2A?displayProperty=nameWithType>. Następnie używa metody <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, aby pobrać wartość siódmego znaku w ciągu i wyświetlić wszystkie znaki w ciągu. Zmienna `b` w przykładzie jest formantem <xref:Windows.UI.Xaml.Controls.TextBlock>.

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 Ponieważ metadane dla obiektu <xref:System.String> są niedostępne, wywołanie metody <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> zgłasza wyjątek <xref:System.NullReferenceException> w czasie wykonywania, gdy zostanie skompilowany z łańcuchem narzędzi .NET Native. Aby wyeliminować wyjątek i wprowadzić niezbędne metadane, Dodaj następujący element `<Type>` do pliku dyrektywy środowiska uruchomieniowego:

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
