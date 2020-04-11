---
title: Typy liczbowe zmiennoprzecinowe — odwołanie do języka C#
description: 'Dowiedz się więcej o wbudowanych typach zmiennoprzecinkowych języka C#: float, double i decimal'
ms.date: 02/10/2020
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
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121481"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="21464-103">Zmiennoprzecinowe typy liczbowe (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="21464-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="21464-104">*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste.</span><span class="sxs-lookup"><span data-stu-id="21464-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="21464-105">Wszystkie typy liczbowe zmiennoprzecinkowe są [typami wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="21464-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="21464-106">Są to również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="21464-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="21464-107">Wszystkie typy liczbowe zmiennoprzecinkowe obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [porównawcze](../operators/comparison-operators.md)i [równościowe.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="21464-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="21464-108">Charakterystyka typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="21464-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="21464-109">C# obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:</span><span class="sxs-lookup"><span data-stu-id="21464-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="21464-110">Typ/słowo kluczowe C#</span><span class="sxs-lookup"><span data-stu-id="21464-110">C# type/keyword</span></span>|<span data-ttu-id="21464-111">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="21464-111">Approximate range</span></span>|<span data-ttu-id="21464-112">Dokładność</span><span class="sxs-lookup"><span data-stu-id="21464-112">Precision</span></span>|<span data-ttu-id="21464-113">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="21464-113">Size</span></span>|<span data-ttu-id="21464-114">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="21464-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="21464-115">±1,5 x 10<sup>−45</sup> do ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="21464-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="21464-116">~6-9 cyfr</span><span class="sxs-lookup"><span data-stu-id="21464-116">~6-9 digits</span></span>|<span data-ttu-id="21464-117">4 bajty</span><span class="sxs-lookup"><span data-stu-id="21464-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="21464-118">±5,0 × 10<sup>−324</sup> do ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="21464-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="21464-119">~15-17 cyfr</span><span class="sxs-lookup"><span data-stu-id="21464-119">~15-17 digits</span></span>|<span data-ttu-id="21464-120">8 bajtów</span><span class="sxs-lookup"><span data-stu-id="21464-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="21464-121">±1,0 x 10<sup>-28</sup> do ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="21464-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="21464-122">28-29 cyfr</span><span class="sxs-lookup"><span data-stu-id="21464-122">28-29 digits</span></span>|<span data-ttu-id="21464-123">16 bajtów</span><span class="sxs-lookup"><span data-stu-id="21464-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="21464-124">W poprzedniej tabeli każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="21464-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="21464-125">Są wymienne.</span><span class="sxs-lookup"><span data-stu-id="21464-125">They are interchangeable.</span></span> <span data-ttu-id="21464-126">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="21464-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="21464-127">Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="21464-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="21464-128">Każdy z typów zmiennoprzecinkowych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość skończoną tego typu.</span><span class="sxs-lookup"><span data-stu-id="21464-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="21464-129">I `float` `double` typy zapewniają również stałe, które reprezentują wartości nie-liczba i nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="21464-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="21464-130">Na przykład `double` typ zawiera następujące <xref:System.Double.NaN?displayProperty=nameWithType>stałe: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, i .</span><span class="sxs-lookup"><span data-stu-id="21464-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="21464-131">Ponieważ `decimal` typ ma większą precyzję i `float` `double`mniejszy zakres niż oba i , jest odpowiedni dla obliczeń finansowych i pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="21464-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="21464-132">Można mieszać [typy integralne](integral-numeric-types.md) i `float` typy i `double` typy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="21464-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="21464-133">W takim przypadku typy integralne są niejawnie konwertowane na `float` jeden z typów zmiennoprzecinkowych i, jeśli to konieczne, typ jest niejawnie konwertowany na `double`.</span><span class="sxs-lookup"><span data-stu-id="21464-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="21464-134">Wyrażenie jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21464-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="21464-135">Jeśli istnieje `double` typ w wyrażeniu, `double`wyrażenie [`bool`](bool.md) ocenia do , lub w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="21464-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="21464-136">Jeśli nie `double` ma żadnego typu w wyrażeniu, wyrażenie ocenia do `float`, lub `bool` w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="21464-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="21464-137">Można również mieszać typy integralne i `decimal` typ w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="21464-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="21464-138">W takim przypadku typy integralną są `decimal` niejawnie konwertowane na typ i wyrażenie ocenia do `decimal`, lub `bool` w porównaniach relacyjnych i równości.</span><span class="sxs-lookup"><span data-stu-id="21464-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="21464-139">Nie można `decimal` mieszać `float` typu `double` z i typów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="21464-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="21464-140">W takim przypadku, jeśli chcesz wykonać operacje arytmetyczne, porównania lub równości, należy jawnie przekonwertować operandy z lub do `decimal` typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="21464-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="21464-141">Można użyć [standardowych ciągów formatu liczbowego](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) do formatowania wartości zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="21464-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="21464-142">Prawdziwe literały</span><span class="sxs-lookup"><span data-stu-id="21464-142">Real literals</span></span>

<span data-ttu-id="21464-143">Typ prawdziwego literału jest określany przez jego sufiks w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21464-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="21464-144">Literał bez przyrostka lub `d` z `D` przyrostkiem lub przyrostkiem jest typu`double`</span><span class="sxs-lookup"><span data-stu-id="21464-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="21464-145">Literał z `f` lub `F` przyrostkiem jest typu`float`</span><span class="sxs-lookup"><span data-stu-id="21464-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="21464-146">Literał z `m` lub `M` przyrostkiem jest typu`decimal`</span><span class="sxs-lookup"><span data-stu-id="21464-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="21464-147">Poniższy kod pokazuje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="21464-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="21464-148">W poprzednim przykładzie pokazano `_` również użycie jako *separator cyfry*, który jest obsługiwany począwszy od C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="21464-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="21464-149">Separatora cyfr można używać z wszelkiego rodzaju literałami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="21464-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="21464-150">Można również użyć notacji naukowej, czyli określić wykładniczą część rzeczywistego literału, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="21464-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="21464-151">Konwersje</span><span class="sxs-lookup"><span data-stu-id="21464-151">Conversions</span></span>

<span data-ttu-id="21464-152">Istnieje tylko jedna niejawna konwersja między `float` zmiennoprzecinkowymi typami liczbowymi: od do `double`.</span><span class="sxs-lookup"><span data-stu-id="21464-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="21464-153">Można jednak przekonwertować dowolny typ zmiennoprzecinkowy na dowolny inny typ zmiennoprzecinkowy z [jawnym rzutowania](../operators/type-testing-and-cast.md#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="21464-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="21464-154">Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="21464-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="21464-155">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="21464-155">C# language specification</span></span>

<span data-ttu-id="21464-156">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="21464-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="21464-157">Typy zmiennoprzecinowe</span><span class="sxs-lookup"><span data-stu-id="21464-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="21464-158">Typ dziesiętny</span><span class="sxs-lookup"><span data-stu-id="21464-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="21464-159">Prawdziwe literały</span><span class="sxs-lookup"><span data-stu-id="21464-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="21464-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21464-160">See also</span></span>

- [<span data-ttu-id="21464-161">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="21464-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="21464-162">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="21464-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="21464-163">Typy integralne</span><span class="sxs-lookup"><span data-stu-id="21464-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="21464-164">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="21464-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="21464-165">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="21464-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
