---
title: Niestandardowe ciągi formatujące TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
ms.openlocfilehash: a5963f9afe422206627a1baea47339ecb81becf0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348319"
---
# <a name="custom-timespan-format-strings"></a>Niestandardowe ciągi formatujące TimeSpan

Ciąg formatu <xref:System.TimeSpan> definiuje reprezentację ciągu <xref:System.TimeSpan> wartości będącej wynikiem operacji formatowania. Niestandardowy ciąg formatu składa się z jednego lub kilku niestandardowych specyfikatorów formatu <xref:System.TimeSpan> wraz z dowolną liczbą znaków literału. Dowolny ciąg, który nie jest [standardowym ciągiem formatu TimeSpan](standard-timespan-format-strings.md) , jest interpretowany jako ciąg niestandardowego formatu <xref:System.TimeSpan>.

> [!IMPORTANT]
> Specyfikatory formatu niestandardowego <xref:System.TimeSpan> nie zawierają symboli zastępczych separatorów, takich jak symbole oddzielające dni od godzin, godziny z minut lub sekund od ułamków sekund. Zamiast tego symbole te muszą być zawarte w ciągu formatu niestandardowego jako literały ciągu. Na przykład `"dd\.hh\:mm"` definiuje kropkę (.) jako separator między dniami a godzinami i dwukropek (:) jako separator między godzinami i minutach.
>
> Specyfikatory formatu niestandardowego <xref:System.TimeSpan> nie zawierają również symbolu znaku, który umożliwia odróżnienie między ujemnymi i dodatnimi przedziałami czasowymi. Aby dołączyć symbol znaku, należy utworzyć ciąg formatu za pomocą logiki warunkowej. Sekcja [inne znaki](#other-characters) zawiera przykład.

Ciąg reprezentujący wartości <xref:System.TimeSpan> są generowane przez wywołania przeciążenia metody <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> i metody obsługujące formatowanie złożone, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Typy formatowania](formatting-types.md) i [formatowanie złożone](composite-formatting.md). Poniższy przykład ilustruje użycie niestandardowych ciągów formatu w operacjach formatowania.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Niestandardowe ciągi formatujące <xref:System.TimeSpan> są również używane przez metody <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> do definiowania wymaganego formatu ciągów wejściowych dla operacji analizowania. (Analizowanie konwertuje ciąg reprezentujący wartość na tę wartość). Poniższy przykład ilustruje użycie standardowych ciągów formatu podczas analizowania operacji.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>W poniższej tabeli opisano specyfikatory niestandardowego formatu daty i godziny.

