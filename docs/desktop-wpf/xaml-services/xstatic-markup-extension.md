---
title: x:Static — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072026"
---
# <a name="xstatic-markup-extension"></a><span data-ttu-id="3cb2e-102">x:Static — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="3cb2e-102">x:Static Markup Extension</span></span>

<span data-ttu-id="3cb2e-103">Odwołuje się do każdej statycznej jednostki kodu według wartości, która jest zdefiniowana w sposób zgodny ze specyfikacją języka wspólnego (CLS).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-103">References any static by-value code entity that is defined in a Common Language Specification (CLS)–compliant way.</span></span> <span data-ttu-id="3cb2e-104">Właściwość statyczna, do którego się odwołuje, może służyć do podania wartości właściwości w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-104">The static property that is referenced can be used to provide the value of a property in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="3cb2e-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="3cb2e-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="3cb2e-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="3cb2e-106">XAML Values</span></span>

| | |
|-|-|
|`prefix`|<span data-ttu-id="3cb2e-107">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-107">Optional.</span></span> <span data-ttu-id="3cb2e-108">Prefiks, który odwołuje się do zamapowane, nie-domyślny obszar nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-108">A prefix that refers to a mapped, non-default XAML namespace.</span></span> <span data-ttu-id="3cb2e-109">`prefix`jest jawnie wyświetlany w użyciu, ponieważ rzadko odwołuje się do właściwości statycznych, które pochodzą z domyślnej przestrzeni nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-109">`prefix` is shown explicitly in the usage because you rarely reference static properties that come from a default XAML namespace.</span></span> <span data-ttu-id="3cb2e-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-110">See Remarks.</span></span>|
|`typeName`|<span data-ttu-id="3cb2e-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-111">Required.</span></span> <span data-ttu-id="3cb2e-112">Nazwa typu, który definiuje żądany element członkowski statyczny.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-112">The name of the type that defines the desired static member.</span></span>|
|`staticMemberName`|<span data-ttu-id="3cb2e-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-113">Required.</span></span> <span data-ttu-id="3cb2e-114">Nazwa żądanego elementu członkowskiego wartości statycznej (stała, właściwość statyczna, pole lub wartość wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-114">The name of the desired static value member (a constant, a static property, a field, or an enumeration value).</span></span>|

## <a name="remarks"></a><span data-ttu-id="3cb2e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3cb2e-115">Remarks</span></span>

<span data-ttu-id="3cb2e-116">Encja kodu, do której się odwołuje, musi być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3cb2e-116">The code entity that is referenced must be one of the following:</span></span>

- <span data-ttu-id="3cb2e-117">Stała</span><span class="sxs-lookup"><span data-stu-id="3cb2e-117">A constant</span></span>
- <span data-ttu-id="3cb2e-118">Właściwość statyczna</span><span class="sxs-lookup"><span data-stu-id="3cb2e-118">A static property</span></span>
- <span data-ttu-id="3cb2e-119">Pole</span><span class="sxs-lookup"><span data-stu-id="3cb2e-119">A field</span></span>
- <span data-ttu-id="3cb2e-120">Wartość wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3cb2e-120">An enumeration value</span></span>

<span data-ttu-id="3cb2e-121">Określanie innej jednostki kodu, takiej jak właściwość niestatyczna, powoduje błąd w czasie kompilacji, jeśli znaczniki XAML są skompilowane lub wyjątek analizy czasu ładowania XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-121">Specifying any other code entity, such as a nonstatic property, causes a compile-time error if the XAML is markup compiled, or a XAML load-time parse exception.</span></span>

<span data-ttu-id="3cb2e-122">Można wprowadzać odwołania do pól statycznych lub właściwości, które nie znajdują się `x:Static` w domyślnej przestrzeni nazw XAML dla bieżącego dokumentu XAML; Jednak wymaga to mapowania prefiksu.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-122">You can make `x:Static` references to static fields or properties that are not in the default XAML namespace for the current XAML document; however, this requires a prefix mapping.</span></span> <span data-ttu-id="3cb2e-123">Przestrzenie nazw XAML są prawie zawsze zdefiniowane w elemencie głównym dokumentu XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-123">XAML namespaces are almost always defined on the root element of the XAML document.</span></span>

<span data-ttu-id="3cb2e-124">Operacje wyszukiwania właściwości statycznych mogą być wykonywane przez usługi .NET XAML Services i ich czytniki XAML i moduły zapisujących XAML, gdy są uruchomione z domyślnym kontekstem schematu XAML.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-124">The lookup operations for static properties can be performed by .NET XAML Services and its XAML readers and XAML writers, when they are running with the default XAML schema context.</span></span> <span data-ttu-id="3cb2e-125">Ten kontekst schematu XAML można użyć odbicia CLR, aby zapewnić niezbędne wartości statyczne dla konstrukcji wykresu obiektu.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-125">This XAML schema context can use CLR reflection to provide the necessary static values for object graph construction.</span></span> <span data-ttu-id="3cb2e-126">Określony `typeName` jest w rzeczywistości nazwa typu XAML, a nie nazwa typu CLR, chociaż są one zasadniczo taką samą nazwę podczas korzystania z domyślnego kontekstu schematu XAML lub podczas korzystania z wszystkich istniejących platform implementujących XAML oparte na programie CLR.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-126">The `typeName` you specify is actually a XAML type name, not a CLR type name, although these are essentially the same name when using the default XAML schema context or when using all existing CLR-based XAML-implementing frameworks.</span></span>

<span data-ttu-id="3cb2e-127">Należy zachować `x:Static` ostrożność podczas dokonywania odwołań, które nie są bezpośrednio typu wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-127">Use caution when you make `x:Static` references that are not directly the type of a property's value.</span></span> <span data-ttu-id="3cb2e-128">W sekwencji przetwarzania XAML podane wartości z rozszerzenia znaczników nie wywołać konwersji wartości dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-128">In the XAML processing sequence, provided values from a markup extension do not invoke additional value conversion.</span></span> <span data-ttu-id="3cb2e-129">Jest to prawdą, `x:Static` nawet jeśli odwołanie tworzy ciąg tekstowy, a konwersja wartości dla wartości atrybutów na podstawie ciągu tekstowego zazwyczaj występuje dla tego określonego elementu członkowskiego lub dla dowolnych wartości członkowskich typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-129">This is true even if your `x:Static` reference creates a text string, and a value conversion for attribute values based on text string typically occurs either for that specific member or for any member values of the return type.</span></span>

<span data-ttu-id="3cb2e-130">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-130">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="3cb2e-131">Token ciągu podany `x:Static` po ciągu identyfikatora jest <xref:System.Windows.Markup.StaticExtension.Member%2A> przypisany <xref:System.Windows.Markup.StaticExtension> jako wartość podstawowej klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-131">The string token provided after the `x:Static` identifier string is assigned as the <xref:System.Windows.Markup.StaticExtension.Member%2A> value of the underlying <xref:System.Windows.Markup.StaticExtension> extension class.</span></span>

<span data-ttu-id="3cb2e-132">Istnieją dwa inne użycia XAML, które są technicznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-132">There are two other XAML usages that are technically possible.</span></span> <span data-ttu-id="3cb2e-133">Jednak te użycia są mniej powszechne, ponieważ są one niepotrzebnie pełne:</span><span class="sxs-lookup"><span data-stu-id="3cb2e-133">However, these usages are less common because they are unnecessarily verbose:</span></span>

01. <span data-ttu-id="3cb2e-134">Składnia elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-134">Object element syntax.</span></span>

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. <span data-ttu-id="3cb2e-135">Składnia atrybutu z jawną właściwością Member dla ciągu inicjowania.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-135">Attribute syntax with explicit Member property for initialization string.</span></span>

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

<span data-ttu-id="3cb2e-136">W implementacji usług .NET XAML obsługa tego rozszerzenia <xref:System.Windows.Markup.StaticExtension> znaczników jest definiowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-136">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.StaticExtension> class.</span></span>

<span data-ttu-id="3cb2e-137">`x:Static`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-137">`x:Static` is a markup extension.</span></span> <span data-ttu-id="3cb2e-138">Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi zawierać wartość.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-138">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must provide a value.</span></span> <span data-ttu-id="3cb2e-139">Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników dla XAML Overview](markup-extensions-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-139">For more information about markup extensions, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="3cb2e-140">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="3cb2e-140">WPF Usage Notes</span></span>

<span data-ttu-id="3cb2e-141">Domyślna przestrzeń nazw XAML używana do programowania WPF nie zawiera wielu przydatnych właściwości statycznych, a większość przydatnych właściwości statycznych `{x:Static}` ma obsługę, taką jak konwertery typów, które ułatwiają użycie bez konieczności.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-141">The default XAML namespace you use for WPF programming does not contain many useful static properties, and most of the useful static properties have support such as type converters that facilitate the usage without requiring `{x:Static}` .</span></span> <span data-ttu-id="3cb2e-142">W przypadku właściwości statycznych należy zamapować prefiks obszaru nazw XAML, jeśli spełniony jest jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="3cb2e-142">For static properties, you must map a prefix for a XAML namespace if one of the following is true:</span></span>

- <span data-ttu-id="3cb2e-143">Odwołujesz się do typu, który istnieje w WPF, ale nie jest częścią`http://schemas.microsoft.com/winfx/2006/xaml/presentation`domyślnej przestrzeni nazw XAML dla WPF ( ).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-143">You are referencing a type that exists in WPF but is not part of the default XAML namespace for WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`).</span></span> <span data-ttu-id="3cb2e-144">Jest to dość typowy scenariusz `x:Static`użycia programu .</span><span class="sxs-lookup"><span data-stu-id="3cb2e-144">This is a fairly common scenario for using `x:Static`.</span></span> <span data-ttu-id="3cb2e-145">Na przykład można użyć `x:Static` odwołania z mapowania przestrzeni nazw <xref:System> XAML do obszaru nazw CLR i zestawu mscorlib w celu odwołania się do właściwości statycznych <xref:System.Environment> klasy.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-145">For example, you might use an `x:Static` reference with a XAML namespace mapping to the <xref:System> CLR namespace and mscorlib assembly in order to reference the static properties of the <xref:System.Environment> class.</span></span>

- <span data-ttu-id="3cb2e-146">Odwołujesz się do typu z zestawu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-146">You are referencing a type from a custom assembly.</span></span>

- <span data-ttu-id="3cb2e-147">Odwołujesz się do typu, który istnieje w WPF zestawu, ale ten typ znajduje się w obszarze nazw CLR, który nie został zamapowany do części domyślnej przestrzeni nazw XAML WPF.</span><span class="sxs-lookup"><span data-stu-id="3cb2e-147">You are referencing a type that exists in a WPF assembly, but that type is within a CLR namespace that was not mapped to be part of the WPF default XAML namespace.</span></span> <span data-ttu-id="3cb2e-148">Mapowanie obszarów nazw CLR do domyślnej przestrzeni nazw XAML dla WPF jest wykonywane przez definicje w różnych zestawach WPF (aby uzyskać więcej informacji na temat tej koncepcji, zobacz [XAML obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-148">The mapping of CLR namespaces into the default XAML namespace for WPF is performed by definitions in the various WPF assemblies (for more information about this concept, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)).</span></span> <span data-ttu-id="3cb2e-149">Niemapowane przestrzenie nazw CLR mogą istnieć, jeśli obszar nazw CLR składa się głównie z definicji <xref:System.Windows.Threading>klas, które zazwyczaj nie są przeznaczone dla XAML, takich jak .</span><span class="sxs-lookup"><span data-stu-id="3cb2e-149">Non-mapped CLR namespaces can exist if that CLR namespace is composed mostly of class definitions that are not typically intended for XAML, such as <xref:System.Windows.Threading>.</span></span>

<span data-ttu-id="3cb2e-150">Aby uzyskać więcej informacji na temat używania prefiksów i obszarów nazw XAML dla WPF, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3cb2e-150">For more information on how to use prefixes and XAML namespaces for WPF, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cb2e-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cb2e-151">See also</span></span>

- [<span data-ttu-id="3cb2e-152">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="3cb2e-152">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="3cb2e-153">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="3cb2e-153">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
