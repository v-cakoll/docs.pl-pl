---
title: Jednostki miary (F#)
description: 'Dowiedz się, jak zmiennoprzecinkowych i podpisane liczby całkowite w języku F # można skojarzyć jednostki miary, które zwykle są używane do wskazywania długość, wielkości i masowej.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 336a1e04426fb39f5ceb98e06a06cd7eadc36e85
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="units-of-measure"></a><span data-ttu-id="73179-103">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="73179-103">Units of Measure</span></span>

<span data-ttu-id="73179-104">Liczby zmiennoprzecinkowe punktu i podpisane liczby całkowite w języku F # można skojarzyć jednostki miary, które zwykle są używane do wskazywania woluminu, długość, masa, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="73179-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="73179-105">Za pomocą ilości z jednostkami, Włącz kompilator, aby sprawdzić, czy relacje arytmetyczne mają prawidłowe jednostki, co pomaga zapobiec błędy programowania.</span><span class="sxs-lookup"><span data-stu-id="73179-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="73179-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73179-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="73179-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73179-107">Remarks</span></span>
<span data-ttu-id="73179-108">Definiuje poprzedniej składni *nazwa jednostki* jednostką miary.</span><span class="sxs-lookup"><span data-stu-id="73179-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="73179-109">Opcjonalny składnik służy do definiowania nowej miary pod względem wcześniej zdefiniowanego jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="73179-110">Na przykład poniższy wiersz definiuje miary `cm` (centymetr).</span><span class="sxs-lookup"><span data-stu-id="73179-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="73179-111">Następujący wiersz definiuje miary `ml` (milliliter) jako centymetr sześcienny (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="73179-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="73179-112">W poprzednich składni *miary* jest formuła, której dotyczy jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="73179-113">W formułach obejmujących jednostki, integralną uprawnienia są obsługiwane (dodatnie i ujemne), spacji między jednostkami wskazuje iloczyn dwóch jednostek `*` wskazuje także produktu jednostek, a `/` wskazuje iloraz jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="73179-114">Wzajemne jednostki, możesz użyć zasilania ujemnej liczby całkowitej lub `/` wskazujące rozdzielenie licznik i mianownik formuły jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="73179-115">Wiele jednostek w mianownika powinny być ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="73179-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="73179-116">Jednostki rozdzielone spacjami po `/` będą interpretowane jako część mianownika, ale wszystkie jednostki po `*` będą interpretowane jako część licznik.</span><span class="sxs-lookup"><span data-stu-id="73179-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="73179-117">Możesz użyć 1 w wyrażeniach jednostki samodzielnie, aby wskazać ilość bez wymiaru, lub wraz z innych jednostek, takich jak licznik.</span><span class="sxs-lookup"><span data-stu-id="73179-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="73179-118">Na przykład jednostki dla stawki powinny być zapisane jako `1/s`, gdzie `s` wskazuje w sekundach.</span><span class="sxs-lookup"><span data-stu-id="73179-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="73179-119">Nawiasy nie są używane w formułach jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="73179-120">Nie określaj konwersja liczbowa stałe w formułach jednostki; można jednak Definiowanie stałych konwersja z jednostki oddzielnie i korzystanie z nich obliczenia zaznaczone jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="73179-121">Na różne sposoby równoważne można pisać formuły jednostki, które oznaczają to samo.</span><span class="sxs-lookup"><span data-stu-id="73179-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="73179-122">W związku z tym kompilator konwertuje formuły jednostki na spójne formularza, który konwertuje ujemna uprawnień odwrotności, grupy jednostek w jeden licznik i mianownik i sortuje jednostki w liczniku i mianownik w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="73179-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="73179-123">Na przykład formuły jednostki `kg m s^-2` i `m /s s * kg` konwertowane są na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="73179-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="73179-124">Jednostki miary jest używany w przestawne wyrażeniach punktu.</span><span class="sxs-lookup"><span data-stu-id="73179-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="73179-125">Za pomocą liczby zmiennoprzecinkowe oraz skojarzone jednostki miary dodaje kolejny poziom zabezpieczeń i pozwala uniknąć błędów niezgodność jednostki, które mogą wystąpić w formułach, gdy używasz lekko typu liczby zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="73179-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="73179-126">Jeśli piszesz zmiennoprzecinkową punktu wyrażenie, które używa jednostki, muszą być zgodne jednostki w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="73179-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="73179-127">Może dodawać adnotacje do literały z formułą jednostki w nawiasach ostrych, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="73179-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="73179-128">Nie należy umieszczać odstęp między liczbą i nawiasu ostrego; jednak można uwzględnić sufiksu literału takich jak `f`, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="73179-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="73179-129">Takie adnotacji zmienia typ literału z typu podstawowego (takich jak `float`) do typu wymiarów, takich jak `float<cm>` lub, w tym przypadku `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="73179-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="73179-130">Jednostka adnotacji `<1>` wskazuje ilość bez wymiaru i jego typ jest odpowiednikiem typu pierwotnego bez parametru jednostki.</span><span class="sxs-lookup"><span data-stu-id="73179-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="73179-131">Typ jednostki miary jest zmiennoprzecinkowej lub podpisany typ całkowity wraz z jednostki dodatkowych adnotacji, wskazane w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="73179-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="73179-132">W związku z tym podczas zapisu typ konwersji z `g` (g) do `kg` (kg) opisano typy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="73179-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="73179-133">Jednostki miary są używane dla jednostki kompilacji sprawdzania, ale nie są zachowywane w środowisku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="73179-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="73179-134">W związku z tym nie wpływają na wydajność.</span><span class="sxs-lookup"><span data-stu-id="73179-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="73179-135">Jednostki miary mogą być stosowane do dowolnego typu, nie tylko zmiennoprzecinkową typy punktów; jednak tylko zmiennoprzecinkowych typów, podpisany typów całkowitych i dziesiętnych typy obsługi wymiarów ilości.</span><span class="sxs-lookup"><span data-stu-id="73179-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="73179-136">W związku z tym tylko warto programu jednostki miary w typach pierwotnych i zagregowanych danych, które zawierają te typy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="73179-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="73179-137">Poniższy przykład przedstawia użycie jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="73179-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="73179-138">W poniższym przykładzie przedstawiono sposób konwertowanie bez wymiaru liczba zmiennoprzecinkowa na wymiarów wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="73179-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="73179-139">Możesz po prostu należy pomnożyć przez 1.0, stosowania wymiary do 1.0.</span><span class="sxs-lookup"><span data-stu-id="73179-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="73179-140">Można to abstrakcyjnej do funkcji, takich jak `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="73179-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="73179-141">Ponadto podczas wymiarów wartości należy przekazać do funkcji, które oczekują bez wymiaru liczby zmiennoprzecinkowe, musisz anulować limit jednostki lub rzutowane na `float` przy użyciu `float` operatora.</span><span class="sxs-lookup"><span data-stu-id="73179-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="73179-142">W tym przykładzie dzielenia przez `1.0<degC>` dla argumentów do `printf` ponieważ `printf` oczekuje ilości bez wymiaru.</span><span class="sxs-lookup"><span data-stu-id="73179-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="73179-143">Następująca sesja przykładzie przedstawiono dane wyjściowe z i dane wejściowe, aby ten kod.</span><span class="sxs-lookup"><span data-stu-id="73179-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="73179-144">Przy użyciu jednostek ogólnych</span><span class="sxs-lookup"><span data-stu-id="73179-144">Using Generic Units</span></span>
<span data-ttu-id="73179-145">Można zapisać ogólne funkcje, które działają na dane, które ma skojarzone jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="73179-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="73179-146">W tym celu określanie typu wraz z ogólnym jednostki jako parametr typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="73179-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="73179-147">Tworzenie typów agregacji w przypadku ogólnych jednostek</span><span class="sxs-lookup"><span data-stu-id="73179-147">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="73179-148">Poniższy kod przedstawia sposób tworzenia typu agregacji, który składa się z poszczególnych wartości zmiennoprzecinkowych mających jednostki, które są ogólne.</span><span class="sxs-lookup"><span data-stu-id="73179-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="73179-149">Dzięki temu jednego typu ma zostać utworzony, który współpracuje z różnych jednostek.</span><span class="sxs-lookup"><span data-stu-id="73179-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="73179-150">Ogólny jednostki zachowują również, typ bezpieczeństwa przez zapewnienie, że typu ogólnego, który ma jeden zestaw jednostek jest innego typu niż tego samego typu ogólnego z innym zestawem jednostek.</span><span class="sxs-lookup"><span data-stu-id="73179-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="73179-151">Podstawy tej metody oznacza, że `Measure` atrybut można stosować do parametru typu.</span><span class="sxs-lookup"><span data-stu-id="73179-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="73179-152">Jednostki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="73179-152">Units at Runtime</span></span>
<span data-ttu-id="73179-153">Jednostki miary są używane w celu sprawdzenia typu statycznego.</span><span class="sxs-lookup"><span data-stu-id="73179-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="73179-154">Gdy wartości zmiennoprzecinkowe są kompilowane, jednostki miary są eliminowane, więc jednostki zostaną utracone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="73179-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="73179-155">W związku z tym każda próba wykonania funkcji zależy od sprawdzania jednostki w czasie wykonywania nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="73179-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="73179-156">Na przykład implementacja `ToString` funkcji, aby wydrukować jednostki nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="73179-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="73179-157">Konwersje</span><span class="sxs-lookup"><span data-stu-id="73179-157">Conversions</span></span>
<span data-ttu-id="73179-158">Aby przekonwertować typu, który zawiera jednostki (na przykład `float<'u>`) do typu, który nie ma jednostki, możesz użyć funkcji konwersja standardowa.</span><span class="sxs-lookup"><span data-stu-id="73179-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="73179-159">Na przykład można użyć `float` do przekonwertowania na `float` wartość, która nie ma jednostki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="73179-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="73179-160">Aby przekonwertować wartość unitless na wartość, która zawiera jednostki, można pomnożyć przez wartość 1 lub 1.0, który jest oznaczony w odpowiednich jednostek.</span><span class="sxs-lookup"><span data-stu-id="73179-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="73179-161">Do pisania warstwy współdziałanie, istnieją jednak także niektóre funkcje explicit, których można użyć do konwersji wartości unitless wartości z jednostkami.</span><span class="sxs-lookup"><span data-stu-id="73179-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="73179-162">Są to [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modułu.</span><span class="sxs-lookup"><span data-stu-id="73179-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="73179-163">Na przykład, aby przekonwertować z unitless `float` do `float<cm>`, użyj [floatwithmeasure —](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="73179-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a><span data-ttu-id="73179-164">Jednostki miary w pakiecie zasilania F #</span><span class="sxs-lookup"><span data-stu-id="73179-164">Units of Measure in the F# Power Pack</span></span>
<span data-ttu-id="73179-165">Biblioteka jednostki jest dostępna w PowerPack F #.</span><span class="sxs-lookup"><span data-stu-id="73179-165">A unit library is available in the F# PowerPack.</span></span> <span data-ttu-id="73179-166">Biblioteka jednostki zawiera jednostki SI i stałych fizycznych.</span><span class="sxs-lookup"><span data-stu-id="73179-166">The unit library includes SI units and physical constants.</span></span>


## <a name="see-also"></a><span data-ttu-id="73179-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73179-167">See Also</span></span>
[<span data-ttu-id="73179-168">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="73179-168">F# Language Reference</span></span>](index.md)
