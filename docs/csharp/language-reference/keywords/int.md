---
title: "int (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7acb8bb482ebf8f5c2b508e7cfd45b5b64aae3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="int-c-reference"></a>int (odwołanie w C#)

`int`Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|Wartość domyślna|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|-2 147 483 2 147 483 648 do 647|32-bitowa liczba całkowita|<xref:System.Int32?displayProperty=nameWithType>|0|  
  
## <a name="literals"></a>Literały  
 
Można zadeklarować i zainicjuj `int` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne.  Jeśli liczba całkowita literału jest poza zakresem `int` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji. 

W poniższym przykładzie liczb całkowitych równa 90,946, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `int` wartości.  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu. 

Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 Literały całkowite mogą również obejmować sufiks, który wskazuje typ, nie ma żadnych sufiks, który wskazuje, ale `int` typu. Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość: 

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [długa](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
 
W tych przykładach 90946 literału jest typu `int`.
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `int` do [długi](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md). Na przykład:  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) Aby `int`. Na przykład następująca instrukcja przypisania spowoduje błąd kompilacji bez rzutowanie:  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `int`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Aby uzyskać więcej informacji w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Int32>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
