---
title: Jak przekonwertować ciąg na liczbę - Przewodnik programowania C#
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 54a4562a5cc493fc287bdf2f6bcf9723557f2a05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157042"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Jak przekonwertować ciąg na liczbę (Przewodnik programowania C#)

[Ciąg](../../language-reference/builtin-types/reference-types.md) można przekonwertować na liczbę, wywołując `Parse` lub `TryParse` metody znalezione`int`na `long` `double`różnych typach liczbowych ( , <xref:System.Convert?displayProperty=nameWithType> , , itp.) lub za pomocą metod w klasie.  
  
 Jeśli masz ciąg, jest nieco bardziej wydajne i `TryParse` proste do [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)wywołania `Parse` metody (na [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)przykład) lub metody (na przykład).  Korzystanie <xref:System.Convert> z metody jest bardziej przydatne <xref:System.IConvertible>dla obiektów ogólnych, które implementują .  
  
 Można użyć `Parse` `TryParse` lub metody na typ liczbowy, który oczekujesz ciąg zawiera, takich jak <xref:System.Int32?displayProperty=nameWithType> typ.  Metoda <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> używa <xref:System.Int32.Parse%2A> wewnętrznie.  Metoda `Parse` zwraca przekonwertowaną liczbę; `TryParse` metoda zwraca <xref:System.Boolean> wartość, która wskazuje, czy konwersja zakończyła się pomyślnie, i zwraca przekonwertowaną liczbę w [ `out` parametrze](../../language-reference/keywords/out.md). Jeśli ciąg nie jest w `Parse` prawidłowym formacie, `TryParse` zgłasza `false`wyjątek, podczas gdy zwraca . Podczas wywoływania `Parse` metody, należy zawsze używać <xref:System.FormatException> obsługi wyjątków do połowu w przypadku, gdy operacja analizy nie powiedzie się.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Wywoływanie metod Parse i TryParse

Metody `Parse` `TryParse` i ignorują biały znak na początku i na końcu ciągu, ale wszystkie inne znaki`int`muszą `long` `ulong`być `float` `decimal`znakami, które tworzą odpowiedni typ numeryczny ( , , , , itp.).  Każdy biały znak w ciągu, który tworzy liczbę powoduje błąd.  Na przykład można `decimal.TryParse` użyć do przeanalizowania "10", "10.3" lub " 10 ", ale nie można użyć tej metody do przeanalizowania 10 z "10X", "1 0" (uwaga`float.TryParse` osadzone miejsce), "10.3" (uwaga osadzone miejsce), "10e1" ( działa tutaj) i tak dalej. Ponadto ciąg, którego wartość `null` <xref:System.String.Empty?displayProperty=nameWithType> jest lub nie można pomyślnie przeanalizować. Można sprawdzić, czy ciąg zerowy lub pusty przed podjęciem <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> próby przeanalizowania go przez wywołanie metody.

W poniższym przykładzie przedstawiono zarówno `Parse` pomyślne, jak i nieudane wywołania i `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

W poniższym przykładzie przedstawiono podejście do analizowania ciągu, który ma zawierać wiodące znaki liczbowe (w tym znaki szesnastkowe) i końcowe znaki nieliczbowe. Przypisuje prawidłowe znaki od początku ciągu do nowego ciągu <xref:System.Int32.TryParse%2A> przed wywołaniem metody. Ponieważ ciągi do przeanalizowania zawierają niewielką liczbę znaków, <xref:System.String.Concat%2A?displayProperty=nameWithType> przykład wywołuje metodę przypisywania prawidłowych znaków do nowego ciągu. Dla większego ciągu <xref:System.Text.StringBuilder> zamiast tego można użyć klasy.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Wywoływanie metody konwertuj

W poniższej tabeli wymieniono <xref:System.Convert> niektóre metody z klasy, za pomocą których można przekonwertować ciąg na liczbę.  
  
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
  
 Poniższy przykład wywołuje <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodę do konwersji ciągu wejściowego do [int](../../language-reference/builtin-types/integral-numeric-types.md). W przykładzie przechwytuje dwa najczęstsze wyjątki, które <xref:System.FormatException> <xref:System.OverflowException>mogą być generowane przez tę metodę i . Jeśli wynikowy numer może być zwiększany <xref:System.Int32.MaxValue?displayProperty=nameWithType>bez przekraczania, przykład dodaje 1 do wyniku i wyświetla dane wyjściowe.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Typy](./index.md)
- [Określanie, czy ciąg reprezentuje wartość numeryczną](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Przykład: Narzędzie formatowania formularzy WinForms w ustonach .NET Core (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
