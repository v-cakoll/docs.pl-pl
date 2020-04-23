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
# <a name="xarray-markup-extension"></a><span data-ttu-id="d4cc9-102">x:Array — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="d4cc9-102">x:Array Markup Extension</span></span>

<span data-ttu-id="d4cc9-103">Zapewnia ogólną obsługę tablic obiektów w języku XAML za pośrednictwem rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="d4cc9-104">Odpowiada to typowi `x:ArrayExtension` XAML w [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="d4cc9-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="d4cc9-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d4cc9-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="d4cc9-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="d4cc9-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="d4cc9-107">Nazwa typu, który `x:Array` będzie zawierać.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="d4cc9-108">`typeName`może być (i często jest) poprzedzony dla obszaru nazw XAML, który zawiera definicje typu XAML.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="d4cc9-109">Zawartość elementów, która jest przypisana `ArrayExtension.Items` do właściwości wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="d4cc9-110">Zazwyczaj te elementy są określone jako jeden lub więcej `x:Array` elementów obiektu zawartych w tagach otwierania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="d4cc9-111">Obiekty określone w tym miejscu mają być przypisane `typeName`do typu XAML określonego w .</span><span class="sxs-lookup"><span data-stu-id="d4cc9-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d4cc9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4cc9-112">Remarks</span></span>

<span data-ttu-id="d4cc9-113">`Type`jest atrybutem wymaganym `x:Array` dla wszystkich elementów obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="d4cc9-114">Wartość `Type` parametru nie musi `x:Type` używać rozszerzenia znaczników; krótka nazwa typu jest typem XAML, który można określić jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="d4cc9-115">W implementacji usług .NET XAML na relację między wejściowym <xref:System.Type> typem XAML a wyjściowym typem CLR utworzonej tablicy ma wpływ kontekst usługi dla rozszerzeń znaczników.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="d4cc9-116">Dane <xref:System.Type> wyjściowe <xref:System.Xaml.XamlType.UnderlyingType%2A> jest wejściowego typu XAML, <xref:System.Xaml.XamlType> po wyszukując niezbędne na <xref:System.Windows.Markup.IXamlTypeResolver> podstawie kontekstu schematu XAML i usługi kontekstu zapewnia.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="d4cc9-117">Podczas przetwarzania zawartość tablicy są przypisywane do `ArrayExtension.Items` właściwości wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="d4cc9-118">W <xref:System.Windows.Markup.ArrayExtension> realizacji jest to reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d4cc9-119">W implementacji usług .NET XAML obsługa tego rozszerzenia <xref:System.Windows.Markup.ArrayExtension> znaczników jest definiowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="d4cc9-120"><xref:System.Windows.Markup.ArrayExtension>nie jest zapieczętowany i może służyć jako podstawa implementacji rozszerzenia znaczników dla niestandardowego typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="d4cc9-121">`x:Array`jest bardziej przeznaczony do rozszerzalności języka ogólnego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="d4cc9-122">Ale `x:Array` może być również przydatne do określania wartości XAML niektórych właściwości, które mają kolekcje obsługiwane przez XAML jako ich zawartość właściwości strukturalnych.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="d4cc9-123">Na przykład można określić zawartość <xref:System.Collections.IEnumerable> właściwości `x:Array` z użyciem.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="d4cc9-124">`x:Array`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="d4cc9-125">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="d4cc9-126">`x:Array`jest częściowo wyjątkiem od tej reguły, ponieważ zamiast dostarczania `x:Array` alternatywnych obsługi wartości atrybutów, zapewnia alternatywną obsługę jego wewnętrznej zawartości tekstu.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="d4cc9-127">To zachowanie umożliwia typy, które mogą nie być obsługiwane przez istniejący model zawartości, które mają być zgrupowane w tablicy i odwołuje się później w kodzie za pomocą dostępu do nazwanej tablicy; można wywołać <xref:System.Array> metody, aby uzyskać poszczególne elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="d4cc9-128">Wszystkie rozszerzenia znaczników w XAML używają{,} `)` nawiasów klamrowych (w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="d4cc9-129">Aby uzyskać więcej informacji na temat rozszerzeń znaczników w ogóle, zobacz [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="d4cc9-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="d4cc9-130">W XAML 2009, `x:Array` jest zdefiniowany jako język pierwotny zamiast rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="d4cc9-131">Aby uzyskać więcej informacji, zobacz [Wbudowane typy dla wspólnych elementów pierwotnych języka XAML](types-for-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="d4cc9-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="d4cc9-132">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="d4cc9-132">WPF Usage Notes</span></span>

<span data-ttu-id="d4cc9-133">Zazwyczaj elementy obiektu, które wypełniają `x:Array` nie są elementami, które istnieją w obszarze nazw [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML i wymagają mapowania prefiksów do nieobezwłastronnego obszaru nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="d4cc9-134">Na przykład poniżej znajduje się prosta tablica `sys` dwóch ciągów, `x`z prefiksem (a także ) zdefiniowanym na poziomie tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="d4cc9-135">Dla typów niestandardowych, które są używane jako elementy tablicy, klasa musi również obsługiwać wymagania dotyczące wystąpienia w XAML jako elementy obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4cc9-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="d4cc9-136">Aby uzyskać więcej informacji, zobacz [XAML i klasy niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="d4cc9-136">For more information, see [XAML and Custom Classes for WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4cc9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4cc9-137">See also</span></span>

- [<span data-ttu-id="d4cc9-138">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d4cc9-138">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="d4cc9-139">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="d4cc9-139">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
