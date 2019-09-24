---
title: Jednostki miary
description: Dowiedz się, w jaki sposób zmiennoprzecinkowe F# i podpisane wartości całkowite w programie mogą mieć skojarzone jednostki miary, które zwykle są używane do wskazywania długości, ilości i masy.
ms.date: 05/16/2016
ms.openlocfilehash: a81f7760301dc580e333d4659a72e6259d2c916b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216686"
---
# <a name="units-of-measure"></a><span data-ttu-id="e599b-103">Jednostki miary</span><span class="sxs-lookup"><span data-stu-id="e599b-103">Units of Measure</span></span>

<span data-ttu-id="e599b-104">Wartości zmiennoprzecinkowe i ze znakami F# całkowitymi w programie mogą mieć skojarzone jednostki miary, które zwykle są używane do wskazywania długości, objętości, masy itd.</span><span class="sxs-lookup"><span data-stu-id="e599b-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="e599b-105">Korzystając z ilości w jednostkach, należy włączyć kompilator, aby sprawdzić, czy relacje arytmetyczne mają poprawne jednostki, co pomaga zapobiegać błędom programowania.</span><span class="sxs-lookup"><span data-stu-id="e599b-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="e599b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e599b-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="e599b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e599b-107">Remarks</span></span>

<span data-ttu-id="e599b-108">Poprzednia składnia definiuje *nazwę jednostki* jako jednostkę miary.</span><span class="sxs-lookup"><span data-stu-id="e599b-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="e599b-109">Opcjonalna część służy do definiowania nowej miary w warunkach wcześniej zdefiniowanych jednostek.</span><span class="sxs-lookup"><span data-stu-id="e599b-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="e599b-110">Na przykład poniższy wiersz definiuje miarę `cm` (centymetr).</span><span class="sxs-lookup"><span data-stu-id="e599b-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="e599b-111">Poniższy wiersz definiuje miarę `ml` (milliliter) jako centymetr sześcienny (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="e599b-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="e599b-112">W poprzedniej składni *miary* jest formułą, która obejmuje jednostki.</span><span class="sxs-lookup"><span data-stu-id="e599b-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="e599b-113">W formułach obejmujących jednostki, obsługiwane są uprawnienia całek (dodatnie i ujemne), spacje między jednostkami wskazują iloczyn dwóch jednostek `*` , wskazuje również iloczyn jednostek i `/` wskazuje iloraz jednostek.</span><span class="sxs-lookup"><span data-stu-id="e599b-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="e599b-114">W przypadku jednostki wzajemnej można użyć ujemnej potęgi całkowitej lub `/` , która wskazuje oddzielenie między licznikiem i mianownikiem formuły jednostkowej.</span><span class="sxs-lookup"><span data-stu-id="e599b-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="e599b-115">Wiele jednostek w mianowniku należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e599b-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="e599b-116">Jednostki rozdzielone spacjami po `/` wartości są interpretowane jako część mianownika, ale wszystkie jednostki `*` po są interpretowane jako część licznika.</span><span class="sxs-lookup"><span data-stu-id="e599b-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="e599b-117">Możesz użyć 1 w wyrażeniach jednostkowych, aby wskazać ilość bez wymiaru lub łącznie z innymi jednostkami, takimi jak w liczniku.</span><span class="sxs-lookup"><span data-stu-id="e599b-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="e599b-118">Na przykład jednostki dla stawki byłyby zapisywane jako `1/s`, gdzie `s` wskazuje sekundy.</span><span class="sxs-lookup"><span data-stu-id="e599b-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="e599b-119">Nawiasy nie są używane w formułach jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="e599b-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="e599b-120">Nie określono liczbowych stałych konwersji w formułach jednostkowych; można jednak definiować stałe konwersji z jednostkami oddzielnie i używać ich w obliczeniach sprawdzanych przez jednostkę.</span><span class="sxs-lookup"><span data-stu-id="e599b-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="e599b-121">Formuły jednostkowe, które oznaczają te same czynności, można napisać na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="e599b-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="e599b-122">W związku z tym kompilator konwertuje formuły jednostkowe na spójną postać, która konwertuje negatywne uprawnienia do reciprocals, grupuje jednostki w pojedynczy licznik i mianownik, a alphabetizes jednostki w liczniku i mianowniku.</span><span class="sxs-lookup"><span data-stu-id="e599b-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="e599b-123">Na przykład formuły `kg m s^-2` jednostkowe i `m /s s * kg` są konwertowane na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="e599b-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="e599b-124">W wyrażeniach zmiennoprzecinkowych są używane jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="e599b-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="e599b-125">Użycie liczb zmiennoprzecinkowych razem ze skojarzonymi jednostkami miary dodaje inny poziom bezpieczeństwa typów i pomaga uniknąć błędów niezgodności jednostek, które mogą wystąpić w formułach w przypadku używania słabo wpisanych liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="e599b-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="e599b-126">Jeśli piszesz wyrażenie zmiennoprzecinkowe używające jednostek, jednostki w wyrażeniu muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="e599b-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="e599b-127">Można dodać adnotacje do literałów z formułą jednostkową w nawiasach kątowych, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="e599b-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="e599b-128">Nie umieszczasz spacji między liczbą i nawiasem ostrym; można jednak dołączyć sufiks literału, taki jak `f`w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e599b-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="e599b-129">Taka adnotacja zmienia typ literału z jego typu pierwotnego (na przykład `float`) na typ wymiarowy, taki jak `float<cm>` lub `float<miles/hour>`, w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="e599b-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="e599b-130">Adnotacja `<1>` jednostki wskazuje ilość bez wymiaru, a jej typ jest równoważny z typem pierwotnym bez parametru jednostki.</span><span class="sxs-lookup"><span data-stu-id="e599b-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="e599b-131">Typ jednostki miary jest zmiennoprzecinkowym lub podpisanym typem całkowitym wraz z dodatkową adnotacją jednostki, wskazanym w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e599b-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="e599b-132">W ten sposób podczas pisania typu konwersji z `g` (gramów) do `kg` (kilogramów) należy opisać typy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e599b-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="e599b-133">Jednostki miary są używane do sprawdzania jednostek czasu kompilacji, ale nie są utrwalane w środowisku wykonawczym.</span><span class="sxs-lookup"><span data-stu-id="e599b-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="e599b-134">W związku z tym nie wpływają one na wydajność.</span><span class="sxs-lookup"><span data-stu-id="e599b-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="e599b-135">Jednostki miary można zastosować do dowolnego typu, a nie tylko typów zmiennoprzecinkowych; jednak tylko typy zmiennoprzecinkowe, podpisane typy całkowite i typy dziesiętne obsługują wielkości zwymiarowane.</span><span class="sxs-lookup"><span data-stu-id="e599b-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="e599b-136">W związku z tym warto używać tylko jednostek miary w typach pierwotnych i w agregacjach, które zawierają te typy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="e599b-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="e599b-137">Poniższy przykład ilustruje użycie jednostek miary.</span><span class="sxs-lookup"><span data-stu-id="e599b-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="e599b-138">Poniższy przykład kodu ilustruje sposób konwersji z liczby zmiennoprzecinkowej bezwymiarowej na zwymiarowaną wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="e599b-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="e599b-139">Przemnożono o 1,0, stosując wymiary do 1,0.</span><span class="sxs-lookup"><span data-stu-id="e599b-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="e599b-140">Można go abstrakcyjnić do funkcji, takiej `degreesFahrenheit`jak.</span><span class="sxs-lookup"><span data-stu-id="e599b-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="e599b-141">Ponadto, gdy wartości wymiarów są przekazywane do funkcji, które oczekują liczb zmiennoprzecinkowych bezwymiarowych, należy anulować jednostki lub rzutować do `float` przy `float` użyciu operatora.</span><span class="sxs-lookup"><span data-stu-id="e599b-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="e599b-142">W tym przykładzie dzieli się przez `1.0<degC>` argumenty z `printf` , ponieważ `printf` oczekuje to ilości bez wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e599b-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="e599b-143">Poniższa przykładowa sesja pokazuje dane wyjściowe z i wejścia do tego kodu.</span><span class="sxs-lookup"><span data-stu-id="e599b-143">The following example session shows the outputs from and inputs to this code.</span></span>

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="e599b-144">Korzystanie z jednostek generycznych</span><span class="sxs-lookup"><span data-stu-id="e599b-144">Using Generic Units</span></span>

