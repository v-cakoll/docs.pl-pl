---
title: Niestandardowe ciągi formatujące TimeSpan — .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b06e367d119a93e872325a85cd951cc5087068be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819635"
---
# <a name="custom-timespan-format-strings"></a>Niestandardowe ciągi formatujące TimeSpan

A <xref:System.TimeSpan> ciąg formatu definiuje reprezentację ciągu <xref:System.TimeSpan> wartość będącą wynikiem operacji formatowania. Ciąg formatu niestandardowego składa się z co najmniej jeden niestandardowy <xref:System.TimeSpan> specyfikatory wraz z dowolnej liczby znaków literałowych formatu. Dowolny ciąg, który nie jest [standardowego ciągu formatu TimeSpan](standard-timespan-format-strings.md) jest interpretowana jako niestandardowy <xref:System.TimeSpan> ciąg formatu.

> [!IMPORTANT]
> Niestandardowy <xref:System.TimeSpan> specyfikatorów formatu nie zawierają symbol zastępczy separator symbole, takie jak symboli, które oddzielają dni od godz., godziny z minuty lub sekundy od ułamków sekund. Zamiast tego te symbole musi zawierać ciąg formatu niestandardowego jako literały ciągów znaków. Na przykład `"dd\.hh\:mm"` definiuje kropki (.) jako separator oddzielający dni i godziny, a następnie dwukropek (:) jako separator godziny i minuty.
>
> Niestandardowe <xref:System.TimeSpan> specyfikatorów formatu nie obejmować symbol znaku, który umożliwia rozróżnianie między interwałami ujemny i dodatni. Aby dołączyć symbol znaku, masz do konstruowania ciągu formatu przy użyciu logiki warunkowej. [Inne znaki](#other-characters) sekcja zawiera przykład.

Ciągów reprezentujących <xref:System.TimeSpan> wartości są tworzone przez wywołania przeciążenia <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, a za pomocą metod, które obsługują formatowanie złożone, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [typy formatowania](formatting-types.md) i [formatowania złożonego](composite-formatting.md). Poniższy przykład ilustruje użycie ciągów formatu niestandardowego w operacjach formatowania.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Niestandardowe <xref:System.TimeSpan> ciągi formatu są również używane przez <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> definiują wymagany format parametru metody wejściowe ciągi dla operacji analizowania. (Podczas analizowania konwertuje ciąg reprezentujący wartość tej wartości.) Poniższy przykład ilustruje użycie ciągów formatu standardowego w operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a> W poniższej tabeli opisano niestandardowych daty i godziny specyfikatorów formatu.

| Specyfikator formatu | Opis | Przykład |
|----------------------|-----------------|-------------|
|"d", "%d"|Liczba dni w odstępie czasu.<br /><br /> Więcej informacji: [Specyfikatora formatu "d" niestandardowych](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"dd"-"dddddddd"|Liczba dni w odstępie czasu dopełniana wiodącymi zerami, zgodnie z potrzebami.<br /><br /> Więcej informacji: ["dd"-specyfikatorów formatu niestandardowego "dddddddd"](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "%h"|Liczba godzin całego w odstępie czasu, które nie są liczone jako część dni. Oznaczona jedną cyfrą godzin nie ma wiodącego zera.<br /><br /> Więcej informacji: [Specyfikatora formatu "h" niestandardowych](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|„hh”|Liczba godzin całego w odstępie czasu, które nie są liczone jako część dni. Godzin jednocyfrowych ma wiodącego zera.<br /><br /> Więcej informacji: ["hh" niestandardowego specyfikatora formatu](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "%m"|Liczba pełnych minut w odstępie czasu, które nie są dołączane jako część godzin lub dni. Minut jednocyfrowych nie ma wiodącego zera.<br /><br /> Więcej informacji: [Specyfikatora formatu "m" niestandardowych](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|„mm”|Liczba pełnych minut w odstępie czasu, które nie są dołączane jako część godzin lub dni. Minut jednocyfrowych ma wiodącego zera.<br /><br /> Więcej informacji: ["mm" niestandardowego specyfikatora formatu](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "%s"|Liczba sekund całego w odstępie czasu, które nie są dołączane jako część godzin, dni lub minut. Oznaczona jedną cyfrą sekund nie ma wiodącego zera.<br /><br /> Więcej informacji: [Specyfikatora formatu "s" niestandardowych](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|„ss”|Liczba sekund całego w odstępie czasu, które nie są dołączane jako część godzin, dni lub minut.  Oznaczona jedną cyfrą sekund ma wiodącego zera.<br /><br /> Więcej informacji: ["ss" niestandardowego specyfikatora formatu](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "%f"|Liczba dziesiątych części sekundy w odstępie czasu.<br /><br /> Więcej informacji: [Specyfikatora formatu "f" niestandardowych](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|„ff”|Liczba setnych części sekundy w odstępie czasu.<br /><br /> Więcej informacji: ["ff" niestandardowego specyfikatora formatu](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|„fff”|Liczba milisekund w odstępie czasu.<br /><br /> Więcej informacji: ["fff" niestandardowego specyfikatora formatu](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|„ffff”|-Dziesięciotysięcznych części sekundy w odstępie czasu.<br /><br /> Więcej informacji: ["ffff" niestandardowego specyfikatora formatu](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|„fffff”|-Stutysięcznych części sekundy w odstępie czasu.<br /><br /> Więcej informacji: ["fffff" niestandardowego specyfikatora formatu](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|„ffffff”|Liczba milionowych części sekundy w odstępie czasu.<br /><br /> Więcej informacji: ["ffffff" niestandardowego specyfikatora formatu](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|„fffffff”|-Dziesięciomilionowych części sekundy (lub ułamkową Takty) w odstępie czasu.<br /><br /> Więcej informacji: ["fffffff" niestandardowego specyfikatora formatu](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "%F"|Liczba dziesiątych części sekundy w odstępie czasu. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "F"](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|„FF”|Liczba setnych części sekundy w odstępie czasu. Wszelkie ułamkowe końcowe zera lub dwóch cyfr zero nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|„FFF”|Liczba milisekund w odstępie czasu. Ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|„FFFF”|-Dziesięciotysięcznych części sekundy w odstępie czasu. Ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|„FFFFF”|-Stutysięcznych części sekundy w odstępie czasu. Ułamkowe końcowe zera nie są uwzględniane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFF"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|„FFFFFF”|Liczba milionowych części sekundy w odstępie czasu. Ułamkowe końcowe zera nie są wyświetlane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|„FFFFFFF”|10 milionach części sekundy w odstępie czasu. Ułamkowe końcowe zera lub siedem zer nie są wyświetlane.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|"*ciąg*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|&#92;|Znak ucieczki.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Jakikolwiek inny znak|Dowolnego znaku o niezmienionym znaczeniu jest interpretowany jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: [Inne znaki](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

## <a name="dSpecifier"></a> Specyfikator formatu niestandardowego "d"

Specyfikator formatu niestandardowego "d" Wyświetla wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę dni w odstępie czasu. Wyświetla pełną liczbę dni w <xref:System.TimeSpan> wartości, nawet jeśli wartość ma więcej niż jedną cyfrę. Jeśli wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwości wynosi zero, specyfikator generuje "0".

Jeśli specyfikator formatu niestandardowego "d" jest używana samodzielnie, należy określić "%d", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Powrót do tabeli](#table)

## <a name="ddSpecifier"></a> "dd"-specyfikatorów formatu niestandardowego "dddddddd"

"Dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" i "dddddddd" niestandardowych specyfikatorów formatu danych wyjściowych wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę dni w odstępie czasu.

Ciąg wyjściowy zawiera minimalną liczbę cyfr określonej przez liczbę znaków "d" w specyfikatorze formatu i są dopełniane zerami wiodącymi, zgodnie z potrzebami. Cyfr z liczbą dni przekracza liczbę znaków "d" w specyfikatorze formatu, pełną liczbę dni, czy dane wyjściowe do ciągu wynikowego.

W poniższym przykładzie użyto tych specyfikatorów formatu, aby wyświetlić reprezentację ciągu, dwa <xref:System.TimeSpan> wartości. Wartość składnik dni pierwszy przedział czasu zero. składnik dni druga wartość 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Powrót do tabeli](#table)

## <a name="hSpecifier"></a> Specyfikator formatu niestandardowego "h"

Specyfikator formatu niestandardowego "h" generuje wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę godzin całego w odstępie czasu, który nie jest liczony jako część jej składnik dni. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwość ma od 0 do 9 i zwraca wartość ciągu dwóch cyfr, gdy wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwości z zakresu od 10 do 23.

Jeśli specyfikator formatu niestandardowego "h" jest używana samodzielnie, należy określić "%h", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "%h" można użyć do interpretacji ciągu numerycznego jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Powrót do tabeli](#table)

## <a name="hhSpecifier"></a> Specyfikator formatu niestandardowego "hh"

Specyfikator formatu niestandardowego "hh" generuje wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę godzin całego w odstępie czasu, który nie jest liczony jako część jej składnik dni. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem wiodącym.

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "hh" można użyć do interpretacji ciągu numerycznego jako liczbę godzin. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "hh".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Powrót do tabeli](#table)

## <a name="mSpecifier"></a> Specyfikator formatu niestandardowego "m"

Specyfikator formatu niestandardowego "m" generuje wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę pełnych minut w odstępie czasu, który nie jest liczony jako część jej składnik dni. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwość ma od 0 do 9 i zwraca wartość ciągu dwóch cyfr, gdy wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwości z zakresu od 10 do 59.

Jeśli specyfikator formatu niestandardowego "m" jest używana samodzielnie, należy określić "%m", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "%m" można użyć do interpretacji ciągu numerycznego jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Powrót do tabeli](#table)

## <a name="mmSpecifier"></a> "Mm" niestandardowego specyfikatora formatu.

Specyfikator formatu niestandardowego "mm" generuje wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę pełnych minut w odstępie czasu, które nie są dołączane jako część składnika godzin lub dni. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem wiodącym.

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "mm" można użyć do interpretacji ciągu numerycznego jako liczbę minut. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Powrót do tabeli](#table)

## <a name="sSpecifier"></a> Specyfikator formatu niestandardowego "s"

Specyfikator formatu niestandardowego "s" generuje wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę sekund całego w odstępie czasu, który nie jest częścią jego godzin, dni lub składnik minut. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwość ma od 0 do 9 i zwraca wartość ciągu dwóch cyfr, gdy wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwości z zakresu od 10 do 59.

Jeśli specyfikator formatu niestandardowego "s" jest używana samodzielnie, należy określić "%s", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "%s" można użyć do interpretacji ciągu numerycznego jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Poniższy przykład ilustruje użycie specyfikator formatu niestandardowego "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Powrót do tabeli](#table)

## <a name="ssSpecifier"></a> Specyfikator formatu niestandardowego "ss"

Specyfikator formatu niestandardowego "ss" generuje wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę sekund całego w odstępie czasu, który nie jest częścią jego godzin, dni lub składnik minut. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem wiodącym.

Zazwyczaj podczas operacji analizowania ciągu wejściowego, który zawiera tylko jeden numer jest interpretowany jako liczba dni. Specyfikator formatu niestandardowego "ss" można użyć do interpretacji ciągu numerycznego jako liczbę sekund. Poniższy przykład stanowi ilustrację.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Poniższy przykład ilustruje użycie specyfikatora formatu niestandardowego "ss".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Powrót do tabeli](#table)

## <a name="fSpecifier"></a> Specyfikator formatu niestandardowego "f"

Specyfikator formatu niestandardowego "f" generuje dziesiątych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie jednej cyfry ułamkowe.

Jeśli specyfikator formatu niestandardowego "f" jest używana samodzielnie, należy określić "%f", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "f", aby wyświetlić liczbę dziesiątych części sekundy w <xref:System.TimeSpan> wartość. "f" jest używany w pierwszej kolejności, jak tylko specyfikatora formatu, a następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="ffSpecifier"></a> Specyfikator formatu niestandardowego "ff"

Specyfikator formatu niestandardowego "ff" generuje setnych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie dwie cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ff", aby wyświetlić liczbę setnych części sekundy w <xref:System.TimeSpan> wartość. "ff" jest używany w pierwszej kolejności, jak tylko specyfikatora formatu, a następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="f3Specifier"></a> Specyfikator formatu niestandardowego "fff"

Specyfikator formatu niestandardowego "fff" (z trzech znaków "f") danych wyjściowych milisekund w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie trzy cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "fff", aby wyświetlić milisekund w <xref:System.TimeSpan> wartość. "fff" jest używany w pierwszej kolejności, jak tylko specyfikatora formatu, a następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="f4Specifier"></a> Specyfikator formatu niestandardowego "ffff"

Specyfikator formatu niestandardowego "ffff" (z czterech znaków "f") danych wyjściowych-dziesięciotysięcznych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie cztery cyfry ułamkowe.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ffff" w celu wyświetlenia liczby dziesięciotysięcznych części sekundy w <xref:System.TimeSpan> wartość. "ffff" jest używany w pierwszej kolejności, jak tylko specyfikatora formatu, a następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="f5Specifier"></a> Specyfikator formatu niestandardowego "fffff"

Specyfikator formatu niestandardowego "fffff" (z pięć znaków "f") danych wyjściowych-stutysięcznych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie pięciu cyfr dziesiętnych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "fffff" w celu wyświetlenia liczby stutysięcznych części sekundy w <xref:System.TimeSpan> wartość. "fffff" jest używany w pierwszej kolejności, jak tylko specyfikatora formatu, a następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="f6Specifier"></a> Specyfikator formatu niestandardowego "ffffff"

Specyfikator formatu niestandardowego "ffffff" (z sześciu znaków "f") danych wyjściowych milionowych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie sześć cyfr dziesiętnych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "ffffff" w celu wyświetlenia liczby milionowych części sekundy w <xref:System.TimeSpan> wartość. Jest używany w pierwszej kolejności, jak tylko specyfikator formatu i następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="f7Specifier"></a> Specyfikator formatu niestandardowego "fffffff"

Specyfikator formatu niestandardowego "fffffff" (z siedem znaków "f") danych wyjściowych dziesięciomilionowych części sekundy (lub ułamkową liczby taktów) w odstępie czasu. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie siedmiu cyfr dziesiętnych.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "fffffff", aby wyświetlić ułamkową liczby taktów w <xref:System.TimeSpan> wartość. Jest używany w pierwszej kolejności, jak tylko specyfikator formatu i następnie łączone ze specyfikatorem "s" w ciągu formatu niestandardowego.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Powrót do tabeli](#table)

## <a name="F_Specifier"></a> Specyfikator formatu niestandardowego "F"

Specyfikator formatu niestandardowego "F" generuje dziesiątych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. Jeśli wartość interwału czasu dziesiątych części sekundy wynosi zero, nie jest on uwzględniony w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności liczba dziesiątych części drugiej cyfra jest opcjonalne.

Jeśli specyfikator formatu niestandardowego "F" jest używana samodzielnie, należy określić "%F", aby go nie jest błędnie zinterpretowana jako ciąg formatu standardowego.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "F", aby wyświetlić liczbę dziesiątych części sekundy w <xref:System.TimeSpan> wartość. Używa również ten specyfikator formatu niestandardowego, podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Powrót do tabeli](#table)

## <a name="FF_Specifier"></a> Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego "FF" generuje setnych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecność liczbę dziesiątych i Liczba setnych części drugiej cyfra jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FF", aby wyświetlić liczbę setnych części sekundy w <xref:System.TimeSpan> wartość. Używa również ten specyfikator formatu niestandardowego, podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Powrót do tabeli](#table)

## <a name="F3_Specifier"></a> Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego "FFF" (z trzech znaków "F") danych wyjściowych milisekund w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecna liczba dziesiątych, Liczba setnych i tysięczne cyfrę na drugiej pozycji jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFF", aby wyświetlić tysięczne sekund w <xref:System.TimeSpan> wartość. Używa również ten specyfikator formatu niestandardowego, podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Powrót do tabeli](#table)

## <a name="F4_Specifier"></a> Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego "FFFF" (z czterech znaków "F") danych wyjściowych-dziesięciotysięcznych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiątych, Liczba setnych, tysięczne i dziesięciotysięcznych części cyfrę na drugiej pozycji jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFF" w celu wyświetlenia liczby dziesięciotysięcznych części sekundy w <xref:System.TimeSpan> wartość. Używa również specyfikator formatu niestandardowego "FFFF" podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Powrót do tabeli](#table)

## <a name="F5_Specifier"></a> Specyfikator formatu niestandardowego "FFFFF"

Specyfikator formatu niestandardowego "FFFFF" (z pięć znaków "F") danych wyjściowych-stutysięcznych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , liczba dziesiątych, Liczba setnych, tysięczne, dziesięciotysięcznych, oraz stutysięcznych części cyfrę na drugiej pozycji jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFF" w celu wyświetlenia liczby stutysięcznych części sekundy w <xref:System.TimeSpan> wartość. Używa również specyfikator formatu niestandardowego "FFFFF" podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Powrót do tabeli](#table)

## <a name="F6_Specifier"></a> Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego "FFFFFF" (z sześciu znaków "F") danych wyjściowych milionowych części sekundy w odstępie czasu. W operacji formatowania wszelkie pozostałe cyfry ułamkowe są obcinane. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody obecność dziesiątych, Liczba setnych, tysięczne, 10 000, sto tysięczne i liczba milionowych części drugiej cyfra jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFFF" w celu wyświetlenia liczby milionowych części sekundy w <xref:System.TimeSpan> wartość. Używa również ten specyfikator formatu niestandardowego, podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Powrót do tabeli](#table)

## <a name="F7_Specifier"></a> Specyfikator formatu niestandardowego "FFFFFFF"

Specyfikator formatu niestandardowego "FFFFFFF" (z siedem znaków "F") danych wyjściowych dziesięciomilionowych części sekundy (lub ułamkową liczby taktów) w odstępie czasu. W przypadku końcowe zera ułamkowe nie są one uwzględnione w ciągu wynikowym. Podczas operacji analizowania, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności siedmiu cyfr ułamkowych do ciągu wejściowego jest opcjonalne.

W poniższym przykładzie użyto specyfikatora formatu niestandardowego "FFFFFFF", aby wyświetlić części ułamkowych części sekundy w <xref:System.TimeSpan> wartość. Używa również ten specyfikator formatu niestandardowego, podczas operacji analizowania.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Powrót do tabeli](#table)

## <a name="other-characters"></a>Inne znaki

Jakikolwiek inny znak o niezmienionym znaczeniu w ciągu formatu, w tym znak odstępu, jest interpretowany jako specyfikator formatu niestandardowego. W większości przypadków obecność innych o niezmienionym znaczeniu znak skutkuje <xref:System.FormatException>.

Istnieją dwa sposoby, aby uwzględnić znak literału w ciągu formatu:

- Należy ją ująć w znaki pojedynczego cudzysłowu (Ogranicznik ciągu literału).

- Należy poprzedzić go ukośnikiem odwrotnym ("\\"), który jest interpretowany jako znak ucieczki. Oznacza to, że w języku C# w formacie ciągu musi być @-quoted, lub znak musi być poprzedzona dodatkowe ukośniki odwrotne.

  W niektórych przypadkach może być konieczne Użyj logikę warunkową, aby uwzględnić literału o zmienionym znaczeniu w ciągu formatu. W poniższym przykładzie użyto logikę warunkową, aby dołączyć symbol znaku dla przedziałów czasowych ujemna.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET nie definiuje gramatyki separatorami w odstępach czasu. Oznacza to, że separatory między dni i godziny, godziny i minuty, minut i sekund i sekund i ułamków sekund musi wszystkie być traktowane jako literały znaków w ciągu formatu.

W poniższym przykładzie użyto znaku ucieczki i pojedynczy cudzysłów, aby zdefiniować niestandardowy ciąg formatu, zawierający słowo "min" w ciągu danych wyjściowych.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Powrót do tabeli](#table)

## <a name="see-also"></a>Zobacz także

- [Formatowanie typów](formatting-types.md)
- [Standardowe ciągi formatujące TimeSpan](standard-timespan-format-strings.md)