---
title: 'Instrukcje: Konwertowanie ciągu na liczbę — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 1ff8db25fd76be6eb77355322d497d61096400aa
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219337"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Instrukcje: Konwertowanie ciągu na liczbę (C# Programming Guide)

Można przekonwertować [ciąg](../../../csharp/language-reference/keywords/string.md) na liczbę, przez wywołanie metody `Parse` lub `TryParse` znaleźć metodę na różne typy liczbowe (`int`, `long`, `double`, itp.), lub za pomocą metod w <xref:System.Convert?displayProperty=nameWithType>klasy.  
  
 Jeśli masz ciąg, jest nieco bardziej efektywne i prostego do wywołania `TryParse` — metoda (na przykład [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)) lub `Parse` — metoda (na przykład [ `var number = int.Parse("11")` ](xref:System.Int32.Parse%2A)).  Za pomocą <xref:System.Convert> metoda jest bardziej użyteczna w przypadku ogólnych obiekty, które implementują <xref:System.IConvertible>.  
  
 Możesz użyć `Parse` lub `TryParse` metody na typ liczbowy, oczekujesz, że zawiera ciąg, taki jak <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> Metoda używa <xref:System.Int32.Parse%2A> wewnętrznie.  `Parse` Metoda zwraca numer przekonwertowany; `TryParse` metoda zwraca <xref:System.Boolean> wartość wskazującą, czy konwersja powiodła się i zwraca numer przekonwertowany w [ `out` parametru](../../../csharp/language-reference/keywords/out.md). Jeśli ciąg nie jest w prawidłowym formacie `Parse` zgłasza wyjątek `TryParse` zwraca [false](../../../csharp/language-reference/keywords/false.md). Podczas wywoływania `Parse` metody, należy zawsze używać obsługi wyjątków do przechwytywania <xref:System.FormatException> w przypadku, gdy operacja analizy nie powiedzie się.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Wywoływanie metod analizowania i TryParse

`Parse` i `TryParse` metody Ignoruj biały znak na początku i na końcu ciągu, ale wszystkie inne znaki musi być znaki, które tworzą odpowiedni typ liczbowy (`int`, `long`, `ulong`, `float`, `decimal`itp.).  Dowolny biały obszar w ciągu, który wchodzi w skład numer spowoduje wystąpienie błędu.  Na przykład, można użyć `decimal.TryParse` można przeanalizować "10", "10.3" lub "10", ale możesz nie można użyć tej metody można przeanalizować 10 z "10 X", "1 0" (Uwaga osadzona spacja), "10. 3" (Uwaga osadzona spacja), "10e1" (`float.TryParse` działające w tym miejscu), i tak dalej. Ponadto, ciąg, którego wartością jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType> zakończy się niepowodzeniem, można pomyślnie przeanalizować. Możesz sprawdzić wartość null lub pusty ciąg przed podjęciem próby go przeanalizować, wywołując <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody. 

W poniższym przykładzie pokazano zarówno pomyślnie, jak i nieudane wywołania `Parse` i `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

W poniższym przykładzie pokazano podejście do analizowania parametrów, który powinien zawierać wiodące znaki numeryczne (takie jak znaki szesnastkowe) i końcowe znaki nienumeryczne. Przypisuje prawidłowych znaków od początku ciągu do nowego ciągu przed wywołaniem <xref:System.Int32.TryParse%2A> metody. Ponieważ ciągi, które można przeanalizować zawierają niewielką liczbę znaków, przykład wywołuje <xref:System.String.Concat%2A?displayProperty=nameWithType> metodę, aby przypisać prawidłowe znaki do nowego ciągu. W przypadku większych ciągu <xref:System.Text.StringBuilder> klasa może być używana zamiast tego. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Wywoływanie metody konwersji

W poniższej tabeli wymieniono niektóre metody z <xref:System.Convert> klasę, która służy do przekonwertowania ciągu na liczbę.  
  
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
  
 Poniższy przykład wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodę, aby przekonwertować ciąg wejściowy [int](../../../csharp/language-reference/keywords/int.md). Przykład wyłapuje dwa najbardziej powszechne wyjątki, które mogą zostać wyrzucone przez tę metodę <xref:System.FormatException> i <xref:System.OverflowException>. Jeśli wynikowe liczbę można zwiększyć bez przekraczania <xref:System.Int32.MaxValue?displayProperty=nameWithType>, przykład dodaje 1 do wyniku i wyświetla dane wyjściowe.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy](../../../csharp/programming-guide/types/index.md)
- [Instrukcje: Określanie, czy ciąg reprezentuje wartość numeryczną](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [.NET Framework 4 Formatting Utility](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
