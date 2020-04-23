---
title: x:Type — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071361"
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="44a3a-102">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="44a3a-102">x:Type Markup Extension</span></span>

<span data-ttu-id="44a3a-103">Dostarcza obiekt CLR, <xref:System.Type> który jest typem podstawowym dla określonego typu XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="44a3a-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="44a3a-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="44a3a-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="44a3a-105">XAML Object Element Usage</span></span>

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a><span data-ttu-id="44a3a-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="44a3a-106">XAML Values</span></span>

|||
|-|-|
|`prefix`|<span data-ttu-id="44a3a-107">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="44a3a-107">Optional.</span></span> <span data-ttu-id="44a3a-108">Prefiks, który mapuje nieobezwykaną przestrzeń nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="44a3a-109">Określenie prefiksu często nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="44a3a-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="44a3a-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="44a3a-110">See Remarks.</span></span>|
|`typeNameValue`|<span data-ttu-id="44a3a-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="44a3a-111">Required.</span></span> <span data-ttu-id="44a3a-112">Nazwa typu, którą można rozwiązać z bieżącą domyślną przestrzenią nazw XAML; lub określony zamapowany `prefix` prefiks, jeśli jest podany.</span><span class="sxs-lookup"><span data-stu-id="44a3a-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|

## <a name="remarks"></a><span data-ttu-id="44a3a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44a3a-113">Remarks</span></span>

<span data-ttu-id="44a3a-114">Rozszerzenie `x:Type` znaczników ma podobną `typeof()` funkcję do operatora `GetType` w języku C# lub operatora w programie Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="44a3a-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>

<span data-ttu-id="44a3a-115">Rozszerzenie `x:Type` znaczników dostarcza zachowanie konwersji od ciągu dla właściwości, które przyjmują typ <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="44a3a-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="44a3a-116">Dane wejściowe są typem XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-116">The input is a XAML type.</span></span> <span data-ttu-id="44a3a-117">Relacja między wejściowym typem XAML <xref:System.Type> a wyjściowym <xref:System.Type> modułem CLR polega na <xref:System.Xaml.XamlType> tym, że dane wyjściowe <xref:System.Windows.Markup.IXamlTypeResolver> są danymi wejściowymi <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType>, po wyszukinięciu niezbędnego kontekstu schematu XAML i usługi świadczonej przez kontekst.</span><span class="sxs-lookup"><span data-stu-id="44a3a-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="44a3a-118">W usługach .NET XAML obsługa tego rozszerzenia znaczników <xref:System.Windows.Markup.TypeExtension> jest definiowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="44a3a-118">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>

<span data-ttu-id="44a3a-119">W określonych implementacjach framework niektóre <xref:System.Type> właściwości, które przyjmują jako wartość, mogą bezpośrednio akceptować nazwę typu (wartość ciągu typu). `Name`</span><span class="sxs-lookup"><span data-stu-id="44a3a-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="44a3a-120">Jednak implementowanie tego zachowania jest złożonym scenariuszem.</span><span class="sxs-lookup"><span data-stu-id="44a3a-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="44a3a-121">Na przykład zobacz sekcję "Uwagi dotyczące użycia WPF", która jest następująca.</span><span class="sxs-lookup"><span data-stu-id="44a3a-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>

<span data-ttu-id="44a3a-122">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="44a3a-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="44a3a-123">Token ciągu podany `x:Type` po ciągu identyfikatora jest <xref:System.Windows.Markup.TypeExtension.TypeName%2A> przypisany <xref:System.Windows.Markup.TypeExtension> jako wartość podstawowej klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="44a3a-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="44a3a-124">W domyślnym kontekście schematu XAML dla usług .NET XAML Services, który jest oparty <xref:System.Reflection.MemberInfo.Name%2A> na typach CLR, <xref:System.Reflection.MemberInfo.Name%2A> wartość tego atrybutu jest albo żądanym typem, albo zawiera poprzedzony prefiksem nieobezwymionego mapowania obszaru nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-124">Under the default XAML schema context for .NET XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>

<span data-ttu-id="44a3a-125">Rozszerzenie `x:Type` znaczników może być używane w składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="44a3a-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="44a3a-126">W takim przypadku określenie wartości <xref:System.Windows.Markup.TypeExtension.TypeName%2A> właściwości jest wymagane do prawidłowego zainicjowania rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="44a3a-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>

<span data-ttu-id="44a3a-127">Rozszerzenie `x:Type` znaczników może być również używane jako atrybut pełne; jednak to użycie nie jest typowe:`<object property="{x:Type TypeName=typeNameValue}" .../>`</span><span class="sxs-lookup"><span data-stu-id="44a3a-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<object property="{x:Type TypeName=typeNameValue}" .../>`</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="44a3a-128">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="44a3a-128">WPF Usage Notes</span></span>

### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="44a3a-129">Domyślny obszar nazw XAML i mapowanie typów</span><span class="sxs-lookup"><span data-stu-id="44a3a-129">Default XAML Namespace and Type Mapping</span></span>

