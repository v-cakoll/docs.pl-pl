---
title: "byte (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords: byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 231a491914071b1d43b5a8938e677be531726e75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="byte-c-reference"></a>byte (odwołanie w C#)

`byte`Określa typ całkowity, który przechowuje wartości opisane w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 do 255.|Liczba całkowita bez znaku 8-bitowych|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  

 Można zadeklarować i zainicjuj `byte` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne. Jeśli liczba całkowita literału jest poza zakresem `byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `byte` wartości.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `byte` do [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długa ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nie można niejawnie przekonwertować-literal liczbowych typów większy rozmiar magazynu do `byte`. Aby uzyskać więcej informacji na magazyn o rozmiarze typów całkowitych zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md). Należy wziąć pod uwagę, na przykład następujące dwa `byte` zmienne `x` i `y`:  
  
```  
byte x = 10, y = 20;  
```  
  
 Następująca instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Aby rozwiązać ten problem, należy użyć rzutowanie:  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Możliwe jest, użyj następujących instrukcji, gdzie zmienna docelowa ma ten sam rozmiar magazynu lub większy rozmiar magazynu:  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ponadto nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `byte`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Podczas wywoływania metody przeciążane, muszą być używane rzutowanie. Należy wziąć pod uwagę, na przykład następujące przeciążone metody, które używają `byte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Przy użyciu `byte` rzutowania gwarantuje, że poprawne typu jest nazywana, na przykład:  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Informacje w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na niejawna konwersja liczbowa reguły, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Byte>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
