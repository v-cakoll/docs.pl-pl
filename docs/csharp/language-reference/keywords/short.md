---
title: "short (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca3c5444c4fa7a49b7169be3e2a5b15d1a72207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="short-c-reference"></a><span data-ttu-id="ad987-102">short (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ad987-102">short (C# Reference)</span></span>

<span data-ttu-id="ad987-103">`short`Określa typ całkowite danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ad987-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="ad987-104">Typ</span><span class="sxs-lookup"><span data-stu-id="ad987-104">Type</span></span>|<span data-ttu-id="ad987-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="ad987-105">Range</span></span>|<span data-ttu-id="ad987-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="ad987-106">Size</span></span>|<span data-ttu-id="ad987-107">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad987-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="ad987-108">-32768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="ad987-108">-32,768 to 32,767</span></span>|<span data-ttu-id="ad987-109">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="ad987-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="ad987-110">Literały</span><span class="sxs-lookup"><span data-stu-id="ad987-110">Literals</span></span>  

<span data-ttu-id="ad987-111">Można zadeklarować i zainicjuj `short` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="ad987-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="ad987-112">Jeśli liczba całkowita literału jest poza zakresem `short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ad987-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="ad987-113">W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `short` wartości.</span><span class="sxs-lookup"><span data-stu-id="ad987-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> <span data-ttu-id="ad987-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny.</span><span class="sxs-lookup"><span data-stu-id="ad987-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="ad987-115">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="ad987-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ad987-116">Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="ad987-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="ad987-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="ad987-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="ad987-118">C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="ad987-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="ad987-119">Literał dziesiętny nie mogą mieć wiodące podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="ad987-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="ad987-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="ad987-120">Some examples are shown below.</span></span>

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="ad987-121">Rozpoznanie przeciążenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="ad987-121">Compiler overload resolution</span></span>

 <span data-ttu-id="ad987-122">Rzutowanie musi być używany podczas wywoływania metody przeciążane.</span><span class="sxs-lookup"><span data-stu-id="ad987-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="ad987-123">Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `short` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="ad987-123">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="ad987-124">Przy użyciu `short` rzutowania gwarantuje, że poprawne typu jest nazywana, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ad987-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="ad987-125">Konwersje</span><span class="sxs-lookup"><span data-stu-id="ad987-125">Conversions</span></span>  

 <span data-ttu-id="ad987-126">Jest wstępnie zdefiniowanych niejawna konwersja z `short` do [int](../../../csharp/language-reference/keywords/int.md), [długi](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [ decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="ad987-126">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="ad987-127">Nie można niejawnie przekonwertować nieliteralnego liczbowych typów większy rozmiar magazynu do `short` (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).</span><span class="sxs-lookup"><span data-stu-id="ad987-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="ad987-128">Należy wziąć pod uwagę, na przykład następujące dwa `short` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="ad987-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="ad987-129">Następująca instrukcja przypisania generuje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](../../../csharp/language-reference/keywords/int.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ad987-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="ad987-130">Aby rozwiązać ten problem, należy użyć rzutowanie:</span><span class="sxs-lookup"><span data-stu-id="ad987-130">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="ad987-131">Istnieje również możliwość użycia poniższych instrukcji, gdzie zmienna docelowa ma ten sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="ad987-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="ad987-132">Nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `short`.</span><span class="sxs-lookup"><span data-stu-id="ad987-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="ad987-133">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="ad987-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="ad987-134">Informacje w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="ad987-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="ad987-135">Aby uzyskać więcej informacji na niejawna konwersja liczbowa reguły, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="ad987-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ad987-136">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ad987-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad987-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad987-137">See Also</span></span>  
 <xref:System.Int16>  
 [<span data-ttu-id="ad987-138">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ad987-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ad987-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ad987-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ad987-140">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ad987-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ad987-141">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="ad987-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="ad987-142">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="ad987-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ad987-143">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="ad987-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="ad987-144">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="ad987-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
