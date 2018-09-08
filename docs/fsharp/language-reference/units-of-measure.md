---
title: Jednostki miary (F#)
description: 'Dowiedz się, jak zmiennoprzecinkowych i wartości liczby całkowitej ze znakiem w języku F # można skojarzyć jednostki miary, które są zazwyczaj używane do wskazać, długości, woluminów i urządzeń pamięci masowej.'
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187890"
---
# <a name="units-of-measure"></a><span data-ttu-id="a135d-103">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="a135d-103">Units of Measure</span></span>

<span data-ttu-id="a135d-104">Zmiennoprzecinkowe wartości liczby całkowitej ze znakiem i punkt w języku F # może być skojarzony jednostki miary, które są zwykle używane do wskazania długość woluminu, masa, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="a135d-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="a135d-105">Za pomocą ilości z jednostkami, Włącz kompilator, aby sprawdzić, czy relacje arytmetyczne mają prawidłowe jednostki, co pomaga zapobiec błędy programowania.</span><span class="sxs-lookup"><span data-stu-id="a135d-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="a135d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a135d-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="a135d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a135d-107">Remarks</span></span>

<span data-ttu-id="a135d-108">Definiuje składni powyżej elementem *nazwa jednostki* jako jednostka miary.</span><span class="sxs-lookup"><span data-stu-id="a135d-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="a135d-109">Opcjonalny składnik jest używane do definiowania nową miarę, posługując się jednostkami uprzednio zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="a135d-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="a135d-110">Na przykład następujący wiersz definiuje środek `cm` (centymetr).</span><span class="sxs-lookup"><span data-stu-id="a135d-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="a135d-111">Następujący wiersz określa miarę `ml` (milliliter) jako centymetr sześcienny (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="a135d-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="a135d-112">W poprzedniej składni *miary* to formuła, która obejmuje jednostki.</span><span class="sxs-lookup"><span data-stu-id="a135d-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="a135d-113">W formułach, obejmujące jednostki, typu całkowitego uprawnień są obsługiwane (pozytywne i negatywne), spacji między jednostkami wskazują iloczyn dwóch jednostek `*` wskazuje także produktu, jednostki i `/` wskazuje iloraz jednostek.</span><span class="sxs-lookup"><span data-stu-id="a135d-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="a135d-114">Wzajemnego jednostki, możesz użyć ujemną liczbę całkowitą potęgą lub `/` oznacza rozdzielenie licznik i mianownik formuły jednostki.</span><span class="sxs-lookup"><span data-stu-id="a135d-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="a135d-115">Wiele jednostek w mianownik powinna być otoczona nawiasami.</span><span class="sxs-lookup"><span data-stu-id="a135d-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="a135d-116">Jednostki rozdzielone spacjami, po `/` są interpretowane jako będące częścią mianownik, ale żadnych jednostek po `*` są interpretowane jako będące częścią licznik.</span><span class="sxs-lookup"><span data-stu-id="a135d-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="a135d-117">W wyrażeniach jednostki samodzielnie, aby wskazać bezwymiarowa ilość, lub wraz z innych jednostek, takich jak licznik, można użyć 1.</span><span class="sxs-lookup"><span data-stu-id="a135d-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="a135d-118">Na przykład jednostki wskaźnik powinny być zapisane jako `1/s`, gdzie `s` wskazuje w sekundach.</span><span class="sxs-lookup"><span data-stu-id="a135d-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="a135d-119">Nawiasy nie są używane w formułach jednostki.</span><span class="sxs-lookup"><span data-stu-id="a135d-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="a135d-120">Nie określaj stałe konwersji numerycznej w formułach jednostki; można jednak oddzielnie Definiowanie stałych konwersji przy użyciu jednostek i ich używać w obliczeniach zaznaczone jednostki.</span><span class="sxs-lookup"><span data-stu-id="a135d-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="a135d-121">Formuły jednostki, które oznaczają to samo można pisać na różne sposoby równoważne.</span><span class="sxs-lookup"><span data-stu-id="a135d-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="a135d-122">W związku z tym kompilator konwertuje formuły jednostki spójne formularza, który konwertuje negatywne potęgi odwrotności, grup jednostek do pojedynczego licznik i mianownik i sortuje w kolejności alfabetycznej jednostki w licznik i mianownik.</span><span class="sxs-lookup"><span data-stu-id="a135d-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="a135d-123">Na przykład formuły jednostki `kg m s^-2` i `m /s s * kg` konwertowane są na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="a135d-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="a135d-124">Jednostki miary są używane w ruchomy punkt wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a135d-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="a135d-125">Za pomocą liczb zmiennoprzecinkowych wraz z skojarzone jednostki miary dodaje kolejny poziom bezpieczeństwa i pomaga uniknąć błędów niezgodności jednostki, które mogą wystąpić w formułach, gdy używasz słabo typizowaną liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="a135d-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="a135d-126">Jeśli piszesz zmiennoprzecinkowy wyrażenie punktu, który używa jednostki, muszą być zgodne jednostki w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a135d-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="a135d-127">Można dodać adnotacje literały przy użyciu formuły jednostki w nawiasy kątowe, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="a135d-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="a135d-128">Nie należy umieszczać odstęp między liczbą a nawias kątowy; Jednakże można dołączyć sufiksu literału takich jak `f`, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a135d-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="a135d-129">Typ literału tych adnotacji zmieni się z jego typ pierwotny (takich jak `float`) typowi zwymiarowany, takich jak `float<cm>` lub, w tym przypadku `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="a135d-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="a135d-130">Jednostka adnotacji `<1>` wskazuje bezwymiarowa ilość, a jego typ jest odpowiednikiem typu pierwotnego bez parametru jednostki.</span><span class="sxs-lookup"><span data-stu-id="a135d-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="a135d-131">Typ jednostki miary jest zmiennoprzecinkowej lub podpisany typ całkowity, wraz z adnotacji dodatkowe jednostki, wskazane w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="a135d-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="a135d-132">Dlatego podczas pisania typ konwersji z `g` (g) do `kg` (kg) opisano typy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a135d-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="a135d-133">Jednostki miary są używane dla jednostki kompilacji sprawdzania, ale nie są zachowywane w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="a135d-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="a135d-134">W związku z tym nie wpływają na wydajność.</span><span class="sxs-lookup"><span data-stu-id="a135d-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="a135d-135">Jednostki miary można zastosować do dowolnego typu, nie tylko zmiennoprzecinkowego punktu; jednak tylko typy zmiennoprzecinkowe, podpisywany typów całkowitych i dziesiętnych typy wymiary techniczną ilości.</span><span class="sxs-lookup"><span data-stu-id="a135d-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="a135d-136">W związku z tym tylko warto użyć jednostki miary na typy pierwotne i agregacji, które zawierają te typy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="a135d-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="a135d-137">Poniższy przykład ilustruje użycie jednostek miary.</span><span class="sxs-lookup"><span data-stu-id="a135d-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="a135d-138">Poniższy kod ilustruje sposób konwertowania z bezwymiarowa liczbę zmiennoprzecinkową do zwymiarowany wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="a135d-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="a135d-139">Możesz po prostu mnożenia 1.0, stosując wymiarów ze 1.0.</span><span class="sxs-lookup"><span data-stu-id="a135d-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="a135d-140">Możesz to abstrakcyjna do funkcji, takich jak `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="a135d-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="a135d-141">Ponadto jeśli przekazujesz zwymiarowany wartości do funkcji, które oczekują bezwymiarowa liczb zmiennoprzecinkowych, należy anulować jednostki lub rzutowane na `float` przy użyciu `float` operatora.</span><span class="sxs-lookup"><span data-stu-id="a135d-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="a135d-142">W tym przykładzie, dzielenie przez `1.0<degC>` dla argumentów `printf` ponieważ `printf` oczekuje bezwymiarowa ilości.</span><span class="sxs-lookup"><span data-stu-id="a135d-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="a135d-143">Następująca sesja przykład przedstawiono dane wyjściowe z i danych wejściowych do tego kodu.</span><span class="sxs-lookup"><span data-stu-id="a135d-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="a135d-144">Przy użyciu ogólnych jednostek</span><span class="sxs-lookup"><span data-stu-id="a135d-144">Using Generic Units</span></span>

<span data-ttu-id="a135d-145">Można napisać ogólnych funkcji, które działają na danych, która ma skojarzone jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="a135d-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="a135d-146">Można to zrobić, określając typ wraz z ogólnych jednostki jako parametr typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a135d-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="a135d-147">Tworzenie typów agregacji za pomocą ogólnego jednostki</span><span class="sxs-lookup"><span data-stu-id="a135d-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="a135d-148">Poniższy kod przedstawia sposób tworzenia typ agregacji, który składa się z pojedynczych wartości zmiennoprzecinkowych, które mają jednostek, które są rodzajowe.</span><span class="sxs-lookup"><span data-stu-id="a135d-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="a135d-149">Dzięki temu jeden typ ma zostać utworzony, która współdziała z różnych jednostek.</span><span class="sxs-lookup"><span data-stu-id="a135d-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="a135d-150">Ponadto ogólne jednostki zachować bezpieczeństwo typów, zapewniając, że typ ogólny, który ma jeden zbiór jednostek jest innego typu niż tego samego typu ogólnego z innym zestawem jednostek.</span><span class="sxs-lookup"><span data-stu-id="a135d-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="a135d-151">Podstawy korzystania z tej techniki jest to, że `Measure` atrybut można stosować do typu parametru.</span><span class="sxs-lookup"><span data-stu-id="a135d-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="a135d-152">Jednostki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="a135d-152">Units at Runtime</span></span>

<span data-ttu-id="a135d-153">Jednostki miary są używane do sprawdzania typu statycznego.</span><span class="sxs-lookup"><span data-stu-id="a135d-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="a135d-154">Po skompilowaniu wartości zmiennoprzecinkowe są eliminowane jednostki miary, dlatego jednostki są tracone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a135d-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="a135d-155">W związku z tym wszelkie próby do implementacji funkcji, która zależy od sprawdzania jednostki w czasie wykonywania nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="a135d-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="a135d-156">Na przykład implementacja `ToString` funkcję umożliwiającą wydrukowanie limit jednostek nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="a135d-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="a135d-157">Konwersje</span><span class="sxs-lookup"><span data-stu-id="a135d-157">Conversions</span></span>

<span data-ttu-id="a135d-158">Można przekonwertować na typ, który ma jednostki (na przykład `float<'u>`) do typu, który nie ma jednostek, można użyć funkcji konwersja standardowa.</span><span class="sxs-lookup"><span data-stu-id="a135d-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="a135d-159">Na przykład, można użyć `float` do przekonwertowania na `float` wartość, która nie ma jednostek, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a135d-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="a135d-160">Aby przekonwertować wartość unitless wartość, która zawiera jednostki, należy pomnożyć przez wartość 1 lub 1.0, która jest oznaczona przy użyciu odpowiednich jednostek.</span><span class="sxs-lookup"><span data-stu-id="a135d-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="a135d-161">Do pisania warstwy współdziałanie, istnieją jednak również niektóre funkcje jawne, używanych do konwersji wartości unitless wartości przy użyciu jednostek.</span><span class="sxs-lookup"><span data-stu-id="a135d-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="a135d-162">Zostały one [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modułu.</span><span class="sxs-lookup"><span data-stu-id="a135d-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="a135d-163">Na przykład, aby przekonwertować unitless `float` do `float<cm>`, użyj [floatwithmeasure —](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a135d-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="a135d-164">Jednostki miary w podstawowej biblioteki F #</span><span class="sxs-lookup"><span data-stu-id="a135d-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="a135d-165">Biblioteka jednostka jest dostępna w `FSharp.Data.UnitSystems.SI` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a135d-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="a135d-166">Zawiera jednostki SI w ich formie symboli (takich jak `m` dla licznika) w `UnitSymbols` podrzędnej przestrzeni nazw, a ich pełną nazwę (np. `meter` dla licznika) w `UnitNames` podrzędnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a135d-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="a135d-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a135d-167">See also</span></span>

- [<span data-ttu-id="a135d-168">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a135d-168">F# Language Reference</span></span>](index.md)