<span data-ttu-id="e599b-145">Można napisać funkcje ogólne, które działają na danych ze skojarzoną jednostką miary.</span><span class="sxs-lookup"><span data-stu-id="e599b-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="e599b-146">W tym celu należy określić typ razem z jednostką ogólną jako parametr typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e599b-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="e599b-147">Tworzenie typów zagregowanych z jednostkami ogólnymi</span><span class="sxs-lookup"><span data-stu-id="e599b-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="e599b-148">Poniższy kod pokazuje, jak utworzyć typ zagregowany składający się z pojedynczych wartości zmiennoprzecinkowych, które mają jednostki, które są ogólne.</span><span class="sxs-lookup"><span data-stu-id="e599b-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="e599b-149">Dzięki temu można utworzyć pojedynczy typ, który działa z różnymi jednostkami.</span><span class="sxs-lookup"><span data-stu-id="e599b-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="e599b-150">Ponadto jednostki ogólne zachowują bezpieczeństwo typu przez zapewnienie, że typ ogólny, który ma jeden zestaw jednostek, jest innego typu niż ten sam typ ogólny z innym zestawem jednostek.</span><span class="sxs-lookup"><span data-stu-id="e599b-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="e599b-151">Podstawą tej metody jest to, że `Measure` atrybut może być stosowany do parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e599b-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="e599b-152">Jednostki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e599b-152">Units at Runtime</span></span>

