---
title: ulong — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 97db22612e900658746f40cd117ff941135027a1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235023"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="3e603-102">ulong (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3e603-102">ulong (C# Reference)</span></span>

<span data-ttu-id="3e603-103">`ulong` — Słowo kluczowe oznacza integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3e603-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="3e603-104">Typ</span><span class="sxs-lookup"><span data-stu-id="3e603-104">Type</span></span>|<span data-ttu-id="3e603-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="3e603-105">Range</span></span>|<span data-ttu-id="3e603-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="3e603-106">Size</span></span>|<span data-ttu-id="3e603-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="3e603-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ulong`|<span data-ttu-id="3e603-108">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="3e603-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="3e603-109">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="3e603-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="3e603-110">Literały</span><span class="sxs-lookup"><span data-stu-id="3e603-110">Literals</span></span>

<span data-ttu-id="3e603-111">Można zadeklarować i zainicjować `ulong` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="3e603-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="3e603-112">Jeśli literał liczby całkowitej jest poza zakresem `ulong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3e603-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="3e603-113">W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `ulong` wartości.</span><span class="sxs-lookup"><span data-stu-id="3e603-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> <span data-ttu-id="3e603-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="3e603-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="3e603-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="3e603-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3e603-116">Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:</span><span class="sxs-lookup"><span data-stu-id="3e603-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="3e603-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="3e603-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="3e603-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="3e603-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="3e603-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="3e603-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="3e603-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="3e603-120">Some examples are shown below.</span></span>

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="3e603-121">Literały całkowite mogą również zawierać sufiks, który oznacza typ.</span><span class="sxs-lookup"><span data-stu-id="3e603-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="3e603-122">Sufiks `UL` lub `ul` jednoznacznie identyfikuje literał liczbowy jako `ulong` wartość.</span><span class="sxs-lookup"><span data-stu-id="3e603-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="3e603-123">`L` Oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e603-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e603-124">I `U` lub `u` oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e603-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e603-125">W poniższym przykładzie użyto `ul` sufiks do oznaczania długich liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="3e603-125">The following example uses the `ul` suffix to denote a long integer:</span></span>

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="3e603-126">Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="3e603-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="3e603-127">int</span><span class="sxs-lookup"><span data-stu-id="3e603-127">int</span></span>](int.md)
2. [<span data-ttu-id="3e603-128">uint</span><span class="sxs-lookup"><span data-stu-id="3e603-128">uint</span></span>](uint.md)
3. [<span data-ttu-id="3e603-129">long</span><span class="sxs-lookup"><span data-stu-id="3e603-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="3e603-130">Przeciążeń z późnym</span><span class="sxs-lookup"><span data-stu-id="3e603-130">Compiler overload resolution</span></span>

<span data-ttu-id="3e603-131">Typowym zastosowaniem sufiks jest wywołanie metody przeciążone.</span><span class="sxs-lookup"><span data-stu-id="3e603-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="3e603-132">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `ulong` i [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="3e603-132">Consider, for example, the following overloaded methods that use `ulong` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

<span data-ttu-id="3e603-133">Przy użyciu sufiksu z `ulong` parametru gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="3e603-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a><span data-ttu-id="3e603-134">Konwersje</span><span class="sxs-lookup"><span data-stu-id="3e603-134">Conversions</span></span>

<span data-ttu-id="3e603-135">Jest wstępnie zdefiniowanych niejawna konwersja z `ulong` do [float](float.md), [double](double.md), lub [dziesiętna](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="3e603-135">There is a predefined implicit conversion from `ulong` to [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="3e603-136">Istnieje niejawna konwersja z `ulong` do dowolnego typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="3e603-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="3e603-137">Na przykład następująca instrukcja generuje błąd kompilacji bez jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="3e603-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

<span data-ttu-id="3e603-138">Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md), [ushort](ushort.md), [uint](uint.md), lub [char](char.md) do `ulong`.</span><span class="sxs-lookup"><span data-stu-id="3e603-138">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), [uint](uint.md), or [char](char.md) to `ulong`.</span></span>

<span data-ttu-id="3e603-139">Ponadto istnieje niejawna konwersja z typów zmiennoprzecinkowych `ulong`.</span><span class="sxs-lookup"><span data-stu-id="3e603-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="3e603-140">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="3e603-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

<span data-ttu-id="3e603-141">Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="3e603-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="3e603-142">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="3e603-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3e603-143">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3e603-143">C# language specification</span></span>

<span data-ttu-id="3e603-144">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e603-144">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3e603-145">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="3e603-145">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e603-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e603-146">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="3e603-147">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3e603-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3e603-148">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3e603-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3e603-149">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3e603-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3e603-150">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="3e603-150">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="3e603-151">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="3e603-151">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="3e603-152">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="3e603-152">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="3e603-153">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="3e603-153">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
