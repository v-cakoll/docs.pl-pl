---
title: Integralne typy liczbowe — odwołanie do języka C#
description: Poznaj zakres, rozmiar magazynu i zastosowania dla każdego z całkowitych typów liczbowych.
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
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739006"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="981d6-103">Integralne typy liczbowe (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="981d6-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="981d6-104">*Integralne typy liczbowe* reprezentują liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="981d6-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="981d6-105">Wszystkie integralne typy liczbowe są [typami wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="981d6-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="981d6-106">Są to również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="981d6-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="981d6-107">Wszystkie integralne typy liczbowe obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [logiczne bitowe,](../operators/bitwise-and-shift-operators.md) [porównanie](../operators/comparison-operators.md)i [równości.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="981d6-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="981d6-108">Charakterystyka typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="981d6-108">Characteristics of the integral types</span></span>

<span data-ttu-id="981d6-109">C# obsługuje następujące wstępnie zdefiniowane typy całek:</span><span class="sxs-lookup"><span data-stu-id="981d6-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="981d6-110">Typ/słowo kluczowe C#</span><span class="sxs-lookup"><span data-stu-id="981d6-110">C# type/keyword</span></span>|<span data-ttu-id="981d6-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="981d6-111">Range</span></span>|<span data-ttu-id="981d6-112">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="981d6-112">Size</span></span>|<span data-ttu-id="981d6-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="981d6-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="981d6-114">od -128 do 127</span><span class="sxs-lookup"><span data-stu-id="981d6-114">-128 to 127</span></span>|<span data-ttu-id="981d6-115">Podpisana 8-bitowa 8-bitowa czkawce</span><span class="sxs-lookup"><span data-stu-id="981d6-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="981d6-116">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="981d6-116">0 to 255</span></span>|<span data-ttu-id="981d6-117">Niepodpisana 8-bitowa 8-bitowa czkawce</span><span class="sxs-lookup"><span data-stu-id="981d6-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="981d6-118">od -32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="981d6-118">-32,768 to 32,767</span></span>|<span data-ttu-id="981d6-119">Podpisana 16-bitowa 10-bitowa 100 000 całkowita</span><span class="sxs-lookup"><span data-stu-id="981d6-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="981d6-120">od 0 do 65 535</span><span class="sxs-lookup"><span data-stu-id="981d6-120">0 to 65,535</span></span>|<span data-ttu-id="981d6-121">Niepodpisana 16-bitowa 10-bitowa 100 000 całkowita</span><span class="sxs-lookup"><span data-stu-id="981d6-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="981d6-122">-2.147.483.648 do 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="981d6-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="981d6-123">Podpisana 32-bitowa całkowita 20da</span><span class="sxs-lookup"><span data-stu-id="981d6-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="981d6-124">od 0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="981d6-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="981d6-125">Niepodpisana 32-bitowa 32-bitowa gnilizna</span><span class="sxs-lookup"><span data-stu-id="981d6-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="981d6-126">-9.223.372.036.854.775.808 do 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="981d6-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="981d6-127">Podpisana 64-bitowa całkowita rzeszj</span><span class="sxs-lookup"><span data-stu-id="981d6-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="981d6-128">od 0 do 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="981d6-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="981d6-129">Niepodpisana 64-bitowa 60-bitowa ćwięk</span><span class="sxs-lookup"><span data-stu-id="981d6-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="981d6-130">W poprzedniej tabeli każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="981d6-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="981d6-131">Są wymienne.</span><span class="sxs-lookup"><span data-stu-id="981d6-131">They are interchangeable.</span></span> <span data-ttu-id="981d6-132">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="981d6-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="981d6-133">Domyślną wartością każdego typu `0`całkowitego jest zero, .</span><span class="sxs-lookup"><span data-stu-id="981d6-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="981d6-134">Każdy z typów całkowitych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="981d6-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="981d6-135">Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania podpisanej liczby całkowitej bez górnej lub dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="981d6-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="981d6-136">Literały liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="981d6-136">Integer literals</span></span>

<span data-ttu-id="981d6-137">Literały całkowite można</span><span class="sxs-lookup"><span data-stu-id="981d6-137">Integer literals can be</span></span>

