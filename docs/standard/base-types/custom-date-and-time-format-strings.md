---
title: Niestandardowe ciągi formatu daty i godziny
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET Framework], time
- date and time strings
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
ms.openlocfilehash: b33366922677b26f8fe99454206cacd5bb124f32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159276"
---
# <a name="custom-date-and-time-format-strings"></a>Niestandardowe ciągi formatu daty i godziny

Ciąg formatu daty i godziny definiuje <xref:System.DateTime> reprezentację tekstową lub <xref:System.DateTimeOffset> wartość wynikającą z operacji formatowania. Może także definiować reprezentację wartości daty i godziny, która jest wymagana w operacji analizowania składni w celu pomyślnego przekonwertowania ciągu na datę i godzinę. Ciąg formatu niestandardowego składa się z co najmniej jednego specyfikatora niestandardowego formatu daty i godziny. Każdy ciąg, który nie jest [standardowym ciągiem formatu daty i godziny,](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) jest interpretowany jako niestandardowy ciąg formatu daty i godziny.

> [!TIP]
> Można pobrać **narzędzie formatowania**, aplikację .NET Core Windows Forms, która umożliwia stosowanie ciągów formatu do wartości liczbowych lub daty i godziny i wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [języka C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) i [Visual Basic.](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)

Niestandardowe ciągi formatu daty i <xref:System.DateTime> godziny <xref:System.DateTimeOffset> mogą być używane z obu i wartości.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>W operacjach formatowania niestandardowe ciągi formatu daty i `ToString` godziny mogą być używane z metodą wystąpienia daty i godziny lub z metodą obsługującym formatowanie złożone. W poniższym przykładzie pokazano oba te zastosowania.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

W operacjach analizy niestandardowe ciągi formatu daty i <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>godziny <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>mogą <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> być używane z , , i metodami. Metody te wymagają, że ciąg wejściowy jest dokładnie zgodny z określonym wzorcem dla operacji analizy, aby odnieść sukces. W poniższym przykładzie przedstawiono <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołanie metody do przeanalizowania daty, która musi zawierać dzień, miesiąc i rok dwucyfrowy.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

