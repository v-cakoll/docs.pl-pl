---
title: "Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)
Możesz przekonwertować [ciąg](../../../csharp/language-reference/keywords/string.md) na liczbę za pomocą metod w <xref:System.Convert> klasy lub przy użyciu `TryParse` znaleziono metody na różne typy liczbowe (int, long, float, itp.).  
  
 Jeśli masz ciąg jest nieco bardziej wydajne i bezpośrednie wywoływanie `TryParse` — metoda (na przykład `int.TryParse("11")`).  Przy użyciu `Convert` metoda jest bardziej użyteczna w przypadku ogólnych obiekty, które implementują <xref:System.IConvertible>.  
  
 Można użyć `Parse` lub `TryParse` metody na typ liczbowy oczekiwany ciąg zawiera, takich jak <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Używa metody <xref:System.Int32.Parse%2A> wewnętrznie.  Jeśli ciąg nie jest prawidłowym formatem `Parse` zgłasza wyjątek `TryParse` zwraca [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Przykład  
 `Parse` i `TryParse` metody Ignoruj odstępy na początku i na końcu ciągu, ale wszystkie inne znaki muszą być znaki, które tworzą odpowiedni typ liczbowy (int, long, ulong, float, decimal, itp.).  Żadnych spacji w ciągu znaków, które tworzą numer spowodować wystąpienie błędu.  Na przykład można użyć `decimal.TryParse` można przeanalizować "10", "10.3", "10", ale nie można użyć tej metody można przeanalizować 10 "10 X", "1 0" (Uwaga miejsca), "10. 3" (Uwaga miejsca), "10e1" (`float.TryParse` działa w tym miejscu) i tak dalej.  
  
 Poniższe przykłady pokazują zarówno zakończone powodzeniem i niepowodzeniem wywołania `Parse` i `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższej tabeli przedstawiono niektóre metody z <xref:System.Convert> klasy, który można użyć.  
  
|Typ liczbowy|Metoda|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 W tym przykładzie wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metody można skonwertować danych wejściowych [ciąg](../../../csharp/language-reference/keywords/string.md) do [int](../../../csharp/language-reference/keywords/int.md) . Dwa najczęściej wyjątki, które mogą być generowane przez tę metodę przechwytuje kod <xref:System.FormatException> i <xref:System.OverflowException>. Jeśli liczbę można zwiększyć bez przepełnienia lokalizacji magazynu liczb całkowitych, program dodaje do wyniku 1 i drukuje dane wyjściowe.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Porady: Określanie, czy ciąg reprezentuje wartość numeryczną](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [Narzędzie formatowania programu .NET framework 4](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
