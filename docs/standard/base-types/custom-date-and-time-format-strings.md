---
title: Niestandardowe ciągi formatujące datę i godzinę — .NET
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
ms.openlocfilehash: ce4aeda8c9fb3c73d133316f985d99e7271411c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103771"
---
# <a name="custom-date-and-time-format-strings"></a>Niestandardowe ciągi formatujące datę i godzinę

Ciąg formatu daty i godziny definiuje reprezentację tekstową <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartość będącą wynikiem operacji formatowania. Może także definiować reprezentację wartości daty i godziny, która jest wymagana w operacji analizowania składni w celu pomyślnego przekonwertowania ciągu na datę i godzinę. Ciąg formatu niestandardowego składa się z co najmniej jednego specyfikatora niestandardowego formatu daty i godziny. Dowolny ciąg, który nie jest [ciągiem standardowego formatu daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) , jest interpretowany jako ciąg niestandardowego formatu daty i godziny.

> [!TIP]
> Możesz pobrać **Narzędzie formatowania**, aplikację .net Core Windows Forms, która umożliwia stosowanie ciągów formatowania do wartości liczbowych lub daty i godziny i wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) i [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Niestandardowe ciągi formatujące datę i godzinę mogą być używane z wartościami <xref:System.DateTime> i <xref:System.DateTimeOffset>.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a>W operacjach formatowania niestandardowe ciągi formatujące datę i czas mogą być używane z metodą `ToString` wystąpienia daty i godziny lub z metodą, która obsługuje formatowanie złożone. W poniższym przykładzie pokazano oba te zastosowania.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

W operacjach analizy niestandardowe ciągi formatujące datę i godzinę mogą być używane z metodami <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>. Te metody wymagają, aby ciąg wejściowy był zgodny z określonym wzorcem w celu pomyślnego wykonania operacji analizy. Poniższy przykład ilustruje wywołanie metody <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, aby przeanalizować datę, która musi zawierać dzień, miesiąc i rok dwucyfrowy.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

W poniższej tabeli opisano specyfikatory niestandardowego formatu daty i godziny oraz pokazano ciąg wynikowy utworzony przez każdy specyfikator formatu. Domyślnie ciągi wynikowe odzwierciedlają konwencje formatowania kultury en-US. Jeśli określony specyfikator formatu generuje zlokalizowany ciąg wynikowy, w przykładzie wymieniono też kulturę, której dotyczy ciąg wynikowy. Aby uzyskać więcej informacji na temat używania niestandardowych ciągów formatu daty i godziny, zobacz sekcję [uwagi](#notes) .

| Specyfikator formatu | Opis | Przykłady |
| ---------------------- | ----------------- | -------------- |
|„d”|Dzień miesiąca z zakresu od 1 do 31.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "d"](#dSpecifier).|2009-06-01T13:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 15|
|„dd”|Dzień miesiąca z zakresu od 01 do 31.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "DD"](#ddSpecifier).|2009-06-01T13:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 15|
|„ddd”|Skrócona nazwa dnia tygodnia.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ddd"](#dddSpecifier).|2009-06-15T13:45:30-> PN (EN-US)<br /><br /> 2009-06-15T13:45:30-> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 > jednostki LUN. (fr-FR)|
|„dddd”|Pełna nazwa dnia tygodnia.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "dddd"](#ddddSpecifier).|2009-06-15T13:45:30-> poniedziałek (pl-US)<br /><br /> 2009-06-15T13:45:30-> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Lundi (fr-FR)|
|„f”|Liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "f"](#fSpecifier).|2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.05-> 0|
|„ff”|Liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#ffSpecifier).|2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> 00|
|„fff”|Liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFF"](#fffSpecifier).|6/15/2009 13:45:30.617-> 617<br /><br /> 6/15/2009 13:45:30.0005-> 000|
|„ffff”|Liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#ffffSpecifier).|2009-06-15T13:45:30.6175000-> 6175<br /><br /> 2009-06-15T13:45:30.0000500-> 0000|
|„fffff”|Liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffff"](#fffffSpecifier).|2009-06-15T13:45:30.6175400-> 61754<br /><br /> 6/15/2009 13:45:30.000005 > 00000|
|„ffffff”|Liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> 000000|
|„fffffff”|Liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffffff"](#fffffffSpecifier).|2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 0001150|
|„F”|Jeśli wartość jest różna od zera, liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "F"](#F_Specifier).|2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.0500000-> (Brak danych wyjściowych)|
|„FF”|Jeśli wartość jest różna od zera, liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#FF_Specifier).|2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> (Brak danych wyjściowych)|
|„FFF”|Jeśli wartość jest różna od zera, liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000-> 617<br /><br /> 2009-06-15T13:45:30.0005000-> (Brak danych wyjściowych)|
|„FFFF”|Jeśli wartość jest różna od zera, liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000-> 5275<br /><br /> 2009-06-15T13:45:30.0000500-> (Brak danych wyjściowych)|
|„FFFFF”|Jeśli wartość jest różna od zera, liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffff"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400-> 61754<br /><br /> 2009-06-15T13:45:30.0000050-> (Brak danych wyjściowych)|
|„FFFFFF”|Jeśli wartość jest różna od zera, liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> (Brak danych wyjściowych)|
|„FFFFFFF”|Jeśli wartość jest różna od zera, liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 000115|
|„g”, „gg”|Okres lub era.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "g" lub "gg"](#gSpecifier).|2009-06-15T13:45:30.6170000-> N.E.|
|„h”|Godzina; używany jest zegar 12-godzinny (wartości od 1 do 12).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "h"](#hSpecifier).|2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 1|
|„hh”|Godzina; używany jest zegar 12-godzinny (wartości od 01 do 12).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "HH"](#hhSpecifier).|2009-06-15T01:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 01|
|„H”|Godzina przy użyciu 24-godzinnego zegara od 0 do 23.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "H"](#H_Specifier).|2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 13|
|„HH”|Godzina; używany jest zegar 24-godzinny (wartości od 00 do 23).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "HH"](#HH_Specifier).|2009-06-15T01:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 13|
|„K”|Informacje o strefie czasowej.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "K"](#KSpecifier).|Z wartościami <xref:System.DateTime>:<br /><br /> 2009-06-15T13:45:30, rodzaj nieokreślony-><br /><br /> 2009-06-15T13:45:30, rodzaj UTC-> Z<br /><br /> 2009-06-15T13:45:30, rodzaj lokalny->-07:00 (zależy od ustawień komputera lokalnego)<br /><br /> Z wartościami <xref:System.DateTimeOffset>:<br /><br /> 2009-06-15T01:45:30-07:00-->-07:00<br /><br /> 2009-06-15T08:45:30 + 00:00--> + 00:00|
|„m”|Minuta; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "m"](#mSpecifier).|2009 — 06-15T01:09:30-> 9<br /><br /> 2009 — 06-15T13:29:30-> 29|
|„mm”|Minuta; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "mm"](#mmSpecifier).|2009 — 06-15T01:09:30-> 09<br /><br /> 2009-06-15T01:45:30-> 45|
|„M”|Miesiąc; wartości z zakresu od 1 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "M"](#M_Specifier).|2009-06-15T13:45:30-> 6|
|„MM”|Miesiąc; wartości z zakresu od 01 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "mm"](#MM_Specifier).|2009 — 06-15T13:45:30 — > 06|
|„MMM”|Skrócona nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMM"](#MMM_Specifier).|2009-06-15T13:45:30-> Jun (pl-US)<br /><br /> 2009-06-15T13:45:30-> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30-> Jun (zu-za)|
|„MMMM”|Pełna nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30-> czerwiec (pl-US)<br /><br /> 2009-06-15T13:45:30-> Juni (da-DK)<br /><br /> 2009-06-15T13:45:30-> uJuni (zu-za)|
|„s”|Sekunda; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "s"](#sSpecifier).|2009 — 06-15T13:45:09-> 9|
|„ss”|Sekunda; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "SS"](#ssSpecifier).|2009 — 06-15T13:45:09-> 09|
|„t”|Pierwszy znak oznaczenia AM/PM.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "t"](#tSpecifier).|2009-06-15T13:45:30-> P (EN-US)<br /><br /> 2009-06-15T13:45:30-> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR)|
|„tt”|Oznaczenie AM/PM.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "tt"](#ttSpecifier).|2009-06-15T13:45:30-> PM (pl-US)<br /><br /> 2009-06-15T13:45:30-> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR)|
|„y”|Rok; wartości z zakresu od 0 do 99.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "y"](#ySpecifier).|0,001-01-01T00:00:00-> 1<br /><br /> 0900-01-01T00:00:00-> 0<br /><br /> 1900-01-01T00:00:00-> 0<br /><br /> 2009 — 06-15T13:45:30-> 9<br /><br /> 2019-06-15T13:45:30-> 19|
|„yy”|Rok; wartości z zakresu od 00 do 99.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "YY"](#yySpecifier).|0,001-01-01T00:00:00-> 01<br /><br /> 0900-01-01T00:00:00-> 00<br /><br /> 1900-01-01T00:00:00-> 00<br /><br /> 2019-06-15T13:45:30-> 19|
|„yyy”|Rok; co najmniej trzy cyfry.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "yyy"](#yyySpecifier).|0,001-01-01T00:00:00-> 001<br /><br /> 0900-01-01T00:00:00-> 900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30-> 2009|
|„yyyy”|Rok jako liczba czterocyfrowa.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "RRRR"](#yyyySpecifier).|0,001-01-01T00:00:00-> 0,001<br /><br /> 0900-01-01T00:00:00-> 0900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30-> 2009|
|„yyyyy”|Rok jako liczba pięciocyfrowa.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "RRRR"](#yyyyySpecifier).|0,001-01-01T00:00:00-> 00001<br /><br /> 2009-06-15T13:45:30-> 02009|
|„z”|Przesunięcie godzinowe względem czasu UTC, bez zer wiodących.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "z"](#zSpecifier).|2009-06-15T13:45:30-07:00->-7|
|„zz”|Przesunięcie godzinowe względem czasu UTC, z zerem wiodącym dla wartości jednocyfrowych.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ZZ"](#zzSpecifier).|2009-06-15T13:45:30-07:00->-07|
|„zzz”|Godzinowe i minutowe przesunięcie względem czasu UTC.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ZZZ"](#zzzSpecifier).|2009-06-15T13:45:30-07:00->-07:00|
|":"|Separator godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego ":"](#timeSeparator).|2009-06-15T13:45:30->: (EN-US)<br /><br /> 2009-06-15T13:45:30->. (it-IT)<br /><br /> 2009-06-15T13:45:30->: (ja-JP)|
|"/"|Separator daty.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "/"](#dateSeparator).|2009-06-15T13:45:30->/(EN-US)<br /><br /> 2009-06-15T13:45:30->-(AR-DZ)<br /><br /> 2009-06-15T13:45:30->. (tr-TR)|
|"*String*"<br /><br /> "*String*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [literały znakowe](#Literals).|2009-06-15T13:45:30 ("ARR:" g:m t)-> ARR: 1:45 P<br /><br /> 2009-06-15T13:45:30 ("ARR:" g:m t)-> ARR: 1:45 P|
|%|Definiuje następujący znak jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji:[Używanie pojedynczego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (% h) — > 1|
|&#92;|Znak ucieczki.<br /><br /> Więcej informacji: [literały znakowe](#Literals) i [Używanie znaku ucieczki](#escape).|2009-06-15T13:45:30 (h \h) — > 1 h|
|Jakikolwiek inny znak|Znak jest kopiowany do ciągu wynikowego bez zmian.<br /><br /> Więcej informacji: [literały znakowe](#Literals).|2009-06-15T01:45:30 (ARR hh: mm t)-> ARR 01:45 A|

W poniższych sekcjach przedstawiono dodatkowe informacje dotyczące poszczególnych specyfikatorów niestandardowego formatu daty i godziny. O ile nie zaznaczono inaczej, każdy specyfikator tworzy identyczną reprezentację ciągu bez względu na to, czy jest używana z wartością <xref:System.DateTime>, czy <xref:System.DateTimeOffset> wartością.

## <a name="dSpecifier"></a>Specyfikator formatu niestandardowego "d"

Specyfikator formatu niestandardowego „d” oznacza dzień miesiąca w postaci liczby z zakresu od 1 do 31. Dzień oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

Jeśli specyfikator formatu "d" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "d". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „d” jest używany w kilku ciągach formatu.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Wróć do tabeli](#table)

## <a name="ddSpecifier"></a>Specyfikator formatu niestandardowego "DD"

Ciąg formatu niestandardowego „dd” przedstawia dzień miesiąca w postaci liczby z zakresu od 01 do 31. Dzień oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „dd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Wróć do tabeli](#table)

## <a name="dddSpecifier"></a>Specyfikator formatu niestandardowego "ddd"

Specyfikator formatu niestandardowego „ddd” przedstawia skróconą nazwę dnia tygodnia. Zlokalizowana Skrócona nazwa dnia tygodnia jest pobierana z właściwości <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „ddd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Wróć do tabeli](#table)

## <a name="ddddSpecifier"></a>Specyfikator formatu niestandardowego "dddd"

Specyfikator formatu niestandardowego „dddd” (plus dowolna liczba dodatkowych specyfikatorów „d”) oznacza pełną nazwę dnia tygodnia. Zlokalizowana nazwa dnia tygodnia jest pobierana z właściwości <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „dddd” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Wróć do tabeli](#table)

## <a name="fSpecifier"></a>Specyfikator formatu niestandardowego "f"

Specyfikator formatu niestandardowego „f” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny.

Jeśli specyfikator formatu "f" jest używany bez innych specyfikatorów formatu, jest interpretowany jako specyfikator standardowego formatu daty i godziny "f". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W przypadku użycia specyfikatorów formatu "f" jako części ciągu formatu dostarczonego do metody <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>lub <xref:System.DateTimeOffset.TryParseExact%2A>, liczba specyfikatorów formatu "f" wskazuje liczbę najbardziej znaczących cyfr części sekund, która musi być obecna pomyślnie Przeanalizuj ciąg.

W poniższym przykładzie specyfikator formatu niestandardowego „f” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="ffSpecifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego „ff” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny.

W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="fffSpecifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego „fff” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny.

W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="ffffSpecifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego „ffff” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny.

Chociaż istnieje możliwość wyświetlenia dziesięciu stutysięcznych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="fffffSpecifier"></a>Specyfikator formatu niestandardowego "fffff"

Specyfikator formatu niestandardowego „fffff” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny.

Chociaż istnieje możliwość wyświetlenia setek stutysięcznych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="ffffffSpecifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego „ffffff” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny.

Chociaż istnieje możliwość wyświetlenia dziesięciomilionowych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="fffffffSpecifier"></a>Specyfikator formatu niestandardowego "fffffff"

Specyfikator formatu niestandardowego „fffffff” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny.

Chociaż istnieje możliwość wyświetlenia dziesięciu dziesięciomilionowych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="F_Specifier"></a>Specyfikator formatu niestandardowego "F"

Specyfikator formatu niestandardowego „F” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.

Jeśli specyfikator formatu "F" jest używany bez innych specyfikatorów formatu, jest interpretowany jako specyfikator standardowego formatu daty i godziny "F". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

Liczba specyfikatorów formatu "F" używanych z metodą <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>lub <xref:System.DateTimeOffset.TryParseExact%2A> wskazuje maksymalną liczbę najbardziej znaczących cyfr części sekund, która może być obecna, aby pomyślnie przeanalizować ciąg.

W poniższym przykładzie specyfikator formatu niestandardowego „F” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="FF_Specifier"></a>Specyfikator formatu niestandardowego "FF"

Specyfikator formatu niestandardowego „FF” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny. Jednak końcowe zera lub dwie cyfry zerowe nie są wyświetlane.

W poniższym przykładzie specyfikator formatu niestandardowego „FF” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="FFF_Specifier"></a>Specyfikator formatu niestandardowego "FFF"

Specyfikator formatu niestandardowego „FFF” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny. Jednak końcowe zera lub trzy cyfry zerowe nie są wyświetlane.

W poniższym przykładzie specyfikator formatu niestandardowego „FFF” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Wróć do tabeli](#table)

## <a name="FFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFF"

Specyfikator formatu niestandardowego „FFFF” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub cztery cyfry zero nie są wyświetlane.

Chociaż istnieje możliwość wyświetlenia dziesięciu stutysięcznych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="FFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFF"

Specyfikator formatu niestandardowego „FFFFF” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub pięć cyfr zero nie są wyświetlane.

Chociaż istnieje możliwość wyświetlenia setek stutysięcznych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="FFFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"

Specyfikator formatu niestandardowego „FFFFFF” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub sześć cyfr zero nie są wyświetlane.

Chociaż istnieje możliwość wyświetlenia dziesięciomilionowych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="FFFFFFF_Specifier"></a>Specyfikator formatu niestandardowego "FFFFFFF"

Specyfikator formatu niestandardowego „FFFFFFF” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub siedem zero cyfr nie są wyświetlane.

Chociaż istnieje możliwość wyświetlenia dziesięciu dziesięciomilionowych drugiego składnika wartości czasu, ta wartość może nie być znacząca. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

[Wróć do tabeli](#table)

## <a name="gSpecifier"></a>Specyfikator formatu niestandardowego "g" lub "gg"

Specyfikator formatu niestandardowego „g” lub „gg” (plus dowolna liczba dodatkowych specyfikatorów „g”) przedstawia okres lub erę, taką jak n.e. Operacja formatowania ignoruje ten specyfikator, jeśli data do sformatowania nie ma skojarzonego okresu lub ciągu ery.

Jeśli specyfikator formatu "g" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "g". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „g” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Wróć do tabeli](#table)

## <a name="hSpecifier"></a>Specyfikator formatu niestandardowego "h"

Specyfikator formatu niestandardowego „h” przedstawia godzinę jako liczbę z zakresu od 1 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „5”.

Jeśli specyfikator formatu "h" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „h” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Wróć do tabeli](#table)

## <a name="hhSpecifier"></a>Specyfikator formatu niestandardowego "HH"

Specyfikator formatu niestandardowego „hh” (plus dowolna liczba dodatkowych specyfikatorów „h”) przedstawia godzinę jako liczbę z zakresu od 01 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „05”.

W poniższym przykładzie specyfikator formatu niestandardowego „hh” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Wróć do tabeli](#table)

## <a name="H_Specifier"></a>Specyfikator formatu niestandardowego "H"

Specyfikator formatu niestandardowego „H” przedstawia godzinę jako liczbę z zakresu od 0 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "H" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „H” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Wróć do tabeli](#table)

## <a name="HH_Specifier"></a>Specyfikator formatu niestandardowego "HH"

Specyfikator formatu niestandardowego „HH” (plus dowolna liczba dodatkowych specyfikatorów „H”) przedstawia godzinę jako liczbę z zakresu od 00 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „HH” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Wróć do tabeli](#table)

## <a name="KSpecifier"></a>Specyfikator formatu niestandardowego "K"

Specyfikator formatu niestandardowego „K” przedstawia informacje o strefie czasowej z wartości daty i godziny. Gdy ten specyfikator formatu jest używany z wartościami <xref:System.DateTime>, ciąg wynikowy jest definiowany przez wartość właściwości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>:

- W przypadku lokalnej strefy czasowej (<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Local?displayProperty=nameWithType>) ten specyfikator jest równoważny specyfikatorowi "ZZZ" i tworzy ciąg wynikowy zawierający przesunięcie lokalne od skoordynowanego czasu uniwersalnego (UTC); na przykład "-07:00".

- W przypadku czasu UTC (<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), ciąg wynikowy zawiera znak "Z" reprezentujący datę UTC.

- W przypadku czasu z nieokreślonej strefy czasowej (czas, którego właściwość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> jest równa <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>) wynik jest równoważny <xref:System.String.Empty?displayProperty=nameWithType>.

W przypadku wartości <xref:System.DateTimeOffset> specyfikator formatu "K" jest równoważny specyfikatorowi formatu "ZZZ" i tworzy ciąg wynikowy zawierający przesunięcie wartości <xref:System.DateTimeOffset> z czasu UTC.

Jeśli specyfikator formatu "K" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

Poniższy przykład wyświetla ciąg, który powoduje użycie specyfikatora formatu niestandardowego "K" z różnymi <xref:System.DateTime> i <xref:System.DateTimeOffset> wartościami w systemie w strefie czasowej USA.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Wróć do tabeli](#table)

## <a name="mSpecifier"></a>Specyfikator formatu niestandardowego "m"

Specyfikator formatu niestandardowego „m” przedstawia minutę jako liczbę z zakresu od 0 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "m" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "m". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „m” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Wróć do tabeli](#table)

## <a name="mmSpecifier"></a>Specyfikator formatu niestandardowego "mm"

Specyfikator formatu niestandardowego „mm” (plus dowolna liczba dodatkowych specyfikatorów „m”) przedstawia minutę jako liczbę z zakresu od 00 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „mm” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Wróć do tabeli](#table)

## <a name="M_Specifier"></a>Specyfikator formatu niestandardowego "M"

Specyfikator formatu niestandardowego „M” przedstawia miesiąc jako liczbę z zakresu od 1 do 12 (lub od 1 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

Jeśli specyfikator formatu "M" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "M". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „M” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Wróć do tabeli](#table) 

## <a name="MM_Specifier"></a>Specyfikator formatu niestandardowego "MM"

Specyfikator formatu niestandardowego „MM” przedstawia miesiąc jako liczbę z zakresu od 01 do 12 (lub od 01 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „MM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Wróć do tabeli](#table)

## <a name="MMM_Specifier"></a>Specyfikator formatu niestandardowego "MMM"

Specyfikator formatu niestandardowego „MMM” przedstawia skróconą nazwę miesiąca. Zlokalizowana Skrócona nazwa miesiąca jest pobierana z właściwości <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „MMM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Wróć do tabeli](#table)

## <a name="MMMM_Specifier"></a>Specyfikator formatu niestandardowego "MMMM"

Specyfikator formatu niestandardowego „MMMM” przedstawia pełną nazwę miesiąca. Zlokalizowana nazwa miesiąca jest pobierana z właściwości <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

W poniższym przykładzie specyfikator formatu niestandardowego „MMMM” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Wróć do tabeli](#table)

## <a name="sSpecifier"></a>Specyfikator formatu niestandardowego "s"

Specyfikator formatu niestandardowego „s” przedstawia sekundy jako liczbę z zakresu od 0 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "s" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "s". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „s” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Wróć do tabeli](#table)

## <a name="ssSpecifier"></a>Specyfikator formatu niestandardowego "SS"

Specyfikator formatu niestandardowego „s” (plus dowolna liczba dodatkowych specyfikatorów „s”) przedstawia sekundy jako liczbę z zakresu od 00 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „ss” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Wróć do tabeli](#table)

## <a name="tSpecifier"></a>Specyfikator formatu niestandardowego "t"

Specyfikator formatu niestandardowego „t” przedstawia pierwszy znak oznaczenia AM/PM. Odpowiednie zlokalizowane oznaczenie jest pobierane z właściwości <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

Jeśli specyfikator formatu "t" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "t". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „t” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Wróć do tabeli](#table)

## <a name="ttSpecifier"></a>Specyfikator formatu niestandardowego "tt"

Specyfikator formatu niestandardowego „tt” (plus dowolna liczba dodatkowych specyfikatorów „t”) przedstawia całe oznaczenie AM/PM. Odpowiednie zlokalizowane oznaczenie jest pobierane z właściwości <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

Upewnij się, że używasz specyfikatora "tt" dla języków, dla których konieczne jest zachowanie rozróżnienia między AM i PM. Przykładem jest język japoński, dla którego oznaczenia AM i PM różnią się w drugim znaku, a nie w pierwszym znaku.

W poniższym przykładzie specyfikator formatu niestandardowego „tt” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Wróć do tabeli](#table)

## <a name="ySpecifier"></a>Specyfikator formatu niestandardowego "y"

Specyfikator formatu niestandardowego „y” przedstawia rok jako jedno- lub dwucyfrową liczbę. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeżeli pierwsza cyfra roku dwucyfrowego rozpoczyna się od zera (na przykład, 2008), liczba jest formatowana bez zera wiodącego.

Jeśli specyfikator formatu "y" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny "y". Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „y” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Wróć do tabeli](#table)

## <a name="yySpecifier"></a>Specyfikator formatu niestandardowego "YY"

Specyfikator formatu niestandardowego „yy” przedstawia rok jako liczbę dwucyfrową. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeśli rok dwucyfrowy ma mniej niż dwie cyfry znaczące, liczba jest dopełniana wiodącymi zerami w celu utworzenia dwóch cyfr.

W operacji analizowania dwucyfrowy rok, który jest analizowany za pomocą specyfikatora formatu niestandardowego "RR", jest interpretowany na podstawie właściwości <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> bieżącego kalendarza dostawcy formatu. W poniższym przykładzie jest analizowany ciąg przedstawiając datę, która ma domyślnie dwucyfrowy rok według domyślnego kalendarza gregoriańskiego w kulturze en-US, która w tym przypadku jest bieżącą kulturą. Następnie zmienia obiekt <xref:System.Globalization.CultureInfo> bieżącej kultury, aby użyć obiektu <xref:System.Globalization.GregorianCalendar>, którego właściwość <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> została zmodyfikowana.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

W poniższym przykładzie specyfikator formatu niestandardowego „yy” jest używany w ciągu formatu niestandardowego.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Wróć do tabeli](#table)

## <a name="yyySpecifier"></a>Specyfikator formatu niestandardowego "yyy"

Specyfikator formatu niestandardowego „yyy” przedstawia rok za pomocą co najmniej trzech cyfr. Jeśli rok ma więcej niż trzy cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż trzy cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia trzech cyfr.

> [!NOTE]
> W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie wszystkich cyfr znaczących.

W poniższym przykładzie specyfikator formatu niestandardowego „yyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Wróć do tabeli](#table)

## <a name="yyyySpecifier"></a>Specyfikator formatu niestandardowego "RRRR"

Specyfikator formatu niestandardowego „yyyy” przedstawia rok za pomocą co najmniej czterech cyfr. Jeśli rok ma więcej niż cztery cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż cztery cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia czterech cyfr.

> [!NOTE]
> W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie co najmniej czterech cyfr.

W poniższym przykładzie specyfikator formatu niestandardowego „yyyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Wróć do tabeli](#table)

## <a name="yyyyySpecifier"></a>Specyfikator formatu niestandardowego "RRRR"

Specyfikator formatu niestandardowego „yyyyy” (plus dowolna liczba dodatkowych specyfikatorów „y”) przedstawia rok za pomocą co najmniej pięciu cyfr. Jeśli rok ma więcej niż pięć cyfr znaczących, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż pięć cyfr, liczba jest dopełniana zerami wiodącymi w celu utworzenia pięciu cyfr.

Jeśli istnieją dodatkowe specyfikatory „y”, liczba jest dopełniana tak wieloma zerami wiodącymi, jak jest to konieczne, aby utworzyć liczbę specyfikatorów „y”.

W poniższym przykładzie specyfikator formatu niestandardowego „yyyyy” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Wróć do tabeli](#table)

## <a name="zSpecifier"></a>Specyfikator formatu niestandardowego "z"

W przypadku wartości <xref:System.DateTime> specyfikator formatu niestandardowego "z" przedstawia podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego od skoordynowanego czasu uniwersalnego (UTC), mierzoną w godzinach. Nie odzwierciedla wartości właściwości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wystąpienia. Z tego powodu specyfikator formatu "z" nie jest zalecany do używania z wartościami <xref:System.DateTime>.

W przypadku wartości <xref:System.DateTimeOffset> ten specyfikator formatu reprezentuje przesunięcie wartości <xref:System.DateTimeOffset> z UTC w godzinach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane bez zera wiodącego.

Jeśli specyfikator formatu "z" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

W poniższym przykładzie specyfikator formatu niestandardowego „z” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Wróć do tabeli](#table)

## <a name="zzSpecifier"></a>Specyfikator formatu niestandardowego "ZZ"

W przypadku wartości <xref:System.DateTime> specyfikator formatu niestandardowego "ZZ" przedstawia podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego od czasu UTC (w godzinach). Nie odzwierciedla wartości właściwości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wystąpienia. Z tego powodu specyfikator formatu "ZZ" nie jest zalecany do używania z wartościami <xref:System.DateTime>.

W przypadku wartości <xref:System.DateTimeOffset> ten specyfikator formatu reprezentuje przesunięcie wartości <xref:System.DateTimeOffset> z UTC w godzinach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „zz” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Wróć do tabeli](#table)

## <a name="zzzSpecifier"></a>Specyfikator formatu niestandardowego "ZZZ"

W przypadku wartości <xref:System.DateTime> specyfikator formatu niestandardowego "ZZZ" reprezentuje podpisane przesunięcie strefy czasowej lokalnego systemu operacyjnego od czasu UTC, mierzoną w godzinach i minutach. Nie odzwierciedla wartości właściwości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wystąpienia. Z tego powodu specyfikator formatu "ZZZ" nie jest zalecany do używania z wartościami <xref:System.DateTime>.

W przypadku wartości <xref:System.DateTimeOffset> ten specyfikator formatu reprezentuje przesunięcie wartości <xref:System.DateTimeOffset> z UTC w godzinach i minutach.

Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

W poniższym przykładzie specyfikator formatu niestandardowego „zzz” jest używany w ciągu formatu niestandardowego.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Wróć do tabeli](#table)

## <a name="timeSeparator"></a>Specyfikator formatu niestandardowego ":"
Specyfikator formatu niestandardowego „:” przedstawia separator godzin, który jest używany do odróżnienia godzin, minut i sekund. Odpowiedni zlokalizowany separator czasu jest pobierany z właściwości <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

> [!NOTE]
> Aby zmienić separator czasu dla określonego ciągu daty i godziny, określ znak separatora w ograniczniku ciągu literału. Na przykład ciąg formatu niestandardowego `hh'_'dd'_'ss` generuje ciąg wynikowy, w którym "\_" (podkreślenie) jest zawsze używany jako separator czasu. Aby zmienić separator czasu dla wszystkich dat dla kultury, Zmień wartość właściwości <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> bieżącej kultury lub Utwórz wystąpienie obiektu <xref:System.Globalization.DateTimeFormatInfo>, przypisz znak do jego właściwości <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> i Wywołaj Przeciążenie metody formatowania, która zawiera parametr <xref:System.IFormatProvider>.

Jeśli specyfikator formatu ":" jest używany bez innych niestandardowych specyfikatorów formatu, jest interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

[Wróć do tabeli](#table)

## <a name="dateSeparator"></a>Specyfikator formatu niestandardowego "/"

Specyfikator formatu niestandardowego „/” oznacza separator daty, który jest używany do odróżnienia lat, miesięcy i dni. Odpowiedni zlokalizowany separator daty jest pobierany z właściwości <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> bieżącej lub określonej kultury.

> [!NOTE]
> Aby zmienić separator daty dla określonego ciągu daty i godziny, określ znak separatora w ograniczniku ciągu literału. Na przykład ciąg formatu niestandardowego `mm'/'dd'/'yyyy` generuje ciąg wynikowy, w którym znak "/" jest zawsze używany jako separator daty. Aby zmienić separator daty dla wszystkich dat dla kultury, Zmień wartość właściwości <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> bieżącej kultury lub Utwórz wystąpienie obiektu <xref:System.Globalization.DateTimeFormatInfo>, przypisz znak do jego właściwości <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> i Wywołaj Przeciążenie metody formatowania, która zawiera parametr <xref:System.IFormatProvider>.

Jeśli specyfikator formatu "/" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy specyfikator formatu daty i godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu jednego specyfikatora formatu, zobacz w dalszej części tego artykułu [użycie jednego specyfikatora formatu niestandardowego](#UsingSingleSpecifiers) .

[Wróć do tabeli](#table)

## <a name="Literals"></a>Literały znaków

Następujące znaki w niestandardowym ciągu formatu daty i godziny są zastrzeżone i są zawsze interpretowane jako znaki formatowania lub, w przypadku znaku ",",/i \\, jako znaki specjalne.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|N|G|h|m|s|
|t|t|porządku|%|:|
|/|"|'|&#92;||

Wszystkie inne znaki są zawsze interpretowane jako literały znakowe, a w operacji formatowania są uwzględniane w niezmienionym ciągu wynikowym.  W operacji analizowania muszą one dokładnie pasować do znaków w ciągu wejściowym; w porównaniu z rozróżnianiem wielkości liter.

Poniższy przykład obejmuje znaki literału "PST" (w przypadku czasu pacyficznego) i "PDT" (w przypadku czasu pacyficznego), aby reprezentować lokalną strefę czasową w ciągu formatu. Należy zauważyć, że ciąg jest uwzględniony w ciągu wynikowym, a ciąg, który zawiera ciąg lokalnego strefy czasowej, również jest analizowany pomyślnie.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Istnieją dwa sposoby, aby wskazać, że znaki mają być interpretowane jako znaki literału, a nie jako znaki rezerwowe, aby mogły być zawarte w ciągu wynikowym lub pomyślnie przeanalizowane w ciągu wejściowym:

- Przez ucieczkę każdego zastrzeżonego znaku. Aby uzyskać więcej informacji, zobacz [Używanie znaku ucieczki](#escape).

Poniższy przykład zawiera znaki literału "PST" (w przypadku standardowego czasu pacyficznego) reprezentujące lokalną strefę czasową w ciągu formatu. Ponieważ zarówno "s", jak i "t" są ciągami formatu niestandardowego, oba znaki muszą zostać poddane ucieczki, aby były interpretowane jako literały znakowe.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Umieszczając cały ciąg literału w cudzysłowach lub apostrofach. Poniższy przykład przypomina poprzednią, z tą różnicą, że "PST" jest ujęty w cudzysłów, aby wskazać, że cały ciąg rozdzielany powinien być interpretowany jako literały znakowe.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Uwagi

### <a name="UsingSingleSpecifiers"></a>Używanie pojedynczego specyfikatora formatu niestandardowego

Ciąg niestandardowego formatu daty i godziny składa się z co najmniej dwóch znaków. Metody formatowania daty i godziny interpretują każdy jednoznakowy ciąg jako ciąg standardowego formatu daty i godziny. Jeśli nie rozpoznają znaku jako prawidłowego specyfikatora formatu, generują <xref:System.FormatException>. Na przykład ciąg formatu, który składa się tylko ze specyfikatora „h”, jest interpretowany jako ciąg standardowego formatu daty i godziny. Jednak w tym konkretnym przypadku wyjątek jest zgłaszany z powodu braku standardowego specyfikatora daty i TimeFormat "h".

Aby użyć jakiegokolwiek specyfikatora niestandardowego formatu daty i godziny jako jedynego specyfikatora w ciągu formatu (tj. użyć samego specyfikatora formatu niestandardowego „d”, „f”, „F”, „g”, „h”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/”), należy przed lub za specyfikatorem umieścić spację albo umieścić specyfikator formatu procent („%”) przed pojedynczym specyfikatorem niestandardowego formatu daty i godziny.

Na przykład "`%h"` jest interpretowany jako ciąg niestandardowego formatu daty i godziny, który wyświetla godzinę reprezentowane przez bieżącą wartość daty i godziny. Można także użyć ciągu formatu „ h” lub „h ”, mimo że zawierają w ciągu wynikowym i spację, i godzinę. W poniższym przykładzie pokazano te trzy ciągi formatu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a>Używanie znaku ucieczki

Znaki „D”, „f”, „F”, „G”, „g”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/” w ciągu formatu są interpretowane jako specyfikatory formatu niestandardowego, a nie jako znaki literału. Aby zapobiec interpretacji znaku jako specyfikatora formatu, można poprzedzić go ukośnikiem odwrotnym (\\), który jest znakiem ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.

Aby uwzględnić ukośnik odwrotny w ciągu wynikowym, należy go wypróbować przy użyciu innego ukośnika odwrotnego (`\\`).

> [!NOTE]
> Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.

W poniższym przykładzie użyto znaku ucieczki, aby uniemożliwić operacji formatowania interpretowanie znaków „h” i „m” jako specyfikatorów formatu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Ustawienia panelu sterowania

Ustawienia **Opcje regionalne i językowe** w panelu sterowania wpływają na ciąg wynikowy generowany przez operację formatowania, która zawiera wiele specyfikatorów niestandardowego formatu daty i godziny. Te ustawienia są używane do inicjowania obiektu <xref:System.Globalization.DateTimeFormatInfo> skojarzonego z bieżącą kulturą wątku, która zapewnia wartości używane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto, jeśli używasz konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> do utworzenia wystąpienia nowego obiektu <xref:System.Globalization.CultureInfo>, który reprezentuje tę samą kulturę co bieżąca kultura systemu, wszelkie dostosowania ustanowione przez element **Opcje regionalne i językowe** w panelu sterowania będą zastosowano do nowego obiektu <xref:System.Globalization.CultureInfo>. Można użyć konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>, aby utworzyć obiekt <xref:System.Globalization.CultureInfo>, który nie odzwierciedla dostosowań systemu.

### <a name="datetimeformatinfo-properties"></a>Właściwości DateTimeFormatInfo

Na formatowanie mają wpływ właściwości bieżącego obiektu <xref:System.Globalization.DateTimeFormatInfo>, który jest dostarczany niejawnie przez bieżącą kulturę wątku lub jawnie przez parametr <xref:System.IFormatProvider> metody, która wywołuje formatowanie. Dla parametru <xref:System.IFormatProvider> należy określić obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę lub obiekt <xref:System.Globalization.DateTimeFormatInfo>.

Ciąg wynikowy utworzony przez wiele specyfikatorów niestandardowego formatu daty i godziny zależy również od właściwości bieżącego obiektu <xref:System.Globalization.DateTimeFormatInfo>. Aplikacja może zmienić wynik tworzony przez niektóre specyfikatory niestandardowego formatu daty i godziny przez zmianę odpowiedniej właściwości <xref:System.Globalization.DateTimeFormatInfo>. Na przykład specyfikator formatu "ddd" dodaje skróconą nazwę dnia tygodnia znalezioną w tablicy ciągów <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> do ciągu wynikowego. Podobnie, specyfikator formatu "MMMM" dodaje pełną nazwę miesiąca znalezioną w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> tablicy ciągów do ciągu wynikowego.

## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Przykład: Narzędzie do formatowania narzędzi systemu .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Przykład: Narzędzie formatowania programu .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