<span data-ttu-id="e599b-153">Jednostki miary są używane do sprawdzania typu statycznego.</span><span class="sxs-lookup"><span data-stu-id="e599b-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="e599b-154">Gdy wartości zmiennoprzecinkowe są kompilowane, jednostki miary są eliminowane, więc jednostki zostaną utracone w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e599b-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="e599b-155">W związku z tym każda próba zaimplementowania funkcji, która zależy od sprawdzania jednostek w czasie wykonywania, nie jest możliwa.</span><span class="sxs-lookup"><span data-stu-id="e599b-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="e599b-156">Na przykład zaimplementowanie `ToString` funkcji do drukowania jednostek nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="e599b-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="e599b-157">Konwersje</span><span class="sxs-lookup"><span data-stu-id="e599b-157">Conversions</span></span>

<span data-ttu-id="e599b-158">Aby skonwertować typ, który ma jednostki (na przykład `float<'u>`) na typ, który nie ma jednostek, można użyć standardowej funkcji konwersji.</span><span class="sxs-lookup"><span data-stu-id="e599b-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="e599b-159">Na przykład można użyć `float` do konwersji `float` na wartość, która nie ma jednostek, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e599b-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="e599b-160">Aby skonwertować wartość bezjednostkową na wartość, która ma jednostki, można pomnożyć wartość 1 lub 1,0, która ma adnotację z odpowiednimi jednostkami.</span><span class="sxs-lookup"><span data-stu-id="e599b-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="e599b-161">Jednak w przypadku pisania warstw współdziałania dostępne są również pewne jawne funkcje, których można użyć do konwersji wartości bezjednostkowych na wartości w jednostkach.</span><span class="sxs-lookup"><span data-stu-id="e599b-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="e599b-162">Znajdują się one w module [Microsoft. FSharp. Core. LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) .</span><span class="sxs-lookup"><span data-stu-id="e599b-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="e599b-163">Na przykład aby przeprowadzić konwersję z bezjednostkowego `float` na a `float<cm>`, użyj [FloatWithMeasure —](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e599b-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="e599b-164">Jednostki miary w bibliotece F# podstawowej</span><span class="sxs-lookup"><span data-stu-id="e599b-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="e599b-165">Biblioteka jednostek jest dostępna w `FSharp.Data.UnitSystems.SI` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e599b-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="e599b-166">Zawiera jednostki si w obu ich `m` symbolach (na przykład dla miernika) `UnitSymbols` w przestrzeni nazw, a `meter` ich pełna nazwa (na przykład dla miernika) w `UnitNames` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e599b-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="e599b-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e599b-167">See also</span></span>

- [<span data-ttu-id="e599b-168">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e599b-168">F# Language Reference</span></span>](index.md)
