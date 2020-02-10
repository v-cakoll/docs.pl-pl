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
ms.openlocfilehash: 9c8b11f9337ee9de90f2d4d96b5be162713bfcbd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093217"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="1003d-103">Zmiennoprzecinkowe typy liczbowe (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="1003d-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="1003d-104">*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste.</span><span class="sxs-lookup"><span data-stu-id="1003d-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="1003d-105">Wszystkie zmiennoprzecinkowe typy liczbowe to [typy wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="1003d-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="1003d-106">Są one również [typami prostymi](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="1003d-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="1003d-107">Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="1003d-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="1003d-108">Charakterystyki typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="1003d-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="1003d-109">C#obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:</span><span class="sxs-lookup"><span data-stu-id="1003d-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="1003d-110">C#Type/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="1003d-110">C# type/keyword</span></span>|<span data-ttu-id="1003d-111">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="1003d-111">Approximate range</span></span>|<span data-ttu-id="1003d-112">Precyzja</span><span class="sxs-lookup"><span data-stu-id="1003d-112">Precision</span></span>|<span data-ttu-id="1003d-113">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="1003d-113">Size</span></span>|<span data-ttu-id="1003d-114">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="1003d-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="1003d-115">± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="1003d-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="1003d-116">~ 6-9 cyfr</span><span class="sxs-lookup"><span data-stu-id="1003d-116">~6-9 digits</span></span>|<span data-ttu-id="1003d-117">4 bajty</span><span class="sxs-lookup"><span data-stu-id="1003d-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="1003d-118">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="1003d-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="1003d-119">~ 15-17 cyfr</span><span class="sxs-lookup"><span data-stu-id="1003d-119">~15-17 digits</span></span>|<span data-ttu-id="1003d-120">8 bajtów</span><span class="sxs-lookup"><span data-stu-id="1003d-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="1003d-121">1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="1003d-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="1003d-122">28-29 cyfr</span><span class="sxs-lookup"><span data-stu-id="1003d-122">28-29 digits</span></span>|<span data-ttu-id="1003d-123">16 bajtów</span><span class="sxs-lookup"><span data-stu-id="1003d-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="1003d-124">W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="1003d-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="1003d-125">Są one zamienne.</span><span class="sxs-lookup"><span data-stu-id="1003d-125">They are interchangeable.</span></span> <span data-ttu-id="1003d-126">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="1003d-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="1003d-127">Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="1003d-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="1003d-128">Każdy z typów zmiennoprzecinkowych ma stałe `MinValue` i `MaxValue`, które zapewniają minimalną i maksymalną skończoną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="1003d-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="1003d-129">Typy `float` i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone.</span><span class="sxs-lookup"><span data-stu-id="1003d-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="1003d-130">Na przykład typ `double` zapewnia następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1003d-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1003d-131">Ponieważ typ `decimal` ma większą precyzję i mniejszy zakres niż `float` i `double`, jest on odpowiedni dla obliczeń finansowych i pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="1003d-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="1003d-132">W wyrażeniu można mieszać typy [całkowite](integral-numeric-types.md) i typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="1003d-132">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="1003d-133">W takim przypadku typy całkowite są konwertowane na typy zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="1003d-133">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="1003d-134">Obliczanie wyrażenia jest wykonywane zgodnie z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="1003d-134">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="1003d-135">Jeśli jeden z typów zmiennoprzecinkowych jest `double`, wyrażenie oblicza do `double`lub do wartości [logicznej](bool.md) w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="1003d-135">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="1003d-136">Jeśli w wyrażeniu nie ma `double` typu, wyrażenie zwróci `float`lub do wartości [logicznej](bool.md) w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="1003d-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="1003d-137">Wyrażenie zmiennoprzecinkowe może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="1003d-137">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="1003d-138">Dodatnie i ujemne zero</span><span class="sxs-lookup"><span data-stu-id="1003d-138">Positive and negative zero</span></span>
- <span data-ttu-id="1003d-139">Dodatnia i ujemna nieskończoność</span><span class="sxs-lookup"><span data-stu-id="1003d-139">Positive and negative infinity</span></span>
- <span data-ttu-id="1003d-140">Wartość niebędąca liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="1003d-140">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="1003d-141">Skończoną zbiór niezerowych wartości</span><span class="sxs-lookup"><span data-stu-id="1003d-141">The finite set of nonzero values</span></span>

<span data-ttu-id="1003d-142">Aby uzyskać więcej informacji na temat tych wartości, zobacz IEEE Standard for Binary-zmiennoprzecinkowej arytmetycznej, dostępny w witrynie sieci Web [IEEE](https://www.ieee.org) .</span><span class="sxs-lookup"><span data-stu-id="1003d-142">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="1003d-143">Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="1003d-143">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="1003d-144">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="1003d-144">Real literals</span></span>

<span data-ttu-id="1003d-145">Typ literału rzeczywistego jest określany na podstawie jego sufiksu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1003d-145">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="1003d-146">Literał bez sufiksu lub z sufiksem `d` lub `D` jest typu `double`</span><span class="sxs-lookup"><span data-stu-id="1003d-146">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="1003d-147">Literał z sufiksem `f` lub `F` jest typu `float`</span><span class="sxs-lookup"><span data-stu-id="1003d-147">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="1003d-148">Literał z sufiksem `m` lub `M` jest typu `decimal`</span><span class="sxs-lookup"><span data-stu-id="1003d-148">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="1003d-149">Poniższy kod ilustruje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="1003d-149">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="1003d-150">W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="1003d-150">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="1003d-151">Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1003d-151">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="1003d-152">Można również użyć notacji wykładniczej, czyli określić część wykładnika rzeczywistego literału, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1003d-152">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="1003d-153">Konwersje</span><span class="sxs-lookup"><span data-stu-id="1003d-153">Conversions</span></span>

<span data-ttu-id="1003d-154">Istnieje tylko jedna niejawna konwersja między typami liczb zmiennoprzecinkowych: od `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="1003d-154">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="1003d-155">Można jednak skonwertować dowolnego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy z [jawnym rzutem](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="1003d-155">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="1003d-156">Aby uzyskać więcej informacji, zobacz [wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1003d-156">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1003d-157">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1003d-157">C# language specification</span></span>

<span data-ttu-id="1003d-158">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="1003d-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1003d-159">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="1003d-159">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="1003d-160">Typ dziesiętny</span><span class="sxs-lookup"><span data-stu-id="1003d-160">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="1003d-161">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="1003d-161">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="1003d-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1003d-162">See also</span></span>

- [<span data-ttu-id="1003d-163">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="1003d-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1003d-164">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="1003d-164">Value types</span></span>](value-types.md)
- [<span data-ttu-id="1003d-165">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="1003d-165">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="1003d-166">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="1003d-166">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="1003d-167">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="1003d-167">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
