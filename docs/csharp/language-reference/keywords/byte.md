---
title: byte (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: ee70b7c804423a35e2db3fe20ac4b66d8d1b98e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505098"
---
# <a name="byte-c-reference"></a><span data-ttu-id="33fe6-102">byte (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="33fe6-102">byte (C# Reference)</span></span>

<span data-ttu-id="33fe6-103">`byte` Wskazuje, że integralny typ, który przechowuje wartości, jak wskazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="33fe6-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="33fe6-104">Typ</span><span class="sxs-lookup"><span data-stu-id="33fe6-104">Type</span></span>|<span data-ttu-id="33fe6-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="33fe6-105">Range</span></span>|<span data-ttu-id="33fe6-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="33fe6-106">Size</span></span>|<span data-ttu-id="33fe6-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="33fe6-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="33fe6-108">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="33fe6-108">0 to 255</span></span>|<span data-ttu-id="33fe6-109">Liczba całkowita bez znaku 8-bitowa</span><span class="sxs-lookup"><span data-stu-id="33fe6-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="33fe6-110">Literały</span><span class="sxs-lookup"><span data-stu-id="33fe6-110">Literals</span></span>  

 <span data-ttu-id="33fe6-111">Można zadeklarować i zainicjować `byte` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="33fe6-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="33fe6-112">Jeśli literał liczby całkowitej jest poza zakresem `byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="33fe6-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="33fe6-113">W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `byte` wartości.</span><span class="sxs-lookup"><span data-stu-id="33fe6-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> <span data-ttu-id="33fe6-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="33fe6-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="33fe6-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="33fe6-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="33fe6-116">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="33fe6-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="33fe6-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="33fe6-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="33fe6-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="33fe6-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="33fe6-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="33fe6-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="33fe6-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="33fe6-120">Some examples are shown below.</span></span>

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a><span data-ttu-id="33fe6-121">Konwersje</span><span class="sxs-lookup"><span data-stu-id="33fe6-121">Conversions</span></span>  
 <span data-ttu-id="33fe6-122">Jest wstępnie zdefiniowanych niejawna konwersja z `byte` do [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="33fe6-122">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="33fe6-123">Nie można niejawnie przekonwertować literału liczbowego rodzaje większy rozmiar magazynu na `byte`.</span><span class="sxs-lookup"><span data-stu-id="33fe6-123">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="33fe6-124">Aby uzyskać więcej informacji na temat rozmiarów pamięci masowej typów całkowitych, zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="33fe6-124">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="33fe6-125">Należy wziąć pod uwagę, na przykład, następujące dwa `byte` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="33fe6-125">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="33fe6-126">Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="33fe6-126">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="33fe6-127">Aby rozwiązać ten problem, należy użyć rzutowania:</span><span class="sxs-lookup"><span data-stu-id="33fe6-127">To fix this problem, use a cast:</span></span>  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="33fe6-128">Możliwe jest jednak zastosować następujące instrukcje, w którym Zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="33fe6-128">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="33fe6-129">Ponadto istnieje niejawna konwersja z typów zmiennoprzecinkowych `byte`.</span><span class="sxs-lookup"><span data-stu-id="33fe6-129">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="33fe6-130">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="33fe6-130">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="33fe6-131">Podczas wywoływania metody przeciążonej, należy użyć rzutowania.</span><span class="sxs-lookup"><span data-stu-id="33fe6-131">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="33fe6-132">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `byte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="33fe6-132">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="33fe6-133">Za pomocą `byte` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="33fe6-133">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="33fe6-134">Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="33fe6-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="33fe6-135">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="33fe6-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="33fe6-136">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33fe6-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33fe6-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33fe6-137">See Also</span></span>  

- <xref:System.Byte>  
- [<span data-ttu-id="33fe6-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33fe6-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="33fe6-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33fe6-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="33fe6-140">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="33fe6-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="33fe6-141">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="33fe6-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="33fe6-142">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="33fe6-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="33fe6-143">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="33fe6-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="33fe6-144">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="33fe6-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
