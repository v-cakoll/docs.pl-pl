---
title: Całkowite typy liczbowe — C# odwołanie
description: Poznaj zakres, rozmiar magazynu i użycie dla każdego z typów całkowitych.
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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093204"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="28304-103">Całkowite typy liczbowe (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="28304-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="28304-104">Całkowite *typy liczbowe* przedstawiają liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="28304-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="28304-105">Wszystkie typy liczb całkowitych są [typami wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="28304-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="28304-106">Są one również [typami prostymi](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="28304-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="28304-107">Wszystkie typy liczbowe całkowite obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [bitowe logiczne](../operators/bitwise-and-shift-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="28304-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="28304-108">Cechy typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="28304-108">Characteristics of the integral types</span></span>

<span data-ttu-id="28304-109">C#obsługuje następujące wstępnie zdefiniowane typy całkowite:</span><span class="sxs-lookup"><span data-stu-id="28304-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="28304-110">C#Type/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="28304-110">C# type/keyword</span></span>|<span data-ttu-id="28304-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="28304-111">Range</span></span>|<span data-ttu-id="28304-112">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="28304-112">Size</span></span>|<span data-ttu-id="28304-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="28304-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="28304-114">-128 do 127</span><span class="sxs-lookup"><span data-stu-id="28304-114">-128 to 127</span></span>|<span data-ttu-id="28304-115">8-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="28304-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="28304-116">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="28304-116">0 to 255</span></span>|<span data-ttu-id="28304-117">8-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="28304-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="28304-118">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="28304-118">-32,768 to 32,767</span></span>|<span data-ttu-id="28304-119">16-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="28304-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="28304-120">od 0 do 65 535</span><span class="sxs-lookup"><span data-stu-id="28304-120">0 to 65,535</span></span>|<span data-ttu-id="28304-121">16-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="28304-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="28304-122">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="28304-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="28304-123">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="28304-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="28304-124">od 0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="28304-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="28304-125">Niepodpisany 32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="28304-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="28304-126">-zakresu od do 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="28304-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="28304-127">64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="28304-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="28304-128">od 0 do 18446744073709551615 są</span><span class="sxs-lookup"><span data-stu-id="28304-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="28304-129">Niepodpisany 64-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="28304-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="28304-130">W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="28304-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="28304-131">Są one zamienne.</span><span class="sxs-lookup"><span data-stu-id="28304-131">They are interchangeable.</span></span> <span data-ttu-id="28304-132">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="28304-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="28304-133">Wartością domyślną każdego typu całkowitego jest zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="28304-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="28304-134">Każdy z typów całkowitych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="28304-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="28304-135">Użyj struktury <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, aby reprezentować liczbę całkowitą ze znakiem bez górnych lub dolnych granic.</span><span class="sxs-lookup"><span data-stu-id="28304-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="28304-136">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="28304-136">Integer literals</span></span>

<span data-ttu-id="28304-137">Literały całkowite mogą być</span><span class="sxs-lookup"><span data-stu-id="28304-137">Integer literals can be</span></span>

- <span data-ttu-id="28304-138">*Decimal*: bez żadnego prefiksu</span><span class="sxs-lookup"><span data-stu-id="28304-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="28304-139">*szesnastkowe*: z prefiksem `0x` lub `0X`</span><span class="sxs-lookup"><span data-stu-id="28304-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="28304-140">*plik binarny*: z prefiksem `0b` lub `0B` ( C# dostępnym w 7,0 i nowszych)</span><span class="sxs-lookup"><span data-stu-id="28304-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="28304-141">Poniższy kod ilustruje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="28304-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="28304-142">W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="28304-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="28304-143">Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="28304-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="28304-144">Typ literału liczby całkowitej jest określany na podstawie jego sufiksu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="28304-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="28304-145">Jeśli literał nie ma sufiksu, jego typ to pierwszy z następujących typów, w którym można przedstawić jego wartość: `int`, `uint`, `long``ulong`.</span><span class="sxs-lookup"><span data-stu-id="28304-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="28304-146">Jeśli literał jest sufiksem `U` lub `u`, jego typ jest pierwszym z następujących typów, w których można reprezentować wartość: `uint``ulong`.</span><span class="sxs-lookup"><span data-stu-id="28304-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="28304-147">Jeśli literał jest sufiksem `L` lub `l`, jego typ jest pierwszym z następujących typów, w których można reprezentować wartość: `long``ulong`.</span><span class="sxs-lookup"><span data-stu-id="28304-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="28304-148">Jako sufiksu można użyć małych liter `l`.</span><span class="sxs-lookup"><span data-stu-id="28304-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="28304-149">Jednak spowoduje to wygenerowanie ostrzeżenia kompilatora, ponieważ `l` można mylić z cyfrą `1`.</span><span class="sxs-lookup"><span data-stu-id="28304-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="28304-150">Użyj `L` do przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="28304-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="28304-151">Jeśli literał jest sufiksem `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`lub `lu`, jego typ to `ulong`.</span><span class="sxs-lookup"><span data-stu-id="28304-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="28304-152">Jeśli wartość reprezentowana przez literał liczby całkowitej przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilatora [CS1021](../../misc/cs1021.md) .</span><span class="sxs-lookup"><span data-stu-id="28304-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="28304-153">Jeśli określony typ literału liczby całkowitej jest `int` a wartość reprezentowana przez literał znajduje się w zakresie typu docelowego, wartość może zostać niejawnie przekonwertowana na `sbyte`, `byte`, `short`, `ushort`, `uint`lub `ulong`:</span><span class="sxs-lookup"><span data-stu-id="28304-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="28304-154">Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie należy do zakresu typu docelowego, wystąpi błąd kompilatora [CS0031](../../misc/cs0031.md) .</span><span class="sxs-lookup"><span data-stu-id="28304-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="28304-155">Można również użyć rzutowania, aby przekonwertować wartość reprezentowaną przez literał liczby całkowitej na typ inny niż określony typ literału:</span><span class="sxs-lookup"><span data-stu-id="28304-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="28304-156">Konwersje</span><span class="sxs-lookup"><span data-stu-id="28304-156">Conversions</span></span>

<span data-ttu-id="28304-157">Można skonwertować dowolny całkowity typ liczbowy do dowolnego innego typu liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="28304-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="28304-158">Jeśli typ docelowy może przechowywać wszystkie wartości typu źródła, konwersja jest niejawna.</span><span class="sxs-lookup"><span data-stu-id="28304-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="28304-159">W przeciwnym razie należy użyć [operatora rzutowania `()`](../operators/type-testing-and-cast.md#cast-operator-) do wywołania jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="28304-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="28304-160">Aby uzyskać więcej informacji, zobacz [wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="28304-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="28304-161">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="28304-161">C# language specification</span></span>

<span data-ttu-id="28304-162">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="28304-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="28304-163">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="28304-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="28304-164">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="28304-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="28304-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28304-165">See also</span></span>

- [<span data-ttu-id="28304-166">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="28304-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="28304-167">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="28304-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="28304-168">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="28304-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="28304-169">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="28304-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="28304-170">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="28304-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
