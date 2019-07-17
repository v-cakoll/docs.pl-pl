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
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236061"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="db53c-103">Zmiennoprzecinkowe typy liczbowe (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="db53c-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="db53c-104">**Typów zmiennoprzecinkowych** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="db53c-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="db53c-105">Wszystkie typy zmiennoprzecinkowe są również typy wartości.</span><span class="sxs-lookup"><span data-stu-id="db53c-105">All floating-point types are also value types.</span></span> <span data-ttu-id="db53c-106">Obsługa wszystkich typów liczbowych zmiennoprzecinkowych [arytmetyczne](../operators/arithmetic-operators.md), [porównania i równości](../operators/equality-operators.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="db53c-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="db53c-107">Właściwości typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="db53c-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="db53c-108">C#obsługuje następujące typy zmiennoprzecinkowe wstępnie zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="db53c-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="db53c-109">C#Wpisz/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="db53c-109">C# type/keyword</span></span>|<span data-ttu-id="db53c-110">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="db53c-110">Approximate range</span></span>|<span data-ttu-id="db53c-111">Dokładność</span><span class="sxs-lookup"><span data-stu-id="db53c-111">Precision</span></span>|<span data-ttu-id="db53c-112">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="db53c-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="db53c-113">±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="db53c-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="db53c-114">~ 6 – 9 cyfr</span><span class="sxs-lookup"><span data-stu-id="db53c-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="db53c-115">±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="db53c-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="db53c-116">około 15 – 17 cyfr</span><span class="sxs-lookup"><span data-stu-id="db53c-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="db53c-117">±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="db53c-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="db53c-118">28 – 29 cyfr</span><span class="sxs-lookup"><span data-stu-id="db53c-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="db53c-119">W powyższej tabeli każdego C# wpisz słowo kluczowe z lewej strony kolumny jest aliasem dla danego typu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="db53c-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="db53c-120">Są one wymienne.</span><span class="sxs-lookup"><span data-stu-id="db53c-120">They are interchangeable.</span></span> <span data-ttu-id="db53c-121">Na przykład następujące deklaracje deklarowanie zmiennych tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="db53c-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="db53c-122">Wartością domyślną każdego typu zmiennoprzecinkowego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="db53c-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="db53c-123">Każdy z typów zmiennoprzecinkowych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość skończoną tego typu.</span><span class="sxs-lookup"><span data-stu-id="db53c-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="db53c-124">`float` i `double` typy zapewniają również stałe, które reprezentują wartości not a liczbą i nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="db53c-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="db53c-125">Na przykład `double` typu zawiera następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db53c-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="db53c-126">Ponieważ `decimal` typ ma większą dokładność i mniejszy zakres niż zarówno `float` i `double`, jest odpowiedni do obliczeń finansowych i walutowych.</span><span class="sxs-lookup"><span data-stu-id="db53c-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="db53c-127">Możesz mieszać [całkowitego](integral-numeric-types.md) typów i typów zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="db53c-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="db53c-128">W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="db53c-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="db53c-129">Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="db53c-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="db53c-130">Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="db53c-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="db53c-131">Jeśli ma nie `double` wpisz wyrażenie wyrażenie daje w wyniku `float`, lub [bool](../keywords/bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="db53c-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="db53c-132">Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="db53c-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="db53c-133">Zero dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="db53c-133">Positive and negative zero</span></span>
- <span data-ttu-id="db53c-134">Dodatnie i ujemne nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="db53c-134">Positive and negative infinity</span></span>
- <span data-ttu-id="db53c-135">Wartość nie a liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="db53c-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="db53c-136">Ograniczone zbiór wartości wartość różną od zera</span><span class="sxs-lookup"><span data-stu-id="db53c-136">The finite set of nonzero values</span></span>

<span data-ttu-id="db53c-137">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](https://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="db53c-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="db53c-138">Można użyć dowolnego [standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md) lub [ciągi niestandardowego formatu liczb](../../../standard/base-types/custom-numeric-format-strings.md) sformatować wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="db53c-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="db53c-139">Literały zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="db53c-139">Floating-point literals</span></span>

<span data-ttu-id="db53c-140">Domyślnie, literał liczbowy zmiennoprzecinkowych po prawej stronie operatora przypisania jest traktowany jako `double`.</span><span class="sxs-lookup"><span data-stu-id="db53c-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="db53c-141">Sufiksy umożliwia konwertowanie zmiennoprzecinkowego lub całkowitego literał dla określonego typu:</span><span class="sxs-lookup"><span data-stu-id="db53c-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="db53c-142">`d` Lub `D` sufiks konwertuje literału do `double`.</span><span class="sxs-lookup"><span data-stu-id="db53c-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="db53c-143">`f` Lub `F` sufiks konwertuje literału do `float`.</span><span class="sxs-lookup"><span data-stu-id="db53c-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="db53c-144">`m` Lub `M` sufiks konwertuje literału do `decimal`.</span><span class="sxs-lookup"><span data-stu-id="db53c-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="db53c-145">W poniższych przykładach pokazano każdego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="db53c-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="db53c-146">Konwersje</span><span class="sxs-lookup"><span data-stu-id="db53c-146">Conversions</span></span>

<span data-ttu-id="db53c-147">Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) z `float` do `double` ponieważ zakres `float` wartości jest podzestawem odpowiednie `double` i bez utraty precyzji z `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="db53c-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="db53c-148">Aby przekonwertować jednego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy należy użyć jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="db53c-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="db53c-149">Jest to nazywane *konwersja zawężająca*.</span><span class="sxs-lookup"><span data-stu-id="db53c-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="db53c-150">Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="db53c-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="db53c-151">Istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a `decimal` typu, ponieważ `decimal` typ ma większą precyzję niż albo `float` lub `double`.</span><span class="sxs-lookup"><span data-stu-id="db53c-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="db53c-152">Aby uzyskać więcej informacji dotyczących niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="db53c-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="db53c-153">Aby uzyskać więcej informacji dotyczących jawnych konwersji liczbowych, zobacz [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="db53c-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db53c-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db53c-154">See also</span></span>

- [<span data-ttu-id="db53c-155">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db53c-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="db53c-156">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="db53c-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="db53c-157">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="db53c-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="db53c-158">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="db53c-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="db53c-159">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="db53c-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="db53c-160">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="db53c-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="db53c-161">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="db53c-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="db53c-162">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="db53c-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="db53c-163">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="db53c-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