<span data-ttu-id="44a3a-130">Domyślna przestrzeń nazw XAML dla programowania WPF zawiera większość typów XAML, których potrzebujesz w typowych scenariuszach XAML; w związku z tym często można uniknąć prefiksów podczas odwoływania się do wartości typu XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="44a3a-131">Może być konieczne zamapowanie prefiksu, jeśli odwołujesz się do typu z zestawu niestandardowego lub dla typów, które istnieją w zestawie WPF, ale pochodzą z obszaru nazw CLR, który nie został zamapowany na domyślny obszar nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="44a3a-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="44a3a-132">Aby uzyskać więcej informacji na temat prefiksów, obszarów nazw XAML i mapowania obszarów nazw CLR, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="44a3a-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="44a3a-133">Właściwości typu obsługujące nazwa typu jako ciąg znaków</span><span class="sxs-lookup"><span data-stu-id="44a3a-133">Type Properties That Support Typename-as-String</span></span>

<span data-ttu-id="44a3a-134">WPF WPF obsługuje techniki, które umożliwiają określanie <xref:System.Type> wartości niektórych właściwości typu bez konieczności użycia rozszerzenia znaczników. `x:Type`</span><span class="sxs-lookup"><span data-stu-id="44a3a-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="44a3a-135">Zamiast tego można określić wartość jako ciąg, który nazywa typ.</span><span class="sxs-lookup"><span data-stu-id="44a3a-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="44a3a-136">Przykładami tego <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> są <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>i .</span><span class="sxs-lookup"><span data-stu-id="44a3a-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44a3a-137">Obsługa tego zachowania nie jest świadczona za pośrednictwem konwerterów typu lub rozszerzeń znaczników.</span><span class="sxs-lookup"><span data-stu-id="44a3a-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="44a3a-138">Zamiast tego jest to zachowanie odroczenia <xref:System.Windows.FrameworkElementFactory>zaimplementowane za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="44a3a-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>

<span data-ttu-id="44a3a-139">Silverlight obsługuje podobną konwencję.</span><span class="sxs-lookup"><span data-stu-id="44a3a-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="44a3a-140">W rzeczywistości program Silverlight obecnie `{x:Type}` nie obsługuje obsługi języka XAML `{x:Type}` i nie akceptuje użycia poza kilkoma okolicznościami, które są przeznaczone do obsługi migracji XAML WPF-Silverlight.</span><span class="sxs-lookup"><span data-stu-id="44a3a-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="44a3a-141">W związku z tym zachowanie typename-as-string jest wbudowany do <xref:System.Type> wszystkich silverlight natywnej oceny właściwości, gdzie jest wartością.</span><span class="sxs-lookup"><span data-stu-id="44a3a-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>

## <a name="xaml-2009"></a><span data-ttu-id="44a3a-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="44a3a-142">XAML 2009</span></span>

<span data-ttu-id="44a3a-143">XAML 2009 zapewnia dodatkową obsługę typów ogólnych i `x:TypeArguments` `x:Type` modyfikuje zachowanie funkcji i zapewnić tę obsługę.</span><span class="sxs-lookup"><span data-stu-id="44a3a-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>

- <span data-ttu-id="44a3a-144">`x:TypeArguments`i skojarzony element obiektu dla ogólnego wystąpienia obiektu może znajdować się na elementach innych niż katalog główny.</span><span class="sxs-lookup"><span data-stu-id="44a3a-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="44a3a-145">Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" [x:TypeArguments Directive](xtypearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="44a3a-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](xtypearguments-directive.md).</span></span>

- <span data-ttu-id="44a3a-146">XAML 2009 obsługuje składnię określania ograniczenia typu ogólnego w znacznikach.</span><span class="sxs-lookup"><span data-stu-id="44a3a-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="44a3a-147">Może to być `x:TypeArguments`używane `x:Type`przez , przez , lub przez dwie funkcje w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="44a3a-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>

- <span data-ttu-id="44a3a-148">Implementacja WPF XAML podczas przetwarzania XAML 2009 dla obciążenia również dodaje tę funkcję do <xref:System.Type>zachowania konwersji typu niejawnego dla niektórych właściwości frameworku, które używają typu .</span><span class="sxs-lookup"><span data-stu-id="44a3a-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>

<span data-ttu-id="44a3a-149">W WPF WPF można użyć XAML 2009 funkcje, ale tylko dla luźne XAML (XAML, który nie jest skompilowany znaczników).</span><span class="sxs-lookup"><span data-stu-id="44a3a-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="44a3a-150">Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="44a3a-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="44a3a-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44a3a-151">See also</span></span>

- <xref:System.Windows.Style>
- [<span data-ttu-id="44a3a-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="44a3a-152">Styling and Templating</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="44a3a-153">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="44a3a-153">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="44a3a-154">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="44a3a-154">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
