---
title: 'Porady: uzupełnianie liczby zerami prowadzącymi'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131973"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Porady: uzupełnianie liczby zerami prowadzącymi

Można dodać Wiodące zera do liczby całkowitej przy użyciu [standardowego ciągu formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" ze specyfikatorem dokładności. Można dodać Wiodące zera do liczb całkowitych i zmiennoprzecinkowych przy użyciu [niestandardowego ciągu formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md). W tym artykule pokazano, jak używać obu metod do uzupełniania liczby wiodących zer.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Aby uzupełnić liczbę całkowitą wiodącymi zerami do określonej długości

1. Określ minimalną liczbę cyfr, jaka ma być wyświetlana wartość całkowita. Dołącz wszystkie znaki wiodące w tej liczbie.

1. Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.

    - Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, wywołaj metodę `ToString(String)` i przekaż ciąg "D*n*" jako wartość parametru `format`, gdzie *n* reprezentuje minimalną długość ciągu.

    - Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, wywołaj metodę `ToString(String)` i przekaż ciąg "X*n*" jako wartość parametru formatu, gdzie *n* reprezentuje minimalną długość ciągu.

Można również użyć ciągu w formacie interpolowanym w obu [C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)lub wywołać metodę, taką jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, która używa [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).

Poniższy przykład formatuje kilka wartości całkowitych wiodących zer, tak aby łączna długość sformatowanej liczby była co najmniej 8 znaków.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić liczbę całkowitą z określoną liczbą zer wiodących

1. Określ, ile wiodących zer ma być wyświetlana wartość całkowita.

1. Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.

    - Formatowanie go jako wartości dziesiętnej wymaga użycia specyfikatora formatu standardowego "D".

    - Formatowanie go jako wartości szesnastkowej wymaga użycia specyfikatora formatu standardowego "X".

1. Ustal długość nieuzupełnionego ciągu liczbowego, wywołując metodę `ToString("D").Length` lub `ToString("X").Length` wartości całkowitej.

1. Dodaj liczbę zer wiodących, które mają być uwzględnione w ciągu sformatowanym do długości nieuzupełnionego ciągu liczbowego. Dodanie liczby zer wiodących określa łączną długość uzupełnionego ciągu.

1. Wywołaj metodę `ToString(String)` wartości całkowitej i przekaż ciąg "D*n*" dla ciągów dziesiętnych i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje łączną długość uzupełnionego ciągu. Można również użyć ciągu formatu "D*n*" lub "X*n*" w metodzie, która obsługuje formatowanie złożone.

Poniższy przykład ilustruje liczbę całkowitą z pięciu wiodących zer.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Aby uzupełnić wartość liczbową wiodącymi zerami do określonej długości

1. Określ liczbę cyfr po lewej stronie przecinka dziesiętnego, w ciągu którego ma zostać wystawiona liczba. Dołącz wszystkie zera wiodące w tej łącznej liczbie cyfr.

1. Zdefiniuj niestandardowy ciąg formatu liczbowego, który używa symbolu zastępczego zero "0" do reprezentowania minimalnej liczby zer.

1. Wywołaj metodę `ToString(String)` i przekaż ją do niestandardowym ciągiem formatu. Można również użyć niestandardowego ciągu formatu z interpolacją ciągu lub metodą, która obsługuje formatowanie złożone.

Poniższy przykład formatuje kilka wartości liczbowych z zerami wiodącymi. W związku z tym łączna długość sformatowanej liczby ma co najmniej osiem cyfr z lewej strony dziesiętnej.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić wartość numeryczną określoną liczbą zer wiodących

1. Określ, ile wiodących zer ma mieć wartość liczbową.

1. Określ liczbę cyfr po lewej stronie przecinka dziesiętnego w nieuzupełnionym ciągu liczbowym:

    1. Ustal, czy ciąg reprezentujący liczbę zawiera symbol separatora dziesiętnego.

    1. Jeśli zawiera symbol separatora dziesiętnego, należy określić liczbę znaków po lewej stronie przecinka dziesiętnego.

         —lub—

         Jeśli nie zawiera symbolu punktu dziesiętnego, ustal długość ciągu.

1. Utwórz niestandardowy ciąg formatujący, który używa:

    - Symbol zastępczy zero "0" dla każdego wiodącego zera, który ma być wyświetlany w ciągu.

    - Symbol zastępczy zero lub symbol zastępczy cyfry "#" reprezentujący każdą cyfrę w postaci ciągu domyślnego.

1. Podaj ciąg formatu niestandardowego jako parametr do metody `ToString(String)` lub do metody, która obsługuje formatowanie złożone.

W poniższym przykładzie przedstawiono dwa <xref:System.Double> wartości z pięcioma zerami wiodącymi.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Zobacz także

- [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
