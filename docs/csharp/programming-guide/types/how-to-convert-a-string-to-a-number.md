---
title: 'Instrukcje: Konwertowanie ciągu na liczbę — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: a75d6dd5fdb74ca3cb6fe28db7415aeb478e2237
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243221"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Instrukcje: Konwertowanie ciągu na liczbę (C# Programming Guide)
Można przekonwertować [ciąg](../../../csharp/language-reference/keywords/string.md) do liczby przy użyciu metod w <xref:System.Convert> klasy lub przy użyciu `TryParse` znaleźć metodę na różne typy liczbowe (int, long, float, itp.).  
  
 Jeśli masz ciąg, jest nieco bardziej efektywne i prostego do wywołania `TryParse` — metoda (na przykład [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)).  Za pomocą <xref:System.Convert> metoda jest bardziej użyteczna w przypadku ogólnych obiekty, które implementują <xref:System.IConvertible>.  
  
 Możesz użyć `Parse` lub `TryParse` metody na typ liczbowy, oczekujesz, że zawiera ciąg, taki jak <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Metoda używa <xref:System.Int32.Parse%2A> wewnętrznie.  Jeśli ciąg nie jest w prawidłowym formacie `Parse` zgłasza wyjątek `TryParse` zwraca [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Przykład  
 `Parse` i `TryParse` metody Ignoruj biały znak na początku i na końcu ciągu, ale wszystkie inne znaki musi być znaki, które tworzą odpowiedni typ liczbowy (int, long, ulong, float, dziesiętny, itp.).  Dowolny biały obszar w ciągu znaków, które tworzą numer powodują wystąpienie błędu.  Na przykład, można użyć `decimal.TryParse` można przeanalizować "10", "10.3", "10", ale możesz nie można użyć tej metody można przeanalizować 10 z "10 X", "1 0" (Uwaga miejsca), "10. 3" (Uwaga miejsca), "10e1" (`float.TryParse` działające w tym miejscu), i tak dalej.  
  
 W przykładach pokazano zarówno pomyślnie, jak i nieudane wywołania `Parse` i `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższej tabeli wymieniono niektóre metody z <xref:System.Convert> klasę, która umożliwia.  
  
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
  
 Ten przykład wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodę, aby konwertować dane wejściowe [ciąg](../../../csharp/language-reference/keywords/string.md) do [int](../../../csharp/language-reference/keywords/int.md) . Ten kod przechwytuje dwa najpopularniejsze wyjątki, które mogą zostać wyrzucone przez tę metodę <xref:System.FormatException> i <xref:System.OverflowException>. Jeśli liczbę można zwiększyć bez przepełnienia lokalizacji magazynu liczb całkowitych, program dodaje do wyniku 1 i drukuje dane wyjściowe.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Typy](../../../csharp/programming-guide/types/index.md)  
- [Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [Narzędzie formatowania programu .NET framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
