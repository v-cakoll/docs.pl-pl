---
title: Typy liczbowe integralne — odwołanie do języka C#
description: Poznaj zakres, rozmiar magazynu i zastosowania dla każdego z typów liczbowych.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093204"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="bc7b6-103">Typy liczbowe integralne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="bc7b6-104">Typy *liczbowe integralne* reprezentują liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="bc7b6-105">Wszystkie typy liczbowe integralne są [typami wartości.](value-types.md)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="bc7b6-106">Są one również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literału](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="bc7b6-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="bc7b6-107">Wszystkie typy liczbowe integralne obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [logiczne bitowe,](../operators/bitwise-and-shift-operators.md) [porównywanie](../operators/comparison-operators.md)i [równość.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="bc7b6-108">Charakterystyka typów integralnych</span><span class="sxs-lookup"><span data-stu-id="bc7b6-108">Characteristics of the integral types</span></span>

<span data-ttu-id="bc7b6-109">C# obsługuje następujące wstępnie zdefiniowane typy całki:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="bc7b6-110">Typ/słowo kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bc7b6-110">C# type/keyword</span></span>|<span data-ttu-id="bc7b6-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="bc7b6-111">Range</span></span>|<span data-ttu-id="bc7b6-112">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="bc7b6-112">Size</span></span>|<span data-ttu-id="bc7b6-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="bc7b6-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="bc7b6-114">od -128 do 127</span><span class="sxs-lookup"><span data-stu-id="bc7b6-114">-128 to 127</span></span>|<span data-ttu-id="bc7b6-115">Podpisana 8-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="bc7b6-116">Od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="bc7b6-116">0 to 255</span></span>|<span data-ttu-id="bc7b6-117">Niepodpisana 8-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="bc7b6-118">od -32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="bc7b6-118">-32,768 to 32,767</span></span>|<span data-ttu-id="bc7b6-119">Podpisana 16-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="bc7b6-120">od 0 do 65 535</span><span class="sxs-lookup"><span data-stu-id="bc7b6-120">0 to 65,535</span></span>|<span data-ttu-id="bc7b6-121">Niepodpisana 16-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="bc7b6-122">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="bc7b6-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="bc7b6-123">Podpisana 32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="bc7b6-124">0 do 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="bc7b6-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="bc7b6-125">Niepodpisana 32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="bc7b6-126">-9 223 372 036.854.775.808 do 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="bc7b6-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="bc7b6-127">Podpisana 64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="bc7b6-128">0 do 18 446 744 773 709 551 615</span><span class="sxs-lookup"><span data-stu-id="bc7b6-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="bc7b6-129">Niepodpisana 64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="bc7b6-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="bc7b6-130">W powyższej tabeli każde słowo kluczowe typu C# z kolumny po lewej stronie jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="bc7b6-131">Są wymienne.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-131">They are interchangeable.</span></span> <span data-ttu-id="bc7b6-132">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="bc7b6-133">Domyślną wartością każdego typu `0`integralnego jest zero, .</span><span class="sxs-lookup"><span data-stu-id="bc7b6-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="bc7b6-134">Każdy z typów całki ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="bc7b6-135"><xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura służy do reprezentowania podpisanej liczby całkowitej bez górnych lub dolnych granic.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="bc7b6-136">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="bc7b6-136">Integer literals</span></span>

<span data-ttu-id="bc7b6-137">Literały całkowite mogą być</span><span class="sxs-lookup"><span data-stu-id="bc7b6-137">Integer literals can be</span></span>

- <span data-ttu-id="bc7b6-138">*dziesiętne:* bez prefiksu</span><span class="sxs-lookup"><span data-stu-id="bc7b6-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="bc7b6-139">*szesnastkowy:* `0x` z `0X` prefiksem lub prefiksem</span><span class="sxs-lookup"><span data-stu-id="bc7b6-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="bc7b6-140">*binarny:* `0b` `0B` z prefiksem lub prefiksem (dostępny w języku C# 7.0 i nowszych)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="bc7b6-141">Poniższy kod przedstawia przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="bc7b6-142">W poprzednim przykładzie pokazano `_` również użycie jako *separatora cyfr*, który jest obsługiwany począwszy od Języka C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="bc7b6-143">Separatora cyfr można używać ze wszystkimi rodzajami literałów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="bc7b6-144">Typ literału całkowitego jest określany przez jego sufiks w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="bc7b6-145">Jeśli literał nie ma sufiksu, jego typ jest pierwszym z następujących `int` `uint`typów, w których można reprezentować jego wartość: , , `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="bc7b6-146">Jeśli literał `U` jest sufiksprzez lub `u`, jego typ jest pierwszym z następujących `uint` `ulong`typów, w których jego wartość może być reprezentowana: , .</span><span class="sxs-lookup"><span data-stu-id="bc7b6-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="bc7b6-147">Jeśli literał `L` jest sufiksprzez lub `l`, jego typ jest pierwszym z następujących `long` `ulong`typów, w których jego wartość może być reprezentowana: , .</span><span class="sxs-lookup"><span data-stu-id="bc7b6-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bc7b6-148">Małej litery `l` można użyć jako sufiksu.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="bc7b6-149">Jednak generuje to ostrzeżenie kompilatora, ponieważ litera `l` może być mylona z cyfrą `1`.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="bc7b6-150">Użyj `L` dla jasności.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="bc7b6-151">Jeśli literał jest sufiksowany `LU` `Lu`przez `lU` `UL`, `Ul` `uL`, `ul`, `ulong`, lub `lu`jego typ jest .</span><span class="sxs-lookup"><span data-stu-id="bc7b6-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="bc7b6-152">Jeśli wartość reprezentowana przez literał całkowity <xref:System.UInt64.MaxValue?displayProperty=nameWithType>przekracza, występuje błąd kompilatora [CS1021.](../../misc/cs1021.md)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="bc7b6-153">Jeżeli określony typ literału `int` całkowitego jest i wartość reprezentowana przez literał jest w zakresie typu docelowego, `sbyte` `byte`wartość `short` `ushort`może `uint`być `ulong`niejawnie konwertowane na , , , , , , lub:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="bc7b6-154">Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie znajduje się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="bc7b6-155">Można również użyć rzutowania do konwersji wartości reprezentowanej przez literał całkowity na typ inny niż określony typ literału:</span><span class="sxs-lookup"><span data-stu-id="bc7b6-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="bc7b6-156">Konwersje</span><span class="sxs-lookup"><span data-stu-id="bc7b6-156">Conversions</span></span>

<span data-ttu-id="bc7b6-157">Można przekonwertować dowolny typ liczbowy na dowolny inny integralny typ numeryczny.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="bc7b6-158">Jeśli typ docelowy może przechowywać wszystkie wartości typu źródłowego, konwersja jest niejawna.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="bc7b6-159">W przeciwnym razie należy użyć [ `()` operatora rzutowania](../operators/type-testing-and-cast.md#cast-operator-) do wywołania jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="bc7b6-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="bc7b6-160">Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje liczbowe](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="bc7b6-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bc7b6-161">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bc7b6-161">C# language specification</span></span>

<span data-ttu-id="bc7b6-162">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bc7b6-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bc7b6-163">Typy całonowe</span><span class="sxs-lookup"><span data-stu-id="bc7b6-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="bc7b6-164">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="bc7b6-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="bc7b6-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc7b6-165">See also</span></span>

- [<span data-ttu-id="bc7b6-166">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bc7b6-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bc7b6-167">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="bc7b6-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="bc7b6-168">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="bc7b6-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="bc7b6-169">Standardowe ciągi formatu numerycznego</span><span class="sxs-lookup"><span data-stu-id="bc7b6-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="bc7b6-170">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="bc7b6-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
