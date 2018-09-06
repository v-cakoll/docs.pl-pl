---
title: Niestandardowe ciągi formatujące datę i godzinę
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab14be82f3dedeab0a1e1e574ce5622d067f72ae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43789020"
---
# <a name="custom-date-and-time-format-strings"></a>Niestandardowe ciągi formatujące datę i godzinę

Ciąg formatu daty i godziny definiuje reprezentację tekstową <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartość będącą wynikiem operacji formatowania. Może także definiować reprezentację wartości daty i godziny, która jest wymagana w operacji analizowania składni w celu pomyślnego przekonwertowania ciągu na datę i godzinę. Ciąg formatu niestandardowego składa się z co najmniej jednego specyfikatora niestandardowego formatu daty i godziny. Dowolny ciąg, który nie jest [ciąg formatu standardowego daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) jest interpretowana jako niestandardowy ciąg daty i godziny formatu.

> [!TIP]
> Możesz pobrać [narzędzie do formatowania](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikację, która umożliwia zastosowanie formatu ciągów do daty i godziny lub wartości liczbowych oraz wyświetlenie ciągu wynikowego.

 Niestandardowa data i ciągi formatu czasu mogą być używane z obu <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-note.md)] 

<a name="table"></a> W operacjach formatowania niestandardowych ciągów daty i godziny format mogą być używane, za pomocą `ToString` metodę wystąpienia daty i godziny lub z metodą, która obsługuje formatowanie złożone. W poniższym przykładzie pokazano oba te zastosowania.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

 Podczas operacji analizowania, niestandardowych ciągów daty i godziny formatu może służyć za pomocą <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody. Aby operacja analizowania mogła zakończyć się pomyślnie, w tych metodach wymagane jest, aby ciąg wejściowy dokładnie pasował do określonego wzorca. W poniższym przykładzie pokazano wywołanie <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody w celu przeanalizowania daty, która musi zawierać dzień, miesiąc i rok w postaci dwóch cyfr.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
 [!code-vb[Formatting.DateAndTime.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

 W poniższej tabeli opisano specyfikatory niestandardowego formatu daty i godziny oraz pokazano ciąg wynikowy utworzony przez każdy specyfikator formatu. Domyślnie ciągi wynikowe odzwierciedlają konwencje formatowania kultury en-US. Jeśli określony specyfikator formatu generuje zlokalizowany ciąg wynikowy, w przykładzie wymieniono też kulturę, której dotyczy ciąg wynikowy. Zobacz sekcję Uwagi, aby uzyskać dodatkowe informacje dotyczące używania ciągów niestandardowego formatu daty i godziny.

| Specyfikator formatu | Opis | Przykłady |
| ---------------------- | ----------------- | -------------- |
|„d”|Dzień miesiąca z zakresu od 1 do 31.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "d"](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -&GT; 15|
|„dd”|Dzień miesiąca z zakresu od 01 do 31.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "dd"](#ddSpecifier).|2009-06-01T13:45:30 -&GT; 01<br /><br /> 2009-06-15T13:45:30 -&GT; 15|
|„ddd”|Skrócona nazwa dnia tygodnia.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ddd"](#dddSpecifier).|2009-06-15T13:45:30 -> Mon (en US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> jednostki lun. (fr-FR)|
|„dddd”|Pełna nazwa dnia tygodnia.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "dddd"](#ddddSpecifier).|2009-06-15T13:45:30 -> poniedziałek (pl pl)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|„f”|Liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "f"](#fSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-15T13:45:30.05 -&GT; 0|
|„ff”|Liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ff"](#ffSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -&GT; 00|
|„fff”|Liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fff"](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|
|„ffff”|Liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ffff"](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -&GT; 6175<br /><br /> 2009-06-15T13:45:30.0000500 -&GT; 0000|
|„fffff”|Liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffff"](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|
|„ffffff”|Liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ffffff"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -&GT; 000000|
|„fffffff”|Liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "fffffff"](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 0001150|
|„F”|Jeśli wartość jest różna od zera, liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "F"](#F_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (Brak danych wyjściowych)|
|„FF”|Jeśli wartość jest różna od zera, liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#FF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (Brak danych wyjściowych)|
|„FFF”|Jeśli wartość jest różna od zera, liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (Brak danych wyjściowych)|
|„FFFF”|Jeśli wartość jest różna od zera, liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -&GT; 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (Brak danych wyjściowych)|
|„FFFFF”|Jeśli wartość jest różna od zera, liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFF"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (Brak danych wyjściowych)|
|„FFFFFF”|Jeśli wartość jest różna od zera, liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (Brak danych wyjściowych)|
|„FFFFFFF”|Jeśli wartość jest różna od zera, liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 000115|
|„g”, „gg”|Okres lub era.<br /><br /> Więcej informacji: ["g" lub "gg" specyfikator formatu niestandardowego](#gSpecifier).|2009-06-15T13:45:30.6170000 -&GT; N.E.|
|„h”|Godzina; używany jest zegar 12-godzinny (wartości od 1 do 12).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "h"](#hSpecifier).|2009-06-15T01:45:30 -&GT; 1<br /><br /> 2009-06-15T13:45:30 -&GT; 1|
|„hh”|Godzina; używany jest zegar 12-godzinny (wartości od 01 do 12).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "hh"](#hhSpecifier).|2009-06-15T01:45:30 -&GT; 01<br /><br /> 2009-06-15T13:45:30 -&GT; 01|
|„H”|Godzina; używany zegar 24-godzinny z zakresu od 0 do 23.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "H"](#H_Specifier).|2009-06-15T01:45:30 -&GT; 1<br /><br /> 2009-06-15T13:45:30 -&GT; 13|
|„HH”|Godzina; używany jest zegar 24-godzinny (wartości od 00 do 23).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "HH"](#HH_Specifier).|2009-06-15T01:45:30 -&GT; 01<br /><br /> 2009-06-15T13:45:30 -&GT; 13|
|„K”|Informacje o strefie czasowej.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "K"](#KSpecifier).|Za pomocą <xref:System.DateTime> wartości:<br /><br /> 2009-06-15T13:45:30, rodzaj nieokreślony--><br /><br /> 2009-06-15T13:45:30, rodzaju Utc -> Z<br /><br /> 2009-06-15T13:45:30, rodzaj lokalny->-07:00 (zależy od ustawień komputera lokalnego)<br /><br /> Za pomocą <xref:System.DateTimeOffset> wartości:<br /><br /> 2009-06-15T01:45:30-07:00--&GT; -07:00<br /><br /> 2009-06---&GT; 15T08:45:30 + 00:00 + 00:00|
|„m”|Minuta; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "m"](#mSpecifier).|2009-06-15T01:09:30 -&GT; 9<br /><br /> 2009-06-15T13:29:30 -&GT; 29|
|„mm”|Minuta; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "mm"](#mmSpecifier).|2009-06-15T01:09:30 -&GT; 09<br /><br /> 2009-06-15T01:45:30 -&GT; 45|
|„M”|Miesiąc; wartości z zakresu od 1 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "M"](#M_Specifier).|2009-06-15T13:45:30 -&GT; 6|
|„MM”|Miesiąc; wartości z zakresu od 01 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MM"](#MM_Specifier).|2009-06-15T13:45:30 -&GT; 06|
|„MMM”|Skrócona nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMM"](#MMM_Specifier).|2009-06-15T13:45:30 -> cze (en US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> cze (zu ZA)|
|„MMMM”|Pełna nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30 -> czerwca (pl pl)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|„s”|Sekunda; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "s"](#sSpecifier).|2009-06-15T13:45:09 -&GT; 9|
|„ss”|Sekunda; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "ss"](#ssSpecifier).|2009-06-15T13:45:09 -&GT; 09|
|„t”|Pierwszy znak oznaczenia AM/PM.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "t"](#tSpecifier).|2009-06-15T13:45:30 -> P (en US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|„tt”|Oznaczenie AM/PM.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "tt"](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|„y”|Rok; wartości z zakresu od 0 do 99.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "y"](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -&GT; 9<br /><br /> 2019-06-15T13:45:30 -&GT; 19|
|„yy”|Rok; wartości z zakresu od 00 do 99.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "yy"](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -&GT; 19|
|„yyy”|Rok; co najmniej trzy cyfry.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "yyy"](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|
|„yyyy”|Rok jako liczba czterocyfrowa.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "yyyy"](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|
|„yyyyy”|Rok jako liczba pięciocyfrowa.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -&GT; 02009|
|„z”|Przesunięcie godzinowe względem czasu UTC, bez zer wiodących.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "z"](#zSpecifier).|2009-06-15T13:45:30-07:00 -&GT; -7|
|„zz”|Przesunięcie godzinowe względem czasu UTC, z zerem wiodącym dla wartości jednocyfrowych.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "zz"](#zzSpecifier).|2009-06-15T13:45:30-07:00-&GT;-07|
|„zzz”|Godzinowe i minutowe przesunięcie względem czasu UTC.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "zzz"](#zzzSpecifier).|2009-06-15T13:45:30-07:00-&GT;-07:00|
|":"|Separator godziny.<br /><br /> Więcej informacji: [":" specyfikator formatu niestandardowego](#timeSeparator).|2009-06-15T13:45:30 ->: (en US)<br /><br /> 2009-06-15T13:45:30 -&GT;. (it-IT)<br /><br /> 2009-06-15T13:45:30 ->: (ja-JP)|
|"/"|Separator daty.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (en US)<br /><br /> 2009-06-15T13:45:30 -> - (ar DZ)<br /><br /> 2009-06-15T13:45:30 -&GT;. (tr-TR)|
|"*ciąg*"<br /><br /> "*ciąg*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [literały znakowe](#Literals).|2009-06-15T13:45:30 ("arr:" g t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ("arr:" g t) -> arr: 1:45 P|
|%|Definiuje następujący znak jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji:[używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|
|\\| Znak ucieczki.<br /><br /> Więcej informacji: [literały znakowe](#Literals) i [korzystając ze znaku ucieczki](#escape).|2009-06-15T13:45:30 (h \h) -> 1 godz.|
|Jakikolwiek inny znak|Znak jest kopiowany do ciągu wynikowego bez zmian.<br /><br /> Więcej informacji: [literały znakowe](#Literals).|2009-06-15T01:45:30 (AAR gg: mm t) -> arr 01:45 a|

 W poniższych sekcjach przedstawiono dodatkowe informacje dotyczące poszczególnych specyfikatorów niestandardowego formatu daty i godziny. Jeśli nie określono inaczej, każdy specyfikator wytwarza identyczną reprezentację ciągu niezależnie od tego, czy jest użyty z <xref:System.DateTime> wartość lub <xref:System.DateTimeOffset> wartość.

<a name="dSpecifier"></a> 

## <a name="the-d-custom-format-specifier"></a>Specyfikator formatu niestandardowego "d"
 Specyfikator formatu niestandardowego „d” oznacza dzień miesiąca w postaci liczby z zakresu od 1 do 31. Dzień oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

 Jeśli specyfikator formatu „d” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „d”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „d” jest używany w kilku ciągach formatu.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

 [Powrót do tabeli](#table)

<a name="ddSpecifier"></a> 

## <a name="the-dd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "dd"
 Ciąg formatu niestandardowego „dd” przedstawia dzień miesiąca w postaci liczby z zakresu od 01 do 31. Dzień oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „dd” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

 [Powrót do tabeli](#table)

<a name="dddSpecifier"></a> 

## <a name="the-ddd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ddd"
 Specyfikator formatu niestandardowego „ddd” przedstawia skróconą nazwę dnia tygodnia. Zlokalizowana skrócona nazwa dnia tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

 W poniższym przykładzie specyfikator formatu niestandardowego „ddd” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

 [Powrót do tabeli](#table)

<a name="ddddSpecifier"></a> 

## <a name="the-dddd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "dddd"
 Specyfikator formatu niestandardowego „dddd” (plus dowolna liczba dodatkowych specyfikatorów „d”) oznacza pełną nazwę dnia tygodnia. Zlokalizowana nazwa dnia tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

 W poniższym przykładzie specyfikator formatu niestandardowego „dddd” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

 [Powrót do tabeli](#table)

<a name="fSpecifier"></a> 

## <a name="the-f-custom-format-specifier"></a>Specyfikator formatu niestandardowego "f"
 Specyfikator formatu niestandardowego „f” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny.

 Jeśli specyfikator formatu „f” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „f”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 Kiedy używasz specyfikatorów formatu "f" jako części ciągu formatu dostarczonego do <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, lub <xref:System.DateTimeOffset.TryParseExact%2A> metody, liczba specyfikatorów formatu "f" wskazuje liczbę najbardziej znaczących cyfr części sekund który musi być obecna, aby pomyślnie przeanalizować składni ciągu.

 W poniższym przykładzie specyfikator formatu niestandardowego „f” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="ffSpecifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ff"
 Specyfikator formatu niestandardowego „ff” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny.

 W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="fffSpecifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "fff"
 Specyfikator formatu niestandardowego „fff” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny.

 W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="ffffSpecifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ffff"
 Specyfikator formatu niestandardowego „ffff” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny.

 Chociaż istnieje możliwość wyświetlenia liczby dziesięciotysięcznych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="fffffSpecifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "fffff"
 Specyfikator formatu niestandardowego „fffff” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny.

 Chociaż istnieje możliwość wyświetlenia liczby stutysięcznych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="ffffffSpecifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ffffff"
 Specyfikator formatu niestandardowego „ffffff” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny.

 Chociaż istnieje możliwość wyświetlenia liczby milionowych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="fffffffSpecifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "fffffff"
 Specyfikator formatu niestandardowego „fffffff” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny.

 Chociaż istnieje możliwość wyświetlenia liczby dziesięciomilionowych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="F_Specifier"></a> 

## <a name="the-f-custom-format-specifier"></a>Specyfikator formatu niestandardowego "F"
 Specyfikator formatu niestandardowego „F” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.

 Jeśli specyfikator formatu „F” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „F”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 Liczba specyfikatorów formatu "F" używane z <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, lub <xref:System.DateTimeOffset.TryParseExact%2A> metoda wskazuje maksymalną liczbę najbardziej znaczących cyfr części sekund, które mogą być obecna, aby pomyślnie przeanalizować składni ciągu.

 W poniższym przykładzie specyfikator formatu niestandardowego „F” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="FF_Specifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FF"
 Specyfikator formatu niestandardowego „FF” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny. Jednak końcowe zera lub dwuzerowe liczby nie są wyświetlane.

 W poniższym przykładzie specyfikator formatu niestandardowego „FF” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="FFF_Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFF"
 Specyfikator formatu niestandardowego „FFF” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny. Jednak końcowe zera lub trzyzerowe liczby nie są wyświetlane.

 W poniższym przykładzie specyfikator formatu niestandardowego „FFF” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [Powrót do tabeli](#table)

<a name="FFFF_Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFFF"
 Specyfikator formatu niestandardowego „FFFF” przedstawia cztery najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę dziesięciotysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub czterozerowe liczby nie są wyświetlane.

 Chociaż istnieje możliwość wyświetlenia liczby dziesięciotysięcznych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="FFFFF_Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFFFF"
 Specyfikator formatu niestandardowego „FFFFF” przedstawia pięć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę stutysięcznych części sekundy w wartości daty i godziny. Jednak końcowe zera lub pięciozerowe liczby nie są wyświetlane.

 Chociaż istnieje możliwość wyświetlenia liczby stutysięcznych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="FFFFFF_Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFFFFF"
 Specyfikator formatu niestandardowego „FFFFFF” przedstawia sześć najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę milionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub sześciozerowe liczby nie są wyświetlane.

 Chociaż istnieje możliwość wyświetlenia liczby milionowych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="FFFFFFF_Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFFFFFF"
 Specyfikator formatu niestandardowego „FFFFFFF” przedstawia siedem najbardziej znaczących cyfr części sekund, czyli przedstawia liczbę dziesięciomilionowych części sekundy w wartości daty i godziny. Jednak końcowe zera lub siedmiozerowe liczby nie są wyświetlane.

 Chociaż istnieje możliwość wyświetlenia liczby dziesięciomilionowych części sekundy z wartości godziny, ta wartość może nie mieć znaczenia. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT w wersji 3.5 (oraz nowszych) i Windows Vista rozdzielczość zegara wynosi około 10–15 milisekund.

 [Powrót do tabeli](#table)

<a name="gSpecifier"></a> 

## <a name="the-g-or-gg-custom-format-specifier"></a>Specyfikator formatu niestandardowego "g" lub "gg"
 Specyfikator formatu niestandardowego „g” lub „gg” (plus dowolna liczba dodatkowych specyfikatorów „g”) przedstawia okres lub erę, taką jak n.e. Operacja formatowania ignoruje ten specyfikator, jeśli z datą, która ma być formatowana, nie jest skojarzony ciąg okresu lub ery.

 Jeśli specyfikator formatu „g” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „g”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „g” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

 [Powrót do tabeli](#table)

<a name="hSpecifier"></a> 

## <a name="the-h-custom-format-specifier"></a>Specyfikator formatu niestandardowego "h"
 Specyfikator formatu niestandardowego „h” przedstawia godzinę jako liczbę z zakresu od 1 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „5”.

 Jeśli specyfikator formatu "h" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy daty i specyfikator formatu godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „h” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [Powrót do tabeli](#table)

<a name="hhSpecifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>Specyfikator formatu niestandardowego "hh"
 Specyfikator formatu niestandardowego „hh” (plus dowolna liczba dodatkowych specyfikatorów „h”) przedstawia godzinę jako liczbę z zakresu od 01 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „05”.

 W poniższym przykładzie specyfikator formatu niestandardowego „hh” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [Powrót do tabeli](#table)

<a name="H_Specifier"></a> 

## <a name="the-h-custom-format-specifier"></a>Specyfikator formatu niestandardowego "H"
 Specyfikator formatu niestandardowego „H” przedstawia godzinę jako liczbę z zakresu od 0 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

 Jeśli specyfikator formatu "H" jest używany bez innych specyfikatorów formatu niestandardowego, jest interpretowany jako standardowy daty i specyfikator formatu godziny i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „H” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

 [Powrót do tabeli](#table)

<a name="HH_Specifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>Specyfikator formatu niestandardowego "HH"
 Specyfikator formatu niestandardowego „HH” (plus dowolna liczba dodatkowych specyfikatorów „H”) przedstawia godzinę jako liczbę z zakresu od 00 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „HH” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

 [Powrót do tabeli](#table)

<a name="KSpecifier"></a> 

## <a name="the-k-custom-format-specifier"></a>Specyfikator formatu niestandardowego "K"
 Specyfikator formatu niestandardowego „K” przedstawia informacje o strefie czasowej z wartości daty i godziny. Gdy ten specyfikator formatu jest używany z <xref:System.DateTime> wartości, ciąg wynikowy jest definiowany przez wartość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości:

-   Dla lokalnej strefy czasowej ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), ten specyfikator jest równoważny specyfikatorowi "zzz" i daje ciąg wynikowy zawierający lokalne przesunięcie względem uniwersalnego czasu koordynowanego (UTC), na przykład, "-07:00".

-   Czas UTC ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), ciąg wynikowy zawiera znak "Z" reprezentującą datę w formacie UTC.

-   Przypadku nieokreślonej strefy czasowej (czas którego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości jest równa <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), wynik jest równoważny <xref:System.String.Empty?displayProperty=nameWithType>.

 Aby uzyskać <xref:System.DateTimeOffset> wartości, specyfikator formatu "K" jest równoważny specyfikatorowi formatu "zzz" i tworzy ciąg wyniku zawierający <xref:System.DateTimeOffset> wartość przesunięcie względem czasu UTC.

 Jeśli specyfikator formatu "K" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy format daty i specyfikator formatu godziny i będzie zgłaszać <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 Poniższy przykład wyświetla ciąg, który jest wynikiem użycia specyfikatora formatu niestandardowego "K" z różnymi <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości w systemie, w Stanach Zjednoczonych Strefa czasowa czasu pacyficznego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

 [Powrót do tabeli](#table)

<a name="mSpecifier"></a> 

## <a name="the-m-custom-format-specifier"></a>Specyfikator formatu niestandardowego "m"
 Specyfikator formatu niestandardowego „m” przedstawia minutę jako liczbę z zakresu od 0 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

 Jeśli specyfikator formatu „m” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „m”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „m” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [Powrót do tabeli](#table)

<a name="mmSpecifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>"Mm" niestandardowego specyfikatora formatu.
 Specyfikator formatu niestandardowego „mm” (plus dowolna liczba dodatkowych specyfikatorów „m”) przedstawia minutę jako liczbę z zakresu od 00 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „mm” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [Powrót do tabeli](#table)

<a name="M_Specifier"></a> 

## <a name="the-m-custom-format-specifier"></a>Specyfikator formatu niestandardowego "M"
 Specyfikator formatu niestandardowego „M” przedstawia miesiąc jako liczbę z zakresu od 1 do 12 (lub od 1 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany bez zera wiodącego.

 Jeśli specyfikator formatu „M” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „M”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „M” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

 [Powrót do tabeli](#table)

<a name="MM_Specifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MM"
 Specyfikator formatu niestandardowego „MM” przedstawia miesiąc jako liczbę z zakresu od 01 do 12 (lub od 01 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „MM” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

 [Powrót do tabeli](#table)

<a name="MMM_Specifier"></a> 

## <a name="the-mmm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MMM"
 Specyfikator formatu niestandardowego „MMM” przedstawia skróconą nazwę miesiąca. Zlokalizowana skrócona nazwa miesiąca jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

 W poniższym przykładzie specyfikator formatu niestandardowego „MMM” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

 [Powrót do tabeli](#table)

<a name="MMMM_Specifier"></a> 

## <a name="the-mmmm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MMMM"
 Specyfikator formatu niestandardowego „MMMM” przedstawia pełną nazwę miesiąca. Zlokalizowana nazwa miesiąca jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

 W poniższym przykładzie specyfikator formatu niestandardowego „MMMM” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

 [Powrót do tabeli](#table)

<a name="sSpecifier"></a> 

## <a name="the-s-custom-format-specifier"></a>Specyfikator formatu niestandardowego "s"
 Specyfikator formatu niestandardowego „s” przedstawia sekundy jako liczbę z zakresu od 0 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana bez zera wiodącego.

 Jeśli specyfikator formatu „s” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „s”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „s” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [Powrót do tabeli](#table)

<a name="ssSpecifier"></a> 

## <a name="the-ss-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ss"
 Specyfikator formatu niestandardowego „s” (plus dowolna liczba dodatkowych specyfikatorów „s”) przedstawia sekundy jako liczbę z zakresu od 00 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „ss” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [Powrót do tabeli](#table)

<a name="tSpecifier"></a> 

## <a name="the-t-custom-format-specifier"></a>Specyfikator formatu niestandardowego "t"
 Specyfikator formatu niestandardowego „t” przedstawia pierwszy znak oznaczenia AM/PM. Odpowiednie zlokalizowane określenie daty jest pobierany z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

 Jeśli specyfikator formatu „t” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „t”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „t” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [Powrót do tabeli](#table)

<a name="ttSpecifier"></a> 

## <a name="the-tt-custom-format-specifier"></a>Specyfikator formatu niestandardowego "tt"
 Specyfikator formatu niestandardowego „tt” (plus dowolna liczba dodatkowych specyfikatorów „t”) przedstawia całe oznaczenie AM/PM. Odpowiednie zlokalizowane określenie daty jest pobierany z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.

 Należy pamiętać, aby używać specyfikatora „tt” w przypadku języków, dla których wymagane jest zachowanie rozróżnienia między oznaczeniami AM i PM. Przykładem jest język japoński, dla którego oznaczenia AM i PM różnią się w drugim znaku, a nie w pierwszym znaku.

 W poniższym przykładzie specyfikator formatu niestandardowego „tt” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [Powrót do tabeli](#table)

<a name="ySpecifier"></a> 

## <a name="the-y-custom-format-specifier"></a>Specyfikator formatu niestandardowego "y"
 Specyfikator formatu niestandardowego „y” przedstawia rok jako jedno- lub dwucyfrową liczbę. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeżeli pierwsza cyfra roku dwucyfrowego rozpoczyna się od zera (na przykład, 2008), liczba jest formatowana bez zera wiodącego.

 Jeśli specyfikator formatu „y” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „y”. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „y” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [Powrót do tabeli](#table)

<a name="yySpecifier"></a> 

## <a name="the-yy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yy"
 Specyfikator formatu niestandardowego „yy” przedstawia rok jako liczbę dwucyfrową. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeśli rok dwucyfrowy ma mniej niż dwie cyfry znaczące, liczba jest dopełniana wiodącymi zerami w celu utworzenia dwóch cyfr.

 Podczas operacji analizowania dwucyfrowy rok, który jest analizowany przy użyciu specyfikatora formatu niestandardowego "yy" jest interpretowany na podstawie <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> właściwości bieżącego kalendarza dostawcy formatu. W poniższym przykładzie jest analizowany ciąg przedstawiając datę, która ma domyślnie dwucyfrowy rok według domyślnego kalendarza gregoriańskiego w kulturze en-US, która w tym przypadku jest bieżącą kulturą. Następnie zmienia bieżącą kulturę <xref:System.Globalization.CultureInfo> obiekt ma być używany <xref:System.Globalization.GregorianCalendar> którego <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> właściwość została zmodyfikowana.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
 [!code-vb[Formatting.DateAndTime.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

 W poniższym przykładzie specyfikator formatu niestandardowego „yy” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [Powrót do tabeli](#table)

<a name="yyySpecifier"></a> 

## <a name="the-yyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyy"
 Specyfikator formatu niestandardowego „yyy” przedstawia rok za pomocą co najmniej trzech cyfr. Jeśli rok ma więcej niż trzy cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż trzy cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia trzech cyfr.

> [!NOTE]
>  W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie wszystkich cyfr znaczących.

 W poniższym przykładzie specyfikator formatu niestandardowego „yyy” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [Powrót do tabeli](#table)

<a name="yyyySpecifier"></a> 

## <a name="the-yyyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyyy"
 Specyfikator formatu niestandardowego „yyyy” przedstawia rok za pomocą co najmniej czterech cyfr. Jeśli rok ma więcej niż cztery cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż cztery cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia czterech cyfr.

> [!NOTE]
>  W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie co najmniej czterech cyfr.

 W poniższym przykładzie specyfikator formatu niestandardowego „yyyy” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [Powrót do tabeli](#table)

<a name="yyyyySpecifier"></a> 

## <a name="the-yyyyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyyyy"
 Specyfikator formatu niestandardowego „yyyyy” (plus dowolna liczba dodatkowych specyfikatorów „y”) przedstawia rok za pomocą co najmniej pięciu cyfr. Jeśli rok ma więcej niż pięć cyfr znaczących, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż pięć cyfr, liczba jest dopełniana zerami wiodącymi w celu utworzenia pięciu cyfr.

 Jeśli istnieją dodatkowe specyfikatory „y”, liczba jest dopełniana tak wieloma zerami wiodącymi, jak jest to konieczne, aby utworzyć liczbę specyfikatorów „y”.

 W poniższym przykładzie specyfikator formatu niestandardowego „yyyyy” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [Powrót do tabeli](#table)

<a name="zSpecifier"></a> 

## <a name="the-z-custom-format-specifier"></a>Specyfikator formatu niestandardowego "z"
 Za pomocą <xref:System.DateTime> wartości, specyfikator formatu niestandardowego "z" reprezentuje oznaczone przesunięcie strefy czasu lokalnego systemu operacyjnego z uniwersalnego czasu koordynowanego (UTC), mierzonego w godzinach. Nie odzwierciedla wartości wystąpienia <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikator formatu "z" nie jest zalecane do użytku z programem <xref:System.DateTime> wartości.

 Za pomocą <xref:System.DateTimeOffset> wartości, ten specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość przesunięcie względem czasu UTC w godzinach.

 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane bez zera wiodącego.

 Jeśli specyfikator formatu "z" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy format daty i specyfikator formatu godziny i będzie zgłaszać <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 W poniższym przykładzie specyfikator formatu niestandardowego „z” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [Powrót do tabeli](#table)

<a name="zzSpecifier"></a> 

## <a name="the-zz-custom-format-specifier"></a>Specyfikator formatu niestandardowego "zz"
 Za pomocą <xref:System.DateTime> wartości, specyfikator formatu niestandardowego "zz" reprezentuje oznaczone przesunięcie strefy czasu lokalnego systemu operacyjnego względem czasu UTC, mierzone w godzinach. Nie odzwierciedla wartości wystąpienia <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikator formatu "zz" nie jest zalecane do użytku z programem <xref:System.DateTime> wartości.

 Za pomocą <xref:System.DateTimeOffset> wartości, ten specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość przesunięcie względem czasu UTC w godzinach.

 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „zz” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [Powrót do tabeli](#table)

<a name="zzzSpecifier"></a> 

## <a name="the-zzz-custom-format-specifier"></a>Specyfikator formatu niestandardowego "zzz"
 Za pomocą <xref:System.DateTime> wartości, specyfikator formatu niestandardowego "zzz" reprezentuje oznaczone przesunięcie strefy czasu lokalnego systemu operacyjnego względem czasu UTC, mierzone w godzinach i minutach. Nie odzwierciedla wartości wystąpienia <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikator formatu "zzz" nie jest zalecane do użytku z programem <xref:System.DateTime> wartości.

 Za pomocą <xref:System.DateTimeOffset> wartości, ten specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość przesunięcie względem czasu UTC w godzinach i minutach.

 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.

 W poniższym przykładzie specyfikator formatu niestandardowego „zzz” jest używany w ciągu formatu niestandardowego.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [Powrót do tabeli](#table)

<a name="timeSeparator"></a> 

## <a name="the--custom-format-specifier"></a>":" Specyfikator formatu niestandardowego
 Specyfikator formatu niestandardowego „:” przedstawia separator godzin, który jest używany do odróżnienia godzin, minut i sekund. Odpowiedni zlokalizowany separator godziny jest pobierany z <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

> [!NOTE]
>  Aby zmienić separator godziny dla określonej ciąg daty i godziny, należy określić znak separatora w ciągu Ogranicznik ciągu literału. Na przykład ciąg formatu niestandardowego `hh'_'dd'_'ss` daje ciąg wynikowy, w którym "\_" (podkreślenie) zawsze jest używany jako separator godziny. Aby zmienić separator godziny dla wszystkich dat dla kultury, zmień wartość <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> właściwości bieżącego kulturze lub wystąpienia <xref:System.Globalization.DateTimeFormatInfo> obiektu, należy przypisać znak do jego <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> właściwości i wywoływać przeciążenia Metoda, która obejmuje formatowania <xref:System.IFormatProvider> parametru.

 Jeśli ":" specyfikator formatu jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy format daty i specyfikator formatu godziny i będzie zgłaszać <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 [Powrót do tabeli](#table)

<a name="dateSeparator"></a> 

## <a name="the--custom-format-specifier"></a>Specyfikator formatu niestandardowego "/"
 Specyfikator formatu niestandardowego „/” oznacza separator daty, który jest używany do odróżnienia lat, miesięcy i dni. Odpowiedni zlokalizowany separator daty jest pobierany z <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> właściwości bieżącej lub określonej kultury.

> [!NOTE]
>  Aby zmienić separator daty dla konkretnego ciąg daty i godziny, należy określić znak separatora w ciągu Ogranicznik ciągu literału. Na przykład ciąg formatu niestandardowego `mm'/'dd'/'yyyy` daje ciąg wynikowy, w którym "/" zawsze jest używany jako separator daty. Aby zmienić separator daty dla wszystkich dat dla kultury, zmień wartość <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> właściwości bieżącego kulturze lub wystąpienia <xref:System.Globalization.DateTimeFormatInfo> obiektu, należy przypisać znak do jego <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> właściwości i wywoływać przeciążenia Metoda, która obejmuje formatowania <xref:System.IFormatProvider> parametru.

 Jeśli specyfikator formatu "/" jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako standardowy format daty i specyfikator formatu godziny i będzie zgłaszać <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu pojedynczego specyfikatora formatu, zobacz [używanie pojedynczego specyfikatora formatu](#UsingSingleSpecifiers) w dalszej części tego tematu.

 [Powrót do tabeli](#table)

<a name="Literals"></a> 

## <a name="character-literals"></a>Literały znakowe
 Następujące znaki w niestandardowych daty i godziny w ciągu formatu są zarezerwowane i są zawsze interpretowane jako formatowanie znaków lub w przypadku właściwości ",", /, a \\, jako znaki specjalne.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|g|h|m|s|
|t|t|z|%|:|
|/|"|'|\||

 Wszystkie inne znaki są zawsze interpretowane jako literały znakowe i, w operacji formatowania, są uwzględnione w ciągu wynikowym bez zmian.  Podczas operacji analizowania muszą one odpowiadać znaków w ciągu wejściowym dokładnie; w porównaniu jest uwzględniana wielkość liter.

 Poniższy przykład zawiera znaki literału "PST" (dla pacyficznego czasu standardowego) i "(PDT)" (dla czasu pacyficznego) do reprezentowania lokalnej strefy czasowej w ciągu formatu. Pamiętaj, że ciągu znajduje się w ciągu wynikowym ciąg, który zawiera ciąg strefy czasu lokalnego również analizowania pomyślnie.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
 [!code-vb[Formatting.DateAndTime.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

 Istnieją dwa sposoby, aby wskazać, że znaki mają być interpretowane jako znaki literału, a nie jako zarezerwowane znaki tak, aby mogą być zawarte w ciągu wynikowym lub pomyślnie przeanalizować ciągu wejściowego:

- Znak zastrzeżony przez każdy anulowania zapewnianego element. Aby uzyskać więcej informacji, zobacz [korzystając ze znaku ucieczki](#escape).
  
  Poniższy przykład zawiera znaki literału "pst" (dla pacyficznego czasu standardowego) do reprezentowania lokalnej strefy czasowej w ciągu formatu. Ponieważ "s" i "t" Tworzenie niestandardowych formatów ciągów, zarówno znaki należy użyć znaków ucieczki, aby być interpretowane jako literały znakowe.
  
  [!code-csharp-interactive[Formatting.DateAndTime.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
  [!code-vb[Formatting.DateAndTime.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Umieszczając cały ciąg literału w cudzysłowie lub w apostrofy. Poniższy przykład przypomina poprzedni, z tą różnicą, że "pst" jest ujęta w znaki cudzysłowu do wskazania, że cały ciąg rozdzielany powinno być interpretowane jako literały znaków.
  
  [!code-csharp-interactive[Formatting.DateAndTime.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
  [!code-vb[Formatting.DateAndTime.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

<a name="Notes"></a> 

## <a name="notes"></a>Uwagi

<a name="UsingSingleSpecifiers"></a> 

### <a name="using-single-custom-format-specifiers"></a>Za pomocą pojedynczego specyfikatora formatu niestandardowego
 Ciąg niestandardowego formatu daty i godziny składa się z co najmniej dwóch znaków. Metody formatowania daty i godziny interpretują każdy jednoznakowy ciąg jako ciąg standardowego formatu daty i godziny. Jeśli nie rozpoznają znaku jako specyfikatora prawidłowego formatu, rzuć <xref:System.FormatException>. Na przykład ciąg formatu, który składa się tylko ze specyfikatora „h”, jest interpretowany jako ciąg standardowego formatu daty i godziny. Jednak w tym konkretnym przypadku jest zwracany wyjątek ponieważ nie istnieje żadne "h" standardowy specyfikator daty i timeformat.

 Aby użyć jakiegokolwiek specyfikatora niestandardowego formatu daty i godziny jako jedynego specyfikatora w ciągu formatu (tj. użyć samego specyfikatora formatu niestandardowego „d”, „f”, „F”, „g”, „h”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/”), należy przed lub za specyfikatorem umieścić spację albo umieścić specyfikator formatu procent („%”) przed pojedynczym specyfikatorem niestandardowego formatu daty i godziny.

 Na przykład "`%h"` jest interpretowana jako niestandardowy daty i godziny ciąg formatu, który wyświetla wartości godziny w postaci wartości bieżącej daty i godziny. Można także użyć ciągu formatu „ h” lub „h ”, mimo że zawierają w ciągu wynikowym i spację, i godzinę. W poniższym przykładzie pokazano te trzy ciągi formatu.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
 [!code-vb[Formatting.DateAndTime.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

<a name="escape"></a> 

### <a name="using-the-escape-character"></a>Korzystając ze znaku unikowego
 Znaki „D”, „f”, „F”, „G”, „g”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/” w ciągu formatu są interpretowane jako specyfikatory formatu niestandardowego, a nie jako znaki literału. Aby zapobiec sytuacji, w której znak jest interpretowany jako specyfikator formatu, można poprzedzić go ukośnikiem odwrotnym (\\), który jest znakiem ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.

 Aby zawrzeć ukośnik odwrotny w ciągu wynikowym, musisz wyjść z niego używając innego ukośnika odwrotnego (`\\`).

> [!NOTE]
>  Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.

 W poniższym przykładzie użyto znaku ucieczki, aby uniemożliwić operacji formatowania interpretowanie znaków „h” i „m” jako specyfikatorów formatu.

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Ustawienia Panelu sterowania
 **Opcje regionalne i językowe** w Panelu sterowania mają wpływ na ciąg tworzony przez operację formatowania obejmującą wiele niestandardowych daty i godziny specyfikatorów formatu. Te ustawienia są stosowane do inicjalizacji <xref:System.Globalization.DateTimeFormatInfo> obiekt skojarzony z bieżącą kulturą wątku, która zapewnia wartości stosowane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

 Ponadto, jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Konstruktor do tworzenia wystąpienia nowego <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę samą kulturę co bieżąca kultura systemu, wszelkie dostosowania ustanowione przez **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Możesz użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor do tworzenia <xref:System.Globalization.CultureInfo> obiektu, który nie będzie odzwierciedlał dostosowań systemu.

### <a name="datetimeformatinfo-properties"></a>Właściwości DateTimeFormatInfo
 Formatowanie mają wpływ właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu, dostarczane niejawnie przez bieżącą kulturę wątku lub jawnie przez <xref:System.IFormatProvider> parametru metody, która wywołuje formatowanie. Aby uzyskać <xref:System.IFormatProvider> parametrów, należy określić <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, lub <xref:System.Globalization.DateTimeFormatInfo> obiektu.

 Ciąg wynikowy tworzony przez wiele niestandardowych daty i godziny specyfikatorów formatu zależy również od właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu. Twoja aplikacja może zmieniać wyniki tworzone przez niektóre niestandardowa data i czas specyfikatorów formatu, zmieniając odpowiadającą im <xref:System.Globalization.DateTimeFormatInfo> właściwości. Na przykład, specyfikator formatu "ddd" dodaje skrót nazwy dnia tygodnia w <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> tablicy ciągów do ciągu wynikowego. Podobnie, specyfikator formatu "MMMM" dodaje pełną nazwę miesiąca w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> tablicy ciągów do ciągu wynikowego.

## <a name="see-also"></a>Zobacz też
 <xref:System.DateTime?displayProperty=nameWithType><xref:System.IFormatProvider?displayProperty=nameWithType>
 [Typy formatowania](../../../docs/standard/base-types/formatting-types.md) [ciągi formatu standardowego daty i godziny](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) [próbki: narzędzie formatowania programu .NET Framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
