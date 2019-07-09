---
title: Zmiennoprzecinkowe typy liczbowe - C# odwołania
description: Omówienie języka C# zmiennoprzecinkowych typów wbudowanych
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664207"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="eb2bc-103">Zmiennoprzecinkowe typy liczbowe (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="eb2bc-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="eb2bc-104">**Typów zmiennoprzecinkowych** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="eb2bc-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="eb2bc-105">Wszystkie typy zmiennoprzecinkowe są również typy wartości.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-105">All floating-point types are also value types.</span></span> <span data-ttu-id="eb2bc-106">Obsługa wszystkich typów liczbowych zmiennoprzecinkowych [arytmetyczne](../operators/arithmetic-operators.md) [porównania i równości](../operators/equality-operators.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="eb2bc-107">W poniższej tabeli przedstawiono dokładności i przybliżonej zakresy dla typów zmiennoprzecinkowych:</span><span class="sxs-lookup"><span data-stu-id="eb2bc-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="eb2bc-108">Typ</span><span class="sxs-lookup"><span data-stu-id="eb2bc-108">Type</span></span>|<span data-ttu-id="eb2bc-109">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="eb2bc-109">Approximate range</span></span>|<span data-ttu-id="eb2bc-110">Dokładność</span><span class="sxs-lookup"><span data-stu-id="eb2bc-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="eb2bc-111">±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="eb2bc-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="eb2bc-112">~ 6 – 9 cyfr</span><span class="sxs-lookup"><span data-stu-id="eb2bc-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="eb2bc-113">±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="eb2bc-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="eb2bc-114">około 15 – 17 cyfr</span><span class="sxs-lookup"><span data-stu-id="eb2bc-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="eb2bc-115">±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="eb2bc-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="eb2bc-116">28 – 29 cyfr</span><span class="sxs-lookup"><span data-stu-id="eb2bc-116">28-29 digits</span></span>|  

<span data-ttu-id="eb2bc-117">Jest wartością domyślną dla wszystkich typów zmiennoprzecinkowych `0`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="eb2bc-118">Każdy z typów zmiennoprzecinkowych ma nazwanych stałych `MinValue` i `MaxValue` minimalne i maksymalne wartości dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="eb2bc-119">`float` i `double` typy mają dodatkowe stałe dla `PositiveInfinity`, `NegativeInfinity`, i `NaN` (w przypadku "nie Number").</span><span class="sxs-lookup"><span data-stu-id="eb2bc-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="eb2bc-120">`decimal` Typu zawiera stałe dla `Zero`, `One`, i `MinusOne`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="eb2bc-121">`decimal` Typ ma większą dokładność i mniejszy zakres niż zarówno `float` i `double`, co czyni go odpowiedni do obliczeń finansowych i walutowych.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="eb2bc-122">Można łączyć typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="eb2bc-123">W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="eb2bc-124">Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="eb2bc-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="eb2bc-125">Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="eb2bc-126">Jeśli ma nie `double` wpisz wyrażenie wyrażenie daje w wyniku `float`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="eb2bc-127">Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="eb2bc-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="eb2bc-128">Zero dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="eb2bc-128">Positive and negative zero</span></span>
- <span data-ttu-id="eb2bc-129">Dodatnie i ujemne nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-129">Positive and negative infinity</span></span>
- <span data-ttu-id="eb2bc-130">Wartość nie a liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="eb2bc-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="eb2bc-131">Ograniczone zbiór wartości wartość różną od zera</span><span class="sxs-lookup"><span data-stu-id="eb2bc-131">The finite set of nonzero values</span></span>

<span data-ttu-id="eb2bc-132">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](https://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="eb2bc-133">Można użyć dowolnego [standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md) lub [ciągi niestandardowego formatu liczb](../../../standard/base-types/custom-numeric-format-strings.md) sformatować wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="eb2bc-134">Literały zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-134">Floating-point literals</span></span>

<span data-ttu-id="eb2bc-135">Domyślnie, literał liczbowy zmiennoprzecinkowych po prawej stronie operatora przypisania jest traktowany jako `double`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="eb2bc-136">Sufiksy umożliwia konwertowanie zmiennoprzecinkowego lub całkowitego literał dla określonego typu:</span><span class="sxs-lookup"><span data-stu-id="eb2bc-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="eb2bc-137">`d` Lub `D` sufiks konwertuje literału do `double`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="eb2bc-138">`f` Lub `F` sufiks konwertuje literału do `float`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="eb2bc-139">`m` Lub `M` sufiks konwertuje literału do `decimal`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="eb2bc-140">W poniższych przykładach pokazano każdego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="eb2bc-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="eb2bc-141">Konwersje</span><span class="sxs-lookup"><span data-stu-id="eb2bc-141">Conversions</span></span>

<span data-ttu-id="eb2bc-142">Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) z `float` do `double` ponieważ zakres `float` wartości jest podzestawem odpowiednie `double` i bez utraty precyzji z `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="eb2bc-143">Aby przekonwertować jednego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy należy użyć jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="eb2bc-144">Jest to nazywane *konwersja zawężająca*.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="eb2bc-145">Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="eb2bc-146">Istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a `decimal` typu, ponieważ `decimal` typ ma większą precyzję niż albo `float` lub `double`.</span><span class="sxs-lookup"><span data-stu-id="eb2bc-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="eb2bc-147">Aby uzyskać więcej informacji dotyczących niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bc-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="eb2bc-148">Aby uzyskać więcej informacji dotyczących jawnych konwersji liczbowych, zobacz [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bc-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb2bc-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb2bc-149">See also</span></span>

- [<span data-ttu-id="eb2bc-150">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eb2bc-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eb2bc-151">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="eb2bc-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="eb2bc-152">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="eb2bc-153">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="eb2bc-154">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="eb2bc-155">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="eb2bc-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="eb2bc-156">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="eb2bc-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="eb2bc-157">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="eb2bc-158">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="eb2bc-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="eb2bc-159">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="eb2bc-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
