---
title: SByte — C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: df184bf32fa09b10c7f3de508ffb73b9cf156b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663406"
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="e1bdb-102">sbyte (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e1bdb-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="e1bdb-103">`sbyte` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="e1bdb-104">Typ</span><span class="sxs-lookup"><span data-stu-id="e1bdb-104">Type</span></span>|<span data-ttu-id="e1bdb-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="e1bdb-105">Range</span></span>|<span data-ttu-id="e1bdb-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="e1bdb-106">Size</span></span>|<span data-ttu-id="e1bdb-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="e1bdb-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="e1bdb-108">-128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-108">-128 to 127</span></span>|<span data-ttu-id="e1bdb-109">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="e1bdb-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="e1bdb-110">Literały</span><span class="sxs-lookup"><span data-stu-id="e1bdb-110">Literals</span></span>  

<span data-ttu-id="e1bdb-111">Można zadeklarować i zainicjować `sbyte` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="e1bdb-112">W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `sbyte` wartości.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="e1bdb-113">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="e1bdb-114">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="e1bdb-115">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="e1bdb-116">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="e1bdb-117">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="e1bdb-118">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="e1bdb-119">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="e1bdb-120">Jeśli literał liczby całkowitej jest poza zakresem `sbyte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="e1bdb-121">Gdy literał liczby całkowitej jest brak przyrostka, jego typ jest to pierwsza z tych typów, w których jej wartość może być reprezentowana: [int](int.md), [uint](uint.md), [długie](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="e1bdb-122">Oznacza to, że w tym przykładzie literały numeryczne `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem z wartością 156, co powoduje przekroczenie <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1bdb-123">W związku z tym operatora rzutowania są potrzebne, i przypisanie musi występować w [unchecked](unchecked.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="e1bdb-124">Przeciążeń z późnym</span><span class="sxs-lookup"><span data-stu-id="e1bdb-124">Compiler overload resolution</span></span>

 <span data-ttu-id="e1bdb-125">Podczas wywoływania przeciążone metody, należy użyć rzutowania.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="e1bdb-126">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `sbyte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="e1bdb-127">Za pomocą `sbyte` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="e1bdb-128">Konwersje</span><span class="sxs-lookup"><span data-stu-id="e1bdb-128">Conversions</span></span>  
 <span data-ttu-id="e1bdb-129">Jest wstępnie zdefiniowanych niejawna konwersja z `sbyte` do [krótki](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [długie](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double ](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="e1bdb-130">Nie można niejawnie przekonwertować nieliteralnego typy liczbowe większy rozmiar magazynu na `sbyte` (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="e1bdb-131">Należy wziąć pod uwagę, na przykład, następujące dwa `sbyte` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="e1bdb-132">Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](../../../csharp/language-reference/keywords/int.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="e1bdb-133">Aby rozwiązać ten problem, rzutowane wyrażenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="e1bdb-134">Możliwe jest jednak należy zastosować następujące polecenia, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="e1bdb-135">Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="e1bdb-136">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="e1bdb-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="e1bdb-137">Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="e1bdb-138">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e1bdb-139">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e1bdb-139">C# Language Specification</span></span>  

<span data-ttu-id="e1bdb-140">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1bdb-140">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="e1bdb-141">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="e1bdb-141">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1bdb-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1bdb-142">See also</span></span>

- <xref:System.SByte>
- [<span data-ttu-id="e1bdb-143">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e1bdb-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="e1bdb-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e1bdb-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e1bdb-145">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e1bdb-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="e1bdb-146">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="e1bdb-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="e1bdb-147">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="e1bdb-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="e1bdb-148">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="e1bdb-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="e1bdb-149">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="e1bdb-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
