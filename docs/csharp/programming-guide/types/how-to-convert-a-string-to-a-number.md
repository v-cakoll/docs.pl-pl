---
title: 'Instrukcje: konwertowanie ciągu na Przewodnik C# programowania w liczbie'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: c39602afbece4faaf6599a5c76f5746defffe03a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417644"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Porady: konwertowanie ciągu na liczbę (Przewodnik programowania w języku C#)

Można przekonwertować [ciąg](../../language-reference/builtin-types/reference-types.md) na liczbę, wywołując metodę `Parse` lub `TryParse`, która znajduje się w różnych typach liczbowych (`int`, `long`, `double`itp.) lub przy użyciu metod w klasie <xref:System.Convert?displayProperty=nameWithType>.  
  
 Jeśli masz ciąg, jest nieco bardziej wydajny i nieskomplikowany, aby wywołać metodę `TryParse` (na przykład [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) lub metodę `Parse` (na przykład [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).  Użycie metody <xref:System.Convert> jest bardziej przydatne w przypadku ogólnych obiektów, które implementują <xref:System.IConvertible>.  
  
 Możesz użyć metod `Parse` lub `TryParse` w typie liczbowym, który powinien być ciągiem zawierającym, na przykład typem <xref:System.Int32?displayProperty=nameWithType>.  Metoda <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> używa <xref:System.Int32.Parse%2A> wewnętrznie.  Metoda `Parse` zwraca przekonwertowaną liczbę; Metoda `TryParse` zwraca wartość <xref:System.Boolean>, która wskazuje, czy konwersja powiodła się, i zwraca przekonwertowaną liczbę w [parametrze`out`](../../language-reference/keywords/out.md). Jeśli ciąg jest w nieprawidłowym formacie, `Parse` zgłasza wyjątek, a `TryParse` zwraca [wartość false](../../language-reference/keywords/false-literal.md). Podczas wywoływania metody `Parse` należy zawsze używać obsługi wyjątków, aby przechwytywać <xref:System.FormatException> w przypadku niepowodzenia operacji analizy.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Wywoływanie metod Parse i TryParse

Metody `Parse` i `TryParse` ignorują odstęp na początku i na końcu ciągu, ale wszystkie inne znaki muszą być znakami, które tworzą odpowiedni typ liczbowy (`int`, `long`, `ulong`, `float`, `decimal`itd.).  Dowolny biały znak w ciągu, który tworzy liczbę, powoduje błąd.  Na przykład można użyć `decimal.TryParse` do analizy "10", "10,3" lub "10", ale nie można użyć tej metody do przeanalizowania 10 z "10X", "1 0" (zanotuj osadzony obszar), "10 .3" (zanotuj przestrzeń osadzoną), "10e1" (`float.TryParse` działa tutaj) i tak dalej. Ponadto ciąg, którego wartość jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType> nie można przeanalizować pomyślnie. Przed próbą przeanalizowania można sprawdzić, czy ciąg ma wartość null lub być pusty, wywołując metodę <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>. 

W poniższym przykładzie pokazano zarówno udane, jak i nieudane wywołania do `Parse` i `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Poniższy przykład ilustruje jedno podejście do analizy ciągu, który powinien zawierać wiodące znaki numeryczne (w tym znaki szesnastkowe) i końcowe znaki niebędące numeryczne. Przypisuje prawidłowe znaki od początku ciągu do nowego ciągu przed wywołaniem metody <xref:System.Int32.TryParse%2A>. Ponieważ ciągi, które mają być analizowane, zawierają niewielką liczbę znaków, przykład wywołuje metodę <xref:System.String.Concat%2A?displayProperty=nameWithType>, aby przypisać prawidłowe znaki do nowego ciągu. W przypadku większego ciągu można użyć klasy <xref:System.Text.StringBuilder>. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Wywoływanie metod konwersji

W poniższej tabeli wymieniono niektóre metody z klasy <xref:System.Convert>, których można użyć do przekonwertowania ciągu na liczbę.  
  
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
  
 Poniższy przykład wywołuje metodę <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType>, aby przekonwertować ciąg wejściowy na [int](../../language-reference/builtin-types/integral-numeric-types.md). Przykład przechwytuje dwa najczęstsze wyjątki, które mogą być zgłaszane przez tę metodę, <xref:System.FormatException> i <xref:System.OverflowException>. Jeśli wynikowa liczba może być zwiększana bez przekroczenia <xref:System.Int32.MaxValue?displayProperty=nameWithType>, przykład dodaje 1 do wyniku i wyświetla dane wyjściowe.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy](./index.md)
- [Instrukcje: określanie, czy ciąg reprezentuje wartość liczbową](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Przykład: Narzędzie do formatowania narzędzi systemu .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
