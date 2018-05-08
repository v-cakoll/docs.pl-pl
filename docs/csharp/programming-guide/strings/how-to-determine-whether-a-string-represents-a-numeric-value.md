---
title: 'Porady: określanie, czy ciąg reprezentuje wartość numeryczną (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: f1e5efca7fb3088064b3f252675b8cae965717f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 Liczbowe pierwotne typy również wdrożenie `Parse` statycznej metody, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse` jest zazwyczaj bardziej wydajne, ponieważ właśnie zwraca wartość FAŁSZ, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze używaj `TryParse` lub `Parse` metod do sprawdzania poprawności danych wejściowych użytkownika z formanty, takie jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: konwertowanie tablicy typu Byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [Instrukcje: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [Instrukcje: konwertowanie ciągów szestnastkowych na typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)  
 [Formatowanie typów](../../../standard/base-types/formatting-types.md)
