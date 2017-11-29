---
title: "int (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords: int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7acb8bb482ebf8f5c2b508e7cfd45b5b64aae3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="int-c-reference"></a><span data-ttu-id="8f590-102">int (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8f590-102">int (C# Reference)</span></span>

<span data-ttu-id="8f590-103">`int`Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8f590-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="8f590-104">Typ</span><span class="sxs-lookup"><span data-stu-id="8f590-104">Type</span></span>|<span data-ttu-id="8f590-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="8f590-105">Range</span></span>|<span data-ttu-id="8f590-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="8f590-106">Size</span></span>|<span data-ttu-id="8f590-107">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f590-107">.NET Framework type</span></span>|<span data-ttu-id="8f590-108">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8f590-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="8f590-109">-2 147 483 2 147 483 648 do 647</span><span class="sxs-lookup"><span data-stu-id="8f590-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="8f590-110">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="8f590-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="8f590-111">0</span><span class="sxs-lookup"><span data-stu-id="8f590-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="8f590-112">Literały</span><span class="sxs-lookup"><span data-stu-id="8f590-112">Literals</span></span>  
 
<span data-ttu-id="8f590-113">Można zadeklarować i zainicjuj `int` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="8f590-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="8f590-114">Jeśli liczba całkowita literału jest poza zakresem `int` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8f590-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="8f590-115">W poniższym przykładzie liczb całkowitych równa 90,946, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `int` wartości.</span><span class="sxs-lookup"><span data-stu-id="8f590-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="8f590-116">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny.</span><span class="sxs-lookup"><span data-stu-id="8f590-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="8f590-117">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="8f590-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="8f590-118">Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="8f590-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="8f590-119">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="8f590-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="8f590-120">C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="8f590-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="8f590-121">Literał dziesiętny nie mogą mieć wiodące podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="8f590-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="8f590-122">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="8f590-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="8f590-123">Literały całkowite mogą również obejmować sufiks, który wskazuje typ, nie ma żadnych sufiks, który wskazuje, ale `int` typu.</span><span class="sxs-lookup"><span data-stu-id="8f590-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="8f590-124">Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość:</span><span class="sxs-lookup"><span data-stu-id="8f590-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="8f590-125">uint</span><span class="sxs-lookup"><span data-stu-id="8f590-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="8f590-126">długa</span><span class="sxs-lookup"><span data-stu-id="8f590-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="8f590-127">ulong</span><span class="sxs-lookup"><span data-stu-id="8f590-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="8f590-128">W tych przykładach 90946 literału jest typu `int`.</span><span class="sxs-lookup"><span data-stu-id="8f590-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="8f590-129">Konwersje</span><span class="sxs-lookup"><span data-stu-id="8f590-129">Conversions</span></span>  
 <span data-ttu-id="8f590-130">Jest wstępnie zdefiniowanych niejawna konwersja z `int` do [długi](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="8f590-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="8f590-131">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8f590-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="8f590-132">Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) Aby `int`.</span><span class="sxs-lookup"><span data-stu-id="8f590-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="8f590-133">Na przykład następująca instrukcja przypisania spowoduje błąd kompilacji bez rzutowanie:</span><span class="sxs-lookup"><span data-stu-id="8f590-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="8f590-134">Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `int`.</span><span class="sxs-lookup"><span data-stu-id="8f590-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="8f590-135">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="8f590-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="8f590-136">Aby uzyskać więcej informacji w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="8f590-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8f590-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8f590-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f590-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f590-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="8f590-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8f590-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f590-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8f590-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f590-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8f590-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8f590-142">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="8f590-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="8f590-143">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="8f590-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="8f590-144">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="8f590-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="8f590-145">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="8f590-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