| Specyfikator formatu | Opis | Przykład |
|----------------------|-----------------|-------------|
|"d", "% d"|Liczba pełnych dni w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"DD" — "dddddddd"|Liczba pełnych dni w przedziale czasu, uzupełniona wiodącymi zerami, zgodnie z potrzebami.<br /><br /> Więcej informacji: [specyfikatory formatu niestandardowego "DD"-"dddddddd"](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "% h"|Liczba pełnych godzin w przedziale czasu, które nie są zliczane jako część dni. Godziny z pojedynczą cyfrą nie mają zera wiodącego.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "h"](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|„hh”|Liczba pełnych godzin w przedziale czasu, które nie są zliczane jako część dni. Godziny z jedną cyfrą mają zero wiodące.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "HH"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "% m"|Liczba pełnych minut w przedziale czasu, które nie są uwzględnione w godzinach lub dniach. Minuty z pojedynczą cyfrą nie mają zera wiodącego.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|„mm”|Liczba pełnych minut w przedziale czasu, które nie są uwzględnione w godzinach lub dniach. Minuty z jedną cyfrą mają wiodące zero.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "mm"](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "% s"|Liczba pełnych sekund w przedziale czasu, które nie są uwzględnione w godzinach, dniach lub minutach. Sekundy o pojedynczej cyfrze nie mają zera wiodącego.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|„ss”|Liczba pełnych sekund w przedziale czasu, które nie są uwzględnione w godzinach, dniach lub minutach.  Kilka sekund ma wiodące zero.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "SS"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "% f"|Dziesiątki sekundy w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "f"](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|„ff”|Setne części sekundy w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|„fff”|Milisekundy w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFF"](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|„ffff”|Dziesięć stutysięcznych sekundy w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|„fffff”|Setki stutysięcznych sekund w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|„ffffff”|Dziesięciomilionowych sekundy w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|„fffffff”|Dziesięć dziesięciomilionowych sekund (lub kresek ułamkowych) w przedziale czasu.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffffff"](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "% F"|Dziesiątki sekundy w przedziale czasu. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "F"](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|„FF”|Setne części sekundy w przedziale czasu. Nie są uwzględniane żadne zera końcowe lub dwie cyfry zerowe.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|„FFF”|Milisekundy w przedziale czasu. Wszystkie zera końcowe nie są uwzględniane.<br /><br /> Więcej informacji:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|„FFFF”|Dziesięć stutysięcznych sekundy w przedziale czasu. Wszystkie zera końcowe nie są uwzględniane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|„FFFFF”|Setki stutysięcznych sekund w przedziale czasu. Wszystkie zera końcowe nie są uwzględniane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffff"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|„FFFFFF”|Dziesięciomilionowych sekundy w przedziale czasu. Wszystkie zera końcowe nie są wyświetlane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|„FFFFFFF”|Dziesięć milionów sekund w przedziale czasu. Nie są wyświetlane żadne zera końcowe lub siedem zer.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|"*String*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|&#92;|Znak ucieczki.<br /><br /> Więcej informacji: [inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Jakikolwiek inny znak|Każdy inny niezmieniony znak jest interpretowany jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: [inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

## <a name="dSpecifier"></a>Specyfikator formatu niestandardowego "d"

Specyfikator formatu niestandardowego "d" wyprowadza wartość właściwości <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, która reprezentuje liczbę pełnych dni w przedziale czasu. Wyświetla pełną liczbę dni w <xref:System.TimeSpan> wartości, nawet jeśli wartość ma więcej niż jedną cyfrę. Jeśli wartość właściwości <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> jest równa zero, specyfikatora wyprowadza "0".

Jeśli specyfikator formatu niestandardowego "d" jest używany samodzielnie, określ "% d", tak aby nie był interpretowany jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Wróć do tabeli](#table)

## <a name="ddSpecifier"></a>Specyfikatory formatu niestandardowego "DD"-"dddddddd"

Specyfikatory formatu niestandardowego "DD", "ddd", "dddd", "dddd", "DDDDDD", "ddddddd" i "dddddddd" wyprowadzają wartość właściwości <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, która reprezentuje liczbę dni pełnych w przedziale czasu.

Ciąg wyjściowy zawiera minimalną liczbę cyfr określoną przez liczbę znaków "d" w specyfikatorze formatu i jest uzupełniona wiodącymi zerami zgodnie z potrzebami. Jeśli cyfry w liczbie dni przekraczają liczbę znaków "d" w specyfikatorze formatu, pełna liczba dni jest wyjściowa w ciągu wynikowym.

W poniższym przykładzie zastosowano te specyfikatory formatu, aby wyświetlić reprezentację ciągu dwóch <xref:System.TimeSpan> wartości. Wartość składnika dni pierwszego interwału wynosi zero; wartość składnika dni sekundy to 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Wróć do tabeli](#table)

## <a name="hSpecifier"></a>Specyfikator formatu niestandardowego "h"

Specyfikator formatu niestandardowego "h" wyprowadza wartość właściwości <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, która reprezentuje liczbę pełnych godzin w przedziale czasu, który nie jest liczony jako część jego składnika dnia. Zwraca wartość ciągu jednocyfrowego, jeśli wartość właściwości <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> wynosi od 0 do 9 i zwraca dwucyfrową wartość ciągu, jeśli wartość właściwości <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> z przedziału od 10 do 23.

Jeśli specyfikator formatu niestandardowego "h" jest używany samodzielnie, określ wartość "% h" tak, aby nie była interpretowana jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "% h", aby zinterpretować ciąg liczbowy jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Wróć do tabeli](#table)

## <a name="hhSpecifier"></a>Specyfikator formatu niestandardowego "HH"

Specyfikator formatu niestandardowego "HH" wyprowadza wartość właściwości <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, która reprezentuje liczbę pełnych godzin w przedziale czasu, który nie jest liczony jako część jego składnika dnia. W przypadku wartości z przewidzianych od 0 do 9 ciąg wyjściowy zawiera wiodące zero.

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "HH", aby zinterpretować ciąg liczbowy jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "HH".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Wróć do tabeli](#table)

## <a name="mSpecifier"></a>Specyfikator formatu niestandardowego "m"

Specyfikator formatu niestandardowego "m" wyprowadza wartość właściwości <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, która reprezentuje liczbę pełnych minut w interwale czasu, który nie jest liczony jako część jego składnika dnia. Zwraca wartość ciągu jednocyfrowego, jeśli wartość właściwości <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> wynosi od 0 do 9 i zwraca wartość ciągu dwucyfrowego, jeśli wartość właściwości <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> z zakresu od 10 do 59.

Jeśli specyfikator formatu niestandardowego "m" jest używany samodzielnie, określ "% m", tak aby nie był interpretowany jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "% m", aby zinterpretować ciąg liczbowy jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Wróć do tabeli](#table)

## <a name="mmSpecifier"></a>Specyfikator formatu niestandardowego "mm"

Specyfikator formatu niestandardowego "mm" wyświetla wartość właściwości <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, która reprezentuje liczbę pełnych minut w przedziale czasu, która nie jest uwzględniona w jego składniku godziny lub dni. W przypadku wartości z przewidzianych od 0 do 9 ciąg wyjściowy zawiera wiodące zero.

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "mm", aby zinterpretować ciąg liczbowy jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Wróć do tabeli](#table)

## <a name="sSpecifier"></a>Specyfikator formatu niestandardowego "s"

Specyfikator formatu niestandardowego "s" wyprowadza wartość właściwości <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, która reprezentuje liczbę całych sekund w interwale czasu, która nie jest uwzględniona w godzinach, dniach lub minutach. Zwraca wartość ciągu jednocyfrowego, jeśli wartość właściwości <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> wynosi od 0 do 9 i zwraca wartość ciągu dwucyfrowego, jeśli wartość właściwości <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> z zakresu od 10 do 59.

Jeśli specyfikator formatu niestandardowego "s" jest używany samodzielnie, określ "% s" tak, aby nie był interpretowany jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "% s", aby zinterpretować ciąg liczbowy jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Wróć do tabeli](#table)

## <a name="ssSpecifier"></a>Specyfikator formatu niestandardowego "SS"

Specyfikator formatu niestandardowego "SS" wyprowadza wartość właściwości <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, która reprezentuje liczbę całych sekund w interwale czasu, która nie jest uwzględniona w godzinach, dniach lub minutach. W przypadku wartości z przewidzianych od 0 do 9 ciąg wyjściowy zawiera wiodące zero.

Zwykle w operacji analizowania ciąg wejściowy, który zawiera tylko jedną liczbę, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "SS", aby zinterpretować ciąg liczbowy jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "SS".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Wróć do tabeli](#table)

## <a name="fSpecifier"></a>Specyfikator formatu niestandardowego "f"

Specyfikator formatu niestandardowego "f" wyświetla dziesiątki sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie jedną cyfrę ułamkową.

Jeśli specyfikator formatu niestandardowego "f" jest używany samodzielnie, określ "% f" tak, aby nie był interpretowany jako ciąg formatu standardowego.

Poniższy przykład używa niestandardowego specyfikatora formatu "f", aby wyświetlić dziesiątki sekundy w wartości <xref:System.TimeSpan>. "f" jest używany jako pierwszy specyfikator formatu, a następnie połączony ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="ffSpecifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego "FF" wyprowadza setne części sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie dwie cyfry ułamkowe.

W poniższym przykładzie zastosowano specyfikator formatu niestandardowego "FF" do wyświetlania setnych części sekundy w wartości <xref:System.TimeSpan>. wartość "FF" jest używana najpierw jako jedyny specyfikator formatu, a następnie połączona ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="f3Specifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego "FFF" (z trzema znakami "f") wyświetla liczbę milisekund w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie trzy cyfry ułamkowe.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFF", aby wyświetlić milisekundy w wartości <xref:System.TimeSpan>. "FFF" jest używany jako pierwszy specyfikator formatu, a następnie połączony ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="f4Specifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego "FFFF" (z czterema znakami "f") wyświetla dziesięć stutysięcznych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie cztery cyfry ułamkowe.

W poniższym przykładzie zastosowano specyfikator formatu niestandardowego "FFFF", aby wyświetlić dziesięć stutysięcznych sekundy w wartości <xref:System.TimeSpan>. "FFFF" jest używany jako pierwszy specyfikator formatu, a następnie połączony ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="f5Specifier"></a>Specyfikator formatu niestandardowego "fffff"

Specyfikator formatu niestandardowego "fffff" (z pięcioma znakami "f") wyświetla liczbę setek-stutysięcznych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie pięć cyfr ułamkowych.

Poniższy przykład używa specyfikatora formatu niestandardowego "fffff" do wyświetlania setek-stutysięcznych sekundy w wartości <xref:System.TimeSpan>. "fffff" jest używany jako pierwszy specyfikator formatu, a następnie połączony ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="f6Specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego "FFFFFF" (z sześcioma znakami "f") wyświetla dziesięciomilionowych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie sześć cyfr ułamkowych.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFFFFF", aby wyświetlić dziesięciomilionowych sekundy w wartości <xref:System.TimeSpan>. Jest używana najpierw jako jedyny specyfikator formatu, a następnie połączona ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="f7Specifier"></a>Specyfikator formatu niestandardowego "fffffff"

Specyfikator formatu niestandardowego "fffffff" (z siedmiu znakami "f") wyprowadza dziesięć dziesięciomilionowych sekund (lub ułamkową liczbę znaczników) w przedziale czasu. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, ciąg wejściowy musi zawierać dokładnie siedem cyfr ułamkowych.

Poniższy przykład używa specyfikatora formatu niestandardowego "fffffff" do wyświetlania ułamkowej liczby taktów w wartości <xref:System.TimeSpan>. Jest używana najpierw jako jedyny specyfikator formatu, a następnie połączona ze specyfikatorem "s" w niestandardowym ciągu formatu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Wróć do tabeli](#table)

## <a name="F_Specifier"></a>Specyfikator formatu niestandardowego "F"

Specyfikator formatu niestandardowego "F" wyświetla dziesiątki sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli wartość dziesiąty przedziału czasu jest równa zero, nie jest ona uwzględniona w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek drugiej cyfry jest opcjonalna.

Jeśli specyfikator formatu niestandardowego "F" jest używany samodzielnie, określ "% F" tak, aby nie był interpretowany jako ciąg formatu standardowego.

Poniższy przykład używa niestandardowego specyfikatora formatu "F", aby wyświetlić dziesiątki sekundy w wartości <xref:System.TimeSpan>. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Wróć do tabeli](#table)

## <a name="FF_Specifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego "FF" wyprowadza setne części sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek i setnych drugiej cyfry jest opcjonalna.

W poniższym przykładzie zastosowano specyfikator formatu niestandardowego "FF" do wyświetlania setnych części sekundy w wartości <xref:System.TimeSpan>. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Wróć do tabeli](#table)

## <a name="F3_Specifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego "FFF" (z trzema znakami "F") wyświetla liczbę milisekund w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek, setnych i stutysięcznych drugiej cyfry jest opcjonalna.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFF", aby wyświetlić stutysięcznych sekundy w wartości <xref:System.TimeSpan>. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Wróć do tabeli](#table)

## <a name="F4_Specifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego "FFFF" (z czterema znakami "F") wyświetla dziesięć stutysięcznych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek, setnych, stutysięcznych i dziesięciu stutysięcznych drugiej cyfry jest opcjonalna.

W poniższym przykładzie zastosowano specyfikator formatu niestandardowego "FFFF", aby wyświetlić dziesięć stutysięcznych sekundy w wartości <xref:System.TimeSpan>. Używa także specyfikatora formatu niestandardowego "FFFF" w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Wróć do tabeli](#table)

## <a name="F5_Specifier"></a>Specyfikator formatu niestandardowego "FFFFF"

Specyfikator formatu niestandardowego "FFFFF" (z pięcioma znakami "F") wyświetla liczbę setek-stutysięcznych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek, setnych, stutysięcznych, dziesięciu-stutysięcznych i setek-stutysięcznych w drugiej cyfra jest opcjonalna.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFFFF" do wyświetlania setek-stutysięcznych sekundy w wartości <xref:System.TimeSpan>. Używa także specyfikatora formatu niestandardowego "FFFFF" w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Wróć do tabeli](#table)

## <a name="F6_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego "FFFFFF" (z sześcioma znakami "F") wyświetla dziesięciomilionowych sekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność dziesiątek, setnych, stutysięcznych, dziesięciu-stutysięcznych, setek-stutysięcznych i dziesięciomilionowych drugiej cyfry jest opcjonalna.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFFFFF", aby wyświetlić dziesięciomilionowych sekundy w wartości <xref:System.TimeSpan>. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Wróć do tabeli](#table)

## <a name="F7_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFFF"

Specyfikator formatu niestandardowego "FFFFFFF" (z siedmiu znakami "F") wyprowadza dziesięć dziesięciomilionowych sekund (lub ułamkową liczbę znaczników) w przedziale czasu. Jeśli istnieją końcowe zera, nie są one uwzględnione w ciągu wynikowym. W operacji analizowania, która wywołuje metodę <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, obecność siedmiu ułamkowych cyfr w ciągu wejściowym jest opcjonalna.

Poniższy przykład używa specyfikatora formatu niestandardowego "FFFFFFF", aby wyświetlić części ułamkowe sekundy w wartości <xref:System.TimeSpan>. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Wróć do tabeli](#table)

## <a name="other-characters"></a>Inne znaki

Każdy inny niezmieniony znak w ciągu formatu, w tym znak odstępu, jest interpretowany jako specyfikator formatu niestandardowego. W większości przypadków obecność dowolnego innego niezmienionego znaku skutkuje <xref:System.FormatException>.

Istnieją dwa sposoby dołączania znaku literału w ciągu formatu:

- Ujmij ją w znaki pojedynczego cudzysłowu (ogranicznik ciągu literału).

- Poprzedzaj go ukośnikiem odwrotnym ("\\"), który jest interpretowany jako znak ucieczki. Oznacza to, że w C#, ciąg formatu musi być @-quotedlub znak literału musi być poprzedzony dodatkowym ukośnikiem odwrotnym.

  W niektórych przypadkach może być konieczne użycie logiki warunkowej w celu uwzględnienia literału ucieczki w ciągu formatu. Poniższy przykład używa logiki warunkowej, aby dołączyć symbol znaku dla ujemnych interwałów czasowych.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

Platforma .NET nie definiuje gramatyki dla separatorów w przedziałach czasu. Oznacza to, że separatory między dni i godziny, godziny i minuty, minuty i sekundy oraz sekundy i ułamki sekund muszą być traktowane jako literały znakowe w ciągu formatu.

Poniższy przykład używa znaku ucieczki i pojedynczego cudzysłowu do definiowania niestandardowego ciągu formatu zawierającego wyraz "minuty" w ciągu danych wyjściowych.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Wróć do tabeli](#table)

## <a name="see-also"></a>Zobacz także

- [Formatowanie typów](formatting-types.md)
- [Standardowe ciągi formatujące TimeSpan](standard-timespan-format-strings.md)
