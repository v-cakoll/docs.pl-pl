---
title: x:Array — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072047"
---
# <a name="xarray-markup-extension"></a>x:Array — Rozszerzenie znaczników

Zapewnia ogólną obsługę tablic obiektów w języku XAML za pośrednictwem rozszerzenia znaczników. Odpowiada to typowi `x:ArrayExtension` XAML w [MS-XAML].

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`typeName`|Nazwa typu, który `x:Array` będzie zawierać. `typeName`może być (i często jest) poprzedzony dla obszaru nazw XAML, który zawiera definicje typu XAML.|
|`arrayContents`|Zawartość elementów, która jest przypisana `ArrayExtension.Items` do właściwości wewnętrznej. Zazwyczaj te elementy są określone jako jeden lub więcej `x:Array` elementów obiektu zawartych w tagach otwierania i zamykania. Obiekty określone w tym miejscu mają być przypisane `typeName`do typu XAML określonego w .|

## <a name="remarks"></a>Uwagi

`Type`jest atrybutem wymaganym `x:Array` dla wszystkich elementów obiektu. Wartość `Type` parametru nie musi `x:Type` używać rozszerzenia znaczników; krótka nazwa typu jest typem XAML, który można określić jako ciąg.

W implementacji usług .NET XAML na relację między wejściowym <xref:System.Type> typem XAML a wyjściowym typem CLR utworzonej tablicy ma wpływ kontekst usługi dla rozszerzeń znaczników. Dane <xref:System.Type> wyjściowe <xref:System.Xaml.XamlType.UnderlyingType%2A> jest wejściowego typu XAML, <xref:System.Xaml.XamlType> po wyszukując niezbędne na <xref:System.Windows.Markup.IXamlTypeResolver> podstawie kontekstu schematu XAML i usługi kontekstu zapewnia.

Podczas przetwarzania zawartość tablicy są przypisywane do `ArrayExtension.Items` właściwości wewnętrznej. W <xref:System.Windows.Markup.ArrayExtension> realizacji jest to reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.

W implementacji usług .NET XAML obsługa tego rozszerzenia <xref:System.Windows.Markup.ArrayExtension> znaczników jest definiowana przez klasę. <xref:System.Windows.Markup.ArrayExtension>nie jest zapieczętowany i może służyć jako podstawa implementacji rozszerzenia znaczników dla niestandardowego typu tablicy.

`x:Array`jest bardziej przeznaczony do rozszerzalności języka ogólnego w języku XAML. Ale `x:Array` może być również przydatne do określania wartości XAML niektórych właściwości, które mają kolekcje obsługiwane przez XAML jako ich zawartość właściwości strukturalnych. Na przykład można określić zawartość <xref:System.Collections.IEnumerable> właściwości `x:Array` z użyciem.

`x:Array`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. `x:Array`jest częściowo wyjątkiem od tej reguły, ponieważ zamiast dostarczania `x:Array` alternatywnych obsługi wartości atrybutów, zapewnia alternatywną obsługę jego wewnętrznej zawartości tekstu. To zachowanie umożliwia typy, które mogą nie być obsługiwane przez istniejący model zawartości, które mają być zgrupowane w tablicy i odwołuje się później w kodzie za pomocą dostępu do nazwanej tablicy; można wywołać <xref:System.Array> metody, aby uzyskać poszczególne elementy tablicy.

Wszystkie rozszerzenia znaczników w XAML używają{,} `)` nawiasów klamrowych (w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć wartość atrybutu. Aby uzyskać więcej informacji na temat rozszerzeń znaczników w ogóle, zobacz [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

W XAML 2009, `x:Array` jest zdefiniowany jako język pierwotny zamiast rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [Wbudowane typy dla wspólnych elementów pierwotnych języka XAML](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Zazwyczaj elementy obiektu, które wypełniają `x:Array` nie są elementami, które istnieją w obszarze nazw [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML i wymagają mapowania prefiksów do nieobezwłastronnego obszaru nazw XAML.

Na przykład poniżej znajduje się prosta tablica `sys` dwóch ciągów, `x`z prefiksem (a także ) zdefiniowanym na poziomie tablicy.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Dla typów niestandardowych, które są używane jako elementy tablicy, klasa musi również obsługiwać wymagania dotyczące wystąpienia w XAML jako elementy obiektu. Aby uzyskać więcej informacji, zobacz [XAML i klasy niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

## <a name="see-also"></a>Zobacz też

- [Rozszerzenia znacznikowania i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Typy migrowane z WPF do System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
