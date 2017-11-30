---
title: "Tabela typów wbudowanych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a>Tabela typów wbudowanych (odwołanie w C#)
W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.  
  
|Typ języka C#|Typ architektury .NET framework|  
|--------------|-------------------------|  
|[wartość logiczna](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[bajtów](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte —](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[podwójne](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[długa](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[obiekt](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[krótki](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[ciąg](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
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
 [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
