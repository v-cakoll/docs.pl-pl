---
title: x:TypeArguments — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071354"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="dc39f-102">x:TypeArguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="dc39f-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="dc39f-103">Przekazuje argumenty typu ograniczające rodzajowy do konstruktora typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="dc39f-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="dc39f-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="dc39f-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="dc39f-105">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="dc39f-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="dc39f-106">Deklaracja elementu obiektu typu XAML, który jest wspierany przez typ ogólny CLR.</span><span class="sxs-lookup"><span data-stu-id="dc39f-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="dc39f-107">Jeśli `object` odwołuje się do typu XAML, który nie pochodzi `object` z domyślnego obszaru nazw XAML, `object` wymaga prefiksu, aby wskazać obszar nazw XAML, gdzie istnieje.</span><span class="sxs-lookup"><span data-stu-id="dc39f-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="dc39f-108">Ciąg, który deklaruje jedną lub więcej nazw typów XAML jako ciągi, który dostarcza argumenty typu dla typu ogólnego CLR.</span><span class="sxs-lookup"><span data-stu-id="dc39f-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="dc39f-109">Zobacz Uwagi, aby uzyskać dodatkowe uwagi składniowe.</span><span class="sxs-lookup"><span data-stu-id="dc39f-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc39f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc39f-110">Remarks</span></span>

