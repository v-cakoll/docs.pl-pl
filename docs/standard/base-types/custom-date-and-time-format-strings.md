---
title: Niestandardowe ciągi formatujące datę i godzinę
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c54a5ec9cdbfd73bccd8f70befcfcff7cf8aac2d
ms.sourcegitcommit: 6f967c86dde55472440f0c8669b0e910ee3c53ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="custom-date-and-time-format-strings"></a>Niestandardowe ciągi formatujące datę i godzinę
Ciąg formatu daty i godziny definiuje Reprezentacja tekstowa typu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartość będącą wynikiem operacji formatowania. Może także definiować reprezentację wartości daty i godziny, która jest wymagana w operacji analizowania składni w celu pomyślnego przekonwertowania ciągu na datę i godzinę. Ciąg formatu niestandardowego składa się z co najmniej jednego specyfikatora niestandardowego formatu daty i godziny. Dowolny ciąg, który nie jest [standardowa Data i godzina ciąg formatu](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) jest interpretowana jako niestandardowa data i godzina ciąg formatu.  
  
 Niestandardowa data i ciągi formatu czasu może być używany z obu <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.  
  
> [!TIP]
>  Możesz pobrać [formatowania narzędzie](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikacji, która umożliwia zastosowanie formatu ciągi do daty i godziny lub wartości liczbowe i wyświetla ciąg wyniku.  
  
<a name="table"></a> W operacji formatowania, niestandardowe ciągi daty i godziny format może być używany z `ToString` metody wystąpienia datę i godzinę lub za pomocą metody, która obsługuje złożone formatowanie. W poniższym przykładzie pokazano oba te zastosowania.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]  
  
 Podczas analizowania operacje, niestandardowej ciągów daty i godziny format może służyć z <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody. Aby operacja analizowania mogła zakończyć się pomyślnie, w tych metodach wymagane jest, aby ciąg wejściowy dokładnie pasował do określonego wzorca. Poniższy przykład przedstawia wywołanie <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę, aby przeanalizować daty, który musi zawierać jeden dzień, miesiąc i rokiem dwucyfrowym.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
 [!code-vb[Formatting.DateAndTime.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]  
  
 W poniższej tabeli opisano specyfikatory niestandardowego formatu daty i godziny oraz pokazano ciąg wynikowy utworzony przez każdy specyfikator formatu. Domyślnie ciągi wynikowe odzwierciedlają konwencje formatowania kultury en-US. Jeśli określony specyfikator formatu generuje zlokalizowany ciąg wynikowy, w przykładzie wymieniono też kulturę, której dotyczy ciąg wynikowy. Zobacz sekcję Uwagi, aby uzyskać dodatkowe informacje dotyczące używania ciągów niestandardowego formatu daty i godziny.  
  
|Specyfikator formatu|Opis|Przykłady|  
|----------------------|-----------------|--------------|  
|„d”|Dzień miesiąca z zakresu od 1 do 31.<br /><br /> Więcej informacji: ["D" specyfikatora formatu niestandardowego](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -&GT; 15|  
|„dd”|Dzień miesiąca z zakresu od 01 do 31.<br /><br /> Więcej informacji: ["Dd" specyfikatora formatu niestandardowego](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -&GT; 15|  
|„ddd”|Skrócona nazwa dnia tygodnia.<br /><br /> Więcej informacji: ["Ddd" specyfikatora formatu niestandardowego](#dddSpecifier).|2009-06-15T13:45:30 -> Mon (en US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> jednostki lun. (fr-FR)|  
|„dddd”|Pełna nazwa dnia tygodnia.<br /><br /> Więcej informacji: ["Dddd" specyfikatora formatu niestandardowego](#ddddSpecifier).|2009-06-15T13:45:30 -> poniedziałek (en US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|  
|„f”|Liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["F" specyfikatora formatu niestandardowego](#fSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-0 -&GT; 15T13:45:30.05|  
|„ff”|Liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["Ff" specyfikatora formatu niestandardowego](#ffSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -&GT; 00|  
|„fff”|Liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: ["Fff" specyfikatora formatu niestandardowego](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|  
|„ffff”|Liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["Ffff" specyfikatora formatu niestandardowego](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -&GT; 6175<br /><br /> 2009-06-0000 -&GT; 15T13:45:30.0000500|  
|„fffff”|Liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["Fffff" specyfikatora formatu niestandardowego](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|  
|„ffffff”|Liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["Ffffff" specyfikatora formatu niestandardowego](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -&GT; 000000|  
|„fffffff”|Liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: ["Fffffff" specyfikatora formatu niestandardowego](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 0001150|  
|„F”|Jeśli wartość jest różna od zera, liczba dziesiątych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu "F" Custom](#F_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (żadne dane wyjściowe)|  
|„FF”|Jeśli wartość jest różna od zera, liczba setnych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#FF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (żadne dane wyjściowe)|  
|„FFF”|Jeśli wartość jest różna od zera, liczba milisekund w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (żadne dane wyjściowe)|  
|„FFFF”|Jeśli wartość jest różna od zera, liczba dziesięciotysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -&GT; 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (żadne dane wyjściowe)|  
|„FFFFF”|Jeśli wartość jest różna od zera, liczba stutysięcznych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFF"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (żadne dane wyjściowe)|  
|„FFFFFF”|Jeśli wartość jest różna od zera, liczba milionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (żadne dane wyjściowe)|  
|„FFFFFFF”|Jeśli wartość jest różna od zera, liczba dziesięciomilionowych części sekundy w wartości daty i godziny.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 000115|  
|„g”, „gg”|Okres lub era.<br /><br /> Więcej informacji: ["g" lub "gg" specyfikatora formatu niestandardowego](#gSpecifier).|2009-06-15T13:45:30.6170000 -> A.D.|  
|„h”|Godzina; używany jest zegar 12-godzinny (wartości od 1 do 12).<br /><br /> Więcej informacji: ["H" specyfikatora formatu niestandardowego](#hSpecifier).|2009-06-1 -&GT; 15T01:45:30<br /><br /> 2009-06-1 -&GT; 15T13:45:30|  
|„hh”|Godzina; używany jest zegar 12-godzinny (wartości od 01 do 12).<br /><br /> Więcej informacji: ["Hh" specyfikatora formatu niestandardowego](#hhSpecifier).|2009-06-01 -&GT; 15T01:45:30<br /><br /> 2009-06-01 -&GT; 15T13:45:30|  
|„H”|Godzina, 24-godzinnym z zakresu od 0 do 23.<br /><br /> Więcej informacji: [specyfikator formatu "H" Custom](#H_Specifier).|2009-06-1 -&GT; 15T01:45:30<br /><br /> 2009-06-15T13:45:30 -&GT; 13|  
|„HH”|Godzina; używany jest zegar 24-godzinny (wartości od 00 do 23).<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "HH"](#HH_Specifier).|2009-06-01 -&GT; 15T01:45:30<br /><br /> 2009-06-15T13:45:30 -&GT; 13|  
|„K”|Informacje o strefie czasowej.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "K"](#KSpecifier).|Z <xref:System.DateTime> wartości:<br /><br /> 2009-06-15T13:45:30, rodzaj nieokreślonych -><br /><br /> 2009-06-15T13:45:30, rodzaju Utc -> Z<br /><br /> 2009-06-15T13:45:30 rodzaj lokalne ->-07: 00 (zależy od ustawień komputera lokalnego)<br /><br /> Z <xref:System.DateTimeOffset> wartości:<br /><br /> 2009-06-15T01:45:30--07--&GT; 07:00:00<br /><br /> 2009-06-15T08:45:30 + 00:00--&GT; + 00:00|  
|„m”|Minuta; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: ["M" specyfikatora formatu niestandardowego](#mSpecifier).|2009-06-15T01:09:30 -&GT; 9<br /><br /> 2009-06-29 -&GT; 15T13:29:30|  
|„mm”|Minuta; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: ["Mm" specyfikatora formatu niestandardowego](#mmSpecifier).|2009-06-09 -&GT; 15T01:09:30<br /><br /> 2009-06-45 -&GT; 15T01:45:30|  
|„M”|Miesiąc; wartości z zakresu od 1 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "M"](#M_Specifier).|2009-06-15T13:45:30 -&GT; 6|  
|„MM”|Miesiąc; wartości z zakresu od 01 do 12.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MM"](#MM_Specifier).|2009-06-06 -&GT; 15T13:45:30|  
|„MMM”|Skrócona nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMM"](#MMM_Specifier).|2009-06-15T13:45:30 -> cze (en US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-cze (zu ZA) -> 15T13:45:30|  
|„MMMM”|Pełna nazwa miesiąca.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30 -> czerwca (en US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|  
|„s”|Sekunda; wartości z zakresu od 0 do 59.<br /><br /> Więcej informacji: ["S" specyfikator formatu niestandardowego](#sSpecifier).|2009-06-15T13:45:09 -&GT; 9|  
|„ss”|Sekunda; wartości z zakresu od 00 do 59.<br /><br /> Więcej informacji: ["Ss" specyfikatora formatu niestandardowego](#ssSpecifier).|2009-06-09 -&GT; 15T13:45:09|  
|„t”|Pierwszy znak oznaczenia AM/PM.<br /><br /> Więcej informacji: ["T" specyfikatora formatu niestandardowego](#tSpecifier).|2009-06-15T13:45:30 -> P (en US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|„tt”|Oznaczenie AM/PM.<br /><br /> Więcej informacji: ["Tt" specyfikatora formatu niestandardowego](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|„y”|Rok; wartości z zakresu od 0 do 99.<br /><br /> Więcej informacji: ["Y" specyfikatora formatu niestandardowego](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -&GT; 9<br /><br /> 2019-06-19 -&GT; 15T13:45:30|  
|„yy”|Rok; wartości z zakresu od 00 do 99.<br /><br /> Więcej informacji: ["Yy" specyfikatora formatu niestandardowego](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-19 -&GT; 15T13:45:30|  
|„yyy”|Rok; co najmniej trzy cyfry.<br /><br /> Więcej informacji: ["Yyy" specyfikatora formatu niestandardowego](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|  
|„yyyy”|Rok jako liczba czterocyfrowa.<br /><br /> Więcej informacji: ["Yyyy" specyfikatora formatu niestandardowego](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|  
|„yyyyy”|Rok jako liczba pięciocyfrowa.<br /><br /> Więcej informacji: ["Yyyyy" specyfikatora formatu niestandardowego](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -&GT; 02009|  
|„z”|Przesunięcie godzinowe względem czasu UTC, bez zer wiodących.<br /><br /> Więcej informacji: ["Z" specyfikatora formatu niestandardowego](#zSpecifier).|2009-06-15T13:45:30-07:00 -&GT; -7|  
|„zz”|Przesunięcie godzinowe względem czasu UTC, z zerem wiodącym dla wartości jednocyfrowych.<br /><br /> Więcej informacji: ["Zz" specyfikatora formatu niestandardowego](#zzSpecifier).|2009-06-15T13:45:30-07:00 -&GT;-07|  
|„zzz”|Godzinowe i minutowe przesunięcie względem czasu UTC.<br /><br /> Więcej informacji: ["Zzz" specyfikatora formatu niestandardowego](#zzzSpecifier).|2009-06-15T13:45:30--07 -&GT; 07:00:00|  
|":"|Separator godziny.<br /><br /> Więcej informacji: [":" specyfikatora formatu niestandardowego](#timeSeparator).|2009-06-15T13:45:30 ->: (en US)<br /><br /> 2009-06-15T13:45:30 -&GT;. (it-IT)<br /><br /> 2009-06-15T13:45:30 ->: (ja-JP)|  
|"/"|Separator daty.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (en US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -&GT;. (tr-TR)|  
|"*ciąg*"<br /><br /> "*ciąg*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [znak literały](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P|  
|%|Definiuje następujący znak jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji:[przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers).|2009-06-1 -> 15T13:45:30 (%h)|  
|\|Znak ucieczki.<br /><br /> Więcej informacji: [znak literały](#Literals) i [przy użyciu znaku ucieczki](#escape).|2009-06-1 h -> 15T13:45:30 (h \h)|  
|Jakikolwiek inny znak|Znak jest kopiowany do ciągu wynikowego bez zmian.<br /><br /> Więcej informacji: [znak literały](#Literals).|2009-06-15T01:45:30 (t arr gg: mm) -> arr 01: 45 A|  
  
 W poniższych sekcjach przedstawiono dodatkowe informacje dotyczące poszczególnych specyfikatorów niestandardowego formatu daty i godziny. Jeśli nie podano inaczej, każdy specyfikator tworzy reprezentacji ciągu taki sam, niezależnie od tego, czy jest używany z <xref:System.DateTime> wartość lub <xref:System.DateTimeOffset> wartość.  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>Specyfikator formatu niestandardowego "d"  
 Specyfikator formatu niestandardowego „d” oznacza dzień miesiąca w postaci liczby z zakresu od 1 do 31. Dzień oznaczony jedną cyfrą jest formatowany bez zera wiodącego.  
  
 Jeśli specyfikator formatu „d” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „d”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „d” jest używany w kilku ciągach formatu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "dd"  
 Ciąg formatu niestandardowego „dd” przedstawia dzień miesiąca w postaci liczby z zakresu od 01 do 31. Dzień oznaczony jedną cyfrą jest formatowany z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „dd” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Powrót do tabeli](#table)  
  
<a name="dddSpecifier"></a>   
## <a name="the-ddd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ddd"  
 Specyfikator formatu niestandardowego „ddd” przedstawia skróconą nazwę dnia tygodnia. Zlokalizowana nazwa skrócona dzień tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „ddd” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ddddSpecifier"></a>   
## <a name="the-dddd-custom-format-specifier"></a>Specyfikator formatu niestandardowego "dddd"  
 Specyfikator formatu niestandardowego „dddd” (plus dowolna liczba dodatkowych specyfikatorów „d”) oznacza pełną nazwę dnia tygodnia. Zlokalizowana nazwa dzień tygodnia jest pobierana z <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „dddd” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="fSpecifier"></a>   
## <a name="the-f-custom-format-specifier"></a>Specyfikator formatu niestandardowego "f"  
 Specyfikator formatu niestandardowego „f” przedstawia najbardziej znaczącą cyfrę części sekund, czyli przedstawia liczbę dziesiątych części sekundy w wartości daty i godziny.  
  
 Jeśli specyfikator formatu „f” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „f”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 Jeśli używasz specyfikatory formatu "f" jako część ciągu formatu przekazany do <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, lub <xref:System.DateTimeOffset.TryParseExact%2A> metody, liczba specyfikatory formatu "f" wskazuje liczbę cyfr znaczących większości ułamek sekund który musi występować pomyślnie przeanalizować składni ciągu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „f” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ff"  
 Specyfikator formatu niestandardowego „ff” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="fffSpecifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "fff"  
 Specyfikator formatu niestandardowego „fff” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „fff” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
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
  
 Jeśli specyfikator formatu „F” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „F”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 Liczba specyfikatory formatu "F", używany z <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, lub <xref:System.DateTimeOffset.TryParseExact%2A> metoda wskazuje maksymalną liczbę cyfr znaczących większości ułamek sekund, które mogą być obecne pomyślnie przeanalizować ciągu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „F” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FF"  
 Specyfikator formatu niestandardowego „FF” przedstawia dwie najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę setnych części sekundy w wartości daty i godziny. Jednak końcowe zera lub dwuzerowe liczby nie są wyświetlane.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „FF” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FFF_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego "FFF"  
 Specyfikator formatu niestandardowego „FFF” przedstawia trzy najbardziej znaczące cyfry części sekund, czyli przedstawia liczbę milisekund w wartości daty i godziny. Jednak końcowe zera lub trzyzerowe liczby nie są wyświetlane.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „FFF” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
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
## <a name="the-g-or-gg-custom-format-specifier"></a>Specyfikator formatu niestandardowego: "g" lub "gg"  
 Specyfikator formatu niestandardowego „g” lub „gg” (plus dowolna liczba dodatkowych specyfikatorów „g”) przedstawia okres lub erę, taką jak n.e. Operacja formatowania ignoruje ten specyfikator, jeśli z datą, która ma być formatowana, nie jest skojarzony ciąg okresu lub ery.  
  
 Jeśli specyfikator formatu „g” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „g”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „g” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]  
  
 [Powrót do tabeli](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specyfikator formatu niestandardowego "h"  
 Specyfikator formatu niestandardowego „h” przedstawia godzinę jako liczbę z zakresu od 1 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „5”.  
  
 Jeśli specyfikator formatu "h" jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „h” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specyfikator formatu niestandardowego "hh"  
 Specyfikator formatu niestandardowego „hh” (plus dowolna liczba dodatkowych specyfikatorów „h”) przedstawia godzinę jako liczbę z zakresu od 01 do 12, czyli godzina jest przedstawiana za pomocą zegara 12-godzinnego, który zlicza pełne godziny od północy lub południa. Określonej godziny po północy nie można odróżnić od tej samej godziny po południu. Godzina nie jest zaokrąglona, a godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym. Na przykład w przypadku godziny 5:43 rano lub po południu użycie tego specyfikatora formatu niestandardowego spowoduje wyświetlenie wartości „05”.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „hh” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Powrót do tabeli](#table)  
  
<a name="H_Specifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specyfikator formatu niestandardowego "H"  
 Specyfikator formatu niestandardowego „H” przedstawia godzinę jako liczbę z zakresu od 0 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana bez zera wiodącego.  
  
 Jeśli specyfikator formatu "H" jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „H” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]  
  
 [Powrót do tabeli](#table)  
  
<a name="HH_Specifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specyfikator formatu niestandardowego "HH"  
 Specyfikator formatu niestandardowego „HH” (plus dowolna liczba dodatkowych specyfikatorów „H”) przedstawia godzinę jako liczbę z zakresu od 00 do 23, czyli godzina jest przedstawiana za pomocą zawierającego zero zegara 24-godzinnego, który zlicza pełne godziny od północy. Godzina oznaczona jedną cyfrą jest formatowana z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „HH” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]  
  
 [Powrót do tabeli](#table)  
  
<a name="KSpecifier"></a>   
## <a name="the-k-custom-format-specifier"></a>Specyfikator formatu niestandardowego "K"  
 Specyfikator formatu niestandardowego „K” przedstawia informacje o strefie czasowej z wartości daty i godziny. Po tym specyfikatorze formatu jest używany z <xref:System.DateTime> zdefiniowano wartości, ciąg wyniku przez wartość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości:  
  
-   Na podstawie lokalnej strefy czasowej ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), to specyfikator jest odpowiednikiem specyfikatora "zzz" i generuje ciąg wyniku zawierający lokalnej przesunięcie z uniwersalnego czasu koordynowanego (UTC); na przykład "-07: 00".  
  
-   Czas UTC ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartość właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), wynik ciąg zawiera znak "Z" do reprezentowania daty UTC.  
  
-   Czas od nieokreślony strefy czasowej (czas których <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> równa właściwości <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), wynik jest odpowiednikiem <xref:System.String.Empty?displayProperty=nameWithType>.  
  
 Dla <xref:System.DateTimeOffset> specyfikator formatu "K" jest odpowiednikiem specyfikator formatu "zzz" i generuje ciąg wyniku zawierający <xref:System.DateTimeOffset> wartość Przesunięcie od czasu UTC.  
  
 Jeśli specyfikator formatu "K" jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie przedstawiono ciąg, który jest wynikiem użycia specyfikator formatu niestandardowego "K" z różnymi <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości w systemie w Stanach Zjednoczonych Czas pacyficzny strefy.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]  
  
 [Powrót do tabeli](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specyfikator formatu niestandardowego "m"  
 Specyfikator formatu niestandardowego „m” przedstawia minutę jako liczbę z zakresu od 0 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana bez zera wiodącego.  
  
 Jeśli specyfikator formatu „m” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „m”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „m” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>"Mm" niestandardowych specyfikatorze formatu  
 Specyfikator formatu niestandardowego „mm” (plus dowolna liczba dodatkowych specyfikatorów „m”) przedstawia minutę jako liczbę z zakresu od 00 do 59. Wynik to liczba pełnych minut, które upłynęły od ostatniej godziny. Minuta oznaczona jedną cyfrą jest formatowana z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „mm” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Powrót do tabeli](#table)  
  
<a name="M_Specifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specyfikator formatu niestandardowego "M"  
 Specyfikator formatu niestandardowego „M” przedstawia miesiąc jako liczbę z zakresu od 1 do 12 (lub od 1 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany bez zera wiodącego.  
  
 Jeśli specyfikator formatu „M” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „M”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „M” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]  
  
 [Powrót do tabeli](#table)  
  
<a name="MM_Specifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MM"  
 Specyfikator formatu niestandardowego „MM” przedstawia miesiąc jako liczbę z zakresu od 01 do 12 (lub od 01 do 13 w przypadku kalendarzy 13-miesięcznych). Miesiąc oznaczony jedną cyfrą jest formatowany z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „MM” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Powrót do tabeli](#table)  
  
<a name="MMM_Specifier"></a>   
## <a name="the-mmm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MMM"  
 Specyfikator formatu niestandardowego „MMM” przedstawia skróconą nazwę miesiąca. Zlokalizowana nazwa skrócona miesiąca są pobierane z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „MMM” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="MMMM_Specifier"></a>   
## <a name="the-mmmm-custom-format-specifier"></a>Specyfikator formatu niestandardowego "MMMM"  
 Specyfikator formatu niestandardowego „MMMM” przedstawia pełną nazwę miesiąca. Zlokalizowana nazwa miesiąca są pobierane z <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „MMMM” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>Specyfikator formatu niestandardowego "s"  
 Specyfikator formatu niestandardowego „s” przedstawia sekundy jako liczbę z zakresu od 0 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana bez zera wiodącego.  
  
 Jeśli specyfikator formatu „s” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „s”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „s” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>Specyfikator formatu niestandardowego "ss"  
 Specyfikator formatu niestandardowego „s” (plus dowolna liczba dodatkowych specyfikatorów „s”) przedstawia sekundy jako liczbę z zakresu od 00 do 59. Wynik przedstawia pełne sekundy, które upłynęły od ostatniej minuty. Sekunda oznaczona jedną cyfrą jest formatowana z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „ss” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Powrót do tabeli](#table)  
  
<a name="tSpecifier"></a>   
## <a name="the-t-custom-format-specifier"></a>Specyfikator formatu niestandardowego "t"  
 Specyfikator formatu niestandardowego „t” przedstawia pierwszy znak oznaczenia AM/PM. Odpowiednie określenia zlokalizowanego są pobierane z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.  
  
 Jeśli specyfikator formatu „t” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „t”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „t” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ttSpecifier"></a>   
## <a name="the-tt-custom-format-specifier"></a>Specyfikator formatu niestandardowego "tt"  
 Specyfikator formatu niestandardowego „tt” (plus dowolna liczba dodatkowych specyfikatorów „t”) przedstawia całe oznaczenie AM/PM. Odpowiednie określenia zlokalizowanego są pobierane z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury. Oznaczenie AM jest stosowanie do wszystkich godzin z zakresu od 0:00:00 (północ) do 11:59:59.999. Oznaczenie PM jest stosowane do wszystkich godzin z zakresu od 12:00:00 (południe) do 23:59:59.999.  
  
 Należy pamiętać, aby używać specyfikatora „tt” w przypadku języków, dla których wymagane jest zachowanie rozróżnienia między oznaczeniami AM i PM. Przykładem jest język japoński, dla którego oznaczenia AM i PM różnią się w drugim znaku, a nie w pierwszym znaku.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „tt” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ySpecifier"></a>   
## <a name="the-y-custom-format-specifier"></a>Specyfikator formatu niestandardowego "y"  
 Specyfikator formatu niestandardowego „y” przedstawia rok jako jedno- lub dwucyfrową liczbę. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeżeli pierwsza cyfra roku dwucyfrowego rozpoczyna się od zera (na przykład, 2008), liczba jest formatowana bez zera wiodącego.  
  
 Jeśli specyfikator formatu „y” jest używany bez innych specyfikatorów formatu niestandardowego, będzie interpretowany jako specyfikator standardowego formatu daty i godziny „y”. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „y” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="yySpecifier"></a>   
## <a name="the-yy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yy"  
 Specyfikator formatu niestandardowego „yy” przedstawia rok jako liczbę dwucyfrową. Jeśli rok ma więcej niż dwie cyfry, w wyniku pojawią się tylko dwie ostatnie cyfry. Jeśli rok dwucyfrowy ma mniej niż dwie cyfry znaczące, liczba jest dopełniana wiodącymi zerami w celu utworzenia dwóch cyfr.  
  
 W operacji analizy dwucyfrowe jest analizować przy użyciu specyfikatora formatu niestandardowego "yy" jest interpretowana na podstawie <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> właściwości bieżącego kalendarza dostawca formatu. W poniższym przykładzie jest analizowany ciąg przedstawiając datę, która ma domyślnie dwucyfrowy rok według domyślnego kalendarza gregoriańskiego w kulturze en-US, która w tym przypadku jest bieżącą kulturą. Następnie zmiany bieżącej kultury <xref:System.Globalization.CultureInfo> obiekt, aby użyć <xref:System.Globalization.GregorianCalendar> którego <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> właściwość została zmodyfikowana.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
 [!code-vb[Formatting.DateAndTime.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „yy” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="yyySpecifier"></a>   
## <a name="the-yyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyy"  
 Specyfikator formatu niestandardowego „yyy” przedstawia rok za pomocą co najmniej trzech cyfr. Jeśli rok ma więcej niż trzy cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż trzy cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia trzech cyfr.  
  
> [!NOTE]
>  W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie wszystkich cyfr znaczących.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „yyy” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="yyyySpecifier"></a>   
## <a name="the-yyyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyyy"  
 Specyfikator formatu niestandardowego „yyyy” przedstawia rok za pomocą co najmniej czterech cyfr. Jeśli rok ma więcej niż cztery cyfry znaczące, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż cztery cyfry, liczba jest dopełniana wiodącymi zerami w celu utworzenia czterech cyfr.  
  
> [!NOTE]
>  W przypadku tajskiego kalendarza buddyjskiego, w którym rok może być liczbą pięciocyfrową, ten specyfikator formatu powoduje wyświetlenie co najmniej czterech cyfr.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „yyyy” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="yyyyySpecifier"></a>   
## <a name="the-yyyyy-custom-format-specifier"></a>Specyfikator formatu niestandardowego "yyyyy"  
 Specyfikator formatu niestandardowego „yyyyy” (plus dowolna liczba dodatkowych specyfikatorów „y”) przedstawia rok za pomocą co najmniej pięciu cyfr. Jeśli rok ma więcej niż pięć cyfr znaczących, są one uwzględnione w ciągu wynikowym. Jeśli rok ma mniej niż pięć cyfr, liczba jest dopełniana zerami wiodącymi w celu utworzenia pięciu cyfr.  
  
 Jeśli istnieją dodatkowe specyfikatory „y”, liczba jest dopełniana tak wieloma zerami wiodącymi, jak jest to konieczne, aby utworzyć liczbę specyfikatorów „y”.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „yyyyy” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="zSpecifier"></a>   
## <a name="the-z-custom-format-specifier"></a>Specyfikator formatu niestandardowego "z"  
 Z <xref:System.DateTime> wartości specyfikatora formatu niestandardowego "z" reprezentuje podpisem przesunięcie strefy czasowej przez lokalny system operacyjny z uniwersalnego czasu koordynowanego (UTC), mierzony w godzinach. Wartość wystąpienia nie są widoczne <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikatora formatu "z" nie jest zalecane do użycia z <xref:System.DateTime> wartości.  
  
 Z <xref:System.DateTimeOffset> wartości, to specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość Przesunięcie od czasu UTC w godzinach.  
  
 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane bez zera wiodącego.  
  
 Jeśli specyfikatora formatu "z" jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „z” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Powrót do tabeli](#table)  
  
<a name="zzSpecifier"></a>   
## <a name="the-zz-custom-format-specifier"></a>Specyfikator formatu niestandardowego "zz"  
 Z <xref:System.DateTime> wartości, specyfikator formatu niestandardowego "zz" reprezentuje podpisem przesunięcie strefy czasowej przez lokalny system operacyjny z formatem UTC, mierzony w godzinach. Wartość wystąpienia nie są widoczne <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikator formatu "zz" nie jest zalecane do użycia z <xref:System.DateTime> wartości.  
  
 Z <xref:System.DateTimeOffset> wartości, to specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość Przesunięcie od czasu UTC w godzinach.  
  
 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „zz” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Powrót do tabeli](#table)  
  
<a name="zzzSpecifier"></a>   
## <a name="the-zzz-custom-format-specifier"></a>Specyfikator formatu niestandardowego "zzz"  
 Z <xref:System.DateTime> wartości, specyfikator formatu niestandardowego "zzz" reprezentuje podpisem przesunięcie strefy czasowej przez lokalny system operacyjny z formatem UTC, mierzony w godzinach i minutach. Wartość wystąpienia nie są widoczne <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości. Z tego powodu specyfikator formatu "zzz" nie jest zalecane do użycia z <xref:System.DateTime> wartości.  
  
 Z <xref:System.DateTimeOffset> wartości, to specyfikator formatu reprezentuje <xref:System.DateTimeOffset> wartość Przesunięcie od czasu UTC w godzinach i minutach.  
  
 Przesuni‪ęcie jest zawsze wyświetlane ze znakiem wiodącym. Znak plus (+) wskazuje godziny wyprzedzające czas UTC, a znak minus (-) wskazuje godziny pozostające w tyle za czasem UTC. Przesunięcie oznaczone jedną cyfrą jest formatowane z zerem wiodącym.  
  
 W poniższym przykładzie specyfikator formatu niestandardowego „zzz” jest używany w ciągu formatu niestandardowego.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Powrót do tabeli](#table)  
  
<a name="timeSeparator"></a>   
## <a name="the--custom-format-specifier"></a>":" Specyfikator formatu niestandardowego  
 Specyfikator formatu niestandardowego „:” przedstawia separator godzin, który jest używany do odróżnienia godzin, minut i sekund. Separator odpowiedni czas zlokalizowane są pobierane z <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
> [!NOTE]
>  Aby zmienić separator godziny dla określonej daty i czasu ciągu, określ znak separatora w ogranicznik literału ciągu. Na przykład ciąg formatu niestandardowego `hh'_'dd'_'ss` generuje ciąg wyniku, w którym "\_" (podkreślenie) zawsze jest używany jako separator czasu. Aby zmienić czas separatora dla wszystkich dat dla kultury, zmień wartość <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> właściwości bieżącego kultury lub utworzenia wystąpienia <xref:System.Globalization.DateTimeFormatInfo> obiekt, należy przypisać znak jego <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> właściwości i wywoływać przeciążenia Formatowanie metodę, która obejmuje <xref:System.IFormatProvider> parametru.  
  
 Jeśli ":" specyfikator formatu jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 [Powrót do tabeli](#table)  
  
<a name="dateSeparator"></a>   
## <a name="the--custom-format-specifier"></a>Specyfikator formatu niestandardowego "/"  
 Specyfikator formatu niestandardowego „/” oznacza separator daty, który jest używany do odróżnienia lat, miesięcy i dni. Separator odpowiednie zlokalizowane daty są pobierane z <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> właściwości bieżącego lub określonej kultury.  
  
> [!NOTE]
>  Aby zmienić separator daty dla określonej daty i czasu ciągu, określ znak separatora w ogranicznik literału ciągu. Na przykład ciąg formatu niestandardowego `mm'/'dd'/'yyyy` generuje ciąg wyniku, w którym "/" zawsze jest używany jako separator daty. Aby zmienić separator daty dla wszystkich dat dla kultury, zmień wartość <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> właściwości bieżącego kultury lub utworzenia wystąpienia <xref:System.Globalization.DateTimeFormatInfo> obiekt, należy przypisać znak jego <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> właściwości i wywoływać przeciążenia Formatowanie metodę, która obejmuje <xref:System.IFormatProvider> parametru.  
  
 Jeśli specyfikator formatu "/" jest używana bez inne specyfikatory formatu niestandardowego, jest interpretowany jako standardowa Data i godzina specyfikator formatu i zgłasza <xref:System.FormatException>. Aby uzyskać więcej informacji o używaniu specyfikator formatu pojedynczego, zobacz [przy użyciu pojedynczego specyfikatory formatu niestandardowego](#UsingSingleSpecifiers) dalszej części tego tematu.  
  
 [Powrót do tabeli](#table)  
  
<a name="Literals"></a>   
## <a name="character-literals"></a>Literały znaków  
 Następujące znaki niestandardowe daty i czasu ciąg formatu są zarezerwowane i są zawsze interpretowane jako formatowanie znaków lub, w przypadku elementu ",", /, i \\, jako znaki specjalne.  
  
||||||  
|-|-|-|-|-|  
|F|H|K|M|d|  
|f|g|h|m|s|  
|t|t|z|%|:|  
|/|"|'|\||  
  
 Wszystkie inne znaki są zawsze interpretowane jako literały znaków, a w ramach operacji formatowania, znajdują się w ciągu wyniku bez zmian.  W ramach operacji analizy muszą one odpowiadać znaków w ciągu wejściowym dokładnie; porównanie jest rozróżniana wielkość liter.  
  
 Poniższy przykład zawiera literały "PST" (dla pacyficznego czasu standardowego) i "PDT" (dla pacyficzny czas letni) do reprezentowania w lokalnej strefie czasowej w ciągu formatu. Należy pamiętać, że ten ciąg jest uwzględniona w parametrach wynik i że ciąg, który zawiera ciąg strefy czasu lokalnego również przeanalizowany pomyślnie.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
 [!code-vb[Formatting.DateAndTime.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]  
  
 Istnieją dwa sposoby, aby wskazać, czy znaki mają być interpretowane jako literał znaków, a nie zarezerwowane znaki tak, aby może być uwzględniona w parametrach wynik lub pomyślnie przeanalizowano w parametrach wejściowych:  
  
-   Przez anulowanie każdego zastrzeżonego znaku. Aby uzyskać więcej informacji, zobacz [przy użyciu znaku ucieczki](#escape).  
  
     Poniższy przykład zawiera literały "pst" (dla pacyficznego czasu standardowego) do reprezentowania w lokalnej strefie czasowej w ciągu formatu. Ponieważ zarówno "s" i "t" są niestandardowych ciągów formatu, oba znaki należy użyć znaków ucieczki interpretowane jako literały znaków.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
     [!code-vb[Formatting.DateAndTime.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]  
  
-   Umieszczając cały ciąg literału w cudzysłowie lub w apostrofy. Poniższy przykład przypomina poprzedni, z wyjątkiem "pst" jest ujęta w cudzysłów, aby wskazać, że cały ciąg rozdzielany powinny być rozumiane jako literały znaków.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
     [!code-vb[Formatting.DateAndTime.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]  
  
<a name="Notes"></a>   
## <a name="notes"></a>Uwagi  
  
<a name="UsingSingleSpecifiers"></a>   
### <a name="using-single-custom-format-specifiers"></a>Używanie specyfikatorów formatu niestandardowego pojedynczego  
 Ciąg niestandardowego formatu daty i godziny składa się z co najmniej dwóch znaków. Metody formatowania daty i godziny interpretują każdy jednoznakowy ciąg jako ciąg standardowego formatu daty i godziny. Jeśli znak nie rozpoznają jako prawidłowym specyfikatorem formatu, generują one <xref:System.FormatException>. Na przykład ciąg formatu, który składa się tylko ze specyfikatora „h”, jest interpretowany jako ciąg standardowego formatu daty i godziny. Jednak w tym przypadku jest zwracany wyjątek, ponieważ nie istnieje, nie standardowe daty "h" i specyfikator timeformat.  
  
 Aby użyć jakiegokolwiek specyfikatora niestandardowego formatu daty i godziny jako jedynego specyfikatora w ciągu formatu (tj. użyć samego specyfikatora formatu niestandardowego „d”, „f”, „F”, „g”, „h”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/”), należy przed lub za specyfikatorem umieścić spację albo umieścić specyfikator formatu procent („%”) przed pojedynczym specyfikatorem niestandardowego formatu daty i godziny.  
  
 Na przykład "`%h"` jest interpretowana jako niestandardowa data i godzina ciąg formatu, który wyświetla godzinę reprezentowany przez wartość bieżącą datę i godzinę. Można także użyć ciągu formatu „ h” lub „h ”, mimo że zawierają w ciągu wynikowym i spację, i godzinę. W poniższym przykładzie pokazano te trzy ciągi formatu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
 [!code-vb[Formatting.DateAndTime.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]  
  
<a name="escape"></a>   
### <a name="using-the-escape-character"></a>Korzystając ze znaku unikowego  
 Znaki „D”, „f”, „F”, „G”, „g”, „H”, „K”, „m”, „M”, „s”, „t”, „y”, „z”, „:”, lub „/” w ciągu formatu są interpretowane jako specyfikatory formatu niestandardowego, a nie jako znaki literału. Aby zapobiec znak interpretowane jako specyfikator formatu, należy się znajdować ukośnik odwrotny (\\), która jest znak ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.  
  
 Aby dołączyć ciąg wyniku ukośnik odwrotny, musi escape go z innym ukośnik odwrotny (`\\`).  
  
> [!NOTE]
>  Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.  
  
 W poniższym przykładzie użyto znaku ucieczki, aby uniemożliwić operacji formatowania interpretowanie znaków „h” i „m” jako specyfikatorów formatu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]  
  
### <a name="control-panel-settings"></a>Ustawienia Panelu sterowania  
 **Opcje regionalne i językowe** ustawienia w Panelu sterowania mają wpływ ciąg wyniku utworzone za pomocą operacji formatowania, która zawiera wiele niestandardowa data i godzina specyfikatory formatu. Te ustawienia są używane do zainicjowania <xref:System.Globalization.DateTimeFormatInfo> obiekt skojarzony z bieżącej kultury wątku, co zapewnia wartości używane do sterowania formatowania. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.  
  
 Ponadto, jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktora, aby utworzyć obiekt klasy <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tego samego kultury bieżącej kultury systemu, wszelkie dostosowania ustala **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Można użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora w celu utworzenia <xref:System.Globalization.CultureInfo> obiekt, który nie odzwierciedla dostosowania systemu.  
  
### <a name="datetimeformatinfo-properties"></a>Właściwości DateTimeFormatInfo  
 Formatowanie ma wpływ właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest dostarczany niejawnie według bieżącej kultury wątku lub jawnie <xref:System.IFormatProvider> parametru metody, która wywołuje formatowania. Dla <xref:System.IFormatProvider> parametr, należy określić <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kultury, lub <xref:System.Globalization.DateTimeFormatInfo> obiektu.  
  
 Ciąg wyniku utworzonego przez wiele niestandardowa data i czas specyfikatory formatu zależy także od właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu. Aplikacja może zmienić wynik utworzonej przez niektóre niestandardowa data i czas specyfikatorów formatu przez zmianę odpowiednich <xref:System.Globalization.DateTimeFormatInfo> właściwości. Specyfikator formatu "ddd" dodaje na przykład nazwa skrócona dzień tygodnia w <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> tablicy ciągów na ciąg wyniku. Podobnie, specyfikator formatu "MMMM" dodaje nazwę pełny miesiąc w <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> tablicy ciągów na ciąg wyniku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Przykład: .NET Framework 4 formatowania narzędzia](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
