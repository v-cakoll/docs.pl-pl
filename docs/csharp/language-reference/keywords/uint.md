---
title: uint — słowo kluczowe (C# odwołania)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 86cbb216bd960251ebd78916fae7865aa10aa5fc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149695"
---
# <a name="uint-c-reference"></a><span data-ttu-id="bf7b5-102">uint (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bf7b5-102">uint (C# Reference)</span></span>

<span data-ttu-id="bf7b5-103">`uint` — Słowo kluczowe oznacza integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="bf7b5-104">Typ</span><span class="sxs-lookup"><span data-stu-id="bf7b5-104">Type</span></span>|<span data-ttu-id="bf7b5-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="bf7b5-105">Range</span></span>|<span data-ttu-id="bf7b5-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="bf7b5-106">Size</span></span>|<span data-ttu-id="bf7b5-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="bf7b5-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`uint`|<span data-ttu-id="bf7b5-108">4 294 967 0 Aby 295</span><span class="sxs-lookup"><span data-stu-id="bf7b5-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="bf7b5-109">Liczba całkowita bez znaku 32-bitowy</span><span class="sxs-lookup"><span data-stu-id="bf7b5-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|

<span data-ttu-id="bf7b5-110">**Uwaga** `uint` typ nie jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="bf7b5-111">Użyj `int` zawsze, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-111">Use `int` whenever possible.</span></span>

## <a name="literals"></a><span data-ttu-id="bf7b5-112">Literały</span><span class="sxs-lookup"><span data-stu-id="bf7b5-112">Literals</span></span>

<span data-ttu-id="bf7b5-113">Można zadeklarować i zainicjować `uint` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="bf7b5-114">Jeśli literał liczby całkowitej jest poza zakresem `uint` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="bf7b5-115">W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `uint` wartości.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> <span data-ttu-id="bf7b5-116">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="bf7b5-117">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-117">Decimal literals have no prefix.</span></span>

<span data-ttu-id="bf7b5-118">Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:</span><span class="sxs-lookup"><span data-stu-id="bf7b5-118">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="bf7b5-119">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="bf7b5-120">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="bf7b5-121">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="bf7b5-122">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-122">Some examples are shown below.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

<span data-ttu-id="bf7b5-123">Literały całkowite mogą również zawierać sufiks, który oznacza typ.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="bf7b5-124">Sufiks `U` lub "u" oznacza albo `uint` lub `ulong`, w zależności od wartości liczbowej literału.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="bf7b5-125">W poniższym przykładzie użyto `u` sufiks, aby wskazać liczbą całkowitą bez znaku obu typów.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="bf7b5-126">Należy zauważyć, że pierwszym literał `uint` ponieważ jej wartość jest mniejsza niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a drugą jest wartość `ulong` ponieważ jej wartość jest większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

<span data-ttu-id="bf7b5-127">Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="bf7b5-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="bf7b5-128">int</span><span class="sxs-lookup"><span data-stu-id="bf7b5-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="bf7b5-129">long</span><span class="sxs-lookup"><span data-stu-id="bf7b5-129">long</span></span>](long.md)
4. [<span data-ttu-id="bf7b5-130">ulong</span><span class="sxs-lookup"><span data-stu-id="bf7b5-130">ulong</span></span>](ulong.md)

## <a name="conversions"></a><span data-ttu-id="bf7b5-131">Konwersje</span><span class="sxs-lookup"><span data-stu-id="bf7b5-131">Conversions</span></span>

<span data-ttu-id="bf7b5-132">Jest wstępnie zdefiniowanych niejawna konwersja z `uint` do [długie](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), lub [ dziesiętna](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b5-132">There is a predefined implicit conversion from `uint` to [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span> <span data-ttu-id="bf7b5-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bf7b5-133">For example:</span></span>

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

<span data-ttu-id="bf7b5-134">Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md), [ushort](ushort.md), lub [char](char.md) do `uint`.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-134">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), or [char](char.md) to `uint`.</span></span> <span data-ttu-id="bf7b5-135">W przeciwnym razie należy użyć rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="bf7b5-136">Na przykład poniższa instrukcja przypisania spowoduje błąd kompilacji bez rzutowania:</span><span class="sxs-lookup"><span data-stu-id="bf7b5-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

<span data-ttu-id="bf7b5-137">Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `uint`.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="bf7b5-138">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="bf7b5-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

<span data-ttu-id="bf7b5-139">Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b5-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="bf7b5-140">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b5-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bf7b5-141">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bf7b5-141">C# language specification</span></span>

<span data-ttu-id="bf7b5-142">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b5-142">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="bf7b5-143">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="bf7b5-143">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7b5-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf7b5-144">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="bf7b5-145">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bf7b5-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bf7b5-146">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bf7b5-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bf7b5-147">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bf7b5-147">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bf7b5-148">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="bf7b5-148">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="bf7b5-149">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="bf7b5-149">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="bf7b5-150">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="bf7b5-150">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="bf7b5-151">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="bf7b5-151">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)