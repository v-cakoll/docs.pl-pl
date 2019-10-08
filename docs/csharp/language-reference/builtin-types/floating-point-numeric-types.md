---
title: Typy liczbowe zmiennoprzecinkowe — C# odwołanie
description: Przegląd wbudowanych typów C# zmiennoprzecinkowych
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002197"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="fcd9c-103">Zmiennoprzecinkowe typy liczbowe (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="fcd9c-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="fcd9c-104">**Typy zmiennoprzecinkowe** są podzbiorem **typów prostych** i mogą być inicjowane za pomocą [*literałów*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="fcd9c-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="fcd9c-105">Wszystkie typy zmiennoprzecinkowe są również typami wartości.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-105">All floating-point types are also value types.</span></span> <span data-ttu-id="fcd9c-106">Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania i równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="fcd9c-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="fcd9c-107">Charakterystyki typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="fcd9c-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="fcd9c-108">C#obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="fcd9c-109">C#Type/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="fcd9c-109">C# type/keyword</span></span>|<span data-ttu-id="fcd9c-110">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="fcd9c-110">Approximate range</span></span>|<span data-ttu-id="fcd9c-111">Dokładność</span><span class="sxs-lookup"><span data-stu-id="fcd9c-111">Precision</span></span>|<span data-ttu-id="fcd9c-112">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="fcd9c-112">Size</span></span>|<span data-ttu-id="fcd9c-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="fcd9c-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="fcd9c-114">± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="fcd9c-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="fcd9c-115">~ 6-9 cyfr</span><span class="sxs-lookup"><span data-stu-id="fcd9c-115">~6-9 digits</span></span>|<span data-ttu-id="fcd9c-116">4 bajty</span><span class="sxs-lookup"><span data-stu-id="fcd9c-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="fcd9c-117">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="fcd9c-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="fcd9c-118">~ 15-17 cyfr</span><span class="sxs-lookup"><span data-stu-id="fcd9c-118">~15-17 digits</span></span>|<span data-ttu-id="fcd9c-119">8 bajtów</span><span class="sxs-lookup"><span data-stu-id="fcd9c-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="fcd9c-120">1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="fcd9c-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="fcd9c-121">28-29 cyfr</span><span class="sxs-lookup"><span data-stu-id="fcd9c-121">28-29 digits</span></span>|<span data-ttu-id="fcd9c-122">16 bajtów</span><span class="sxs-lookup"><span data-stu-id="fcd9c-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="fcd9c-123">W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="fcd9c-124">Są one zamienne.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-124">They are interchangeable.</span></span> <span data-ttu-id="fcd9c-125">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="fcd9c-126">Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="fcd9c-127">Każdy z typów zmiennoprzecinkowych ma stałe `MinValue` i `MaxValue`, które zapewniają minimalną i maksymalną skończoną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="fcd9c-128">Typy `float` i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="fcd9c-129">Na przykład typ `double` zawiera następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fcd9c-130">Ponieważ typ `decimal` ma większą precyzję i mniejszy zakres niż `float` i `double`, jest to odpowiednie dla obliczeń finansowych i pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="fcd9c-131">W wyrażeniu można mieszać typy [całkowite](integral-numeric-types.md) i typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="fcd9c-132">W takim przypadku typy całkowite są konwertowane na typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="fcd9c-133">Obliczanie wyrażenia jest wykonywane zgodnie z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="fcd9c-134">Jeśli jeden z typów zmiennoprzecinkowych ma wartość `double`, wyrażenie oblicza do `double` lub do wartości [logicznej](../keywords/bool.md) w porównaniach relacyjnych lub porównaniach dla równości.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="fcd9c-135">Jeśli w wyrażeniu nie ma żadnego typu `double`, wyrażenie zwróci wartość `float` lub do wartości [logicznej](../keywords/bool.md) w porównaniach relacyjnych lub porównaniach dla równości.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="fcd9c-136">Wyrażenie zmiennoprzecinkowe może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="fcd9c-137">Dodatnie i ujemne zero</span><span class="sxs-lookup"><span data-stu-id="fcd9c-137">Positive and negative zero</span></span>
- <span data-ttu-id="fcd9c-138">Dodatnia i ujemna nieskończoność</span><span class="sxs-lookup"><span data-stu-id="fcd9c-138">Positive and negative infinity</span></span>
- <span data-ttu-id="fcd9c-139">Wartość niebędąca liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="fcd9c-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="fcd9c-140">Skończoną zbiór niezerowych wartości</span><span class="sxs-lookup"><span data-stu-id="fcd9c-140">The finite set of nonzero values</span></span>

<span data-ttu-id="fcd9c-141">Aby uzyskać więcej informacji na temat tych wartości, zobacz IEEE Standard for Binary-zmiennoprzecinkowej arytmetycznej, dostępny w witrynie sieci Web [IEEE](https://www.ieee.org) .</span><span class="sxs-lookup"><span data-stu-id="fcd9c-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="fcd9c-142">Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="fcd9c-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="fcd9c-143">Literały zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="fcd9c-143">Floating-point literals</span></span>

<span data-ttu-id="fcd9c-144">Domyślnie literał liczbowy zmiennoprzecinkowy po prawej stronie operatora przypisania jest traktowany jako `double`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-144">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="fcd9c-145">Można użyć sufiksów do przekonwertowania literału zmiennoprzecinkowego lub całkowitego na określony typ:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-145">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="fcd9c-146">Sufiks `d` lub `D` konwertuje literał na `double`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-146">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="fcd9c-147">Sufiks `f` lub `F` konwertuje literał na `float`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-147">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="fcd9c-148">Sufiks `m` lub `M` konwertuje literał na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-148">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="fcd9c-149">W poniższych przykładach pokazano każdy sufiks:</span><span class="sxs-lookup"><span data-stu-id="fcd9c-149">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="fcd9c-150">Konwersje</span><span class="sxs-lookup"><span data-stu-id="fcd9c-150">Conversions</span></span>

<span data-ttu-id="fcd9c-151">Istnieje niejawna konwersja (nazywana *konwersją rozszerzającą*) z `float` do `double`, ponieważ zakres `float` wartości jest prawidłowym podzbiorem `double` i nie ma żadnej utraty dokładności od `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-151">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="fcd9c-152">Należy użyć jawnego rzutowania do przekonwertowania jednego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-152">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="fcd9c-153">Jest to tzw. *Konwersja na wąskie*.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-153">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="fcd9c-154">Jawny przypadek jest wymagany, ponieważ konwersja może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-154">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="fcd9c-155">Nie istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a typem `decimal`, ponieważ typ `decimal` ma większą precyzję niż `float` lub `double`.</span><span class="sxs-lookup"><span data-stu-id="fcd9c-155">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="fcd9c-156">Aby uzyskać więcej informacji na temat niejawnych konwersji liczbowych, zobacz [tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="fcd9c-156">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="fcd9c-157">Aby uzyskać więcej informacji na temat jawnych konwersji liczbowych, zobacz [jawna tabela konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="fcd9c-157">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcd9c-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcd9c-158">See also</span></span>

- [<span data-ttu-id="fcd9c-159">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="fcd9c-159">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fcd9c-160">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="fcd9c-160">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="fcd9c-161">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="fcd9c-161">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="fcd9c-162">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="fcd9c-162">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="fcd9c-163">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="fcd9c-163">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="fcd9c-164">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="fcd9c-164">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="fcd9c-165">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="fcd9c-165">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="fcd9c-166">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="fcd9c-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="fcd9c-167">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="fcd9c-167">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
