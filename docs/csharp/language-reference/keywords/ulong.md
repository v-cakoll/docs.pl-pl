---
title: "ulong (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2058d9f6a228b13938fe08d7e2fb11e3b9f4600a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ulong-c-reference"></a><span data-ttu-id="38026-102">ulong (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="38026-102">ulong (C# Reference)</span></span>

<span data-ttu-id="38026-103">`ulong` — Słowo kluczowe Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="38026-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="38026-104">Typ</span><span class="sxs-lookup"><span data-stu-id="38026-104">Type</span></span>|<span data-ttu-id="38026-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="38026-105">Range</span></span>|<span data-ttu-id="38026-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="38026-106">Size</span></span>|<span data-ttu-id="38026-107">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38026-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="38026-108">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="38026-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="38026-109">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="38026-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="38026-110">Literały</span><span class="sxs-lookup"><span data-stu-id="38026-110">Literals</span></span>  

<span data-ttu-id="38026-111">Można zadeklarować i zainicjuj `ulong` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="38026-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="38026-112">Jeśli liczba całkowita literału jest poza zakresem `ulong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="38026-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="38026-113">W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `ulong` wartości.</span><span class="sxs-lookup"><span data-stu-id="38026-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> <span data-ttu-id="38026-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny.</span><span class="sxs-lookup"><span data-stu-id="38026-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="38026-115">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="38026-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="38026-116">Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="38026-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="38026-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="38026-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="38026-118">C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="38026-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="38026-119">Literał dziesiętny nie mogą mieć wiodące podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="38026-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="38026-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="38026-120">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="38026-121">Literały całkowite mogą również obejmować sufiks, który wskazuje typ.</span><span class="sxs-lookup"><span data-stu-id="38026-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="38026-122">Sufiks `UL` lub `ul` jednoznacznie identyfikuje literałem jako `ulong` wartość.</span><span class="sxs-lookup"><span data-stu-id="38026-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="38026-123">`L` Określa sufiks `ulong` jeśli przekracza wartość literału <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38026-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38026-124">I `U` lub `u` Określa sufiks `ulong` jeśli przekracza wartość literału <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38026-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38026-125">W poniższym przykładzie użyto `ul` sufiks określający długich liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="38026-125">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="38026-126">Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość:</span><span class="sxs-lookup"><span data-stu-id="38026-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="38026-127">int</span><span class="sxs-lookup"><span data-stu-id="38026-127">int</span></span>](int.md)
2. [<span data-ttu-id="38026-128">uint</span><span class="sxs-lookup"><span data-stu-id="38026-128">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="38026-129">długa</span><span class="sxs-lookup"><span data-stu-id="38026-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="38026-130">Rozpoznanie przeciążenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="38026-130">Compiler overload resolution</span></span>
  
 <span data-ttu-id="38026-131">Typowe Użyj sufiksu jest wywołanie metody przeciążone.</span><span class="sxs-lookup"><span data-stu-id="38026-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="38026-132">Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `ulong` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="38026-132">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="38026-133">Przy użyciu sufiksu z `ulong` parametru gwarantuje, że poprawne typu jest nazywana, na przykład:</span><span class="sxs-lookup"><span data-stu-id="38026-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="38026-134">Konwersje</span><span class="sxs-lookup"><span data-stu-id="38026-134">Conversions</span></span>  
 <span data-ttu-id="38026-135">Jest wstępnie zdefiniowanych niejawna konwersja z `ulong` do [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="38026-135">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="38026-136">Nie jest niejawna konwersja z `ulong` do dowolnego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="38026-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="38026-137">Na przykład następująca instrukcja spowoduje błąd kompilacji bez jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="38026-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="38026-138">Jest wstępnie zdefiniowanych niejawna konwersja z [bajtów](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `ulong`.</span><span class="sxs-lookup"><span data-stu-id="38026-138">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="38026-139">Ponadto nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `ulong`.</span><span class="sxs-lookup"><span data-stu-id="38026-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="38026-140">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="38026-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="38026-141">Informacje w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="38026-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="38026-142">Aby uzyskać więcej informacji na niejawna konwersja liczbowa reguły, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="38026-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="38026-143">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="38026-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38026-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38026-144">See Also</span></span>  
 <xref:System.UInt64>  
 [<span data-ttu-id="38026-145">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="38026-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="38026-146">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="38026-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="38026-147">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="38026-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="38026-148">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="38026-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="38026-149">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="38026-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="38026-150">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="38026-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="38026-151">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="38026-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
