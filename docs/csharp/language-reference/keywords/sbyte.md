---
title: sbyte (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: 4a2d13463348c2f0c32aec076623f59040d1d81f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289195"
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="99e32-102">sbyte (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="99e32-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="99e32-103">`sbyte` Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="99e32-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="99e32-104">Typ</span><span class="sxs-lookup"><span data-stu-id="99e32-104">Type</span></span>|<span data-ttu-id="99e32-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="99e32-105">Range</span></span>|<span data-ttu-id="99e32-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="99e32-106">Size</span></span>|<span data-ttu-id="99e32-107">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99e32-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="99e32-108">-128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="99e32-108">-128 to 127</span></span>|<span data-ttu-id="99e32-109">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="99e32-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="99e32-110">Literały</span><span class="sxs-lookup"><span data-stu-id="99e32-110">Literals</span></span>  

<span data-ttu-id="99e32-111">Można zadeklarować i zainicjuj `sbyte` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od 7.0 C#) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="99e32-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="99e32-112">W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `sbyte` wartości.</span><span class="sxs-lookup"><span data-stu-id="99e32-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="99e32-113">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny.</span><span class="sxs-lookup"><span data-stu-id="99e32-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="99e32-114">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="99e32-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="99e32-115">Uruchamianie z C# w wersji 7.0, dodano kilka funkcji w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="99e32-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="99e32-116">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="99e32-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="99e32-117">C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="99e32-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="99e32-118">Literał dziesiętny nie mogą mieć wiodące podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="99e32-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="99e32-119">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="99e32-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="99e32-120">Jeśli liczba całkowita literału jest poza zakresem `sbyte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="99e32-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="99e32-121">Jeśli literał całkowity nie sufiks, jego typ jest pierwsza z tych typów, w których jej wartość może być reprezentowany: [int](int.md), [uint](uint.md), [długi](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="99e32-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="99e32-122">Oznacza to, że w tym przykładzie literałach numerycznych `0x9A` i `0b10011010` będą interpretowane jako 32-bitowych liczb całkowitych ze znakiem z wartością 156, którego rozmiar przekracza <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99e32-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99e32-123">W związku z tym jest potrzebny operatora rzutowania i przypisania musi występować w [niezaznaczone](unchecked.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="99e32-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="99e32-124">Rozpoznanie przeciążenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="99e32-124">Compiler overload resolution</span></span>

 <span data-ttu-id="99e32-125">Rzutowanie musi być używany podczas wywoływania metody przeciążane.</span><span class="sxs-lookup"><span data-stu-id="99e32-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="99e32-126">Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `sbyte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="99e32-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="99e32-127">Przy użyciu `sbyte` rzutowania gwarantuje, że poprawne typu jest nazywana, na przykład:</span><span class="sxs-lookup"><span data-stu-id="99e32-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="99e32-128">Konwersje</span><span class="sxs-lookup"><span data-stu-id="99e32-128">Conversions</span></span>  
 <span data-ttu-id="99e32-129">Jest wstępnie zdefiniowanych niejawna konwersja z `sbyte` do [krótki](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [długi](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne ](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="99e32-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="99e32-130">Nie można niejawnie przekonwertować nieliteralnego liczbowych typów większy rozmiar magazynu do `sbyte` (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).</span><span class="sxs-lookup"><span data-stu-id="99e32-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="99e32-131">Należy wziąć pod uwagę, na przykład następujące dwa `sbyte` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="99e32-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="99e32-132">Następująca instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](../../../csharp/language-reference/keywords/int.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="99e32-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="99e32-133">Aby rozwiązać ten problem, należy rzutować wyrażenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="99e32-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="99e32-134">Możliwe jest jednak należy zastosować następujące instrukcje, gdzie zmienna docelowa ma ten sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="99e32-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="99e32-135">Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="99e32-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="99e32-136">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="99e32-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="99e32-137">Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="99e32-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="99e32-138">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="99e32-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="99e32-139">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99e32-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99e32-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99e32-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="99e32-141">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="99e32-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="99e32-142">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="99e32-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="99e32-143">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="99e32-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="99e32-144">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="99e32-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="99e32-145">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="99e32-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="99e32-146">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="99e32-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="99e32-147">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="99e32-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
