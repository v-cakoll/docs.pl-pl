---
title: "ushort (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83fa657303e8392997b04b7d80cdbcdbf39de887
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-c-reference"></a>ushort (odwołanie w C#)

`ushort` — Słowo kluczowe wskazuje typ całkowite danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 do 65 535.|Liczba całkowita bez znaku 16-bitowych|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  

Można zadeklarować i zainicjuj `ushort` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne. Jeśli liczba całkowita literału jest poza zakresem `ushort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `ushort` wartości.    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>Rozpoznanie przeciążenia kompilatora
  
 Rzutowanie musi być używany podczas wywoływania metody przeciążone. Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `ushort` i [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 Przy użyciu `ushort` rzutowania gwarantuje, że poprawne typu jest nazywana, na przykład:  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `ushort` do [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [liczb zmiennoprzecinkowych ](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [bajtów](../../../csharp/language-reference/keywords/byte.md) lub [char](../../../csharp/language-reference/keywords/char.md) do `ushort`. W przeciwnym razie rzutowanie musi posłużyć do wykonania konwersji jawnej. Należy wziąć pod uwagę, na przykład następujące dwa `ushort` zmienne `x` i `y`:  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 Następująca instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Aby rozwiązać ten problem, należy użyć rzutowanie:  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 Możliwe jest jednak należy zastosować następujące instrukcje, gdzie zmienna docelowa ma ten sam rozmiar magazynu lub większy rozmiar magazynu:  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `ushort`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.UInt16>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
