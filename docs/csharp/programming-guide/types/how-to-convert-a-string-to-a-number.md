---
title: 'Instrukcje: Konwertuj ciąg na Przewodnik C# programowania w liczbie'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 8b2e6fdc6248ca65213ea83942d792f983bd3b3b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588391"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Instrukcje: Konwertuj ciąg na liczbę (C# Przewodnik programowania)

Można przekonwertować [ciąg](../../language-reference/keywords/string.md) na liczbę poprzez `Parse` wywołanie metody lub `TryParse` w różnych typach liczbowych (`int`, `long` `double`, itp.) lub przy użyciu metod w <xref:System.Convert?displayProperty=nameWithType> klasie.  
  
 Jeśli masz ciąg, jest `TryParse` nieco bardziej wydajny i nieskomplikowany do wywołania metody (na [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)przykład) lub `Parse` metody (na przykład [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).  Użycie metody jest bardziej przydatne w przypadku ogólnych obiektów, które implementują <xref:System.IConvertible>. <xref:System.Convert>  
  
 Można użyć `Parse` lub `TryParse` metod dla typu liczbowego, który powinien <xref:System.Int32?displayProperty=nameWithType> zawierać ciąg, na przykład typ.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> Metoda używa<xref:System.Int32.Parse%2A> wewnętrznie.  Metoda zwraca przekonwertowaną liczbę `TryParse` ; Metoda zwraca <xref:System.Boolean> wartość wskazującą, czy konwersja powiodła się [ `out` ](../../language-reference/keywords/out.md), i zwraca przekonwertowaną liczbę w parametrze. `Parse` Jeśli ciąg jest w nieprawidłowym formacie, `Parse` zgłasza wyjątek, a `TryParse` zwraca [wartość false](../../language-reference/keywords/false-literal.md). Podczas wywoływania `Parse` metody należy zawsze używać obsługi wyjątków, aby <xref:System.FormatException> przechwytywać w przypadku niepowodzenia operacji analizy.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Wywoływanie metod Parse i TryParse

`ulong``int` `long`Metody i ignorująodstępnapoczątkuinakońcuciągu,alewszystkieinneznakimusząbyćznakami,któretworząodpowiednitypliczbowy(,,,`TryParse` `Parse` `float` ,`decimal`itp.).  Dowolny biały znak w ciągu, który tworzy liczbę, powoduje błąd.  Na przykład można użyć `decimal.TryParse` , aby przeanalizować wartość "10", "10,3" lub "10", ale nie można użyć tej metody do przeanalizowania 10 z "10X", "1 0" (zanotować przestrzeń osadzoną), "10 .3" (zanotuj przestrzeń osadzoną), "10e1" (`float.TryParse` działa tutaj) i tak dalej. Ponadto ciąg, którego wartość jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType> nie można przeanalizować pomyślnie. Przed próbą przeanalizowania można sprawdzić, czy ciąg ma wartość null lub być pusty, <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> wywołując metodę. 

W poniższym przykładzie pokazano zarówno udane, jak i nieudane wywołania `Parse` do `TryParse`i.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Poniższy przykład ilustruje jedno podejście do analizy ciągu, który powinien zawierać wiodące znaki numeryczne (w tym znaki szesnastkowe) i końcowe znaki niebędące numeryczne. Przypisuje prawidłowe znaki od początku ciągu do nowego ciągu przed wywołaniem <xref:System.Int32.TryParse%2A> metody. Ponieważ ciągi, które mają być analizowane, zawierają niewielką liczbę znaków, przykład wywołuje metodę, <xref:System.String.Concat%2A?displayProperty=nameWithType> aby przypisać prawidłowe znaki do nowego ciągu. W przypadku większego ciągu <xref:System.Text.StringBuilder> można użyć klasy. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Wywoływanie metod konwersji

Poniższa tabela zawiera listę metod z <xref:System.Convert> klasy, których można użyć do przekonwertowania ciągu na liczbę.  
  
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
  
 Poniższy przykład wywołuje metodę, <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> aby przekonwertować ciąg wejściowy na [int](../../language-reference/builtin-types/integral-numeric-types.md). Przykład przechwytuje dwa najczęstsze wyjątki, które mogą być zgłaszane przez tę metodę, <xref:System.FormatException> i <xref:System.OverflowException>. Jeśli wynikowy numer można zwiększyć bez przekroczenia <xref:System.Int32.MaxValue?displayProperty=nameWithType>, przykład dodaje 1 do wyniku i wyświetla dane wyjściowe.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Typy](./index.md)
- [Instrukcje: Określanie, czy ciąg reprezentuje wartość liczbową](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Narzędzie do formatowania .NET Framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
