---
title: Standardowe ciągi formatujące datę i godzinę
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
ms.assetid: bb79761a-ca08-44ee-b142-b06b3e2fc22b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6939efa608f4887dfdb00abe8292bec841929440
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664642"
---
# <a name="standard-date-and-time-format-strings"></a>Standardowe ciągi formatujące datę i godzinę
W ciągu standardowego formatu daty i godziny pojedynczy specyfikator formatu jest używany do definiowania tekstowej reprezentacji wartości daty i godziny. Ciągu formatu daty i godziny, który zawiera więcej niż jeden znak, w tym znak odstępu, jest interpretowany jako niestandardowy ciąg daty i godziny formatu; Aby uzyskać więcej informacji, zobacz [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Ciągu formatu standardowego lub niestandardowego można używać na dwa sposoby:  
  
- Aby zdefiniować ciąg będący wynikiem operacji formatowania.  
  
- Aby zdefiniować tekstową reprezentację wartości daty i godziny, który może zostać przekonwertowany na <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości podczas operacji analizy.  

> [!TIP]
>  Możesz pobrać [narzędzie do formatowania](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikację, która umożliwia zastosowanie formatu ciągów liczbowego lub daty i godziny, wartości oraz wyświetlenie ciągu wynikowego.  

Standardowy format daty i ciągi formatu czasu mogą być używane z obu <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.  
  
[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a> W poniższej tabeli opisano standardowy format daty i czasu specyfikatorów formatu. Jeśli nie określono inaczej, określonego standardowy daty i czas formatowania specyfikator wytwarza identyczną reprezentację ciągu niezależnie od tego, czy jest użyty z <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartość. Zobacz [uwagi](#Notes) sekcji, aby uzyskać dodatkowe informacje na temat przy użyciu standardowych ciągów daty i godziny formatu.  
  
|Specyfikator formatu|Opis|Przykłady|  
|----------------------|-----------------|--------------|  
|„d”|Wzorzec daty krótkiej.<br /><br /> Więcej informacji:[daty krótkiej ("d") specyfikator formatu](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 06-15/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|„D”|Wzorzec daty długiej.<br /><br /> Więcej informacji:[specyfikator formatu daty długiej ("D")](#LongDate).|2009-06-15T13:45:30 -> poniedziałek, czerwiec 15, 2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|  
|„f”|Wzorzec pełnej daty/godziny (godzina krótka).<br /><br /> Więcej informacji: [Specyfikator formatu godziny krótkiej ("f") pełnej daty](#FullDateShortTime).|2009-06-15T13:45:30 -> poniedziałek, czerwiec 15, 2009 1:45 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|„F”|Wzorzec pełnej daty/godziny (godzina długa).<br /><br /> Więcej informacji: [Pełnej daty i czasu specyfikator formatu godziny ("F")](#FullDateLongTime).|2009-06-15T13:45:30 -> poniedziałek, czerwiec 15, 2009 1:45:30 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|„g”|Wzorzec ogólnej daty/godziny (godzina krótka).<br /><br /> Więcej informacji: [Specyfikator formatu ogólnego daty i godziny krótkiej ("g")](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en US)<br /><br /> 2009-06-06-15/2009-> 15T13:45:30 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|  
|„G”|Wzorzec ogólnej daty/godziny (godzina długa).<br /><br /> Więcej informacji: [Specyfikator formatu ogólnego daty długiej i godziny ("G")](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 06-15/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|  
|„M”, „m”|Wzorzec miesiąc/dzień.<br /><br /> Więcej informacji: [Specyfikator formatu miesiąca ("M", "m")](#MonthDay).|2009-06-15T13:45:30 -> 15 czerwca (pl pl)<br /><br /> 2009-06-15T13:45:30 -> 15. juni (da DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|  
|„O”, „o”|Wzorzec dwustronnej konwersji data/godzina.<br /><br /> Więcej informacji: [Specyfikatora formatu konwersji dwustronnej ("O", "o")](#Roundtrip).|<xref:System.DateTime> Wartości:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc)--> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> Wartości:<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00|  
|„R”, „r”|Wzorzec RFC1123.<br /><br /> Więcej informacji: [RFC1123 ("R", "r") specyfikator formatu](#RFC1123).|2009-06-15T13:45:30 -> pon, 15 cze 2009 20:45:30 GMT|  
|„s”|Wzorzec sortowalnej daty/godziny.<br /><br /> Więcej informacji: [Specyfikatora formatu sortowalnego ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|„t”|Wzorzec godziny krótkiej.<br /><br /> Więcej informacji: [Specyfikator formatu godziny krótkiej ("t")](#ShortTime).|2009-06-15T13:45:30 -> 1:45 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|  
|„T”|Wzorzec godziny długiej.<br /><br /> Więcej informacji: [Specyfikator formatu godziny długiej ("T")](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar — na przykład)|  
|„u”|Wzorzec uniwersalnej sortowalnej daty/godziny.<br /><br /> Więcej informacji: [Uniwersalny sortowalny ("u") specyfikatora formatu](#UniversalSortable).|Za pomocą <xref:System.DateTime> wartość: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> Za pomocą <xref:System.DateTimeOffset> wartość: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|  
|„U”|Wzorzec uniwersalnej pełnej daty/godziny.<br /><br /> Więcej informacji: [Specyfikator uniwersalnego pełnego ("U") formatu](#UniversalFull).|2009-06-15T13:45:30 -> poniedziałek, czerwiec 15, 2009 8:45:30 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|„Y”, „y”|Wzorzec roku i miesiąca.<br /><br /> Więcej informacji: [Specyfikator formatu miesiąca ("Y") roku](#YearMonth).|2009-06-15T13:45:30 -> 2009 czerwca (pl pl)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|  
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator.|Zgłasza wyjątek czasu wykonywania <xref:System.FormatException>.|  
  
## <a name="how-standard-format-strings-work"></a>Sposób działania ciągów formatu standardowego  
 W operacji formatowania ciąg formatu standardowego jest po prostu aliasem ciągu formatu niestandardowego. Zaletą użycia aliasu w celu odwołania się do ciągu formatu niestandardowego jest to, że ciąg formatu niestandardowego może być różny, mimo że alias pozostaje niezmienny. Jest to ważne, ponieważ ciągi reprezentujące wartości daty i godziny są zazwyczaj różne w zależności od kultury. Na przykład ciąg formatu standardowego „d” wskazuje, że wartość daty i godziny zostanie wyświetlona przy użyciu wzorca daty krótkiej. Ten wzorzec dla niezmiennej kultury to „MM/dd/yyyy”. Dla kultury fr-FR jest to „dd/MM/yyyy”. Dla kultury ja-JP jest to „yyyy/MM/dd”.  
  
 Jeśli ciąg formatu standardowego w operacji formatowania jest mapowany na ciąg formatu niestandardowego danej kultury, aplikacja może definiować określoną kulturę, której ciągi formatu niestandardowego są używane na jeden z poniższych sposobów:  
  
- Można użyć domyślnej (bieżącej) kultury. W poniższym przykładzie data jest wyświetlana przy użyciu formatu daty krótkiej dla bieżącej kultury. Bieżącą kulturą jest w tym przypadku kultura en-US.  
  
     [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
- Możesz przekazać <xref:System.Globalization.CultureInfo> obiekt reprezentujący kulturę, której formatowanie ma być używany do metody, która ma <xref:System.IFormatProvider> parametru. W poniższym przykładzie data jest wyświetlana przy użyciu formatu daty krótkiej dla kultury pt-BR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
- Możesz przekazać <xref:System.Globalization.DateTimeFormatInfo> obiekt, który dostarcza informacje o formatowaniu do metody, która ma <xref:System.IFormatProvider> parametru. Poniższy przykład wyświetla datę przy użyciu formatu daty krótkiej z <xref:System.Globalization.DateTimeFormatInfo> obiektu dla kultury hr-HR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  Aby uzyskać informacje dotyczące dostosowywania wzorców lub ciągów używanych w formatowaniu wartości daty i godziny, zobacz <xref:System.Globalization.NumberFormatInfo> temat poświęcony klasie.  
  
 W niektórych przypadkach ciąg formatu standardowego służy jako wygodny skrót dla dłuższego ciągu formatu niestandardowego, który jest niezmienny. Cztery ciągi formatu standardowego należą do tej kategorii: "O" (lub "o"), "R" (lub "r"), "s" i "u". Te ciągi odpowiadają ciągom formatów niestandardowych, które są zdefiniowane przez niezmienną kulturę. Wytwarzają one reprezentacje wartości daty i godziny w postaci ciągu, które mają być identyczne dla różnych kultur. W poniższej tabeli przedstawiono informacje dotyczące tych czterech ciągów standardowych formatów daty i godziny.  
  
|Ciąg formatu standardowego|Definiowany przez właściwość DateTimeFormatInfo.InvariantInfo|Ciąg formatu niestandardowego|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|„O” lub „o”|Brak|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|„R” lub „r”|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|„s”|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|„u”|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Ciągi w standardowym formacie można również w operacji analizowania za pomocą <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> metody, które wymagają ciąg wejściowy dokładnie odpowiada wzorcowi jako warunek powodzenia operacji analizy. Wiele ciągów formatów standardowych jest mapowanych na wielu ciągów formatów niestandardowych, więc wartość daty i godziny może być reprezentowana przez wiele formatów, a operacja analizy i tak zakończy się powodzeniem. Należy określić ciąg formatu niestandardowego lub ciągów, które odpowiadają ciągowi formatu standardowego, wywołując <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> metody. W poniższym przykładzie są wyświetlane ciągi formatów niestandardowych mapowane na ciąg formatu standardowego „d” (wzorzec daty krótkiej).  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 W poniższych sekcjach opisano specyfikatory formatu standardowego dla <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Specyfikator formatu daty krótkiej („d”)  
 Specyfikator formatu standardowego "d" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez określoną kulturę <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> właściwości niezmiennej kultury to "MM/dd/yyyy".  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Określa ciąg, który oddziela składniki daty: rok, miesiąc i dzień.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „d”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [Powrót do tabeli](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>Specyfikator formatu daty długiej („D”)  
 Specyfikator formatu standardowego "D" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez bieżącą <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „dddd, dd MMMM yyyy”.  
  
 Poniższa tabela zawiera listę właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektów, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „D”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>Specyfikator formatu pełnej daty i godziny krótkiej („f”)  
 Specyfikator formatu standardowego „f” reprezentuje kombinację wzorców daty długiej („D”) i godziny krótkiej („t”), rozdzielonych spacją.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu określonego <xref:System.Globalization.DateTimeFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego zwracany przez <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> i <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> właściwości niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definiuje format składnika daty w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „f”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>Specyfikator formatu pełnej daty i godziny długiej („F”)  
 Specyfikator formatu standardowego "F" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez bieżącą <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „dddd, dd MMMM yyyy HH:mm:ss”.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> właściwość niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „F”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>Specyfikator formatu daty ogólnej i godziny krótkiej („g”)  
 Specyfikator formatu standardowego „g” reprezentuje kombinację wzorców daty krótkiej („g”) i godziny krótkiej („t”), rozdzielonych spacją.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu określonego <xref:System.Globalization.DateTimeFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> i <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> właściwości niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definiuje format składnika daty w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Określa ciąg, który oddziela składniki daty: rok, miesiąc i dzień.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „g”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>Specyfikator formatu daty ogólnej i godziny długiej („G”)  
 Specyfikator formatu standardowego „G” reprezentuje kombinację wzorców daty krótkiej („d”) i godziny długiej („T”), rozdzielonych spacją.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu określonego <xref:System.Globalization.DateTimeFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> i <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> właściwości niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definiuje format składnika daty w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Określa ciąg, który oddziela składniki daty: rok, miesiąc i dzień.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „G”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]  
  
 [Powrót do tabeli](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>Specyfikator formatu miesiąca („M”, „m”)  
 Specyfikator formatu standardowego "M" lub "m" przedstawia niestandardowa data i godzina ciąg formatu, który jest definiowany przez bieżącą <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „MMMM dd”.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „m”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>Specyfikator formatu dwustronnej konwersji („O”, „o”)  
 Specyfikator formatu standardowego "O" lub "o" reprezentuje niestandardowa data i ciąg formatu godziny przy użyciu wzorca, który zachowuje informacje o strefie czasowej i emituje ciąg wynikowy, który jest zgodny z normą ISO 8601. Aby uzyskać <xref:System.DateTime> wartości, ten specyfikator formatu służy do zachowania wartości daty i godziny wraz z <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwość w tekście. Sformatowany ciąg można analizować wstecznie, używając <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> lub <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metoda Jeśli `styles` parametr ma wartość <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.  
  
 Specyfikator formatu standardowego "O" lub "o" odpowiada to "yyyy '-' MM'-'dd'T' HH': 'mm':'ss '." Ciąg formatu niestandardowego fffffffK"dla <xref:System.DateTime> wartości i" yyyy '-' MM'-'dd'T' HH': 'mm':'ss '. " Ciąg formatu niestandardowego fffffffzzz"dla <xref:System.DateTimeOffset> wartości. W tym ciągu pary znaków apostrofu, które oddzielają pojedyncze znaki, takie jak łączniki, dwukropki i litera „T”, wskazują, że indywidualny znak jest literałem, który nie może być zmieniony. Apostrofy nie znajdują się w ciągu wyjściowym.  
  
 Specyfikator formatu standardowego "O" lub "o" (oraz "yyyy '-' MM'-'dd'T' HH': 'mm':'ss '." Ciąg formatu niestandardowego fffffffK") korzysta z trzech sposobów, które ISO 8601 reprezentuje informacje o strefie czasowej, aby zachować <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTime> wartości:  
  
- Składnik strefy czasowej <xref:System.DateTimeKind.Local?displayProperty=nameWithType> wartości daty i godziny jest przesunięta względem czasu UTC (na przykład +01: 00, -07:00). Wszystkie <xref:System.DateTimeOffset> wartości również są przedstawiane w tym formacie.  
  
- Składnik strefy czasowej <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> korzysta z wartości daty i godziny "Z" (która zawiera zero przesunięcie) do reprezentowania UTC.  
  
- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> wartości daty i godziny nie ma żadnych informacji o strefie czasowej.  
  
 Ponieważ specyfikator formatu standardowego "O" lub "o" jest zgodny ze standardem międzynarodowym, formatowania lub analizowania operacji, która zawsze używa specyfikator używana Niezmienna kultura i kalendarz gregoriański.  
  
 Ciągi, które są przekazywane do `Parse`, `TryParse`, `ParseExact`, i `TryParseExact` metody <xref:System.DateTime> i <xref:System.DateTimeOffset> można analizować za pomocą specyfikatora formatu "O" lub "o", jeśli są one w jednym z tych formatów. W przypadku właściwości <xref:System.DateTime> obiektów, analizy składni przeciążenia, które wywołujesz powinny również obejmować `styles` parametru z wartością <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Należy pamiętać, że jeśli wywołujesz metodę analizy przy użyciu ciągu formatu niestandardowego, który odpowiada "O" lub "o" specyfikatora formatu, nie będą otrzymywać te same wyniki "O" lub "o". Jest to spowodowane analizowania metody, które używają ciągu formatu niestandardowego nie można przeanalizować reprezentację wartości daty i godziny, które nie ma składnika strefy czasowej, lub użyj "Z", aby wskazać UTC.  
  
 W poniższym przykładzie użyto specyfikatora formatu "o", aby wyświetlić szereg <xref:System.DateTime> wartości i <xref:System.DateTimeOffset> wartość w systemie, w Stanach Zjednoczonych Strefa czasowa czasu pacyficznego.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Poniższy przykład używa specyfikatora formatu "o", aby utworzyć sformatowany ciąg, a następnie przywrócenie oryginalnej wartości daty i godziny przez wywołanie datę i godzinę `Parse` metody.  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Powrót do tabeli](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>Specyfikator formatu RFC1123 („R”, „r”)  
 Specyfikator formatu standardowego "R" lub "r" reprezentuje niestandardowa data i ciąg formatu godziny, który jest definiowany przez <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> właściwości. Wzorzec odzwierciedla zdefiniowany standard, a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „ddd, dd MMM yyyy HH':'mm':'ss 'GMT'”. Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.  
  
 Ciąg wynikowy mają wpływ następujące właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> właściwość, która reprezentuje niezmienną kulturę.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definiuje format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definiuje skrócone nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definiuje skrócone nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
  
 Mimo że standard RFC 1123 wyraża czas jako uniwersalny czas koordynowany (UTC), operacja formatowania nie modyfikuje wartości <xref:System.DateTime> obiekt, który jest formatowana. W związku z tym, należy przekonwertować <xref:System.DateTime> wartość na czas UTC, wywołując <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda przed wykonaniem operacji formatowania. Z kolei <xref:System.DateTimeOffset> automatycznie wykonać tę konwersję wartości; nie trzeba wywoływac <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda przed operacją formatowania.  
  
 W poniższym przykładzie użyto specyfikatora formatu "r", aby wyświetlić <xref:System.DateTime> i <xref:System.DateTimeOffset> wartość w systemie, w Stanach Zjednoczonych Strefa czasowa czasu pacyficznego.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Powrót do tabeli](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Specyfikator formatu sortowalnego („s”)  
 Specyfikator formatu standardowego "s" przedstawia niestandardowa data i ciąg formatu godziny, który jest definiowany przez <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> właściwości. Wzorzec odzwierciedla zdefiniowany standard (ISO 8601), a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „yyyy'-'MM'-'dd'T'HH':'mm':'ss”.  
  
 Specyfikator formatu "s" ma na celu wyprodukowania ciągi wynikowe, które stale sortowanie w kolejności rosnącej lub malejącej na podstawie wartości daty i godziny. W wyniku chociaż specyfikator formatu standardowego "s" reprezentuje wartość daty i godziny w jednolitym formacie, operacji formatowania nie modyfikuje wartości formatowanego w celu odzwierciedlenia obiektu daty i godziny jego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości lub jego <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> wartość. Na przykład ciągi wynikowe generowane przez formatowanie wartości daty i godziny 2014-11-15T18:32:17 + 00:00 i 2014-11-15T18:32:17 + 08:00 są identyczne.  
  
 Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.  
  
 W poniższym przykładzie użyto specyfikatora formatu "s", aby wyświetlić <xref:System.DateTime> i <xref:System.DateTimeOffset> wartość w systemie, w Stanach Zjednoczonych Strefa czasowa czasu pacyficznego.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Specyfikator formatu godziny krótkiej („t”)  
 Specyfikator formatu standardowego "t" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez bieżącą <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „HH:mm”.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu określonego <xref:System.Globalization.DateTimeFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> właściwość niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „t”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [Powrót do tabeli](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>Specyfikator formatu godziny długiej („T”)  
 Specyfikator formatu standardowego "T" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez określoną kulturę <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> właściwości. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „HH:mm:ss”.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> właściwość niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „T”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [Powrót do tabeli](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>Specyfikator uniwersalnego sortowalnego formatu („u”)  
 Specyfikator formatu standardowego "u" reprezentuje niestandardowa data i ciąg formatu godziny, który jest definiowany przez <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> właściwości. Wzorzec odzwierciedla zdefiniowany standard, a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „yyyy'-'MM'-'dd HH':'mm':'ss'Z'”. Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.  
  
 Mimo że ciąg wynikowy powinien wyrażać czas jako uniwersalny czas koordynowany (UTC), bez konwersji oryginalny <xref:System.DateTime> wartość odbywa się podczas operacji formatowania. W związku z tym, należy przekonwertować <xref:System.DateTime> wartość na czas UTC, wywołując <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda przed jego sformatowaniem.  Z kolei <xref:System.DateTimeOffset> automatycznie wykonać tę konwersję wartości; nie trzeba wywoływac <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda przed operacją formatowania.  
  
 W poniższym przykładzie użyto specyfikatora formatu „u”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Powrót do tabeli](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Specyfikator uniwersalnego pełnego formatu („U”)  
 Specyfikator formatu standardowego "U" reprezentuje niestandardowa data i godzina ciąg formatu, który jest definiowany przez określonej kultury <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> właściwości. Wzorzec jest taki sam, jak wzorzec specyfikatora „F”. Jednak <xref:System.DateTime> wartość jest automatycznie konwertowana na czas UTC, przed jego sformatowaniem.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które mogą sterować formatowaniem zwracanego ciągu. Specyfikator formatu niestandardowego, który jest zwracany przez <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> właściwość niektórych kultur może nie mieć używać wszystkich właściwości.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|  
  
 Specyfikator formatu "U" nie jest obsługiwana przez <xref:System.DateTimeOffset> typu i zgłasza <xref:System.FormatException> Jeśli jest używany do formatowania <xref:System.DateTimeOffset> wartość.  
  
 W poniższym przykładzie użyto specyfikatora formatu „U”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Powrót do tabeli](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Specyfikator formatu roku i miesiąca („Y”)  
 Specyfikator formatu standardowego "Y" lub "t" reprezentuje niestandardowa data i ciąg formatu godziny, który jest definiowany przez <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> właściwości określonej kultury. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „yyyy MMMM”.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.DateTimeFormatInfo> obiektu właściwości, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Definiuje ogólny format ciągu wynikowego.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|  
  
 W poniższym przykładzie użyto specyfikatora formatu „y”, aby wyświetlić wartość daty i godziny.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [Powrót do tabeli](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>Uwagi  
  
### <a name="control-panel-settings"></a>Ustawienia panelu sterowania  
 Ustawienia w **Opcje regionalne i językowe** elementu w Panelu sterowania wpływają na ciągi wynikowe generowane przez operację formatowania. Te ustawienia są stosowane do inicjalizacji <xref:System.Globalization.DateTimeFormatInfo> obiekt skojarzony z bieżącą kulturą wątku, która zapewnia wartości stosowane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.  
  
 Ponadto, jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Konstruktor do tworzenia wystąpienia nowego <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę samą kulturę co bieżąca kultura systemu, wszelkie dostosowania ustanowione przez **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Możesz użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor do tworzenia <xref:System.Globalization.CultureInfo> obiektu, który nie będzie odzwierciedlał dostosowań systemu.  
  
### <a name="datetimeformatinfo-properties"></a>Właściwości obiektu DateTimeFormatInfo  
 Formatowanie mają wpływ właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu, dostarczane niejawnie przez bieżącą kulturę wątku lub jawnie przez <xref:System.IFormatProvider> parametru metody, która wywołuje formatowanie. Dla <xref:System.IFormatProvider> parametru, aplikacja musi podawać <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje datę i godzinę, o których konwencje formatowania określonej kultury. Wiele standardowych daty i godziny specyfikatorów formatu są aliasami wzorców formatowania definiowanych przez właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu. Twoja aplikacja może zmieniać wyniki tworzone przez niektóre standardowy format daty i godziny specyfikatorów formatu, zmieniając wzorców odpowiadającego formatu odpowiednią datę i godzinę <xref:System.Globalization.DateTimeFormatInfo> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Przykład: .NET Framework 4 formatowanie narzędzia](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