- <span data-ttu-id="981d6-138">*dziesiętne:* bez prefiksu</span><span class="sxs-lookup"><span data-stu-id="981d6-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="981d6-139">*szesnastkowe:* `0X` z prefiksem lub prefiksem `0x`</span><span class="sxs-lookup"><span data-stu-id="981d6-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="981d6-140">*binary*: `0b` z `0B` prefiksem lub (dostępnym w języku C# 7.0 i nowszym)</span><span class="sxs-lookup"><span data-stu-id="981d6-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="981d6-141">Poniższy kod pokazuje przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="981d6-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="981d6-142">W poprzednim przykładzie pokazano `_` również użycie jako *separator cyfry*, który jest obsługiwany począwszy od C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="981d6-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="981d6-143">Separatora cyfr można używać z wszelkiego rodzaju literałami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="981d6-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="981d6-144">Typ literału liczby całkowitej jest określany przez jego sufiks w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="981d6-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="981d6-145">Jeśli literał nie ma sufiksu, jego typ jest pierwszym z następujących `int`typów, w których jego wartość może być reprezentowana: , `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="981d6-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="981d6-146">`U` Jeśli literał jest sufiksem przez lub `u`, jego typ jest pierwszym z następujących `uint` `ulong`typów, w których jego wartość może być reprezentowana: , .</span><span class="sxs-lookup"><span data-stu-id="981d6-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="981d6-147">`L` Jeśli literał jest sufiksem przez lub `l`, jego typ jest pierwszym z następujących `long` `ulong`typów, w których jego wartość może być reprezentowana: , .</span><span class="sxs-lookup"><span data-stu-id="981d6-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="981d6-148">Można użyć litery małych `l` jako sufiksu.</span><span class="sxs-lookup"><span data-stu-id="981d6-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="981d6-149">Jednak to generuje ostrzeżenie kompilatora, ponieważ `l` literę `1`można pomylić z cyfrą .</span><span class="sxs-lookup"><span data-stu-id="981d6-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="981d6-150">Użyj `L` dla jasności.</span><span class="sxs-lookup"><span data-stu-id="981d6-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="981d6-151">Jeśli literał jest sufiksem `uL` `ul`przez `LU` `UL` `Ul`, `lU`, `lu`, , `ulong` `Lu`, , lub , jego typ jest .</span><span class="sxs-lookup"><span data-stu-id="981d6-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="981d6-152">Jeśli wartość reprezentowana przez litera liczba <xref:System.UInt64.MaxValue?displayProperty=nameWithType>całkowita przekracza , występuje błąd kompilatora [CS1021.](../../misc/cs1021.md)</span><span class="sxs-lookup"><span data-stu-id="981d6-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="981d6-153">Jeśli określony typ literału całkowitej `int` jest i wartość reprezentowana przez literał znajduje się w zakresie typu docelowego, wartość może być niejawnie konwertowane na `sbyte`, `byte` `short`, , `ushort`, `uint`, lub `ulong`:</span><span class="sxs-lookup"><span data-stu-id="981d6-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="981d6-154">Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie mieści się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)</span><span class="sxs-lookup"><span data-stu-id="981d6-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="981d6-155">Można również użyć rzutowania do konwersji wartości reprezentowanej przez literał liczby całkowitej na typ inny niż określony typ literału:</span><span class="sxs-lookup"><span data-stu-id="981d6-155">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="981d6-156">Konwersje</span><span class="sxs-lookup"><span data-stu-id="981d6-156">Conversions</span></span>

<span data-ttu-id="981d6-157">Można przekonwertować dowolny całkowity typ liczbowy na dowolny inny integralny typ liczbowy.</span><span class="sxs-lookup"><span data-stu-id="981d6-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="981d6-158">Jeśli typ docelowy może przechowywać wszystkie wartości typu źródła, konwersja jest niejawna.</span><span class="sxs-lookup"><span data-stu-id="981d6-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="981d6-159">W przeciwnym razie należy użyć [wyrażenia rzutowego](../operators/type-testing-and-cast.md#cast-expression) do wykonania konwersji jawnej.</span><span class="sxs-lookup"><span data-stu-id="981d6-159">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="981d6-160">Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje numeryczne](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="981d6-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="981d6-161">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="981d6-161">C# language specification</span></span>

<span data-ttu-id="981d6-162">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="981d6-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="981d6-163">Typy integralne</span><span class="sxs-lookup"><span data-stu-id="981d6-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="981d6-164">Literały liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="981d6-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="981d6-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="981d6-165">See also</span></span>

- [<span data-ttu-id="981d6-166">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="981d6-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="981d6-167">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="981d6-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="981d6-168">Typy zmiennoprzecinowe</span><span class="sxs-lookup"><span data-stu-id="981d6-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="981d6-169">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="981d6-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="981d6-170">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="981d6-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
