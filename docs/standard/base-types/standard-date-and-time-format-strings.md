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
ms.openlocfilehash: 5db29046bfe67c530fe3a613c126c3841e6402e1
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242754"
---
# <a name="standard-date-and-time-format-strings"></a>Standardowe ciągi formatujące datę i godzinę

W ciągu standardowego formatu daty i godziny pojedynczy specyfikator formatu jest używany do definiowania tekstowej reprezentacji wartości daty i godziny. Dowolny ciąg formatu daty i godziny, który zawiera więcej niż jeden znak, w tym biały znak, jest interpretowany jako niestandardowy ciąg formatu daty i godziny; Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Ciągu formatu standardowego lub niestandardowego można używać na dwa sposoby:

- Aby zdefiniować ciąg będący wynikiem operacji formatowania.

- Aby zdefiniować reprezentację tekstową wartości daty i <xref:System.DateTime> godziny, która może być przekonwertowana na lub <xref:System.DateTimeOffset> wartość przez operację analizy.

> [!TIP]
> Można pobrać **narzędzie formatowania**, aplikację .NET Core Windows Forms, która umożliwia stosowanie ciągów formatu do wartości liczbowych lub wartości daty i godziny oraz wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [języka C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) i [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Standardowe ciągi formatu daty i <xref:System.DateTime> <xref:System.DateTimeOffset> godziny mogą być używane z obu i wartości.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>W poniższej tabeli opisano specyfikatory standardowego formatu daty i godziny. O ile nie zaznaczono inaczej, określony format daty i godziny określonego standardu <xref:System.DateTime> tworzy <xref:System.DateTimeOffset> identyczną reprezentację ciągu, niezależnie od tego, czy jest on używany z wartością czy wartością. Zobacz sekcję [Notatki,](#Notes) aby uzyskać dodatkowe informacje na temat używania standardowych ciągów formatu daty i godziny.

|Specyfikator formatu|Opis|Przykłady|
|----------------------|-----------------|--------------|
|„d”|Wzorzec daty krótkiej.<br /><br /> Więcej informacji:[Specyfikator formatu daty krótkiej ("d")](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|
|„D”|Wzorzec daty długiej.<br /><br /> Więcej informacji:[Specyfikator formatu Long Date ("D").](#LongDate)|2009-06-15T13:45:30 -> poniedziałek, 15 czerwca 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|
|„f”|Wzorzec pełnej daty/godziny (godzina krótka).<br /><br /> Więcej informacji: [Specyfikator formatu formatu full date short time ("f").](#FullDateShortTime)|2009-06-15T13:45:30 -> poniedziałek, 15 czerwca 2009 13:45 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτράα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|„F”|Wzorzec pełnej daty/godziny (godzina długa).<br /><br /> Więcej informacji: [Specyfikator formatu pełnego czasu ("F").](#FullDateLongTime)|2009-06-15T13:45:30 -> poniedziałek, 15 czerwca 2009 13:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτράα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|„g”|Wzorzec ogólnej daty/godziny (godzina krótka).<br /><br /> Więcej informacji: [Ogólny terminostatek formatu daty krótkiej ("g").](#GeneralDateShortTime)|2009-06-15T13:45:30 -> 6/15/2009 13:45 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|
|„G”|Wzorzec ogólnej daty/godziny (godzina długa).<br /><br /> Więcej informacji: [Ogólny specyfikator formatu daty długiej ("G").](#GeneralDateLongTime)|2009-06-15T13:45:30 -> 6/15/2009 13:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|
|„M”, „m”|Wzorzec miesiąc/dzień.<br /><br /> Więcej informacji: [Specyfikator formatu miesiąca ("M", "m")](#MonthDay).|2009-06-15T13:45:30 -> 15 czerwca (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|
|„O”, „o”|Wzorzec dwustronnej konwersji data/godzina.<br /><br /> Więcej informacji: [Specyfikator formatu w obie strony ("O", "o")](#Roundtrip).|<xref:System.DateTime>Wartości:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset>Wartości:<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.000000-07:00|
|„R”, „r”|Wzorzec RFC1123.<br /><br /> Więcej informacji: [Specyfikator formatu RFC1123 ("R", "r").) Format Specifier](#RFC1123).|2009-06-15T13:45:30 -> pon, 15 cze 2009 20:45:30 GMT|
|„s”|Wzorzec sortowalnej daty/godziny.<br /><br /> Więcej informacji: [Specyfikator formatu sortowania ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|
|„t”|Wzorzec godziny krótkiej.<br /><br /> Więcej informacji: [Specyfikator formatu krótkiego czasu ("t")](#ShortTime).|2009-06-15T13:45:30 -> 13:45 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|
|„T”|Wzorzec godziny długiej.<br /><br /> Więcej informacji: [Specyfikator formatu long time ("T").](#LongTime)|2009-06-15T13:45:30 -> 13:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)|
|„u”|Wzorzec uniwersalnej sortowalnej daty/godziny.<br /><br /> Więcej informacji: [Uniwersalny specyfikator formatu sortowania ("u").](#UniversalSortable)|O <xref:System.DateTime> wartości: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> O <xref:System.DateTimeOffset> wartości: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|
|„U”|Wzorzec uniwersalnej pełnej daty/godziny.<br /><br /> Więcej informacji: [Specyfikator formatu Universal Full ("U").](#UniversalFull)|2009-06-15T13:45:30 -> poniedziałek, 15 czerwca 2009 20:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτάρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|
|„Y”, „y”|Wzorzec roku i miesiąca.<br /><br /> Więcej informacji: [Specyfikator formatu miesiąca roku ("Y").](#YearMonth)|2009-06-15T13:45:30 -> czerwiec 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator.|Rzuca czas <xref:System.FormatException>wykonywania .|

## <a name="how-standard-format-strings-work"></a>Sposób działania ciągów formatu standardowego

W operacji formatowania ciąg formatu standardowego jest po prostu aliasem ciągu formatu niestandardowego. Zaletą użycia aliasu w celu odwołania się do ciągu formatu niestandardowego jest to, że ciąg formatu niestandardowego może być różny, mimo że alias pozostaje niezmienny. Jest to ważne, ponieważ ciągi reprezentujące wartości daty i godziny są zazwyczaj różne w zależności od kultury. Na przykład ciąg formatu standardowego „d” wskazuje, że wartość daty i godziny zostanie wyświetlona przy użyciu wzorca daty krótkiej. Ten wzorzec dla niezmiennej kultury to „MM/dd/yyyy”. Dla kultury fr-FR jest to „dd/MM/yyyy”. Dla kultury ja-JP jest to „yyyy/MM/dd”.

Jeśli ciąg formatu standardowego w operacji formatowania jest mapowany na ciąg formatu niestandardowego danej kultury, aplikacja może definiować określoną kulturę, której ciągi formatu niestandardowego są używane na jeden z poniższych sposobów:

- Można użyć domyślnej (bieżącej) kultury. W poniższym przykładzie data jest wyświetlana przy użyciu formatu daty krótkiej dla bieżącej kultury. Bieżącą kulturą jest w tym przypadku kultura en-US.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Można przekazać <xref:System.Globalization.CultureInfo> obiekt reprezentujący kulturę, której formatowanie ma być używane <xref:System.IFormatProvider> do metody, która ma parametr. W poniższym przykładzie data jest wyświetlana przy użyciu formatu daty krótkiej dla kultury pt-BR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Obiekt, <xref:System.Globalization.DateTimeFormatInfo> który udostępnia informacje o formatowaniu, do <xref:System.IFormatProvider> metody, która ma parametr. W poniższym przykładzie jest wyświetlana <xref:System.Globalization.DateTimeFormatInfo> data przy użyciu formatu daty krótkiej z obiektu dla kultury hr-HR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Aby uzyskać informacje na temat dostosowywania wzorców lub ciągów używanych <xref:System.Globalization.NumberFormatInfo> w formatowaniu wartości daty i godziny, zobacz temat klasy.

W niektórych przypadkach ciąg formatu standardowego służy jako wygodny skrót dla dłuższego ciągu formatu niestandardowego, który jest niezmienny. Cztery ciągi formatu standardowego należą do tej kategorii: „O” (lub „o”), „R” (lub „r”), „s” i „u”. Te ciągi odpowiadają ciągom formatów niestandardowych, które są zdefiniowane przez niezmienną kulturę. Wytwarzają one reprezentacje wartości daty i godziny w postaci ciągu, które mają być identyczne dla różnych kultur. W poniższej tabeli przedstawiono informacje dotyczące tych czterech ciągów standardowych formatów daty i godziny.

|Ciąg formatu standardowego|Definiowany przez właściwość DateTimeFormatInfo.InvariantInfo|Ciąg formatu niestandardowego|
|----------------------------|----------------------------------------------------------|--------------------------|
|„O” lub „o”|Brak|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|„R” lub „r”|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|„s”|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|„u”|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Ciągi formatu standardowego mogą być również <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> używane <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> w operacjach analizowania z lub metod, które wymagają ciągu wejściowego, aby dokładnie zgodne z określonego wzorca dla operacji analizy zakończyć się pomyślnie. Wiele ciągów formatów standardowych jest mapowanych na wielu ciągów formatów niestandardowych, więc wartość daty i godziny może być reprezentowana przez wiele formatów, a operacja analizy i tak zakończy się powodzeniem. Można określić ciąg formatu niestandardowego lub ciągi, które <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> odpowiadają ciągom w formacie standardowym, wywołując metodę. W poniższym przykładzie są wyświetlane ciągi formatów niestandardowych mapowane na ciąg formatu standardowego „d” (wzorzec daty krótkiej).

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

W poniższych sekcjach opisano specyfikatory formatu standardowego <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

<a name="ShortDate"></a>

## <a name="the-short-date-d-format-specifier"></a>Specyfikator formatu daty krótkiej („d”)

Specyfikator formatu standardowego "d" reprezentuje niestandardowy ciąg formatu daty <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> i godziny, który jest zdefiniowany przez właściwość określonej kultury. Na przykład ciąg formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> który jest zwracany przez właściwość kultury niezmiennej jest "MM/dd/yyyy".

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które kontrolują formatowanie zwracanego ciągu.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definiuje ogólny format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Określa ciąg, który oddziela składniki daty: rok, miesiąc i dzień.|

W poniższym przykładzie użyto specyfikatora formatu „d”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
[!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]

[Powrót do stołu](#table)

<a name="LongDate"></a>

## <a name="the-long-date-d-format-specifier"></a>Specyfikator formatu daty długiej („D”)

Specyfikator formatu standardowego "D" reprezentuje niestandardowy ciąg formatu <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> daty i godziny, który jest zdefiniowany przez bieżącą właściwość. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „dddd, dd MMMM yyyy”.

W poniższej tabeli wymieniono właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu, które kontrolują formatowanie zwracanego ciągu.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definiuje ogólny format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|

W poniższym przykładzie użyto specyfikatora formatu „D”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
[!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]

[Powrót do stołu](#table)

<a name="FullDateShortTime"></a>

## <a name="the-full-date-short-time-f-format-specifier"></a>Specyfikator formatu pełnej daty i godziny krótkiej („f”)

Specyfikator formatu standardowego „f” reprezentuje kombinację wzorców daty długiej („D”) i godziny krótkiej („t”), rozdzielonych spacją.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.DateTimeFormatInfo> formatowaniu określonego obiektu. W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> zwracany przez i właściwości niektórych kultur może nie korzystać ze wszystkich właściwości.

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

[Powrót do stołu](#table)

<a name="FullDateLongTime"></a>

## <a name="the-full-date-long-time-f-format-specifier"></a>Specyfikator formatu pełnej daty i godziny długiej („F”)

Specyfikator formatu standardowego "F" reprezentuje niestandardowy ciąg formatu <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> daty i godziny, który jest zdefiniowany przez bieżącą właściwość. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „dddd, dd MMMM yyyy HH:mm:ss”.

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> który jest zwracany przez właściwość niektórych kultur może nie korzystać ze wszystkich właściwości.

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

[Powrót do stołu](#table)

<a name="GeneralDateShortTime"></a>

## <a name="the-general-date-short-time-g-format-specifier"></a>Specyfikator formatu daty ogólnej i godziny krótkiej („g”)

Specyfikator formatu standardowego „g” reprezentuje kombinację wzorców daty krótkiej („g”) i godziny krótkiej („t”), rozdzielonych spacją.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.DateTimeFormatInfo> formatowaniu określonego obiektu. W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> który <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> jest zwracany przez i właściwości niektórych kultur może nie korzystać ze wszystkich właściwości.

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

[Powrót do stołu](#table)

<a name="GeneralDateLongTime"></a>

## <a name="the-general-date-long-time-g-format-specifier"></a>Specyfikator formatu daty ogólnej i godziny długiej („G”)

Specyfikator formatu standardowego „G” reprezentuje kombinację wzorców daty krótkiej („d”) i godziny długiej („T”), rozdzielonych spacją.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.DateTimeFormatInfo> formatowaniu określonego obiektu. W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> który <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> jest zwracany przez i właściwości niektórych kultur może nie korzystać ze wszystkich właściwości.

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

[Powrót do stołu](#table)

<a name="MonthDay"></a>

## <a name="the-month-m-m-format-specifier"></a>Specyfikator formatu miesiąca („M”, „m”)

Specyfikator formatu standardowego "M" lub "m" reprezentuje niestandardowy ciąg <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> formatu daty i godziny, który jest zdefiniowany przez bieżącą właściwość. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „MMMM dd”.

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które kontrolują formatowanie zwracanego ciągu.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Definiuje ogólny format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|

W poniższym przykładzie użyto specyfikatora formatu „m”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
[!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]

[Powrót do stołu](#table)

<a name="Roundtrip"></a>

## <a name="the-round-trip-o-o-format-specifier"></a>Specyfikator formatu dwustronnej konwersji („O”, „o”)

Specyfikator formatu standardowego "O" lub "o" reprezentuje niestandardowy ciąg formatu daty i godziny przy użyciu wzorca, który zachowuje informacje o strefie czasowej i emituje ciąg wyników zgodny z normą ISO 8601. Dla <xref:System.DateTime> wartości ten specyfikator formatu jest przeznaczony do <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> zachowania wartości daty i godziny wraz z właściwością w tekście. Sformatowany ciąg można przeanalizować za <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> pomocą metody `styles` lub, <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>jeśli parametr jest ustawiony na .

Specyfikator formatu standardowego "O" lub "o" odpowiada "rrrr'-'MM'-'dd':'mm':''ss'.' fffffK" ciąg niestandardowego <xref:System.DateTime> formatu dla wartości i "yyyy'-'MM'-'dd':'mm':'ss'.' fffffzzz" ciąg niestandardowego <xref:System.DateTimeOffset> formatu dla wartości. W tym ciągu pary znaków apostrofu, które oddzielają pojedyncze znaki, takie jak łączniki, dwukropki i litera „T”, wskazują, że indywidualny znak jest literałem, który nie może być zmieniony. Apostrofy nie znajdują się w ciągu wyjściowym.

Specyfikator formatu standardowego "O" lub "o" (oraz "rrrr'-'MM'-'dd':'mm':''ss'.' fffffK" ciąg formatu niestandardowego) wykorzystuje trzy sposoby, że ISO 8601 reprezentuje informacje o strefie czasowej, aby zachować <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTime> wartości:

- Składnik strefy czasowej wartości <xref:System.DateTimeKind.Local?displayProperty=nameWithType> daty i godziny jest przesunięciem z czasu UTC (na przykład +01:00, -07:00). Wszystkie <xref:System.DateTimeOffset> wartości są również reprezentowane w tym formacie.

- Składnik strefy czasowej wartości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> daty i godziny używa "Z" (co oznacza zero przesunięcia) do reprezentowania utc.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>wartości daty i godziny nie mają informacji o strefie czasowej.

Ponieważ specyfikator formatu standardowego "O" lub "o" jest zgodny z międzynarodowym standardem, operacja formatowania lub analizowania używana przez specyfikatora zawsze używa kultury niezmiennej i kalendarza gregoriańskiego.

Ciągi, które są `Parse` `TryParse`przekazywane `ParseExact`do `TryParseExact` , <xref:System.DateTime> <xref:System.DateTimeOffset> , i metody i mogą być analizowane przy użyciu specyfikatora formatu "O" lub "o", jeśli znajdują się one w jednym z tych formatów. W przypadku <xref:System.DateTime> obiektów przeciążenie analizujące, które można wywołać, powinno również zawierać `styles` parametr o <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>wartości . Należy zauważyć, że jeśli wywołasz metodę analizowania z ciągiem formatu niestandardowego, który odpowiada specyfikatorowi formatu "O" lub "o", nie uzyskasz tych samych wyników co "O" lub "o". Dzieje się tak, ponieważ metody analizowania, które używają ciągu formatu niestandardowego, nie mogą przeanalizować reprezentacji ciągu wartości daty i godziny, które nie są używane jako składnik strefy czasowej, lub użyć "Z", aby wskazać utc.

W poniższym przykładzie użyto specyfikatora formatu <xref:System.DateTime> "o" do wyświetlania serii wartości i <xref:System.DateTimeOffset> wartości w systemie w strefie czasowej Pacyfiku Stanów Zjednoczonych.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

W poniższym przykładzie użyto specyfikatora formatu "o", aby utworzyć sformatowany ciąg, a `Parse` następnie przywraca oryginalną wartość daty i godziny, wywołując metodę daty i godziny.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Powrót do stołu](#table)

<a name="RFC1123"></a>

## <a name="the-rfc1123-r-r-format-specifier"></a>Specyfikator formatu RFC1123 („R”, „r”)

Specyfikator formatu standardowego "R" lub "r" reprezentuje niestandardowy ciąg <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> formatu daty i godziny, który jest zdefiniowany przez właściwość. Wzorzec odzwierciedla zdefiniowany standard, a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „ddd, dd MMM yyyy HH':'mm':'ss 'GMT'”. Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.

Ciąg wynikowy ma wpływ następujące właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> przez właściwość, która reprezentuje kultury niezmienne.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definiuje format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definiuje skrócone nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definiuje skrócone nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|

Mimo że standard RFC 1123 wyraża czas jako skoordynowany czas uniwersalny (UTC), <xref:System.DateTime> operacja formatowania nie modyfikuje wartości obiektu, który jest formatowany. W związku z tym <xref:System.DateTime> należy przekonwertować <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> wartość UTC, wywołując metodę przed wykonaniem operacji formatowania. Z kolei <xref:System.DateTimeOffset> wartości wykonują tę konwersję automatycznie; nie ma potrzeby wywoływania <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody przed operacją formatowania.

W poniższym przykładzie użyto specyfikatora <xref:System.DateTime> formatu <xref:System.DateTimeOffset> "r", aby wyświetlić wartość i wartość w systemie w strefie czasowej Pacyfiku Stanów Zjednoczonych.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Powrót do stołu](#table)

<a name="Sortable"></a>

## <a name="the-sortable-s-format-specifier"></a>Specyfikator formatu sortowalnego („s”)

Specyfikator formatu standardowego "s" reprezentuje niestandardowy ciąg formatu daty i godziny, który jest zdefiniowany przez <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> właściwość. Wzorzec odzwierciedla zdefiniowany standard (ISO 8601), a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „yyyy'-'MM'-'dd'T'HH':'mm':'ss”.

Celem specyfikatora formatu "s" jest tworzenie ciągów wyników, które sortują konsekwentnie w kolejności rosnącej lub malejącej na podstawie wartości daty i godziny. W rezultacie, chociaż specyfikator formatu standardowego "s" reprezentuje wartość daty i godziny w spójnym formacie, operacja formatowania nie modyfikuje wartości obiektu daty i godziny, który jest sformatowany w celu odzwierciedlenia jego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości lub jej <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> wartości. Na przykład ciągi wyników uzyskane przez formatowanie wartości daty i godziny 2014-11-15T18:32:17+00:00 i 2014-11-15T18:32:17+08:00 są identyczne.

Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.

W poniższym przykładzie użyto specyfikatora <xref:System.DateTime> formatu <xref:System.DateTimeOffset> "s", aby wyświetlić wartość i wartość w systemie w strefie czasowej Pacyfiku Stanów Zjednoczonych.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Powrót do stołu](#table)

<a name="ShortTime"></a>

## <a name="the-short-time-t-format-specifier"></a>Specyfikator formatu godziny krótkiej („t”)

Specyfikator formatu standardowego "t" reprezentuje niestandardowy ciąg formatu <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> daty i godziny, który jest zdefiniowany przez bieżącą właściwość. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „HH:mm”.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.DateTimeFormatInfo> formatowaniu określonego obiektu. W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> który jest zwracany przez właściwość niektórych kultur może nie korzystać ze wszystkich właściwości.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|

W poniższym przykładzie użyto specyfikatora formatu „t”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
[!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]

[Powrót do stołu](#table)

<a name="LongTime"></a>

## <a name="the-long-time-t-format-specifier"></a>Specyfikator formatu godziny długiej („T”)

Specyfikator formatu standardowego "T" reprezentuje niestandardowy ciąg formatu daty <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> i godziny, który jest zdefiniowany przez właściwość określonej kultury. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „HH:mm:ss”.

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> który jest zwracany przez właściwość niektórych kultur może nie korzystać ze wszystkich właściwości.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definiuje format składnika godziny w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|

W poniższym przykładzie użyto specyfikatora formatu „T”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
[!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]

[Powrót do stołu](#table)

<a name="UniversalSortable"></a>

## <a name="the-universal-sortable-u-format-specifier"></a>Specyfikator uniwersalnego sortowalnego formatu („u”)

Specyfikator formatu standardowego "u" reprezentuje niestandardowy ciąg formatu daty i godziny, który jest zdefiniowany przez <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> właściwość. Wzorzec odzwierciedla zdefiniowany standard, a właściwość jest tylko do odczytu. Dlatego też zawsze jest taki sam, niezależnie od używanej kultury oraz dostarczonego dostawcy formatów. Ciąg formatu niestandardowego to „yyyy'-'MM'-'dd HH':'mm':'ss'Z'”. Gdy jest używany ten specyfikator formatu standardowego, w operacji formatowania lub analizowania zawsze jest używana niezmienna kultura.

Mimo że ciąg wynikowy powinien wyrażać czas jako skoordynowany czas <xref:System.DateTime> uniwersalny (UTC), podczas operacji formatowania nie jest wykonywana żadna konwersja oryginalnej wartości. W związku z tym <xref:System.DateTime> należy przekonwertować <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> wartość UTC, wywołując metodę przed formatowaniem go.  Z kolei <xref:System.DateTimeOffset> wartości wykonują tę konwersję automatycznie; nie ma potrzeby wywoływania <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody przed operacją formatowania.

W poniższym przykładzie użyto specyfikatora formatu „u”, aby wyświetlić wartość daty i godziny.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Powrót do stołu](#table)

<a name="UniversalFull"></a>

## <a name="the-universal-full-u-format-specifier"></a>Specyfikator uniwersalnego pełnego formatu („U”)

Specyfikator formatu standardowego "U" reprezentuje niestandardowy ciąg formatu daty <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> i godziny, który jest zdefiniowany przez właściwość określonej kultury. Wzorzec jest taki sam, jak wzorzec specyfikatora „F”. Jednak <xref:System.DateTime> wartość jest automatycznie konwertowana na utc przed jej sformatowania.

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które mogą kontrolować formatowanie zwracanego ciągu. Specyfikator formatu niestandardowego, <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> który jest zwracany przez właściwość niektórych kultur może nie korzystać ze wszystkich właściwości.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definiuje ogólny format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definiuje zlokalizowane nazwy dni, które mogą być wyświetlane w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definiuje ciąg, który rozdziela składniki godziny, minuty i sekundy w ciągu reprezentującym godzinę.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Określa ciąg, który wskazuje czas od północy do południa (z wyłączeniem południa), w formacie 12-godzinnym.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Określa ciąg, który wskazuje czas od południa do północy (z wyłączeniem północy), w formacie 12-godzinnym.|

Specyfikator formatu "U" nie jest <xref:System.DateTimeOffset> obsługiwany przez <xref:System.FormatException> typ i rzuca, <xref:System.DateTimeOffset> jeśli jest używany do formatowania wartości.

W poniższym przykładzie użyto specyfikatora formatu „U”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Powrót do stołu](#table)

<a name="YearMonth"></a>

## <a name="the-year-month-y-y-format-specifier"></a>Specyfikator formatu roku i miesiąca („Y”)

Specyfikator formatu standardowego "Y" lub "y" reprezentuje niestandardowy ciąg <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> formatu daty i godziny, który jest zdefiniowany przez właściwość określonej kultury. Na przykład ciąg formatu niestandardowego dla niezmiennej kultury to „yyyy MMMM”.

W poniższej <xref:System.Globalization.DateTimeFormatInfo> tabeli wymieniono właściwości obiektu, które kontrolują formatowanie zwracanego ciągu.

|Właściwość|Opis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Definiuje ogólny format ciągu wynikowego.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definiuje zlokalizowane nazwy miesięcy, które mogą być wyświetlane w ciągu wynikowym.|

W poniższym przykładzie użyto specyfikatora formatu „y”, aby wyświetlić wartość daty i godziny.

[!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
[!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]

[Powrót do stołu](#table)

<a name="Notes"></a>

## <a name="notes"></a>Uwagi

### <a name="control-panel-settings"></a>Ustawienia panelu sterowania

Ustawienia w elemencie **Opcje regionalne i językowe** w Panelu sterowania mają wpływ na ciąg wynikowy wytwarzany przez operację formatowania. Te ustawienia są używane <xref:System.Globalization.DateTimeFormatInfo> do inicjowania obiektu skojarzonego z bieżącą kulturą wątku, która zawiera wartości używane do regulowania formatowania. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> konstruktora do tworzenia <xref:System.Globalization.CultureInfo> wystąpienia nowego obiektu, który reprezentuje tę samą kulturę co bieżąca kultura systemowa, wszystkie dostosowania <xref:System.Globalization.CultureInfo> ustanowione przez element Opcje regionalne i **językowe** w Panelu sterowania zostaną zastosowane do nowego obiektu. Konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> służy do <xref:System.Globalization.CultureInfo> tworzenia obiektu, który nie odzwierciedla dostosowania systemu.

### <a name="datetimeformatinfo-properties"></a>Właściwości obiektu DateTimeFormatInfo

Formatowanie zależy od właściwości bieżącego <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest niejawnie przez bieżącą <xref:System.IFormatProvider> kulturę wątku lub jawnie przez parametr metody, która wywołuje formatowanie. Dla <xref:System.IFormatProvider> parametru aplikacji należy <xref:System.Globalization.CultureInfo> określić obiekt, który reprezentuje <xref:System.Globalization.DateTimeFormatInfo> kultury lub obiektu, który reprezentuje konwencji formatowania określonej kultury i godziny. Wiele specyfikatorów standardowego formatu daty i godziny to aliasy do <xref:System.Globalization.DateTimeFormatInfo> formatowania wzorców zdefiniowanych przez właściwości bieżącego obiektu. Aplikacja może zmienić wynik wyprodukowany przez niektóre standardowe specyfikatory formatu daty i <xref:System.Globalization.DateTimeFormatInfo> godziny, zmieniając odpowiednie wzorce formatu daty i godziny odpowiedniej właściwości.

## <a name="see-also"></a>Zobacz też

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Niestandardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Przykład: narzędzie do formatowania .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Przykład: narzędzie do formatowania .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
