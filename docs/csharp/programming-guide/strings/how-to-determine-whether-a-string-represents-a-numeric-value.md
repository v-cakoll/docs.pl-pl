---
title: 'Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: dcba1651c736b58b2c95bac21f086c46417629df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980753"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną (C# Programming Guide)
Aby ustalić, czy ciąg jest prawidłową reprezentacją określonego typu liczbowego, używa się statycznej `TryParse` metodę, która jest zaimplementowana przez wszystkich pierwotnych typów liczbowych, a także typy takie jak <xref:System.DateTime> i <xref:System.Net.IPAddress>. Poniższy przykład pokazuje, jak ustalić, czy jest nieprawidłowy "108" warunki [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Jeśli ciąg zawiera znaki nienumeryczne lub wartość liczbowa jest zbyt duży lub za mały dla tego typu został określony, `TryParse` zwraca wartość false, a także Ustawia parametr out zero. W przeciwnym razie zwraca wartość true i Ustawia parametr out liczbową wartość ciągu.  
  
> [!NOTE]
>  Ciąg może zawierać tylko znaki numeryczne i nadal nie jest prawidłowa dla typu którego `TryParse` używanej metody. Na przykład "256" nie jest prawidłową wartością dla `byte` , ale jest on prawidłowy dla `int`. "98.6" nie jest prawidłową wartością dla `int` , ale jest on prawidłowy `decimal`.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób użycia `TryParse` za pomocą ciągów reprezentujących `long`, `byte`, i `decimal` wartości.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Pierwotny liczbowe również typy implementują `Parse` statyczną metodę, która zgłasza wyjątek, jeśli ciąg nie jest prawidłową liczbą. `TryParse` jest zazwyczaj bardziej efektywne, ponieważ po prostu zwraca wartość false, jeśli liczba jest nieprawidłowa.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze używaj `TryParse` lub `Parse` metod, aby sprawdzić dane wejściowe użytkownika z formantów takich jak pola tekstowe i pola kombi.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [Instrukcje: Konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [Instrukcje: Konwertowanie ciągów szesnastkowych, które typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analizowanie ciągów liczbowych](../../../standard/base-types/parsing-numeric.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
