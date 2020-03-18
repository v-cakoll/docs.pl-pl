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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131973"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Porady: uzupełnianie liczby zerami prowadzącymi

Zera wiodące można dodawać do liczby całkowitej za pomocą [standardowego ciągu formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" z precyzyjnym specyfikatorem. Można dodać zera wiodące zarówno do liczb całkowitych, jak i zmiennoprzecinkowych, używając [niestandardowego ciągu formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md). W tym artykule pokazano, jak używać obu metod do pad liczba z zer wiodących.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Aby podkładki liczby całkowitej z zerami wiodącymi do określonej długości

1. Określ minimalną liczbę cyfr, która ma być wyświetlana wartość całkowita. W tym numerze uwzględnij wszystkie cyfry wiodące.

1. Określ, czy liczba całkowita ma być wyświetlana jako wartość dziesiętna, czy szesnastkowa.

    - Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, należy wywołać `ToString(String)` jej metodę i przekazać ciąg "D*n"* jako wartość `format` parametru, gdzie *n* reprezentuje minimalną długość ciągu.

    - Aby wyświetlić liczbę całkowitą jako wartość szesnastkowa, należy wywołać jej `ToString(String)` metodę i przekazać ciąg "X*n"* jako wartość parametru formatu, gdzie *n* reprezentuje minimalną długość ciągu.

Można również użyć ciągu formatu w interpolowanym ciągu w [językach C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) <xref:System.String.Format%2A?displayProperty=nameWithType> Basic <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>lub można wywołać metodę, taką jak lub , która używa [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).

Poniższy przykład formatuje kilka wartości całkowitych z zerami wiodącymi, dzięki czemu całkowita długość sformatowanej liczby wynosi co najmniej osiem znaków.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Aby podkładki liczby całkowitej z określoną liczbę zer wiodących

1. Określ, ile zer wiodących ma być wyświetlana wartość całkowita.

1. Określ, czy liczba całkowita ma być wyświetlana jako wartość dziesiętna, czy szesnastkowa.

    - Formatowanie go jako wartości dziesiętnej wymaga użycia specyfikatora formatu standardowego "D".

    - Formatowanie go jako wartości szesnastkowej wymaga użycia specyfikatora formatu standardowego "X".

1. Określ długość niezalanego ciągu liczbowego, wywołując wartość `ToString("D").Length` lub `ToString("X").Length` metodę liczby całkowitej.

1. Dodaj liczbę zer wiodących, które mają zostać uwzględnione w sformatowanym ciągu, do długości niezawiązanego ciągu liczbowego. Dodanie liczby zer wiodących definiuje całkowitą długość wyściełanego ciągu.

1. Wywołaj `ToString(String)` metodę wartości całkowitej i przekaż ciąg "D*n"* dla ciągów dziesiętnych i "X*n"* dla ciągów szesnastkowych, gdzie *n* reprezentuje całkowitą długość wyściełanego ciągu. Można również użyć ciągu formatu "D*n"* lub "X*n"* w metodzie obsługującej formatowanie złożone.

Poniższy przykład klocki wartość całkowitą z pięcioma zerami wiodącymi.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Aby poddać wartość liczbową zerom wiodącym do określonej długości

1. Określ, ile cyfr po lewej stronie dziesiętnego ma być reprezentacja ciągu liczby. Uwzględnij wszystkie zera wiodące w tej całkowitej liczbie cyfr.

1. Zdefiniuj niestandardowy ciąg formatu liczbowego, który używa zero zastępczego symbolu "0" do reprezentowania minimalnej liczby zer.

1. Wywołaj `ToString(String)` metodę numeru i przekaż jej ciąg formatu niestandardowego. Można również użyć niestandardowego ciągu formatu z interpolacją ciągów lub z metodą obsługującym formatowanie złożone.

Poniższy przykład formatuje kilka wartości liczbowych z zerami wiodącymi. W rezultacie całkowita długość sformatowanej liczby wynosi co najmniej osiem cyfr po lewej stronie miejsca po przecinku.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Aby poddać wartość liczbową określoną liczbą zer wiodących

1. Określ, ile zer wiodących ma mieć wartość liczbową.

1. Określ liczbę cyfr po lewej stronie dziesiętnego w niezaopatrzonym ciągu liczbowym:

    1. Określ, czy reprezentacja ciągu liczby zawiera symbol przecinka dziesiętnego.

    1. Jeśli zawiera symbol przecinka dziesiętnego, należy określić liczbę znaków po lewej stronie przecinka dziesiętnego.

         — lub —

         Jeśli nie zawiera symbolu przecinka dziesiętnego, należy określić długość ciągu.

1. Utwórz ciąg formatu niestandardowego, który używa:

    - Zero symbol zastępczy "0" dla każdego z wiodących zer, które mają być wyświetlane w ciągu.

    - Zero symbol zastępczy lub symbol zastępczy cyfry "#" do reprezentowania każdej cyfry w ciągu domyślnym.

1. Podaj ciąg formatu niestandardowego jako `ToString(String)` parametr do metody liczby lub do metody obsługującej formatowanie złożone.

Poniższy przykład klocki dwie <xref:System.Double> wartości z pięciu zer wiodących.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Zobacz też

- [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