<span data-ttu-id="dc39f-111">W większości przypadków typy XAML, które są `typeString` używane jako element informacji w ciągu są poprzedzone.</span><span class="sxs-lookup"><span data-stu-id="dc39f-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="dc39f-112">Typowe typy ograniczeń ogólnych CLR <xref:System.Int32> (na przykład i) <xref:System.String>pochodzą z bibliotek klas podstawowych CLR.</span><span class="sxs-lookup"><span data-stu-id="dc39f-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="dc39f-113">Te biblioteki nie są mapowane do typowych domyślnych obszarów nazw XAML specyficznych dla struktury i dlatego wymagają mapowania prefiksów dla użycia XAML.</span><span class="sxs-lookup"><span data-stu-id="dc39f-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="dc39f-114">Można określić więcej niż jedną nazwę typu XAML za pomocą ogranicznika przecinka.</span><span class="sxs-lookup"><span data-stu-id="dc39f-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="dc39f-115">Jeśli same ograniczenia ogólne używają typów ogólnych, argumenty typu zagnieżdżonego mogą być zawarte w nawiasach ().</span><span class="sxs-lookup"><span data-stu-id="dc39f-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="dc39f-116">Należy zauważyć, `x:TypeArguments` że ta definicja jest specyficzna dla usług .NET XAML i przy użyciu kopii clr.</span><span class="sxs-lookup"><span data-stu-id="dc39f-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="dc39f-117">Definicję na poziomie języka można znaleźć w [ \[sekcji MS-XAML\] 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="dc39f-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="dc39f-118">Przykłady użycia</span><span class="sxs-lookup"><span data-stu-id="dc39f-118">Usage Examples</span></span>

<span data-ttu-id="dc39f-119">W poniższych przykładach załóżmy, że następujące definicje przestrzeni nazw XAML są zadeklarowane:</span><span class="sxs-lookup"><span data-stu-id="dc39f-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="dc39f-120">>\<ciągu listy</span><span class="sxs-lookup"><span data-stu-id="dc39f-120">List\<String></span></span>

<span data-ttu-id="dc39f-121">`<scg:List x:TypeArguments="sys:String" ...>`wystąpienia nowego <xref:System.Collections.Generic.List%601> z argumentem <xref:System.String> typu.</span><span class="sxs-lookup"><span data-stu-id="dc39f-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="dc39f-122">Ciąg\<słownika,Ciąg></span><span class="sxs-lookup"><span data-stu-id="dc39f-122">Dictionary\<String,String></span></span>

<span data-ttu-id="dc39f-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`wystąpienia nowego <xref:System.Collections.Generic.Dictionary%602> z dwoma <xref:System.String> argumentami typu.</span><span class="sxs-lookup"><span data-stu-id="dc39f-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="dc39f-124">Kolejka<Ciąg KeyValuePair,\<Ciąg>></span><span class="sxs-lookup"><span data-stu-id="dc39f-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="dc39f-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601> wystąpienia nowego, który ma ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami <xref:System.String> typu <xref:System.String>ograniczenia wewnętrznego i .</span><span class="sxs-lookup"><span data-stu-id="dc39f-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="dc39f-126">XAML 2006 i WPF Ogólne użycie XAML</span><span class="sxs-lookup"><span data-stu-id="dc39f-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="dc39f-127">W przypadku użycia XAML 2006 i XAML używanego w aplikacjach `x:TypeArguments` WPF istnieją następujące ograniczenia dotyczące ogólnych użycia typu z XAML w ogóle:</span><span class="sxs-lookup"><span data-stu-id="dc39f-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="dc39f-128">Tylko element główny pliku XAML może obsługiwać ogólne użycie XAML, które odwołuje się do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="dc39f-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="dc39f-129">Element główny musi być mapowana do typu ogólnego z co najmniej jednym argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="dc39f-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="dc39f-130">Może to być na przykład <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="dc39f-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="dc39f-131">Funkcje strony są podstawowym scenariuszem obsługi użycia ogólnego XAML w WPF.</span><span class="sxs-lookup"><span data-stu-id="dc39f-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="dc39f-132">Element główny XAML element obiektu dla ogólnego musi `x:Class`również zadeklarować klasę częściową przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="dc39f-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="dc39f-133">Jest to prawdą, nawet jeśli definiowanie akcji kompilacji WPF.</span><span class="sxs-lookup"><span data-stu-id="dc39f-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="dc39f-134">`x:TypeArguments`nie można odwoływać się do zagnieżdżonych ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="dc39f-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="dc39f-135">XAML 2009 lub XAML 2006 bez zależności WPF 3.0 lub WPF 3.5</span><span class="sxs-lookup"><span data-stu-id="dc39f-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="dc39f-136">W usługach .NET XAML dla XAML 2006 lub XAML 2009 ograniczenia związane z WPF ogólne użycie XAML są złagodzone.</span><span class="sxs-lookup"><span data-stu-id="dc39f-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="dc39f-137">Można utworzyć wystąpienie elementu obiektu ogólnego w dowolnym miejscu w znacznikach XAML, które może obsługiwać system typu kopii zapasowej i model obiektu.</span><span class="sxs-lookup"><span data-stu-id="dc39f-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="dc39f-138">Jeśli używasz XAML 2009 zamiast mapowania typów podstawowych CLR w celu uzyskania typów XAML dla pierwotnych języków wspólnych, można użyć [wbudowanych typów dla wspólnych elementów pierwotnych języka XAML](types-for-primitives.md) jako elementów informacyjnych w `typeString`pliku .</span><span class="sxs-lookup"><span data-stu-id="dc39f-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="dc39f-139">Na przykład można zadeklarować następujące (mapowania prefiksów nie są wyświetlane, ale x jest przestrzenią nazw XAML języka XAML dla XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="dc39f-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="dc39f-140">W WPF I podczas kierowania .NET Framework 4 lub .NET Core 3.0 (lub nowsze), `x:TypeArguments` można użyć funkcji XAML 2009 wraz z, ale tylko dla luźnego XAML (XAML, który nie jest skompilowany znaczników).</span><span class="sxs-lookup"><span data-stu-id="dc39f-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="dc39f-141">Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="dc39f-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="dc39f-142">Jeśli chcesz oznaczyć skompilować XAML, należy działać zgodnie z ograniczeniami opisanymi w [XAML 2006 i WPF Generic XAML usages](#xaml-2006-and-wpf-generic-xaml-usages) sekcji.</span><span class="sxs-lookup"><span data-stu-id="dc39f-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="dc39f-143">BAML jest obsługiwany tylko w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc39f-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc39f-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc39f-144">See also</span></span>

- [<span data-ttu-id="dc39f-145">x:Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="dc39f-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="dc39f-146">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="dc39f-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="dc39f-147">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="dc39f-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="dc39f-148">Typy ogólne w XAML</span><span class="sxs-lookup"><span data-stu-id="dc39f-148">Generics in XAML</span></span>](generics.md)
