---
title: "Porady: określanie, czy ciąg reprezentuje wartość numeryczną (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 850c5d0e7a246b2319ba841dae9884c90390d38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Porady: określanie, czy ciąg reprezentuje wartość numeryczną (Przewodnik programowania w języku C#)
Aby określić, czy ciąg jest prawidłowy reprezentację określonego typu liczbowego, użyj statycznych `TryParse` metodę, która jest zaimplementowana przez wszystkie pierwotne typy liczbowe, a także typy takich jak <xref:System.DateTime> i <xref:System.Net.IPAddress>. Poniższy przykład przedstawia sposób określania, czy jest prawidłową "108" warunki [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaków nienumerycznych lub wartość liczbowa jest za duża albo za mała dla tego typu określono, `TryParse` zwraca wartość false i Ustawia parametr out na zero. W przeciwnym razie zwraca wartość true i Ustawia parametr out liczbowa wartość ciągu.  
  
> [!NOTE]
>  Ciąg może zawierać tylko cyfry i nadal nie jest prawidłowa dla typu którego `TryParse` używanej metody. Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest on prawidłowy dla `int`. "98.6" nie jest prawidłową wartością dla `int` jest prawidłowy, ale `decimal`.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `TryParse` z reprezentacji ciągu `long`, `byte`, i `decimal` wartości.  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Liczbowe pierwotne typy również wdrożenie `Parse` statycznej metody, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse`jest zazwyczaj bardziej wydajne, ponieważ właśnie zwraca wartość FAŁSZ, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze używaj `TryParse` lub `Parse` metod do sprawdzania poprawności danych wejściowych użytkownika z formanty, takie jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [Porady: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [Porady: Konwertowanie ciągów szesnastkowych, które typy numeryczne](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)  
 [Formatowanie tekstu](../../../standard/base-types/formatting-types.md)
