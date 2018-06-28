---
title: uint (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: 8ee19688ff0a6687bcf761857958aa2022fdb0c8
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027814"
---
# <a name="uint-c-reference"></a><span data-ttu-id="89df1-102">uint (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="89df1-102">uint (C# Reference)</span></span>

<span data-ttu-id="89df1-103">`uint` — Słowo kluczowe oznacza, że typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="89df1-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="89df1-104">Typ</span><span class="sxs-lookup"><span data-stu-id="89df1-104">Type</span></span>|<span data-ttu-id="89df1-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="89df1-105">Range</span></span>|<span data-ttu-id="89df1-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="89df1-106">Size</span></span>|<span data-ttu-id="89df1-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="89df1-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="89df1-108">4 294 967 0 Aby 295</span><span class="sxs-lookup"><span data-stu-id="89df1-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="89df1-109">Liczba całkowita 32-bitowa bez znaku</span><span class="sxs-lookup"><span data-stu-id="89df1-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="89df1-110">**Uwaga** `uint` typu nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="89df1-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="89df1-111">Użyj `int` zawsze, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="89df1-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="89df1-112">Literały</span><span class="sxs-lookup"><span data-stu-id="89df1-112">Literals</span></span>  

<span data-ttu-id="89df1-113">Można zadeklarować i zainicjuj `uint` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od 7.0 C#) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="89df1-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="89df1-114">Jeśli liczba całkowita literału jest poza zakresem `uint` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89df1-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="89df1-115">W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `uint` wartości.</span><span class="sxs-lookup"><span data-stu-id="89df1-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="89df1-116">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny.</span><span class="sxs-lookup"><span data-stu-id="89df1-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="89df1-117">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="89df1-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="89df1-118">Uruchamianie z C# w wersji 7.0, dodano kilka funkcji w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="89df1-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="89df1-119">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="89df1-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="89df1-120">C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="89df1-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="89df1-121">Literał dziesiętny nie mogą mieć wiodące podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="89df1-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="89df1-122">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="89df1-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="89df1-123">Literały całkowite mogą również obejmować sufiks, który wskazuje typ.</span><span class="sxs-lookup"><span data-stu-id="89df1-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="89df1-124">Sufiks `U` lub "u" oznacza albo `uint` lub `ulong`, w zależności od liczbowa wartość literału.</span><span class="sxs-lookup"><span data-stu-id="89df1-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="89df1-125">W poniższym przykładzie użyto `u` sufiks określający całkowitą bez znaku obu typów.</span><span class="sxs-lookup"><span data-stu-id="89df1-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="89df1-126">Należy zauważyć, że pierwszy literał `uint` , ponieważ jej wartość jest mniejsza niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a drugą jest wartość `ulong` , ponieważ jej wartość jest większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89df1-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="89df1-127">Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość:</span><span class="sxs-lookup"><span data-stu-id="89df1-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="89df1-128">int</span><span class="sxs-lookup"><span data-stu-id="89df1-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="89df1-129">long</span><span class="sxs-lookup"><span data-stu-id="89df1-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="89df1-130">ulong</span><span class="sxs-lookup"><span data-stu-id="89df1-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="89df1-131">Konwersje</span><span class="sxs-lookup"><span data-stu-id="89df1-131">Conversions</span></span>  
 <span data-ttu-id="89df1-132">Jest wstępnie zdefiniowanych niejawna konwersja z `uint` do [długi](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [ decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="89df1-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="89df1-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="89df1-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="89df1-134">Jest wstępnie zdefiniowanych niejawna konwersja z [bajtów](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `uint`.</span><span class="sxs-lookup"><span data-stu-id="89df1-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="89df1-135">W przeciwnym razie należy użyć rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="89df1-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="89df1-136">Na przykład następująca instrukcja przypisania spowoduje błąd kompilacji bez rzutowanie:</span><span class="sxs-lookup"><span data-stu-id="89df1-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="89df1-137">Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `uint`.</span><span class="sxs-lookup"><span data-stu-id="89df1-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="89df1-138">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="89df1-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="89df1-139">Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="89df1-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="89df1-140">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="89df1-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="89df1-141">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="89df1-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89df1-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89df1-142">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="89df1-143">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="89df1-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="89df1-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="89df1-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="89df1-145">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="89df1-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="89df1-146">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="89df1-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="89df1-147">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="89df1-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="89df1-148">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="89df1-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="89df1-149">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="89df1-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