W poniższej tabeli opisano specyfikatory niestandardowego formatu daty i godziny oraz pokazano ciąg wynikowy utworzony przez każdy specyfikator formatu. Domyślnie ciągi wynikowe odzwierciedlają konwencje formatowania kultury en-US. Jeśli określony specyfikator formatu generuje zlokalizowany ciąg wynikowy, w przykładzie wymieniono też kulturę, której dotyczy ciąg wynikowy. Aby uzyskać więcej informacji na temat używania niestandardowych ciągów daty i godziny formatu, zobacz [uwagi](#notes) sekcji.

| Specyfikator formatu | Opis | Przykłady |
| ---------------------- | ----------------- | -------------- |
|„d”|Dzień miesiąca z zakresu od 1 do 31.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "d"](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|„dd”|Dzień miesiąca z zakresu od 01 do 31.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "dd"](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|„ddd”|Skrócona nazwa dnia tygodnia.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ddd"](#dddSpecifier).|2009-06-15T13:45:30 -> pon (en-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|„dddd”|Pełna nazwa dnia tygodnia.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "dddd"](#ddddSpecifier).|2009-06-15T13:45:30 -> poniedziałek (en-US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|„f”|Liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "f"](#fSpecifier).|2009-06-15T13:45:30.617000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|„ff”|Liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ff"](#ffSpecifier).|2009-06-15T13:45:30.617000 -> 61<br /><br /> 2009-06-15T13:45:30.005000 -> 00|
|„fff”|Liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fff"](#fffSpecifier).|15.06.2009 13:45:30.617 -> 617<br /><br /> 15.06.2009 13:45:30.0005 -> 000|
|„ffff”|Liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ffff"](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500 -> 0000|
|„fffff”|Liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fffff"](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 15.06.2009 13:45:30.000005 -> 00000|
|„ffffff”|Liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ffffff"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|
|„fffffff”|Liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "fffffff"](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|„F”|Jeśli wartość jest różna od zera, liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "F"](#F_Specifier).|2009-06-15T13:45:30.617000 -> 6<br /><br /> 2009-06-15T13:45:30.050000 -> (bez wyjścia)|
|„FF”|Jeśli wartość jest różna od zera, liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FF"](#FF_Specifier).|2009-06-15T13:45:30.617000 -> 61<br /><br /> 2009-06-15T13:45:30.005000 -> (brak wyjścia)|
|„FFF”|Jeśli wartość jest różna od zera, liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.000500 -> (brak wyjścia)|
|„FFFF”|Jeśli wartość jest różna od zera, liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (brak wyjścia)|
|„FFFFF”|Jeśli wartość jest różna od zera, liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFF"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (bez wyjścia)|
|„FFFFFF”|Jeśli wartość jest różna od zera, liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (brak wyjścia)|
|„FFFFFFF”|Jeśli wartość jest różna od zera, liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|„g”, „gg”|Okres lub era.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "g" lub "gg"](#gSpecifier).|2009-06-15T13:45:30.617000 -> A.D.|
|„h”|Godzina; używany jest zegar 12-godzinny (wartości od 1 do 12).<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "h"](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|„hh”|Godzina; używany jest zegar 12-godzinny (wartości od 01 do 12).<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "hh"](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|„H”|Godzina, przy użyciu zegara 24-godzinnego od 0 do 23.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "H"](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|„HH”|Godzina; używany jest zegar 24-godzinny (wartości od 00 do 23).<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "HH"](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|„K”|Informacje o strefie czasowej.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "K"](#KSpecifier).|Z <xref:System.DateTime> wartościami:<br /><br /> 2009-06-15T13:45:30, Rodzaj Nieokreślony -><br /><br /> 2009-06-15T13:45:30, Rodzaj Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind Local -> -07:00 (w zależności od ustawień komputera lokalnego)<br /><br /> Z <xref:System.DateTimeOffset> wartościami:<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|„m”|Minuta; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "m"](#mSpecifier).|2009-06-15T01:09:30 -> 9<br /><br /> 2009-06-15T13:29:30 -> 29|
|„mm”|Minuta; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "mm"](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|„M”|Miesiąc; wartości z zakresu od 1 do 12.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "M"](#M_Specifier).|2009-06-15T13:45:30 -> 6|
|„MM”|Miesiąc; wartości z zakresu od 01 do 12.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "MM"](#MM_Specifier).|2009-06-15T13:45:30 -> 06|
|„MMM”|Skrócona nazwa miesiąca.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "MMM"](#MMM_Specifier).|2009-06-15T13:45:30 -> Jun (en-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Jun (zu-ZA)|
|„MMMM”|Pełna nazwa miesiąca.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30 -> czerwcu (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|„s”|Sekunda; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "s"](#sSpecifier).|2009-06-15T13:45:09 -> 9|
|„ss”|Sekunda; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "ss"](#ssSpecifier).|2009-06-15T13:45:09 -> 09|
|„t”|Pierwszy znak oznaczenia AM/PM.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "t"](#tSpecifier).|2009-06-15T13:45:30 -> P (en-US)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|„tt”|Oznaczenie AM/PM.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "tt"](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en-USA)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|„y”|Rok; wartości z zakresu od 0 do 99.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "y"](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|„yy”|Rok; wartości z zakresu od 00 do 99.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "yy"](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|„yyy”|Rok; co najmniej trzy cyfry.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "yyy"](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|„yyyy”|Rok jako liczba czterocyfrowa.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "yyyy"](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|„yyyyy”|Rok jako liczba pięciocyfrowa.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|„z”|Przesunięcie godzinowe względem czasu UTC, bez zer wiodących.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "z"](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|
|„zz”|Przesunięcie godzinowe względem czasu UTC, z zerem wiodącym dla wartości jednocyfrowych.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "zz"](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|
|„zzz”|Godzinowe i minutowe przesunięcie względem czasu UTC.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "zzz"](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|Separator godziny.<br /><br /> Więcej informacji: [":" Specyfikator formatu niestandardowego](#timeSeparator).|2009-06-15T13:45:30 -> : (en-US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|
|"/"|Separator daty.<br /><br /> Więcej informacji: [Specyfikator formatu niestandardowego "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (en-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*ciąg*"<br /><br /> '*ciąg*'|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [Literały znaków](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P|
|%|Definiuje następujący znak jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji:[Korzystanie z pojedynczych specyfikatorów formatu niestandardowego](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|
|&#92;|Znak ucieczki.<br /><br /> Więcej informacji: [Literały znaków](#Literals) i [użycie znaku ucieczki](#escape).|2009-06-15T13:45:30 (h \h) -> 1 godz.|
|Jakikolwiek inny znak|Znak jest kopiowany do ciągu wynikowego bez zmian.<br /><br /> Więcej informacji: [Literały znaków](#Literals).|2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A|

W poniższych sekcjach przedstawiono dodatkowe informacje dotyczące poszczególnych specyfikatorów niestandardowego formatu daty i godziny. O ile nie zaznaczono inaczej, każdy specyfikator tworzy reprezentację ciągu <xref:System.DateTime> identycznego, niezależnie od tego, czy jest używany z wartością, czy wartością. <xref:System.DateTimeOffset>

## <a name="dSpecifier"></a>Specyfikator formatu niestandardowego "d"

Specyfikator formatu niestandardowego „d” oznacza dzień miesiąca w postaci liczby z zakresu od 1 do 31. Dzień oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

Jeśli specyfikator formatu "d" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "d". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „d” jest używany w kilku ciągach formatu.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Powrót do stołu](#table)

## <a name="ddSpecifier"></a>Specyfikator formatu niestandardowego "dd"

Ciąg formatu niestandardowego „dd” przedstawia dzień miesiąca w postaci liczby z zakresu od 01 do 31. Dzień oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „dd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Powrót do stołu](#table)

## <a name="dddSpecifier"></a>Specyfikator formatu niestandardowego "ddd"

Specyfikator formatu niestandardowego „ddd” przedstawia skróconą nazwę dnia tygodnia. Zlokalizowana skrócona nazwa dnia tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „ddd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Powrót do stołu](#table)

## <a name="ddddSpecifier"></a>Specyfikator formatu niestandardowego "dddd"

Specyfikator formatu niestandardowego „dddd” (plus dowolna liczba dodatkowych specyfikatorów „d”) oznacza pełną nazwę dnia tygodnia. Zlokalizowana nazwa dnia tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „dddd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Powrót do stołu](#table)

## <a name="fSpecifier"></a>Specyfikator formatu niestandardowego "f"

Specyfikator formatu niestandardowego „f” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny.

Jeśli specyfikator formatu "f" jest używany bez innych specyfikatorów formatu, jest interpretowany jako standardowy specyfikator daty i godziny "f". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W przypadku użycia specyfikatorów formatu "f" jako <xref:System.DateTime.ParseExact%2A>części <xref:System.DateTime.TryParseExact%2A> <xref:System.DateTimeOffset.ParseExact%2A>ciągu <xref:System.DateTimeOffset.TryParseExact%2A> formatu dostarczonego do , , lub metody, liczba specyfikatorów formatu "f" wskazuje liczbę najbardziej znaczących cyfr ułamka sekund, które muszą być obecne, aby pomyślnie przeanalizować ciąg.

W poniższym przykładzie specyfikator formatu niestandardowego „f” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="ffSpecifier"></a>Specyfikator formatu niestandardowego "ff"

Specyfikator formatu niestandardowego „ff” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny.

W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="fffSpecifier"></a>Specyfikator formatu niestandardowego "fff"

Specyfikator formatu niestandardowego „fff” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny.

W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="ffffSpecifier"></a>Specyfikator formatu niestandardowego "ffff"

Specyfikator formatu niestandardowego „ffff” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny.

Chociaż możliwe jest wyświetlenie dziesięciu tysięczni drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="fffffSpecifier"></a>Specyfikator formatu niestandardowego "fffff"

Specyfikator formatu niestandardowego „fffff” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny.

Chociaż możliwe jest wyświetlenie stu tysięczni drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="ffffffSpecifier"></a>Specyfikator formatu niestandardowego "ffffff"

Specyfikator formatu niestandardowego „ffffff” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny.

Chociaż możliwe jest wyświetlanie milionowych części drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="fffffffSpecifier"></a>Specyfikator formatu niestandardowego "fffffff"

Specyfikator formatu niestandardowego „fffffff” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny.

Chociaż możliwe jest wyświetlenie dziesięciu milionowych części drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="F_Specifier"></a>Specyfikator formatu niestandardowego "F"

Specyfikator formatu niestandardowego „F” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.

Jeśli specyfikator formatu "F" jest używany bez innych specyfikatorów formatu, jest interpretowany jako standardowy specyfikator daty i godziny "F". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

Liczba specyfikatorów formatu "F" <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A>używanych z , , <xref:System.DateTimeOffset.ParseExact%2A>, lub <xref:System.DateTimeOffset.TryParseExact%2A> metody wskazuje maksymalną liczbę najbardziej znaczących cyfr ułamka sekund, które mogą być obecne, aby pomyślnie przeanalizować ciąg.

W poniższym przykładzie specyfikator formatu niestandardowego „F” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="FF_Specifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego „FF” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny. Jednak końcowe zera lub dwie cyfry zerowe nie są wyświetlane.

W poniższym przykładzie specyfikator formatu niestandardowego „FF” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="FFF_Specifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego „FFF” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny. Jednak końcowe zera lub trzy cyfry zerowe nie są wyświetlane.

W poniższym przykładzie specyfikator formatu niestandardowego „FFF” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Powrót do stołu](#table)

## <a name="FFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego „FFFF” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub cztery cyfry zerowe nie są wyświetlane.

Chociaż możliwe jest wyświetlenie dziesięciu tysięczni drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="FFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFF"

Specyfikator formatu niestandardowego „FFFFF” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub pięć cyfr zerowych nie są wyświetlane.

Chociaż możliwe jest wyświetlenie stu tysięczni drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="FFFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego „FFFFFF” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub sześć cyfr zerowych nie są wyświetlane.

Chociaż możliwe jest wyświetlanie milionowych części drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="FFFFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFFF"

Specyfikator formatu niestandardowego „FFFFFFF” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub siedem cyfr zerowych nie są wyświetlane.

Chociaż możliwe jest wyświetlenie dziesięciu milionowych części drugiego składnika wartości czasu, wartość ta może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Powrót do stołu](#table)

## <a name="gSpecifier"></a>Specyfikator formatu niestandardowego "g" lub "gg"

Specyfikator formatu niestandardowego „g” lub „gg” (plus dowolna liczba dodatkowych specyfikatorów „g”) przedstawia okres lub erę, taką jak n.e. Operacja formatowania ignoruje ten specyfikator, jeśli data, która ma zostać sformatowana, nie ma skojarzonego ciągu okresu lub ery.

Jeśli specyfikator formatu "g" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "g". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „g” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Powrót do stołu](#table)

## <a name="hSpecifier"></a>Specyfikator formatu niestandardowego "h"

Specyfikator formatu niestandardowego „h” przedstawia godzinę jako liczbę z zakresu od 1 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „5”.

Jeśli specyfikator formatu "h" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza . <xref:System.FormatException> Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „h” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Powrót do stołu](#table)

## <a name="hhSpecifier"></a>Specyfikator formatu niestandardowego "hh"

Specyfikator formatu niestandardowego „hh” (plus dowolna liczba dodatkowych specyfikatorów „h”) przedstawia godzinę jako liczbę z zakresu od 01 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „05”.

W poniższym przykładzie specyfikator formatu niestandardowego „hh” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Powrót do stołu](#table)

## <a name="H_Specifier"></a>Specyfikator formatu niestandardowego "H"

Specyfikator formatu niestandardowego „H” przedstawia godzinę jako liczbę z zakresu od 0 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "H" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza wartość <xref:System.FormatException>. Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „H” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Powrót do stołu](#table)

## <a name="HH_Specifier"></a>Specyfikator formatu niestandardowego "HH"

Specyfikator formatu niestandardowego „HH” (plus dowolna liczba dodatkowych specyfikatorów „H”) przedstawia godzinę jako liczbę z zakresu od 00 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „HH” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Powrót do stołu](#table)

## <a name="KSpecifier"></a>Specyfikator formatu niestandardowego "K"

Specyfikator formatu niestandardowego „K” przedstawia informacje o strefie czasowej z wartości daty i godziny. Gdy ten specyfikator <xref:System.DateTime> formatu jest używany z wartościami, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> ciąg wynikowy jest definiowany przez wartość właściwości:

- Dla lokalnej strefy czasowej <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> (wartość właściwości ) ten specyfikator jest odpowiednikiem specyfikatora "zzz" i generuje ciąg wynikowy zawierający przesunięcie lokalne z skoordynowanego <xref:System.DateTimeKind.Local?displayProperty=nameWithType>czasu uniwersalnego (UTC); na przykład "-07:00".

- Dla czasu UTC <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> (wartość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>właściwości ), ciąg wynik zawiera znak "Z" do reprezentowania daty UTC.

- Przez czas z nieokreślonej strefy czasowej <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> (czas, <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>którego właściwość jest <xref:System.String.Empty?displayProperty=nameWithType>równa), wynik jest odpowiednikiem .

Dla <xref:System.DateTimeOffset> wartości specyfikator formatu "K" jest odpowiednikiem specyfikatora formatu "zzz" i generuje ciąg wynikowy zawierający przesunięcie <xref:System.DateTimeOffset> wartości z czasu UTC.

Jeśli specyfikator formatu "K" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza wartość <xref:System.FormatException>. Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie jest wyświetlany ciąg, który wynika z używania <xref:System.DateTime> <xref:System.DateTimeOffset> specyfikatora formatu niestandardowego "K" z różnymi i wartościami w systemie w strefie czasowej Pacyfiku usa.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Powrót do stołu](#table)

## <a name="mSpecifier"></a>Specyfikator formatu niestandardowego "m"

Specyfikator formatu niestandardowego „m” przedstawia minutę jako liczbę z zakresu od 0 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "m" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "m". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „m” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Powrót do stołu](#table)

## <a name="mmSpecifier"></a>Specyfikator formatu niestandardowego "mm"

Specyfikator formatu niestandardowego „mm” (plus dowolna liczba dodatkowych specyfikatorów „m”) przedstawia minutę jako liczbę z zakresu od 00 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „mm” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Powrót do stołu](#table)

## <a name="M_Specifier"></a>Specyfikator formatu niestandardowego "M"

Specyfikator formatu niestandardowego „M” przedstawia miesiąc jako liczbę z zakresu od 1 do 12 (lub od 1 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

Jeśli specyfikator formatu "M" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "M". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „M” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Powrót do stołu](#table)

## <a name="MM_Specifier"></a>Specyfikator formatu niestandardowego "MM"

Specyfikator formatu niestandardowego „MM” przedstawia miesiąc jako liczbę z zakresu od 01 do 12 (lub od 01 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „MM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Powrót do stołu](#table)

## <a name="MMM_Specifier"></a>Specyfikator formatu niestandardowego "MMM"

Specyfikator formatu niestandardowego „MMM” przedstawia skróconą nazwę miesiąca. Zlokalizowana skrócona nazwa miesiąca jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „MMM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Powrót do stołu](#table)

## <a name="MMMM_Specifier"></a>Specyfikator formatu niestandardowego "MMMM"

Specyfikator formatu niestandardowego „MMMM” przedstawia pełną nazwę miesiąca. Zlokalizowana nazwa miesiąca jest pobierana <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> z właściwości bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „MMMM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Powrót do stołu](#table)

## <a name="sSpecifier"></a>Specyfikator formatu niestandardowego "s"

Specyfikator formatu niestandardowego „s” przedstawia sekundy jako liczbę z zakresu od 0 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "s" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "s". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „s” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Powrót do stołu](#table)

## <a name="ssSpecifier"></a>Specyfikator formatu niestandardowego "ss"

Specyfikator formatu niestandardowego „s” (plus dowolna liczba dodatkowych specyfikatorów „s”) przedstawia sekundy jako liczbę z zakresu od 00 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „ss” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Powrót do stołu](#table)

## <a name="tSpecifier"></a>Specyfikator formatu niestandardowego "t"

Specyfikator formatu niestandardowego „t” przedstawia pierwszy znak oznaczenia AM/PM. Odpowiednie zlokalizowane desygnator jest <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> pobierana z lub właściwości bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

Jeśli specyfikator formatu "t" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "t". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „t” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Powrót do stołu](#table)

## <a name="ttSpecifier"></a>Specyfikator formatu niestandardowego "tt"

Specyfikator formatu niestandardowego „tt” (plus dowolna liczba dodatkowych specyfikatorów „t”) przedstawia całe oznaczenie AM/PM. Odpowiednie zlokalizowane desygnator jest <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> pobierana z lub właściwości bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

Upewnij się, że używasz specyfikatora "tt" dla języków, dla których konieczne jest zachowanie rozróżnienia między AM i PM. Przykładem jest język japoński, dla którego oznaczenia AM i PM różnią się w drugim znaku, a nie w pierwszym znaku.

W poniższym przykładzie specyfikator formatu niestandardowego „tt” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Powrót do stołu](#table)

## <a name="ySpecifier"></a>Specyfikator formatu niestandardowego "y"

Specyfikator formatu niestandardowego „y” przedstawia rok jako jedno- lub dwucyfrową liczbę. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeżeli pierwsza cyfra roku dwucyfrowego rozpoczyna się od zera (na przykład, 2008), liczba jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "y" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny "y". Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „y” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Powrót do stołu](#table)

## <a name="yySpecifier"></a>Specyfikator formatu niestandardowego "yy"

Specyfikator formatu niestandardowego „yy” przedstawia rok jako liczbę dwucyfrową. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeśli rok dwucyfrowy ma mniej niż dwie cyfry znaczące, liczba jest dopełniana wiodącymi zerami w celu utworzenia dwóch cyfr.

W operacji analizy dwucyfrowy rok analizowany przy użyciu specyfikatora formatu niestandardowego "yy" <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> jest interpretowany na podstawie właściwości bieżącego kalendarza dostawcy formatu. W poniższym przykładzie jest analizowany ciąg przedstawiając datę, która ma domyślnie dwucyfrowy rok według domyślnego kalendarza gregoriańskiego w kulturze en-US, która w tym przypadku jest bieżącą kulturą. Następnie zmienia <xref:System.Globalization.CultureInfo> obiekt bieżącej kultury, <xref:System.Globalization.GregorianCalendar> aby <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> użyć obiektu, którego właściwość została zmodyfikowana.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

W poniższym przykładzie specyfikator formatu niestandardowego „yy” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Powrót do stołu](#table)

## <a name="yyySpecifier"></a>Specyfikator formatu niestandardowego "yyy"

Specyfikator formatu niestandardowego „yyy” przedstawia rok za pomocą co najmniej trzech cyfr. Jeśli rok ma więcej niż trzy cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż trzy cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia trzech cyfr.

> [!NOTE]
> W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie wszystkich cyfr znaczących.

W poniższym przykładzie specyfikator formatu niestandardowego „yyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Powrót do stołu](#table)

## <a name="yyyySpecifier"></a>Specyfikator formatu niestandardowego "yyyy"

Specyfikator formatu niestandardowego „yyyy” przedstawia rok za pomocą co najmniej czterech cyfr. Jeśli rok ma więcej niż cztery cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż cztery cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia czterech cyfr.

> [!NOTE]
> W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie co najmniej czterech cyfr.

W poniższym przykładzie specyfikator formatu niestandardowego „yyyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Powrót do stołu](#table)

## <a name="yyyyySpecifier"></a>Specyfikator formatu niestandardowego "yyyyy"

Specyfikator formatu niestandardowego „yyyyy” (plus dowolna liczba dodatkowych specyfikatorów „y”) przedstawia rok za pomocą co najmniej pięciu cyfr. Jeśli rok ma więcej niż pięć cyfr znaczących, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż pięć cyfr, liczba jest dopełniana zerami wiodącymi w celu utworzenia pięciu cyfr.

Jeśli istnieją dodatkowe specyfikatory „y”, liczba jest dopełniana tak wieloma zerami wiodącymi, jak jest to konieczne, aby utworzyć liczbę specyfikatorów „y”.

W poniższym przykładzie specyfikator formatu niestandardowego „yyyyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Powrót do stołu](#table)

## <a name="zSpecifier"></a>Specyfikator formatu niestandardowego "z"

Z <xref:System.DateTime> wartościami specyfikator formatu niestandardowego "z" reprezentuje podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego z skoordynowanego czasu uniwersalnego (UTC), mierzonego w godzinach. Nie odzwierciedla wartość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości wystąpienia. Z tego powodu specyfikator formatu "z" nie <xref:System.DateTime> jest zalecany do użycia z wartościami.

Z <xref:System.DateTimeOffset> wartościami ten specyfikator <xref:System.DateTimeOffset> formatu reprezentuje przesunięcie wartości z czasu UTC w godzinach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane bez zera wiodącego.

Jeśli specyfikator formatu "z" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza . <xref:System.FormatException> Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

W poniższym przykładzie specyfikator formatu niestandardowego „z” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Powrót do stołu](#table)

## <a name="zzSpecifier"></a>Specyfikator formatu niestandardowego "zz"

Z <xref:System.DateTime> wartościami specyfikator formatu niestandardowego "zz" reprezentuje podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego z czasu UTC, mierzone w godzinach. Nie odzwierciedla wartość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości wystąpienia. Z tego powodu specyfikator formatu "zz" nie <xref:System.DateTime> jest zalecany do użycia z wartościami.

Z <xref:System.DateTimeOffset> wartościami ten specyfikator <xref:System.DateTimeOffset> formatu reprezentuje przesunięcie wartości z czasu UTC w godzinach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „zz” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Powrót do stołu](#table)

## <a name="zzzSpecifier"></a>Specyfikator formatu niestandardowego "zzz"

Z <xref:System.DateTime> wartościami specyfikator formatu niestandardowego "zzz" reprezentuje podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego z utc, mierzone w godzinach i minutach. Nie odzwierciedla wartość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości wystąpienia. Z tego powodu specyfikator formatu "zzz" nie <xref:System.DateTime> jest zalecany do użycia z wartościami.

Z <xref:System.DateTimeOffset> wartościami ten specyfikator <xref:System.DateTimeOffset> formatu reprezentuje przesunięcie wartości z czasu UTC w godzinach i minutach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „zzz” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Powrót do stołu](#table)

## <a name="timeSeparator"></a>":" specyfikator formatu niestandardowego
Specyfikator formatu niestandardowego „:” przedstawia separator godzin, który jest używany do odróżnienia godzin, minut i sekund. Odpowiedni zlokalizowany separator czasu jest <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> pobierany z właściwości bieżącej lub określonej kultury.

> [!NOTE]
> Aby zmienić separator czasu dla określonego ciągu daty i godziny, należy określić znak separatora w ramach ogranicznika ciągu literału. Na przykład ciąg `hh'_'dd'_'ss` formatu niestandardowego tworzy ciąg\_wynikowy, w którym " " (znak podkreślenia) jest zawsze używany jako separator czasu. Aby <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> zmienić separator czasu dla wszystkich dat dla kultury, należy zmienić wartość właściwości bieżącej <xref:System.Globalization.DateTimeFormatInfo> kultury lub utworzyć wystąpienia <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> obiektu, przypisać znak do jego właściwości i <xref:System.IFormatProvider> wywołać przeciążenie metody formatowania, która zawiera parametr.

Jeśli specyfikator formatu ":" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza . <xref:System.FormatException> Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

[Powrót do stołu](#table)

## <a name="dateSeparator"></a>Specyfikator formatu niestandardowego "/"

Specyfikator formatu niestandardowego „/” oznacza separator daty, który jest używany do odróżnienia lat, miesięcy i dni. Odpowiedni zlokalizowany separator dat jest <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> pobierany z właściwości bieżącej lub określonej kultury.

> [!NOTE]
> Aby zmienić separator daty dla określonego ciągu daty i godziny, należy określić znak separatora w ramach ogranicznika ciągu literału. Na przykład ciąg `mm'/'dd'/'yyyy` formatu niestandardowego tworzy ciąg wynik, w którym "/" jest zawsze używany jako separator daty. Aby <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> zmienić separator daty dla wszystkich dat dla kultury, należy zmienić wartość właściwości bieżącej <xref:System.Globalization.DateTimeFormatInfo> kultury lub utworzyć wystąpienia <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> obiektu, przypisać znak do jego właściwości i <xref:System.IFormatProvider> wywołać przeciążenie metody formatowania, która zawiera parametr.

Jeśli specyfikator formatu "/" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy specyfikator daty i godziny i zgłasza wartość <xref:System.FormatException>. Aby uzyskać więcej informacji na temat używania specyfikatora pojedynczego formatu, zobacz [Korzystanie z specyfikatorów pojedynczego formatu niestandardowego](#UsingSingleSpecifiers) w dalszej części tego artykułu.

[Powrót do stołu](#table)

## <a name="Literals"></a>Literały znaków

Następujące znaki w niestandardowym ciągu formatu daty i godziny są zastrzeżone i są zawsze interpretowane jako \\znaki formatowania lub, w przypadku ", ',,, i , jako znaki specjalne.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|k|g|h|m|s|
|t|t|z|%|:|
|/|"|'|&#92;||

Wszystkie inne znaki są zawsze interpretowane jako literały znaków i w operacji formatowania są uwzględniane w ciągu wyników bez zmian.  W operacji analizy muszą dokładnie odpowiadać znakom w ciągu wejściowym; w porównaniu jest rozróżniana wielkość liter.

Poniższy przykład zawiera literały "PST" (dla pacific standard time) i "PDT" (dla czasu letniego Pacyfiku) do reprezentowania lokalnej strefy czasowej w ciągu formatu. Należy zauważyć, że ciąg jest uwzględniony w ciągu wynikowym, a ciąg zawierający lokalny ciąg strefy czasowej również pomyślnie analizuje.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Istnieją dwa sposoby wskazania, że znaki mają być interpretowane jako znaki literału, a nie jako znaki rezerwowe, dzięki czemu mogą być zawarte w ciągu wyników lub pomyślnie przeanalizowane w ciągu wejściowym:

- Przez ucieczkę każdego zastrzeżonego znaku. Aby uzyskać więcej informacji, zobacz [Korzystanie ze znaku ucieczki](#escape).

Poniższy przykład zawiera literały znaków "pst" (dla Pacific Standard time) do reprezentowania lokalnej strefy czasowej w ciągu formatu. Ponieważ zarówno "s", jak i "t" są ciągami formatu niestandardowego, oba znaki muszą być unikane, aby były interpretowane jako literały znaków.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Poprzez załączanie całego ciągu literału w cudzysłowie lub apostrofy. Poniższy przykład jest podobny do poprzedniego, z tą różnicą, że "pst" jest ujęty w cudzysłów, aby wskazać, że cały rozdzielany ciąg powinien być interpretowany jako literały znaków.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Uwagi

### <a name="UsingSingleSpecifiers"></a>Używanie specyfikatorów pojedynczego formatu niestandardowego

Ciąg niestandardowego formatu daty i godziny składa się z co najmniej dwóch znaków. Metody formatowania daty i godziny interpretują każdy jednoznakowy ciąg jako ciąg standardowego formatu daty i godziny. Jeśli nie rozpoznają znaku jako prawidłowego specyfikatora <xref:System.FormatException>formatu, wyrzucą plik . Na przykład ciąg formatu, który składa się tylko ze specyfikatora „h”, jest interpretowany jako ciąg standardowego formatu daty i godziny. Jednak w tym konkretnym przypadku wyjątek jest zgłaszany, ponieważ nie ma "h" standardowy identyfikator i specyfikator formatu czasu.

Aby użyć jakiegokolwiek specyfikatora niestandardowego formatu daty i godziny jako jedynego specyfikatora w ciągu formatu (tj. użyć samego specyfikatora formatu niestandardowego „d”, „f”, „F”, „g”, „h”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/”), należy przed lub za specyfikatorem umieścić spację albo umieścić specyfikator formatu procent („%”) przed pojedynczym specyfikatorem niestandardowego formatu daty i godziny.

Na przykład`%h"` " jest interpretowany jako niestandardowy ciąg formatu daty i godziny, który wyświetla godzinę reprezentowaną przez bieżącą wartość daty i godziny. Można także użyć ciągu formatu „ h” lub „h ”, mimo że zawierają w ciągu wynikowym i spację, i godzinę. W poniższym przykładzie pokazano te trzy ciągi formatu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a>Używanie znaku ucieczki

Znaki „D”, „f”, „F”, „G”, „g”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/” w ciągu formatu są interpretowane jako specyfikatory formatu niestandardowego, a nie jako znaki literału. Aby zapobiec interpretowaniu znaku jako specyfikatora formatu, można go\\poprzedzić ukośnikiem odwrotnym ( ), który jest znakiem ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.

Aby uwzględnić ukośnik odwrotny w ciągu wynikowym,`\\`należy go uniknąć za pomocą innego ukośnika odwrotnego ( ).

> [!NOTE]
> Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.

W poniższym przykładzie użyto znaku ucieczki, aby uniemożliwić operacji formatowania interpretowanie znaków „h” i „m” jako specyfikatorów formatu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Ustawienia Panelu sterowania

Ustawienia **Opcje regionalne i językowe** w Panelu sterowania mają wpływ na ciąg wyników tworzony przez operację formatowania, która zawiera wiele niestandardowych specyfikatorów daty i godziny. Ustawienia te są używane do <xref:System.Globalization.DateTimeFormatInfo> inicjowania obiektu skojarzonego z bieżącą kulturą wątku, który zawiera wartości używane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> jeśli używasz konstruktora do tworzenia wystąpienia <xref:System.Globalization.CultureInfo> nowy obiekt, który reprezentuje tę samą kulturę jak bieżąca kultura systemu, wszelkie dostosowania ustanowione przez **regionalnyi i język opcje** element w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> można użyć <xref:System.Globalization.CultureInfo> do utworzenia obiektu, który nie odzwierciedla dostosowania systemu.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo właściwości

Formatowanie zależy od właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest niejawnie dostarczany przez bieżącą kulturę wątku lub jawnie przez <xref:System.IFormatProvider> parametr metody, która wywołuje formatowanie. Dla <xref:System.IFormatProvider> parametru należy określić <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę <xref:System.Globalization.DateTimeFormatInfo> lub obiekt.

Ciąg wynikowy wytwarzany przez wiele specyfikatorów formatu daty i <xref:System.Globalization.DateTimeFormatInfo> godziny niestandardowej również zależy od właściwości bieżącego obiektu. Aplikacja może zmienić wynik wyprodukowany przez niektóre niestandardowe specyfikatory <xref:System.Globalization.DateTimeFormatInfo> daty i godziny, zmieniając odpowiednią właściwość. Na przykład specyfikator formatu "ddd" dodaje skróconą nazwę <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> dnia tygodnia znalezioną w tablicy ciągu do ciągu wynikowego. Podobnie specyfikator formatu "MMMM" dodaje pełną <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> nazwę miesiąca znalezioną w tablicy ciągu do ciągu wynikowego.

## <a name="see-also"></a>Zobacz też

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Przykład: Narzędzie formatowania formularzy WinForms w ustonach .NET Core (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Przykład: Narzędzie formatowania formularzy WinForms w programie .NET Core (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
