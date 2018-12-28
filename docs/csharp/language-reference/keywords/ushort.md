---
title: ushort — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614465"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="dd5a2-102">ushort (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dd5a2-102">ushort (C# Reference)</span></span>

<span data-ttu-id="dd5a2-103">`ushort` — Słowo kluczowe wskazuje typ liczby całkowitej danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="dd5a2-104">Typ</span><span class="sxs-lookup"><span data-stu-id="dd5a2-104">Type</span></span>|<span data-ttu-id="dd5a2-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="dd5a2-105">Range</span></span>|<span data-ttu-id="dd5a2-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="dd5a2-106">Size</span></span>|<span data-ttu-id="dd5a2-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="dd5a2-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ushort`|<span data-ttu-id="dd5a2-108">0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-108">0 to 65,535</span></span>|<span data-ttu-id="dd5a2-109">Liczba całkowita bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="dd5a2-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="dd5a2-110">Literały</span><span class="sxs-lookup"><span data-stu-id="dd5a2-110">Literals</span></span>

<span data-ttu-id="dd5a2-111">Można zadeklarować i zainicjować `ushort` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="dd5a2-112">Jeśli literał liczby całkowitej jest poza zakresem `ushort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="dd5a2-113">W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](int.md) do `ushort` wartości.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `ushort` values.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> <span data-ttu-id="dd5a2-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="dd5a2-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="dd5a2-116">Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="dd5a2-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="dd5a2-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="dd5a2-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="dd5a2-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="dd5a2-121">Przeciążeń z późnym</span><span class="sxs-lookup"><span data-stu-id="dd5a2-121">Compiler overload resolution</span></span>

<span data-ttu-id="dd5a2-122">Należy użyć rzutowania, po wywołaniu metody przeciążone.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="dd5a2-123">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `ushort` i [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-123">Consider, for example, the following overloaded methods that use `ushort` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

<span data-ttu-id="dd5a2-124">Za pomocą `ushort` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a><span data-ttu-id="dd5a2-125">Konwersje</span><span class="sxs-lookup"><span data-stu-id="dd5a2-125">Conversions</span></span>

<span data-ttu-id="dd5a2-126">Jest wstępnie zdefiniowanych niejawna konwersja z `ushort` do [int](int.md), [uint](uint.md), [długie](long.md), [ulong](ulong.md), [float ](float.md), [double](double.md), lub [dziesiętna](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="dd5a2-126">There is a predefined implicit conversion from `ushort` to [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="dd5a2-127">Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md) lub [char](char.md) do `ushort`.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-127">There is a predefined implicit conversion from [byte](byte.md) or [char](char.md) to `ushort`.</span></span> <span data-ttu-id="dd5a2-128">W przeciwnym razie rzutowania może służyć do wykonania jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="dd5a2-129">Należy wziąć pod uwagę, na przykład, następujące dwa `ushort` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>

```csharp
ushort x = 5, y = 12;
```

<span data-ttu-id="dd5a2-130">Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

<span data-ttu-id="dd5a2-131">Aby rozwiązać ten problem, należy użyć rzutowania:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-131">To fix this problem, use a cast:</span></span>

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

<span data-ttu-id="dd5a2-132">Możliwe jest jednak należy zastosować następujące polecenia, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="dd5a2-133">Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `ushort`.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="dd5a2-134">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="dd5a2-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

<span data-ttu-id="dd5a2-135">Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="dd5a2-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="dd5a2-136">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="dd5a2-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dd5a2-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dd5a2-137">C# language specification</span></span>

<span data-ttu-id="dd5a2-138">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd5a2-138">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="dd5a2-139">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="dd5a2-139">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd5a2-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd5a2-140">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="dd5a2-141">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dd5a2-141">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd5a2-142">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dd5a2-142">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd5a2-143">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dd5a2-143">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dd5a2-144">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="dd5a2-144">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="dd5a2-145">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="dd5a2-145">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="dd5a2-146">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="dd5a2-146">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="dd5a2-147">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="dd5a2-147">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
