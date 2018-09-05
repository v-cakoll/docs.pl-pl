---
title: int (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 95ac267bc70d2e7873593c08e0b10cb50fefd8c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524047"
---
# <a name="int-c-reference"></a><span data-ttu-id="fed4e-102">int (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fed4e-102">int (C# Reference)</span></span>

<span data-ttu-id="fed4e-103">`int` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="fed4e-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="fed4e-104">Typ</span><span class="sxs-lookup"><span data-stu-id="fed4e-104">Type</span></span>|<span data-ttu-id="fed4e-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="fed4e-105">Range</span></span>|<span data-ttu-id="fed4e-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="fed4e-106">Size</span></span>|<span data-ttu-id="fed4e-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="fed4e-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`int`|<span data-ttu-id="fed4e-108">-2 147 483 2 147 483 648 do 647</span><span class="sxs-lookup"><span data-stu-id="fed4e-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="fed4e-109">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="fed4e-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="fed4e-110">Literały</span><span class="sxs-lookup"><span data-stu-id="fed4e-110">Literals</span></span>  
 
<span data-ttu-id="fed4e-111">Można zadeklarować i zainicjować `int` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="fed4e-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="fed4e-112">Jeśli literał liczby całkowitej jest poza zakresem `int` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fed4e-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="fed4e-113">W poniższym przykładzie liczb całkowitych równa 90,946, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `int` wartości.</span><span class="sxs-lookup"><span data-stu-id="fed4e-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="fed4e-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="fed4e-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="fed4e-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="fed4e-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="fed4e-116">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="fed4e-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="fed4e-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="fed4e-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="fed4e-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="fed4e-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="fed4e-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="fed4e-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="fed4e-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="fed4e-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="fed4e-121">Literały całkowite mogą również zawierać sufiks, który oznacza typ., mimo że istnieje nie przyrostka, który oznacza `int` typu.</span><span class="sxs-lookup"><span data-stu-id="fed4e-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="fed4e-122">Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="fed4e-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="fed4e-123">uint</span><span class="sxs-lookup"><span data-stu-id="fed4e-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="fed4e-124">long</span><span class="sxs-lookup"><span data-stu-id="fed4e-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="fed4e-125">ulong</span><span class="sxs-lookup"><span data-stu-id="fed4e-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="fed4e-126">W tych przykładach 90946 literał jest typu `int`.</span><span class="sxs-lookup"><span data-stu-id="fed4e-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="fed4e-127">Konwersje</span><span class="sxs-lookup"><span data-stu-id="fed4e-127">Conversions</span></span>  
 <span data-ttu-id="fed4e-128">Jest wstępnie zdefiniowanych niejawna konwersja z `int` do [długie](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="fed4e-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="fed4e-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fed4e-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="fed4e-130">Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) Aby `int`.</span><span class="sxs-lookup"><span data-stu-id="fed4e-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="fed4e-131">Na przykład poniższa instrukcja przypisania spowoduje błąd kompilacji bez rzutowania:</span><span class="sxs-lookup"><span data-stu-id="fed4e-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="fed4e-132">Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `int`.</span><span class="sxs-lookup"><span data-stu-id="fed4e-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="fed4e-133">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="fed4e-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="fed4e-134">Aby uzyskać więcej informacji na wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="fed4e-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fed4e-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fed4e-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fed4e-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fed4e-136">See Also</span></span>

- <xref:System.Int32>  
- [<span data-ttu-id="fed4e-137">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fed4e-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fed4e-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fed4e-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fed4e-139">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fed4e-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="fed4e-140">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="fed4e-140">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="fed4e-141">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="fed4e-141">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="fed4e-142">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="fed4e-142">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="fed4e-143">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="fed4e-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
