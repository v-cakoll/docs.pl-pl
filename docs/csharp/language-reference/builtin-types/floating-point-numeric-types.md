---
title: Typy liczbowe zmiennoprzecinkowe — C# odwołanie
description: Przegląd wbudowanych typów C# zmiennoprzecinkowych
ms.date: 10/22/2019
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
ms.openlocfilehash: 23aa33c6887db48a12f995efc5e1e2220d30216c
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552278"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="a6c5e-103">Zmiennoprzecinkowe typy liczbowe (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="a6c5e-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="a6c5e-104">**Typy zmiennoprzecinkowe** są podzbiorem **typów prostych** i mogą być inicjowane za pomocą [*literałów*](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="a6c5e-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="a6c5e-105">Wszystkie typy zmiennoprzecinkowe są również typami wartości.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-105">All floating-point types are also value types.</span></span> <span data-ttu-id="a6c5e-106">Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="a6c5e-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="a6c5e-107">Charakterystyki typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="a6c5e-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="a6c5e-108">C#obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="a6c5e-109">C#Type/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="a6c5e-109">C# type/keyword</span></span>|<span data-ttu-id="a6c5e-110">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="a6c5e-110">Approximate range</span></span>|<span data-ttu-id="a6c5e-111">Dokładność</span><span class="sxs-lookup"><span data-stu-id="a6c5e-111">Precision</span></span>|<span data-ttu-id="a6c5e-112">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="a6c5e-112">Size</span></span>|<span data-ttu-id="a6c5e-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="a6c5e-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="a6c5e-114">± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="a6c5e-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="a6c5e-115">~ 6-9 cyfr</span><span class="sxs-lookup"><span data-stu-id="a6c5e-115">~6-9 digits</span></span>|<span data-ttu-id="a6c5e-116">4 bajty</span><span class="sxs-lookup"><span data-stu-id="a6c5e-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="a6c5e-117">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="a6c5e-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="a6c5e-118">~ 15-17 cyfr</span><span class="sxs-lookup"><span data-stu-id="a6c5e-118">~15-17 digits</span></span>|<span data-ttu-id="a6c5e-119">8 bajtów</span><span class="sxs-lookup"><span data-stu-id="a6c5e-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="a6c5e-120">1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="a6c5e-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="a6c5e-121">28-29 cyfr</span><span class="sxs-lookup"><span data-stu-id="a6c5e-121">28-29 digits</span></span>|<span data-ttu-id="a6c5e-122">16 bajtów</span><span class="sxs-lookup"><span data-stu-id="a6c5e-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="a6c5e-123">W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="a6c5e-124">Są one zamienne.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-124">They are interchangeable.</span></span> <span data-ttu-id="a6c5e-125">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="a6c5e-126">Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="a6c5e-127">Każdy z typów zmiennoprzecinkowych ma stałe `MinValue` i `MaxValue`, które zapewniają minimalną i maksymalną skończoną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="a6c5e-128">Typy `float` i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="a6c5e-129">Na przykład typ `double` zapewnia następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a6c5e-130">Ponieważ typ `decimal` ma większą precyzję i mniejszy zakres niż `float` i `double`, jest on odpowiedni dla obliczeń finansowych i pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="a6c5e-131">W wyrażeniu można mieszać typy [całkowite](integral-numeric-types.md) i typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="a6c5e-132">W takim przypadku typy całkowite są konwertowane na typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="a6c5e-133">Obliczanie wyrażenia jest wykonywane zgodnie z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="a6c5e-134">Jeśli jeden z typów zmiennoprzecinkowych jest `double`, wyrażenie oblicza do `double`lub do wartości [logicznej](bool.md) w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="a6c5e-135">Jeśli w wyrażeniu nie ma `double` typu, wyrażenie zwróci `float`lub do wartości [logicznej](bool.md) w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="a6c5e-136">Wyrażenie zmiennoprzecinkowe może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="a6c5e-137">Dodatnie i ujemne zero</span><span class="sxs-lookup"><span data-stu-id="a6c5e-137">Positive and negative zero</span></span>
- <span data-ttu-id="a6c5e-138">Dodatnia i ujemna nieskończoność</span><span class="sxs-lookup"><span data-stu-id="a6c5e-138">Positive and negative infinity</span></span>
- <span data-ttu-id="a6c5e-139">Wartość niebędąca liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="a6c5e-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="a6c5e-140">Skończoną zbiór niezerowych wartości</span><span class="sxs-lookup"><span data-stu-id="a6c5e-140">The finite set of nonzero values</span></span>

<span data-ttu-id="a6c5e-141">Aby uzyskać więcej informacji na temat tych wartości, zobacz IEEE Standard for Binary-zmiennoprzecinkowej arytmetycznej, dostępny w witrynie sieci Web [IEEE](https://www.ieee.org) .</span><span class="sxs-lookup"><span data-stu-id="a6c5e-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="a6c5e-142">Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="a6c5e-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="a6c5e-143">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="a6c5e-143">Real literals</span></span>

<span data-ttu-id="a6c5e-144">Typ literału rzeczywistego jest określany na podstawie jego sufiksu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="a6c5e-145">Literał bez sufiksu lub z sufiksem `d` lub `D` jest typu `double`</span><span class="sxs-lookup"><span data-stu-id="a6c5e-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="a6c5e-146">Literał z sufiksem `f` lub `F` jest typu `float`</span><span class="sxs-lookup"><span data-stu-id="a6c5e-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="a6c5e-147">Literał z sufiksem `m` lub `M` jest typu `decimal`</span><span class="sxs-lookup"><span data-stu-id="a6c5e-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="a6c5e-148">Poniższy kod ilustruje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="a6c5e-149">W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="a6c5e-150">Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="a6c5e-151">Można również użyć notacji wykładniczej, czyli określić część wykładnika rzeczywistego literału, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a6c5e-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="a6c5e-152">Konwersje</span><span class="sxs-lookup"><span data-stu-id="a6c5e-152">Conversions</span></span>

<span data-ttu-id="a6c5e-153">Istnieje tylko jedna niejawna konwersja między typami liczb zmiennoprzecinkowych: od `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="a6c5e-153">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="a6c5e-154">Można jednak skonwertować dowolnego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy z [jawnym rzutem](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="a6c5e-154">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="a6c5e-155">Aby uzyskać więcej informacji, zobacz [wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="a6c5e-155">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6c5e-156">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a6c5e-156">C# language specification</span></span>

<span data-ttu-id="a6c5e-157">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a6c5e-157">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a6c5e-158">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="a6c5e-158">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="a6c5e-159">Typ dziesiętny</span><span class="sxs-lookup"><span data-stu-id="a6c5e-159">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="a6c5e-160">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="a6c5e-160">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="a6c5e-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6c5e-161">See also</span></span>

- [<span data-ttu-id="a6c5e-162">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="a6c5e-162">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a6c5e-163">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="a6c5e-163">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="a6c5e-164">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="a6c5e-164">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="a6c5e-165">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="a6c5e-165">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="a6c5e-166">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="a6c5e-166">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="a6c5e-167">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="a6c5e-167">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
