---
title: sbyte (odwołanie w C#)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c3950e11e1a81cf7263e146705c351e3dd8a6e9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sbyte-c-reference"></a>sbyte (odwołanie w C#)

`sbyte` Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 do 127 znaków.|8-bitową liczbę całkowitą ze znakiem|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  

Można zadeklarować i zainicjuj `sbyte` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od 7.0 C#) literału do niego dane binarne. 

W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `sbyte` wartości.    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu.

Uruchamianie z C# w wersji 7.0, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

 Poniżej przedstawiono kilka przykładów.

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Jeśli liczba całkowita literału jest poza zakresem `sbyte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji. Jeśli literał całkowity nie sufiks, jego typ jest pierwsza z tych typów, w których jej wartość może być reprezentowany: [int](int.md), [uint](uint.md), [długi](long.md), [ulong](ulong.md). Oznacza to, że w tym przykładzie literałach numerycznych `0x9A` i `0b10011010` będą interpretowane jako 32-bitowych liczb całkowitych ze znakiem z wartością 156, którego rozmiar przekracza <xref:System.SByte.MaxValue?displayProperty=nameWithType>. W związku z tym jest potrzebny operatora rzutowania i przypisania musi występować w [niezaznaczone](unchecked.md) kontekstu. 

## <a name="compiler-overload-resolution"></a>Rozpoznanie przeciążenia kompilatora

 Rzutowanie musi być używany podczas wywoływania metody przeciążane. Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `sbyte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Przy użyciu `sbyte` rzutowania gwarantuje, że poprawne typu jest nazywana, na przykład:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `sbyte` do [krótki](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [długi](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne ](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nie można niejawnie przekonwertować nieliteralnego liczbowych typów większy rozmiar magazynu do `sbyte` (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych). Należy wziąć pod uwagę, na przykład następujące dwa `sbyte` zmienne `x` i `y`:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 Następująca instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](../../../csharp/language-reference/keywords/int.md) domyślnie.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Aby rozwiązać ten problem, należy rzutować wyrażenia, jak w poniższym przykładzie:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Możliwe jest jednak należy zastosować następujące instrukcje, gdzie zmienna docelowa ma ten sam rozmiar magazynu lub większy rozmiar magazynu:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `sbyte`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.SByte>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
