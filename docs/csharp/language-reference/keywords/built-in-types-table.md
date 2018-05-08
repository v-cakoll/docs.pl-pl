---
title: Tabela typów wbudowanych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 7407d18c58dd3d12337c6845627d83f02eaf7fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="built-in-types-table-c-reference"></a>Tabela typów wbudowanych (odwołanie w C#)
W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.  
  
|Typ języka C#|Typ architektury .NET framework|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są określane jako typów prostych.  
  
 Słowa kluczowe typu C# i ich aliasy są wymienne. Na przykład można zadeklarować zmiennej całkowitą przy użyciu jednej z następujących deklaracji:  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Aby wyświetlić rzeczywisty typ dla dowolnego typu C#, należy użyć metody systemu `GetType()`. Na przykład następująca instrukcja wyświetla alias systemu, który reprezentuje typ `myVariable`:  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Można również użyć [typeof](../../../csharp/language-reference/keywords/typeof.md) operatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
