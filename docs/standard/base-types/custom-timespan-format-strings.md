---
title: Niestandardowe ciągi formatu TimeSPan
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348319"
---
# <a name="custom-timespan-format-strings"></a>Niestandardowe ciągi formatu TimeSPan

Ciąg <xref:System.TimeSpan> formatu definiuje reprezentację <xref:System.TimeSpan> ciągu wartości, która wynika z operacji formatowania. Ciąg formatu niestandardowego składa <xref:System.TimeSpan> się z jednego lub więcej specyfikatorów formatu niestandardowego wraz z dowolną liczbą znaków literału. Każdy ciąg, który nie jest [standardowym ciągiem formatu TimeSpan,](standard-timespan-format-strings.md) jest interpretowany jako ciąg formatu niestandardowego. <xref:System.TimeSpan>

> [!IMPORTANT]
> Specyfikatory formatu niestandardowego <xref:System.TimeSpan> nie zawierają symboli separatora symboli zastępczych, takich jak symbole oddzielające dni od godzin, godzin od minut lub sekund od ułamkowych sekund. Zamiast tego te symbole muszą być zawarte w ciągu formatu niestandardowego jako literały ciągów. Na przykład `"dd\.hh\:mm"` definiuje kropkę (.) jako separator między dniami i godzinami oraz dwukropek (:) jako separator między godzinami a minutami.
>
> Specyfikatory formatu niestandardowego <xref:System.TimeSpan> również nie zawierają symbolu znaku, który umożliwia rozróżnienie między ujemnymi i dodatnimi interwałami czasu. Aby dołączyć symbol znaku, należy skonstruować ciąg formatu przy użyciu logiki warunkowej. Sekcja [Inne znaki](#other-characters) zawiera przykład.

Reprezentacje ciągów <xref:System.TimeSpan> wartości są tworzone przez wywołania <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> przeciążenia metody i za pomocą metod <xref:System.String.Format%2A?displayProperty=nameWithType>obsługujących formatowanie złożone, takie jak . Aby uzyskać więcej informacji, zobacz [Formatowanie typów](formatting-types.md) i [formatowania złożonego](composite-formatting.md). W poniższym przykładzie przedstawiono użycie ciągów formatu niestandardowego w operacjach formatowania.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Ciągi formatu niestandardowego <xref:System.TimeSpan> <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> są <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> również używane przez i metody do definiowania wymaganego formatu ciągów wejściowych dla operacji analizy. (Analizowanie konwertuje reprezentację ciągu wartości na tę wartość). W poniższym przykładzie przedstawiono użycie standardowych ciągów formatu w operacjach analizy.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>W poniższej tabeli opisano niestandardowe specyfikatory daty i godziny.

| Specyfikator formatu | Opis | Przykład |
|----------------------|-----------------|-------------|
|"d", "%d"|Liczba całych dni w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d`--> "6"<br /><br /> `d\.hh\:mm`--> "6.14:32"|
|"dd"-"ddddddddd"|Liczba całych dni w przedziale czasowym, wyściełane zerami wiodącymi w razie potrzeby.<br /><br /> Więcej informacji: [Specyfikatory niestandardowego formatu "dd"-"ddddddddddd.](#ddSpecifier)|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd`--> "006"<br /><br /> `dd\.hh\:mm`--> "06.14:32"|
|"h", "%h"|Liczba godzin całych w przedziale czasu, które nie są liczone jako część dni. Godziny jednocyfrowe nie mają zera wiodącego.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "h"](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h`--> "14"<br /><br /> `hh\:mm`--> "14:32"|
|„hh”|Liczba godzin całych w przedziale czasu, które nie są liczone jako część dni. Godziny jednocyfrowe mają zero wiodące.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "hh"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh`--> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh`--> 08|
|"m", "%m"|Liczba minut całych w przedziale czasu, które nie są uwzględniane w ramach godzin lub dni. Minuty jednocyfrowe nie mają zera wiodącego.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m`--> "8"<br /><br /> `h\:m`--> "14:8"|
|„mm”|Liczba minut całych w przedziale czasu, które nie są uwzględniane w ramach godzin lub dni. Minuty jednocyfrowe mają zero wiodące.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "mm"](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm`--> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss`--> 6.08:05:17|
|"s", "%s"|Liczba sekund w przedziale czasu, które nie są uwzględniane jako część godzin, dni lub minut. Jednocyfrowe sekundy nie mają zera wiodącego.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s`--> 12<br /><br /> `s\.fff`--> 12.965|
|„ss”|Liczba sekund w przedziale czasu, które nie są uwzględniane jako część godzin, dni lub minut.  Jednocyfrowe sekundy mają zero wiodące.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ss"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss`--> 06<br /><br /> `ss\.fff`--> 06.965|
|"f", "%f"|Dziesiąte sekundy w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "f"](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f`--> 8<br /><br /> `ss\.f`--> 06,8|
|„ff”|Setne części sekundy w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ff"](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff`--> 89<br /><br /> `ss\.ff`--> 06.89|
|„fff”|Milisekundy w przedziale czasu.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fff"](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff`--> 895<br /><br /> `ss\.fff`--> 06.895|
|„ffff”|Dziesięć tysięczności sekundy w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ffff"](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff`--> 8954<br /><br /> `ss\.ffff`--> 06.8954|
|„fffff”|Sto tysięczni sekundy w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff`--> 89543<br /><br /> `ss\.fffff`--> 06.89543|
|„ffffff”|Milionowe sekundy w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ffffff"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff`--> 895432<br /><br /> `ss\.ffffff`--> 06.895432|
|„fffffff”|Dziesięć milionowych sekundy (lub znaczników ułamkowych) w przedziale czasowym.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fffffff"](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff`--> 8954321<br /><br /> `ss\.fffffff`--> 06.8954321|
|"F", "%F"|Dziesiąte sekundy w przedziale czasowym. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "F"](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|„FF”|Setne części sekundy w przedziale czasowym. Wszelkie ułamkowe końcowe zera lub dwie cyfry zerowe nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|„FFF”|Milisekundy w przedziale czasu. Wszelkie ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|„FFFF”|Dziesięć tysięczności sekundy w przedziale czasowym. Wszelkie ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|„FFFFF”|Sto tysięczni sekundy w przedziale czasowym. Wszelkie ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFF"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|„FFFFFF”|Milionowe sekundy w przedziale czasowym. Wszystkie ułamkowe końcowe zera nie są wyświetlane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|„FFFFFFF”|Dziesięć milionów sekundy w przedziale czasowym. Nie są wyświetlane żadne ułamkowe końcowe zera lub siedem zer.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|'*ciąg*'|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss`--> "14:32:17"|
|&#92;|Znak ucieczki.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|
|Jakikolwiek inny znak|Każdy inny znak nieuciekł jest interpretowany jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|

## <a name="dSpecifier"></a>Specyfikator formatu niestandardowego "d"

Specyfikator formatu niestandardowego "d" <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę całych dni w przedziale czasu. Generuje pełną liczbę dni w <xref:System.TimeSpan> wartości, nawet jeśli wartość ma więcej niż jedną cyfrę. Jeśli wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwości jest zero, specyfikator wyprowadza "0".

Jeśli specyfikator formatu niestandardowego "d" jest używany samodzielnie, określ "%d", aby nie był błędnie interpretowany jako standardowy ciąg formatu. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Powrót do stołu](#table)

## <a name="ddSpecifier"></a>Specyfikatory formatu niestandardowego "dd"-"ddddddddd"

"ddd", "ddd", "dddd", "ddddd", "ddddddd", "ddddddd" i "ddddddd" specyfikatory niestandardowe wyprowadzają wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwości, która reprezentuje liczbę całych dni w przedziale czasowym.

Ciąg wyjściowy zawiera minimalną liczbę cyfr określoną przez liczbę znaków "d" w specyfikatorze formatu i jest wyściełana zerami wiodącymi w razie potrzeby. Jeśli cyfry w liczbie dni przekraczają liczbę znaków "d" w specyfikatorze formatu, pełna liczba dni jest wyświetlana w ciągu wyników.

W poniższym przykładzie użyto tych specyfikatorów <xref:System.TimeSpan> formatu do wyświetlenia reprezentacji ciągu dwóch wartości. Wartość składnika dni pierwszego przedziału czasu wynosi zero; wartość składnika dni drugiego wynosi 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Powrót do stołu](#table)

## <a name="hSpecifier"></a>Specyfikator formatu niestandardowego "h"

Specyfikator formatu niestandardowego "h" <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę godzin całych w przedziale czasu, który nie jest liczony jako część jego składnika dnia. Zwraca jednocyfrową wartość ciągu, jeśli <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> wartość właściwości jest od 0 do 9 i zwraca dwucyfrową wartość ciągu, jeśli wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwości mieści się w zakresie od 10 do 23.

Jeśli specyfikator formatu niestandardowego "h" jest używany samodzielnie, określ "%h", aby nie był błędnie interpretowany jako standardowy ciąg formatu. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "%h", aby zinterpretować ciąg liczbowy jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Powrót do stołu](#table)

## <a name="hhSpecifier"></a>Specyfikator formatu niestandardowego "hh"

Specyfikator formatu niestandardowego "hh" <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę godzin całych w przedziale czasu, który nie jest liczony jako część jego składnika dnia. Dla wartości od 0 do 9 ciąg wyjściowy zawiera zero wiodące.

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "hh", aby zinterpretować ciąg liczbowy jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "hh".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Powrót do stołu](#table)

## <a name="mSpecifier"></a>Specyfikator formatu niestandardowego "m"

Specyfikator formatu niestandardowego "m" <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę minut całych w przedziale czasu, który nie jest liczony jako część jego składnika dnia. Zwraca jednocyfrową wartość ciągu, jeśli <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> wartość właściwości jest od 0 do 9 i zwraca dwucyfrową wartość ciągu, jeśli wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwości mieści się w zakresie od 10 do 59.

Jeśli specyfikator formatu niestandardowego "m" jest używany samodzielnie, określ "%m", aby nie był błędnie interpretowany jako standardowy ciąg formatu. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "%m", aby zinterpretować ciąg liczbowy jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Powrót do stołu](#table)

## <a name="mmSpecifier"></a>Specyfikator formatu niestandardowego "mm"

Specyfikator formatu niestandardowego "mm" <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę minut całych w przedziale czasu, który nie jest uwzględniony jako część jego składnika godziny lub dni. Dla wartości od 0 do 9 ciąg wyjściowy zawiera zero wiodące.

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "mm", aby zinterpretować ciąg liczbowy jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Powrót do stołu](#table)

## <a name="sSpecifier"></a>Specyfikator formatu niestandardowego "s"

Specyfikator formatu niestandardowego "s" <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę sekund w czasie, który nie jest uwzględniony jako część jego składnika godzin, dni lub minut. Zwraca jednocyfrową wartość ciągu, jeśli <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> wartość właściwości jest od 0 do 9 i zwraca dwucyfrową wartość ciągu, jeśli wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwości mieści się w zakresie od 10 do 59.

Jeśli specyfikator formatu niestandardowego "s" jest używany samodzielnie, określ "%s", aby nie był błędnie interpretowany jako standardowy ciąg formatu. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "%s", aby zinterpretować ciąg liczbowy jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Powrót do stołu](#table)

## <a name="ssSpecifier"></a>Specyfikator formatu niestandardowego "ss"

Specyfikator formatu niestandardowego "ss" <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> generuje wartość właściwości, która reprezentuje liczbę sekund w czasie, który nie jest uwzględniony jako część jego składnika godziny, dni lub minut. Dla wartości od 0 do 9 ciąg wyjściowy zawiera zero wiodące.

Zwykle w operacji analizy ciąg wejściowy, który zawiera tylko jeden numer, jest interpretowany jako liczba dni. Zamiast tego można użyć specyfikatora formatu niestandardowego "ss", aby zinterpretować ciąg numeryczny jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

W poniższym przykładzie przedstawiono użycie specyfikatora formatu niestandardowego "ss".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Powrót do stołu](#table)

## <a name="fSpecifier"></a>Specyfikator formatu niestandardowego "f"

Specyfikator formatu niestandardowego "f" generuje dziesiąte części sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie jedną cyfrę ułamkową.

Jeśli specyfikator formatu niestandardowego "f" jest używany samodzielnie, określ "%f", aby nie był błędnie interpretowany jako standardowy ciąg formatu.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "f", aby wyświetlić dziesiąte części sekundy w <xref:System.TimeSpan> wartości. "f" jest używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="ffSpecifier"></a>Specyfikator formatu niestandardowego "ff"

Specyfikator formatu niestandardowego "ff" generuje setne części sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie dwie cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ff", aby wyświetlić setne części sekundy w <xref:System.TimeSpan> wartości. "ff" jest używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="f3Specifier"></a>Specyfikator formatu niestandardowego "fff"

Specyfikator formatu niestandardowego "fff" (z trzema znakami "f") generuje milisekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie trzy cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego <xref:System.TimeSpan> "fff" do wyświetlania milisekund w wartości. "fff" jest używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="f4Specifier"></a>Specyfikator formatu niestandardowego "ffff"

Specyfikator formatu niestandardowego "ffff" (z czterema znakami "f") generuje dziesięć tysięcznych sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie cztery cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ffff", <xref:System.TimeSpan> aby wyświetlić dziesięć tysięczników sekundy w wartości. "ffff" jest używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="f5Specifier"></a>Specyfikator formatu niestandardowego "fffff"

Specyfikator formatu niestandardowego "fffff" (z pięcioma znakami "f") generuje sto tysięcznych sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie pięć cyfr ułamkowych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "fffff", <xref:System.TimeSpan> aby wyświetlić sto tysięczni sekundy w wartości. "fffff" jest używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="f6Specifier"></a>Specyfikator formatu niestandardowego "ffffff"

"ffffff" specyfikator formatu niestandardowego (z sześcioma znakami "f") generuje milionowe sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie sześć cyfr ułamkowych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ffffff", aby wyświetlić milionowe części sekundy w <xref:System.TimeSpan> wartości. Jest on używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="f7Specifier"></a>Specyfikator formatu niestandardowego "fffffff"

Specyfikator formatu niestandardowego "fffffff" (z siedmioma znakami "f") generuje dziesięć milionowych części sekundy (lub ułamkową liczbę znaczników) w przedziale czasowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, ciąg wejściowy musi zawierać dokładnie siedem cyfr ułamkowych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "fffffff", aby wyświetlić ułamkową liczbę znaczników w <xref:System.TimeSpan> wartości. Jest on używany najpierw jako jedyny specyfikator formatu, a następnie w połączeniu z specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do stołu](#table)

## <a name="F_Specifier"></a>Specyfikator formatu niestandardowego "F"

Specyfikator formatu niestandardowego "F" generuje dziesiąte części sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli wartość dziesiątej sekundy przedziału czasu wynosi zero, nie jest uwzględniana w ciągu wyników. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych drugiej cyfry jest opcjonalna.

Jeśli specyfikator formatu niestandardowego "F" jest używany samodzielnie, określ "%F", aby nie był błędnie interpretowany jako standardowy ciąg formatu.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "F", aby wyświetlić dziesiąte części sekundy w <xref:System.TimeSpan> wartości. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Powrót do stołu](#table)

## <a name="FF_Specifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego "FF" generuje setne części sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych i setnych drugiej cyfry jest opcjonalna.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FF", aby wyświetlić setne części sekundy w <xref:System.TimeSpan> wartości. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Powrót do stołu](#table)

## <a name="F3_Specifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego "FFF" (z trzema znakami "F") generuje milisekundy w przedziale czasu. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych, setnych i tysięcznach drugiej cyfry jest opcjonalna.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFF" do wyświetlania tysięczni sekundy w <xref:System.TimeSpan> wartości. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Powrót do stołu](#table)

## <a name="F4_Specifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego "FFFF" (z czterema znakami "F") generuje dziesięć tysięcznych sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych, setnych, tysięcznych i dziesiątych tysięczni drugiej cyfry jest opcjonalna.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFF", <xref:System.TimeSpan> aby wyświetlić dziesięć tysięcznasekundy sekundy w wartości. Używa również specyfikatora formatu niestandardowego "FFFF" w operacji analizy.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Powrót do stołu](#table)

## <a name="F5_Specifier"></a>Specyfikator formatu niestandardowego "FFFFF"

Specyfikator formatu niestandardowego "FFFFF" (z pięcioma znakami "F") generuje sto tysięcznych sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych, setnych, tysięcznych, dziesiątek tysięcznych i stu tysięczni drugiej cyfry jest opcjonalna.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFF" <xref:System.TimeSpan> do wyświetlania setek tysięczników sekundy w wartości. Używa również specyfikatora formatu niestandardowego "FFFFF" w operacji analizy.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Powrót do stołu](#table)

## <a name="F6_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego "FFFFFF" (z sześcioma znakami "F") generuje milionowe sekundy w przedziale czasowym. W operacji formatowania wszystkie pozostałe cyfry ułamkowe są obcinane. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność dziesiątych, setnych, tysięcznych, dziesiątek tysięcznych, setnych i milionowych drugiej cyfry jest opcjonalna.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFFF", aby wyświetlić milionowe części sekundy w <xref:System.TimeSpan> wartości. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Powrót do stołu](#table)

## <a name="F7_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFFF"

Specyfikator formatu niestandardowego "FFFFFFF" (z siedmioma znakami "F") generuje dziesięć milionowych części sekundy (lub ułamkową liczbę znaczników) w przedziale czasowym. Jeśli istnieją wszelkie końcowe ułamkowe zera, nie są one uwzględniane w ciągu wynikowym. W operacji analizy, która <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> wywołuje <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> lub metody, obecność siedmiu cyfr ułamkowych w ciągu wejściowym jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFFFF" do wyświetlania ułamkowych części sekundy w <xref:System.TimeSpan> wartości. Używa również tego specyfikatora formatu niestandardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Powrót do stołu](#table)

## <a name="other-characters"></a>Inne znaki

Każdy inny znak nieuniknął w ciągu formatu, w tym znak odstępu, jest interpretowany jako specyfikator formatu niestandardowego. W większości przypadków obecność jakiegokolwiek innego nieunikniętego znaku skutkuje <xref:System.FormatException>

Istnieją dwa sposoby dołączania znaku literału w ciągu formatu:

- Ujmij go w pojedynczy cudzysłów (ogranicznik ciągu literału).

- Poprzedzaj go ukośnikiem odwrotnym ("\\"), który jest interpretowany jako znak ucieczki. Oznacza to, że w języku C#, ciąg formatu musi być @-quotedalbo , lub znak literału musi być poprzedzony dodatkowym ukośniku odwrotnym.

  W niektórych przypadkach może być trzeba użyć logiki warunkowej, aby uwzględnić literał uciekł w ciągu formatu. W poniższym przykładzie użyto logiki warunkowej, aby uwzględnić symbol znaku dla ujemnych interwałów czasu.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET nie definiuje gramatyki dla separatorów w odstępach czasu. Oznacza to, że separatory między dniami i godzinami, godzinami i minutami, minutami i sekundami oraz sekundami i ułamkami sekundy muszą być traktowane jako literały znaków w ciągu formatu.

W poniższym przykładzie użyto zarówno znaku ucieczki, jak i pojedynczego cudzysłowu do zdefiniowania niestandardowego ciągu formatu zawierającego słowo "minuty" w ciągu wyjściowym.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Powrót do stołu](#table)

## <a name="see-also"></a>Zobacz też

- [Formatowanie typów](formatting-types.md)
- [Standardowe ciągi formatujące TimeSpan](standard-timespan-format-strings.md)
