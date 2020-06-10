---
title: Typy liczbowe zmiennoprzecinkowe — odwołanie w C#
description: 'Dowiedz się więcej na temat wbudowanych typów zmiennoprzecinkowych C#: zmiennoprzecinkowych, podwójnych i dziesiętnych'
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
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662670"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="5a9ae-103">Zmiennoprzecinkowe typy liczbowe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a9ae-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="5a9ae-104">*Typy liczbowe zmiennoprzecinkowe* reprezentują liczby rzeczywiste.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="5a9ae-105">Wszystkie zmiennoprzecinkowe typy liczbowe to [typy wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="5a9ae-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="5a9ae-106">Są one również [typami prostymi](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="5a9ae-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="5a9ae-107">Wszystkie zmiennoprzecinkowe typy liczbowe obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="5a9ae-108">Charakterystyki typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="5a9ae-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="5a9ae-109">Język C# obsługuje następujące wstępnie zdefiniowane typy zmiennoprzecinkowe:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="5a9ae-110">Typ C#/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="5a9ae-110">C# type/keyword</span></span>|<span data-ttu-id="5a9ae-111">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="5a9ae-111">Approximate range</span></span>|<span data-ttu-id="5a9ae-112">Dokładność</span><span class="sxs-lookup"><span data-stu-id="5a9ae-112">Precision</span></span>|<span data-ttu-id="5a9ae-113">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="5a9ae-113">Size</span></span>|<span data-ttu-id="5a9ae-114">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="5a9ae-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="5a9ae-115">± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="5a9ae-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="5a9ae-116">~ 6-9 cyfr</span><span class="sxs-lookup"><span data-stu-id="5a9ae-116">~6-9 digits</span></span>|<span data-ttu-id="5a9ae-117">4 bajty</span><span class="sxs-lookup"><span data-stu-id="5a9ae-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="5a9ae-118">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="5a9ae-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="5a9ae-119">~ 15-17 cyfr</span><span class="sxs-lookup"><span data-stu-id="5a9ae-119">~15-17 digits</span></span>|<span data-ttu-id="5a9ae-120">8 bajtów</span><span class="sxs-lookup"><span data-stu-id="5a9ae-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="5a9ae-121">1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="5a9ae-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="5a9ae-122">28-29 cyfr</span><span class="sxs-lookup"><span data-stu-id="5a9ae-122">28-29 digits</span></span>|<span data-ttu-id="5a9ae-123">16 bajtów</span><span class="sxs-lookup"><span data-stu-id="5a9ae-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="5a9ae-124">W powyższej tabeli każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="5a9ae-125">Są one zamienne.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-125">They are interchangeable.</span></span> <span data-ttu-id="5a9ae-126">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="5a9ae-127">Wartość domyślna każdego typu zmiennoprzecinkowego wynosi zero, `0` .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="5a9ae-128">Każdy z typów zmiennoprzecinkowych ma `MinValue` `MaxValue` stałe i, które zapewniają minimalną i maksymalną skończoną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="5a9ae-129">`float`Typy i `double` zawierają również stałe, które reprezentują wartości nieliczbowe i nieskończone.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="5a9ae-130">Na przykład `double` Typ zawiera następujące stałe: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5a9ae-131">Ponieważ `decimal` Typ ma większą precyzję i mniejszy zakres niż `float` i `double` , jest odpowiedni do obliczeń finansowych i pieniężnych.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="5a9ae-132">Można mieszać typy [całkowite](integral-numeric-types.md) i `float` `double` typy i w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="5a9ae-133">W takim przypadku typy całkowite są niejawnie konwertowane na jeden z typów zmiennoprzecinkowych i, w razie potrzeby, `float` Typ jest niejawnie konwertowany na `double` .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="5a9ae-134">Wyrażenie jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="5a9ae-135">Jeśli `double` w wyrażeniu występuje typ, wyrażenie oblicza do `double` , lub do [`bool`](bool.md) porównania relacyjnego i równości.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="5a9ae-136">Jeśli wyrażenie nie ma żadnego `double` typu, wyrażenie oblicza do `float` , lub do `bool` porównania relacyjne i równość.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="5a9ae-137">Można również mieszać typy całkowite i `decimal` Typ w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="5a9ae-138">W takim przypadku typy całkowite są niejawnie konwertowane na `decimal` Typ, a wyrażenie oblicza do `decimal` , lub do `bool` porównania relacyjne i równość.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="5a9ae-139">Nie można mieszać `decimal` typu z `float` `double` typami i w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="5a9ae-140">W tym przypadku, jeśli chcesz wykonywać operacje arytmetyczne, porównania lub równości, musisz jawnie skonwertować operandy z lub do `decimal` typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="5a9ae-141">Aby sformatować wartość zmiennoprzecinkową, można użyć [standardowych ciągów formatu liczb](../../../standard/base-types/standard-numeric-format-strings.md) lub [niestandardowych ciągów formatu liczbowego](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="5a9ae-142">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="5a9ae-142">Real literals</span></span>

<span data-ttu-id="5a9ae-143">Typ literału rzeczywistego jest określany na podstawie jego sufiksu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="5a9ae-144">Literał bez sufiksu lub z `d` `D` sufiksem or jest typu`double`</span><span class="sxs-lookup"><span data-stu-id="5a9ae-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="5a9ae-145">Literał z `f` `F` sufiksem or jest typu`float`</span><span class="sxs-lookup"><span data-stu-id="5a9ae-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="5a9ae-146">Literał z `m` `M` sufiksem or jest typu`decimal`</span><span class="sxs-lookup"><span data-stu-id="5a9ae-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="5a9ae-147">Poniższy kod ilustruje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="5a9ae-148">W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany, zaczynając od języka C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="5a9ae-149">Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="5a9ae-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="5a9ae-150">Można również użyć notacji wykładniczej, czyli określić część wykładnika literału rzeczywistego, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5a9ae-150">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="5a9ae-151">Konwersje</span><span class="sxs-lookup"><span data-stu-id="5a9ae-151">Conversions</span></span>

<span data-ttu-id="5a9ae-152">Istnieje tylko jedna niejawna konwersja między typami liczb zmiennoprzecinkowych: z `float` do `double` .</span><span class="sxs-lookup"><span data-stu-id="5a9ae-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="5a9ae-153">Można jednak skonwertować dowolnego typu zmiennoprzecinkowego na inny typ zmiennoprzecinkowy z [jawnym rzutem](../operators/type-testing-and-cast.md#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="5a9ae-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="5a9ae-154">Aby uzyskać więcej informacji, zobacz [wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="5a9ae-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5a9ae-155">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a9ae-155">C# language specification</span></span>

<span data-ttu-id="5a9ae-156">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5a9ae-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5a9ae-157">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="5a9ae-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="5a9ae-158">Typ dziesiętny</span><span class="sxs-lookup"><span data-stu-id="5a9ae-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="5a9ae-159">Literały prawdziwe</span><span class="sxs-lookup"><span data-stu-id="5a9ae-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="5a9ae-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a9ae-160">See also</span></span>

- [<span data-ttu-id="5a9ae-161">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a9ae-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5a9ae-162">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="5a9ae-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="5a9ae-163">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="5a9ae-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="5a9ae-164">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="5a9ae-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="5a9ae-165">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="5a9ae-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
