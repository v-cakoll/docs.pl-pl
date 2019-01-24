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
ms.openlocfilehash: e94928f17a31cdadae11f69c37a4f148452b5d2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699743"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="f69ef-102">x:Array — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="f69ef-102">x:Array Markup Extension</span></span>
<span data-ttu-id="f69ef-103">Oferuje ogólną pomoc techniczną dla tablic obiektów w XAML poprzez rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="f69ef-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="f69ef-104">Odpowiada to `x:ArrayExtension` typu XAML w [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="f69ef-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="f69ef-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f69ef-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f69ef-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="f69ef-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="f69ef-107">Nazwa typu, Twoje `x:Array` będzie zawierać.</span><span class="sxs-lookup"><span data-stu-id="f69ef-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="f69ef-108">`typeName` może być (i często jest) prefiks dla XAML przestrzeń nazw zawierająca XAML definicje typów.</span><span class="sxs-lookup"><span data-stu-id="f69ef-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="f69ef-109">Zawartość elementów, która jest przypisana do wewnętrznych `ArrayExtension.Items` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f69ef-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="f69ef-110">Zazwyczaj te elementy są określane jako co najmniej jeden obiekt zawartym w elemencie `x:Array` znaczników otwierających i zamykających.</span><span class="sxs-lookup"><span data-stu-id="f69ef-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="f69ef-111">Obiekty określone w tym polu powinny być można przypisać do typu XAML określonego w `typeName`.</span><span class="sxs-lookup"><span data-stu-id="f69ef-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f69ef-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f69ef-112">Remarks</span></span>  
 <span data-ttu-id="f69ef-113">`Type` jest wymaganego atrybutu dla wszystkich `x:Array` obiektu elementów.</span><span class="sxs-lookup"><span data-stu-id="f69ef-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="f69ef-114">A `Type` wartość parametru nie trzeba używać `x:Type` — rozszerzenie znaczników; krótką nazwę typu jest typu XAML, który może być określony jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="f69ef-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="f69ef-115">W przypadku wdrażania usług programu .NET Framework XAML, relacji między typ XAML w danych wejściowych i wyjściowych CLR <xref:System.Type> z utworzona tablica ma wpływ kontekst usługi rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="f69ef-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="f69ef-116">Dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> wejściowego typu XAML, po wyszukaniu niezbędne <xref:System.Xaml.XamlType> oparte na kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver> dostarcza kontekst usługi.</span><span class="sxs-lookup"><span data-stu-id="f69ef-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="f69ef-117">Podczas przetwarzania zawartości tablicy są przypisane do `ArrayExtension.Items` wewnętrzną właściwość.</span><span class="sxs-lookup"><span data-stu-id="f69ef-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="f69ef-118">W <xref:System.Windows.Markup.ArrayExtension> wdrażania, jest reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f69ef-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f69ef-119">W implementacji .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.ArrayExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="f69ef-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="f69ef-120"><xref:System.Windows.Markup.ArrayExtension> nie jest zapieczętowany i może służyć jako podstawa dla implementacji rozszerzenia znaczników dla typu niestandardowego tablicy.</span><span class="sxs-lookup"><span data-stu-id="f69ef-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="f69ef-121">`x:Array` jest więcej przeznaczony dla ogólnych możliwość języka XAML.</span><span class="sxs-lookup"><span data-stu-id="f69ef-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="f69ef-122">Ale `x:Array` może być również przydatne w przypadku określania wartości XAML niektórych właściwości, które przyjmują obsługiwane XAML kolekcji jako ich zawartość właściwości strukturalne.</span><span class="sxs-lookup"><span data-stu-id="f69ef-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="f69ef-123">Na przykład można określić zawartość <xref:System.Collections.IEnumerable> właściwość o `x:Array` użycia.</span><span class="sxs-lookup"><span data-stu-id="f69ef-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="f69ef-124">`x:Array` jest rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="f69ef-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="f69ef-125">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="f69ef-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f69ef-126">`x:Array` częściowo są wyjątkiem od tej reguły, ponieważ zamiast podawać inny atrybut obsługi wartości `x:Array` zapewnia alternatywną obsługę swoją zawartość tekst wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f69ef-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="f69ef-127">To zachowanie umożliwia typy, które nie mogą być obsługiwane przez istniejący model zawartości może być pogrupowane w tablicy i do których odwołuje się w dalszej części związanym z kodem, uzyskując dostęp do tablicy o nazwie; Możesz wywołać <xref:System.Array> metody w celu uzyskania tablicy poszczególne elementy.</span><span class="sxs-lookup"><span data-stu-id="f69ef-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="f69ef-128">Wszystkie rozszerzenia znaczników w XAML ujmować w nawiasy klamrowe ({,} `)` w składni swoich atrybutów, która jest Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f69ef-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="f69ef-129">Aby uzyskać więcej informacji na temat rozszerzenia znaczników ogólnie rzecz biorąc, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f69ef-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="f69ef-130">XAML 2009 roku `x:Array` jest zdefiniowany jako język pierwotnych zamiast rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="f69ef-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="f69ef-131">Aby uzyskać więcej informacji, zobacz [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="f69ef-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="f69ef-132">Uwagi dotyczące użytkowania WPF</span><span class="sxs-lookup"><span data-stu-id="f69ef-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="f69ef-133">Zazwyczaj elementów obiektu, służące do wypełniania `x:Array` nie są elementami, które istnieją w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw XAML i muszą być mapowane prefiks przestrzeni nazw XAML innych niż domyślne.</span><span class="sxs-lookup"><span data-stu-id="f69ef-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="f69ef-134">Na przykład Oto prostej tablicy dwa ciągi przy użyciu `sys` prefiksu (a także `x`) zdefiniowana na poziomie tablicy.</span><span class="sxs-lookup"><span data-stu-id="f69ef-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="f69ef-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="f69ef-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="f69ef-136">Niestandardowe typy, które są używane jako elementów tablicy klasa również musi obsługiwać wymagania dotyczące wystąpienia w XAML jako elementy obiektu.</span><span class="sxs-lookup"><span data-stu-id="f69ef-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="f69ef-137">Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowe dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="f69ef-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69ef-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f69ef-138">See also</span></span>
- [<span data-ttu-id="f69ef-139">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f69ef-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f69ef-140">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="f69ef-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
