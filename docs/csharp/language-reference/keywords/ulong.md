---
title: ulong (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 96975bcfc270694a59a19e7c40183083dbc5bd98
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960224"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="cd24b-102">ulong (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cd24b-102">ulong (C# Reference)</span></span>

<span data-ttu-id="cd24b-103">`ulong` — Słowo kluczowe oznacza integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cd24b-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="cd24b-104">Typ</span><span class="sxs-lookup"><span data-stu-id="cd24b-104">Type</span></span>|<span data-ttu-id="cd24b-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="cd24b-105">Range</span></span>|<span data-ttu-id="cd24b-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="cd24b-106">Size</span></span>|<span data-ttu-id="cd24b-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="cd24b-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="cd24b-108">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="cd24b-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="cd24b-109">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="cd24b-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="cd24b-110">Literały</span><span class="sxs-lookup"><span data-stu-id="cd24b-110">Literals</span></span>  

<span data-ttu-id="cd24b-111">Można zadeklarować i zainicjować `ulong` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="cd24b-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="cd24b-112">Jeśli literał liczby całkowitej jest poza zakresem `ulong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cd24b-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="cd24b-113">W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `ulong` wartości.</span><span class="sxs-lookup"><span data-stu-id="cd24b-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> <span data-ttu-id="cd24b-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="cd24b-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="cd24b-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="cd24b-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="cd24b-116">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="cd24b-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="cd24b-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="cd24b-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="cd24b-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="cd24b-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="cd24b-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="cd24b-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="cd24b-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="cd24b-120">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="cd24b-121">Literały całkowite mogą również zawierać sufiks, który oznacza typ.</span><span class="sxs-lookup"><span data-stu-id="cd24b-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="cd24b-122">Sufiks `UL` lub `ul` jednoznacznie identyfikuje literał liczbowy jako `ulong` wartość.</span><span class="sxs-lookup"><span data-stu-id="cd24b-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="cd24b-123">`L` Oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd24b-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd24b-124">I `U` lub `u` oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd24b-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd24b-125">W poniższym przykładzie użyto `ul` sufiks do oznaczania długich liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="cd24b-125">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="cd24b-126">Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="cd24b-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="cd24b-127">int</span><span class="sxs-lookup"><span data-stu-id="cd24b-127">int</span></span>](int.md)
2. [<span data-ttu-id="cd24b-128">uint</span><span class="sxs-lookup"><span data-stu-id="cd24b-128">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="cd24b-129">long</span><span class="sxs-lookup"><span data-stu-id="cd24b-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="cd24b-130">Przeciążeń z późnym</span><span class="sxs-lookup"><span data-stu-id="cd24b-130">Compiler overload resolution</span></span>
  
 <span data-ttu-id="cd24b-131">Typowym zastosowaniem sufiks jest wywołanie metody przeciążone.</span><span class="sxs-lookup"><span data-stu-id="cd24b-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="cd24b-132">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `ulong` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="cd24b-132">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="cd24b-133">Przy użyciu sufiksu z `ulong` parametru gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="cd24b-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="cd24b-134">Konwersje</span><span class="sxs-lookup"><span data-stu-id="cd24b-134">Conversions</span></span>  
 <span data-ttu-id="cd24b-135">Jest wstępnie zdefiniowanych niejawna konwersja z `ulong` do [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="cd24b-135">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="cd24b-136">Istnieje niejawna konwersja z `ulong` do dowolnego typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="cd24b-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="cd24b-137">Na przykład następująca instrukcja generuje błąd kompilacji bez jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="cd24b-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="cd24b-138">Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `ulong`.</span><span class="sxs-lookup"><span data-stu-id="cd24b-138">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="cd24b-139">Ponadto istnieje niejawna konwersja z typów zmiennoprzecinkowych `ulong`.</span><span class="sxs-lookup"><span data-stu-id="cd24b-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="cd24b-140">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="cd24b-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="cd24b-141">Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="cd24b-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="cd24b-142">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="cd24b-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cd24b-143">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cd24b-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd24b-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd24b-144">See Also</span></span>  
 <xref:System.UInt64>  
 [<span data-ttu-id="cd24b-145">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cd24b-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd24b-146">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cd24b-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd24b-147">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cd24b-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cd24b-148">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="cd24b-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="cd24b-149">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="cd24b-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="cd24b-150">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="cd24b-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="cd24b-151">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="cd24b-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
