---
title: Praca z kalendarzami
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28e1979b6ceb1b343764900cc7d49a576a7a4030
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630550"
---
# <a name="working-with-calendars"></a>Praca z kalendarzami

Wartość daty i godziny reprezentuje moment w czasie, ale jej reprezentacja w postaci ciągu jest zależna od kultury, ponieważ zależy zarówno od konwencji używanych do wyświetlania wartości daty i godziny obowiązujących w danej kulturze, jak i od kalendarza używanego w tej kulturze. W tym temacie przedstawiono obsługę kalendarzy w programie .NET i omówiono użycie klas kalendarza podczas pracy z wartościami dat.

## <a name="calendars-in-net"></a>Kalendarze w programie .NET

Wszystkie kalendarze w programie .NET pochodzą <xref:System.Globalization.Calendar?displayProperty=nameWithType> z klasy, która udostępnia podstawową implementację kalendarza. Jedną z klas, które dziedziczy z <xref:System.Globalization.Calendar> klasy, <xref:System.Globalization.EastAsianLunisolarCalendar> jest Klasa, która jest klasą bazową dla wszystkich kalendarzy księżycowo-słoneczny. Platforma .NET obejmuje następujące implementacje kalendarza:

* <xref:System.Globalization.ChineseLunisolarCalendar>, który reprezentuje kalendarz chiński księżycowo-słoneczny.

* <xref:System.Globalization.GregorianCalendar>, która reprezentuje kalendarz gregoriański. Ten kalendarz jest dalej podzielony na podtypy (takie jak arabski i Bliski Wschód francuski), które są zdefiniowane przez <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> Wyliczenie. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Właściwość określa podtyp kalendarza gregoriańskiego.

* <xref:System.Globalization.HebrewCalendar>, która reprezentuje kalendarz hebrajski.

* <xref:System.Globalization.HijriCalendar>, która reprezentuje kalendarz Hidżry.

* <xref:System.Globalization.JapaneseCalendar>, która reprezentuje Kalendarz japoński.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, który reprezentuje japoński kalendarz księżycowo-słoneczny.

* <xref:System.Globalization.JulianCalendar>, który reprezentuje kalendarz juliańskim.

* <xref:System.Globalization.KoreanCalendar>, która reprezentuje kalendarz koreański.

* <xref:System.Globalization.KoreanLunisolarCalendar>, który reprezentuje kalendarz Koreański księżycowo-słoneczny.

* <xref:System.Globalization.PersianCalendar>, który reprezentuje kalendarz perski.

* <xref:System.Globalization.TaiwanCalendar>, który reprezentuje kalendarz tajwański.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, który reprezentuje kalendarz księżycowo-słoneczny Tajwanu.

* <xref:System.Globalization.ThaiBuddhistCalendar>, która przedstawia tajlandzki kalendarz Buddyjski.

* <xref:System.Globalization.UmAlQuraCalendar>, który reprezentuje kalendarz UM Al Qura.

Kalendarza można używać na jeden z dwóch sposobów:

* Jako kalendarz używany przez określoną kulturę. Każdy <xref:System.Globalization.CultureInfo> obiekt ma bieżący kalendarz, który jest kalendarzem aktualnie używanym przez obiekt. Reprezentacje wszystkich wartości daty i godziny w formacie ciągu automatycznie odzwierciedlają bieżącą kulturę i jej bieżący kalendarz. Zazwyczaj bieżącym kalendarzem jest kalendarz domyślny kultury. <xref:System.Globalization.CultureInfo>obiekty zawierają również opcjonalne kalendarze, które obejmują dodatkowe kalendarze, które mogą być używane w kulturze.

* Jako kalendarz autonomiczny, niezależny od określonej kultury. W takim przypadku <xref:System.Globalization.Calendar> metody są używane do wyrażania dat jako wartości, które odzwierciedlają kalendarz.

Należy pamiętać, że sześć klas <xref:System.Globalization.ChineseLunisolarCalendar>kalendarzowych <xref:System.Globalization.JulianCalendar>— <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar>,, <xref:System.Globalization.TaiwanLunisolarCalendar> , i — może być używane tylko jako kalendarze autonomiczne. Nie są one używane przez żadną kulturę ani jako kalendarz domyślny, ani jako kalendarz opcjonalny.

## <a name="calendars-and-cultures"></a>Kalendarze i kultury

Każda kultura ma domyślny kalendarz, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwość. Właściwość zwraca tablicę obiektów, która określa wszystkie kalendarze obsługiwane przez określoną kulturę, w tym kalendarz domyślny tej kultury. <xref:System.Globalization.Calendar> <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>

Poniższy przykład ilustruje <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości i <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> . Tworzy `CultureInfo` obiekty dla kultur tajski (Tajlandia) i japoński (Japonia) i wyświetla ich domyślne i opcjonalne kalendarze. Należy zauważyć, że w obu przypadkach kalendarz domyślny kultury jest również uwzględniony w <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekcji.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendarz aktualnie używany przez określony <xref:System.Globalization.CultureInfo> obiekt jest zdefiniowany przez <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwość kultury. <xref:System.Globalization.DateTimeFormatInfo> Obiekt kultury jest zwracany <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> przez właściwość. Po utworzeniu kultury jego wartość domyślna jest taka sama jak wartość <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Można jednak zmienić bieżący kalendarz kultury na dowolny kalendarz zawarty w tablicy zwracanej przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwość. Jeśli spróbujesz ustawić bieżący kalendarz do kalendarza, który nie jest uwzględniony w <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> wartości właściwości <xref:System.ArgumentException> , zostanie zgłoszony.

W poniższym przykładzie jest zmieniany kalendarz używany przez kulturę Arabski (Arabia Saudyjska). Najpierw tworzy wystąpienie <xref:System.DateTime> wartości i wyświetla go przy użyciu bieżącej kultury — w tym przypadku jest to angielski (Stany Zjednoczone) i kalendarz bieżącej kultury (który w tym przypadku jest kalendarzem gregoriańskim). Następnie bieżąca kultura jest zmieniana na Arabski (Arabia Saudyjska) i data jest wyświetlana przy użyciu domyślnego kalendarza tej kultury, czyli Um Al-Qura. Następnie wywołuje metodę, `CalendarExists` aby określić, czy Kalendarz Hidżry jest obsługiwany przez kulturę arabską (Arabia Saudyjska). Ten kalendarz jest obsługiwany, więc bieżący kalendarz jest zmieniany na kalendarz Hidżry i ponownie jest wyświetlana data. Należy zauważyć, że w każdym przypadku data jest wyświetlana przy użyciu bieżącego kalendarza bieżącej kultury.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Daty i kalendarze

Z wyjątkiem konstruktorów, które zawierają parametr typu <xref:System.Globalization.Calendar> i zezwalają na elementy daty (to znaczy miesiąc, dzień i rok), aby odzwierciedlić wartości w wyznaczeniym kalendarzu, obie <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są zawsze w oparciu o kalendarz gregoriański. Oznacza to, na przykład, że <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Właściwość zwraca rok w kalendarzu gregoriańskim, <xref:System.DateTime.Day%2A?displayProperty=nameWithType> a właściwość zwraca dzień miesiąca w kalendarzu gregoriańskim.

> [!IMPORTANT]
> Ważne jest, aby pamiętać o różnicy między wartością daty a jej reprezentacją w formacie ciągu. Pierwsza jest oparta na kalendarzu gregoriańskim, a druga na bieżącym kalendarzu określonej kultury.

Poniższy przykład ilustruje tę różnicę między <xref:System.DateTime> właściwościami i odpowiednimi <xref:System.Globalization.Calendar> metodami. W tym przykładzie bieżącą kulturą jest Arabski (Egipt), a bieżącym kalendarzem jest Um Al Qura. <xref:System.DateTime> Wartość jest ustawiona na piętnasty dzień siódmego miesiąca 2011. Jest to oczywiste, że jest interpretowana jako data gregoriański, ponieważ te same wartości są zwracane przez <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę, gdy używa konwencji niezmiennej kultury. Reprezentacja tej daty w formacie ciągu, która jest formatowana z użyciem konwencji bieżącej kultury, to 14/08/32, co odpowiada dacie w kalendarzu Um Al Qura. Następnie członkowie `DateTime` i `Calendar` są używani do zwrócenia dnia, miesiąca <xref:System.DateTime> i roku wartości. W każdym przypadku wartości zwracane przez <xref:System.DateTime> elementy członkowskie odzwierciedlają wartości w kalendarzu gregoriańskim, a wartości zwracane przez <xref:System.Globalization.UmAlQuraCalendar> elementy członkowskie odzwierciedlają wartości w kalendarzu UUM Al-Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Tworzenie wystąpień dat na podstawie kalendarza

Ponieważ <xref:System.DateTime> wartości <xref:System.DateTimeOffset> i są oparte na kalendarzu gregoriańskim, należy wywołać przeciążony Konstruktor, który zawiera parametr typu <xref:System.Globalization.Calendar> , aby utworzyć wystąpienie wartości daty, jeśli chcesz użyć wartości Day, Month lub Year z inny kalendarz. Możesz również wywołać jedno z przeciążeń określonej <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metody kalendarza, aby <xref:System.DateTime> utworzyć wystąpienie obiektu na podstawie wartości określonego kalendarza.

Poniższy <xref:System.DateTime> przykład tworzy wystąpienie jednej wartości przez <xref:System.Globalization.HebrewCalendar> przekazanie obiektu do <xref:System.DateTime> konstruktora i tworzy <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> wystąpienie drugiej <xref:System.DateTime> wartości przez wywołanie metody. Ponieważ dwie wartości są tworzone z identycznymi wartościami w kalendarzu hebrajskim, wywołanie <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> metody pokazuje, że dwie <xref:System.DateTime> wartości są równe.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Przedstawianie dat w bieżącym kalendarzu

Metody formatowania daty i godziny zawsze używają bieżącego kalendarza podczas konwertowania dat na ciągi. Oznacza to, że reprezentacja roku, miesiąca i dnia miesiąca w formacie ciągu odzwierciedla bieżący kalendarz i nie musi to być kalendarz gregoriański.

W poniższym przykładzie pokazano, jak bieżący kalendarz wpływa na reprezentację daty w formacie ciągu. Bieżąca kultura jest zmieniana na Chiński (tradycyjny, Tajwan) i jest tworzone wystąpienie wartości daty. Następnie wyświetla bieżący kalendarz i datę, zmienia bieżący kalendarz na <xref:System.Globalization.TaiwanCalendar>, a następnie wyświetla bieżący kalendarz i datę ponownie. Gdy data jest wyświetlana po raz pierwszy, jest przedstawiana jako data w kalendarzu gregoriańskim. Gdy data jest wyświetlana po raz drugi, jest przedstawiana jako data w kalendarzu tajwańskim.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Przedstawianie dat w kalendarzu innym niż bieżący

Aby przedstawić datę przy użyciu kalendarza, który nie jest bieżącym kalendarzem danej kultury, należy wywołać metody tego <xref:System.Globalization.Calendar> obiektu. Na przykład <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType> <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>,, i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody konwertują rok, miesiąc i dzień na wartości, które odzwierciedlają określony kalendarz.

> [!WARNING]
> Niektóre kalendarze nie są opcjonalnymi kalendarzami żadnej kultury, więc przedstawianie dat za pomocą tych kalendarzy zawsze wymaga wywołania metod kalendarza. Dotyczy to wszystkich kalendarzy <xref:System.Globalization.EastAsianLunisolarCalendar>, które pochodzą z klas, <xref:System.Globalization.JulianCalendar>, i. <xref:System.Globalization.PersianCalendar>

Poniższy przykład używa <xref:System.Globalization.JulianCalendar> obiektu do utworzenia wystąpienia daty, 9 stycznia 1905 w kalendarzu juliańskim. Gdy ta data jest wyświetlana przy użyciu kalendarza domyślnego (gregoriańskiego), jest przedstawiana jako 22 stycznia 1905 roku. Wywołania poszczególnych <xref:System.Globalization.JulianCalendar> metod umożliwiają, aby data była reprezentowana w kalendarzu juliańskim.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendarze i zakresy dat

Najwcześniejsza data obsługiwana przez kalendarz jest wskazywana przez <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> właściwość Calendar. Dla tej <xref:System.Globalization.GregorianCalendar> klasy Data to 1 stycznia 0001 0001 Większość innych kalendarzy w programie .NET obsługuje późniejszą datę. Próba pracy z wartością daty i godziny, która poprzedza najwcześniejszą obsługiwaną datę kalendarza, zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek.

Istnieje jednak jeden ważny wyjątek. Wartość <xref:System.DateTime> domyślna (niezainicjowana) obiektu <xref:System.DateTimeOffset> i <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> obiektu jest równa wartości. Jeśli spróbujesz sformatować tę datę w kalendarzu, który nie obsługuje 1 stycznia 0001 0001 i nie podasz specyfikatora formatu, Metoda formatowania używa specyfikatora formatu "s" (sortowanie daty/godziny) zamiast specyfikatora formatu "G" (wzorzec ogólnej daty/godziny). W związku z tym operacja <xref:System.ArgumentOutOfRangeException> formatowania nie zgłasza wyjątku. W zamian zwróci nieobsługiwaną datę. Jest to zilustrowane w poniższym przykładzie, który wyświetla wartość <xref:System.DateTime.MinValue?displayProperty=nameWithType> , gdy bieżąca kultura jest ustawiona na japoński (Japonia) z kalendarzem japońskim i na arabski (Egipt) z kalendarzem UM Al Qura. Ustawia również bieżącą kulturę na angielski (Stany Zjednoczone) i wywołuje <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metodę z każdym z tych <xref:System.Globalization.CultureInfo> obiektów. W każdym przypadku data jest wyświetlana z użyciem wzorca sortowalnej daty/godziny.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Praca z wymazywaniem

Daty w kalendarzach są zazwyczaj dzielone na ery. Jednak klasy w programie .NET nie obsługują każdej oceny era zdefiniowanej przez kalendarz i większość <xref:System.Globalization.Calendar> klas obsługuje tylko pojedynczą ERA. <xref:System.Globalization.Calendar> Tylko klasy <xref:System.Globalization.JapaneseLunisolarCalendar> i obsługują wiele wymazanych. <xref:System.Globalization.JapaneseCalendar>

> [!IMPORTANT]
> Reiwa ERA, nowe ERA w <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar>, rozpocznie się od 1 maja 2019. Ta zmiana ma wpływ na wszystkie aplikacje korzystające z tych kalendarzy. Aby uzyskać więcej informacji, zobacz następujące artykuły:
> - [Obsługa nowej ERA w kalendarzu japońskim w programie .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), które dokumenty zostały dodane do platformy .NET, aby obsługiwać kalendarze z wieloma wymazywanymi i omawiać najlepsze rozwiązania w zakresie obsługi kalendarzy wieloletnich.
> - [Przygotuj aplikację dla japońskiej zmiany ery](/windows/uwp/design/globalizing/japanese-era-change), która zawiera informacje dotyczące testowania aplikacji w systemie Windows w celu zapewnienia ich gotowości do zmiany ERA.
> - [Podsumowanie nowych, japońskich aktualizacji ery dla .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), które zawierają informacje o .NET Framework aktualizacjach dla poszczególnych wersji systemu Windows, które są powiązane z nowym kalendarzem japońskim — ERA, nowe funkcje .NET Framework do obsługi wieloetapowej oceny, a także zawiera elementy do Poszukaj w temacie Testowanie aplikacji.

Ocena ERA w większości kalendarzy oznacza bardzo długi czas. Na przykład w kalendarzu gregoriańskim bieżące era obejmuje więcej niż dwa Millennia. <xref:System.Globalization.JapaneseCalendar> Dla<xref:System.Globalization.JapaneseLunisolarCalendar>i, dwa kalendarze, które obsługują wiele wymazania, nie jest to przypadek. Era odpowiada okresowi Imperatora Reign. Obsługa wielu wymazów, szczególnie w przypadku, gdy górny limit bieżącej ery jest nieznany, stanowi specjalne wyzwania.

### <a name="eras-and-era-names"></a>Nazwy wymazane i era

W programie .NET liczby całkowite reprezentujące wymazanie obsługiwane przez określoną implementację kalendarza są przechowywane w odwrotnej kolejności w <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tablicy. Bieżąca ERA (która jest era z ostatnim zakresem czasu) ma wartość indeks zero, a dla <xref:System.Globalization.Calendar> klas, które obsługują wiele wymazania, każdy kolejny indeks odzwierciedla poprzednią ocenę. Właściwość static <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> definiuje indeks bieżącej ery <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> w tablicy; jest to stała, której wartość jest zawsze równa zero. Poszczególne <xref:System.Globalization.Calendar> klasy zawierają także pola statyczne, które zwracają wartość bieżącej ery. Zostały one wymienione w poniższej tabeli.

| Klasa kalendarza                                        | Pole bieżącej ery                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

Nazwa, która odnosi się do określonego numeru ERA, można pobrać, przekazując liczbę ERA do <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metody lub. <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> Poniższy przykład wywołuje te metody, aby pobrać informacje o obsłudze ERA w <xref:System.Globalization.GregorianCalendar> klasie. Wyświetla datę kalendarza gregoriańskiego, która odpowiada 1 stycznia w drugim roku bieżącej oceny ERA, a także datę kalendarza gregoriańskiego, która odpowiada 1 stycznia w drugim roku każdej z obsługiwanych ery w kalendarzu japońskim.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Ponadto niestandardowy format daty i godziny „g” dołącza nazwę ery kalendarza do reprezentacji daty i godziny w formacie ciągu. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Tworzenie wystąpienia daty z era

Dla dwóch <xref:System.Globalization.Calendar> klas, które obsługują wiele wymazania, Data, która składa się z określonego roku, miesiąca i dnia wartości miesiąca, może być niejednoznaczna. Na przykład wszystkie wymazywane, obsługiwane przez <xref:System.Globalization.JapaneseCalendar> lata mające numer 1. Normalnie, jeśli era nie jest określona, metody daty i godziny oraz kalendarza zakładają, że wartości należą do bieżącej ery. Jest <xref:System.DateTime.%23ctor%2A> to prawdziwe dla <xref:System.DateTimeOffset.%23ctor%2A> konstruktorów, które obejmują parametry typu <xref:System.Globalization.Calendar>, a także metody [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) i [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) . Poniższy przykład tworzy wystąpienie daty, która reprezentuje 1 stycznia drugiego roku nieokreślonego ery. W przypadku wykonania przykładu, gdy Reiwa era to bieżąca ERA, data jest interpretowana jako drugi rok Reiwa ERA. Era, 令和, poprzedza rok w ciągu zwracanym przez <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> metodę i odpowiada 1 stycznia 2020 w kalendarzu gregoriańskim. (Reiwa era rozpoczyna się w roku 2019 kalendarza gregoriańskiego).

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Jednak w przypadku zmiany ery zamiar tego kodu jest niejednoznaczny. Jest datą przeznaczoną do reprezentowania drugiego roku bieżącej ery lub czy ma reprezentować drugi rok oceny Heisei era? Istnieją dwa sposoby, aby uniknąć tej niejednoznaczności:

- Utwórz wystąpienie wartości daty i godziny przy użyciu klasy <xref:System.Globalization.GregorianCalendar> domyślnej. Następnie można użyć kalendarza japońskiego lub w japońskim kalendarzu księżycowo-słoneczny w celu przedstawienia ciągu dat, jak pokazano w poniższym przykładzie.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Wywołaj metodę daty i godziny, która jawnie określa ERA. Obejmuje to następujące metody:

  - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Metoda<xref:System.Globalization.JapaneseCalendar> klasy or .<xref:System.Globalization.JapaneseLunisolarCalendar>

  - <xref:System.DateTimeOffset> <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> <xref:System.Globalization.DateTimeStyles> Metoda analizy lub,<xref:System.DateTime.ParseExact%2A>taka jak,, lub<xref:System.DateTime.TryParseExact%2A>, która zawiera ciąg do przeanalizowania i opcjonalnie argumentu, jeśli bieżąca kultura jest Japońska — Japonia (" <xref:System.DateTime> ja-JP ") i kalendarzową kulturą jest <xref:System.Globalization.JapaneseCalendar>. Ciąg, który ma być analizowany, musi zawierać ERA.

  - Metoda analizy <xref:System.DateTimeOffset> lub, która zawiera <xref:System.IFormatProvider>parametr typu. `provider` <xref:System.DateTime> `provider`musi <xref:System.Globalization.CultureInfo> być obiektem, który reprezentuje kulturę Japońska — Japonia ("ja-JP"), której bieżący <xref:System.Globalization.JapaneseCalendar> Kalendarz lub obiekt <xref:System.Globalization.DateTimeFormatInfo> , którego <xref:System.Globalization.DateTimeFormatInfo.Calendar> właściwość jest <xref:System.Globalization.JapaneseCalendar>. Ciąg, który ma być analizowany, musi zawierać ERA.

  W poniższym przykładzie zastosowano trzy z tych metod w celu utworzenia wystąpienia daty i godziny w Meiji ERA, która zaczęła się od 8 września 1868 i została zakończona 29 lipca 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Podczas pracy z kalendarzami, które obsługują wiele operacji wymazywania, należy *zawsze* używać gregoriańskiej daty do tworzenia wystąpienia daty lub określić ERA w przypadku wystąpienia daty i godziny w oparciu o ten kalendarz.

W przypadku określania oceny ekologicznej <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metody, należy podać indeks era we <xref:System.Globalization.Calendar.Eras> właściwości Calendar. Jednak w przypadku kalendarzy, których wymazywanie podlegają zmianom, te indeksy nie są wartościami stałymi; Bieżąca era jest w indeksie 0, a najstarsza era jest w `Eras.Length - 1`indeksie. Gdy do kalendarza zostanie dodane nowe ERA, indeksy poprzednio wymazane zwiększają się o jeden. Odpowiedni indeks ERA można podać w następujący sposób:

- W przypadku dat w bieżącej era należy zawsze używać <xref:System.Globalization.Calendar.CurrentEra> właściwości Calendar.

- W przypadku dat w określonym era Użyj <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metody, aby pobrać indeks, który odpowiada określonej nazwie ERA. Wymaga to, aby <xref:System.Globalization.JapaneseCalendar> był bieżącym kalendarzem <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę ja-JP.  (Ta technika działa <xref:System.Globalization.JapaneseLunisolarCalendar> prawidłowo, ponieważ obsługuje takie same wymazywanie <xref:System.Globalization.JapaneseCalendar>jak). Poprzedni przykład ilustruje to podejście.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendarze, wymazywane i zakres dat: Kontrole zakresu swobodnego

Podobnie jak w przypadku <xref:System.Globalization.JapaneseCalendar> pojedynczych kalendarzy obsługiwane są zakresy dat, wymazywane w i <xref:System.Globalization.JapaneseLunisolarCalendar> klasy są również obsługiwane. Wcześniej program .NET używał rygorystycznych kontroli zakresu ery, aby zapewnić, że data specyficzna dla ery była w zakresie tej ery. Oznacza to, że jeśli data znajduje się poza zakresem określonej ery, metoda zgłasza <xref:System.ArgumentOutOfRangeException>. Obecnie platforma .NET domyślnie używa kontroli przedziału. Aktualizacje wszystkich wersji platformy .NET wprowadzono swobodne kontrole zakresu ery; podjęto próbę utworzenia wystąpienia dla konkretnej daty dotyczącej ery, która jest poza zakresem określonych przepływów ERA, do następującej ery i nie jest zgłaszany żaden wyjątek.

Poniższy przykład próbuje utworzyć wystąpienie daty w roku 65th na Showa ERA, która zaczęła się od 25 grudnia 1926 i zakończyła się 7 stycznia 1989. Ta data odpowiada 9 stycznia 1990, który jest poza zakresem Showa ERA w <xref:System.Globalization.JapaneseCalendar>. Jak przedstawiono dane wyjściowe z przykładu, Data wyświetlana przez przykład to 9 stycznia 1990 w drugim roku Heisei ERA.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Jeśli kontrole zakresu swobodnego są niepożądane, można przywrócić ścisłe kontrole zakresu na wiele sposobów, w zależności od wersji platformy .NET, w której działa aplikacja:

- **.NET Core:** Do pliku konfiguracyjnego *. Core. Runtime. JSON* można dodać następujące elementy:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4,6 lub nowszy:** Można ustawić następujący przełącznik AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Nazwa | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |Typ | REG_SZ |
   |Wartość | true |

W przypadku włączenia kontroli ścisłego zakresu w poprzednim przykładzie jest <xref:System.ArgumentOutOfRangeException> zgłaszany i wyświetlany następujący wynik:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Przedstawianie dat w kalendarzach z wieloma wymazywanymi

Jeśli obiekt obsługuje wymazywanie i jest bieżącym kalendarzem <xref:System.Globalization.CultureInfo> obiektu, era jest uwzględniona w ciągu reprezentującym wartość daty i godziny dla wzorców pełnej daty i godziny, daty długiej i daty krótkiej. <xref:System.Globalization.Calendar> W poniższym przykładzie są wyświetlane te wzorce, gdy bieżącą kulturą jest Japonia (Japoński), a bieżącym kalendarzem jest kalendarz japoński.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Klasa jest jedyną klasą kalendarzową w programie .NET, która obsługuje daty w więcej niż jednej ERA i która może być bieżącym kalendarzem <xref:System.Globalization.CultureInfo> obiektu <xref:System.Globalization.CultureInfo> — w odniesieniu do obiektu, który reprezentuje kulturę japońską (Japonia). <xref:System.Globalization.JapaneseCalendar>

Specyfikator formatu niestandardowego „g” dołącza erę do ciągu wynikowego dla każdego kalendarza. W poniższym przykładzie użyto ciągu formatu niestandardowego „MM-dd-yyyy g” w celu dołączenia ery do ciągu wynikowego, gdy bieżącym kalendarzem jest kalendarz gregoriański.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

W przypadku, gdy ciąg reprezentujący datę jest wyrażony w kalendarzu, który nie jest bieżącym kalendarzem, <xref:System.Globalization.Calendar> Klasa <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> zawiera metodę, która może <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>być używana razem z metodami <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>,, <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> i do jednoznacznie wskazują datę, a także ocenę ERA, do której należy. Poniższy przykład używa klasy, <xref:System.Globalization.JapaneseLunisolarCalendar> aby dostarczyć ilustrację. Należy jednak pamiętać, że w tym opisową nazwę lub skrót zamiast liczby całkowitej dla oceny ERA w ciągu wynikowym, należy utworzyć wystąpienie <xref:System.Globalization.DateTimeFormatInfo> obiektu i utworzyć <xref:System.Globalization.JapaneseCalendar> jego bieżący kalendarz. <xref:System.Globalization.JapaneseLunisolarCalendar> (Kalendarz nie może być bieżącym kalendarzem żadnej kultury, ale w tym przypadku dwa kalendarze mają te same wartości wymazywane).

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

W kalendarzach japońskich pierwszy rok era nosi nazwę Gannen (元年). Na przykład zamiast Heisei 1, pierwszy rok oceny era Heisei można opisać jako Heisei Gannen. Platforma .NET przyjmuje niniejszą Konwencję w operacjach formatowania dat i godzin sformatowanych przy użyciu następujących standardowych lub niestandardowych ciągów formatu daty i godziny, gdy są <xref:System.Globalization.CultureInfo> one używane z obiektem, który reprezentuje kulturę Japońska-Japonia ("ja-JP") za pomocą <xref:System.Globalization.JapaneseCalendar> Klasa:

- [Wzorzec daty długiej](../base-types/standard-date-and-time-format-strings.md#LongDate), wskazywany przez ciąg standardowego formatu daty i godziny "D".
- [Wzorzec pełnej daty długiej](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), wskazywany przez ciąg standardowego formatu daty i godziny "F".
- [Wzorzec pełnej daty i godziny](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), wskazywany przez ciąg standardowego formatu daty i godziny "f".
- [Wzorzec rok/miesiąc](../base-types/standard-date-and-time-format-strings.md#YearMonth), wskazywany przez ciąg x "lub" y "standardowego formatu daty i godziny.
- [ [Ciąg formatu daty i godziny](../base-types/custom-date-and-time-format-strings.md)"GGY" "lub" ggy年 ".

Na przykład poniższy przykład wyświetla datę w pierwszym roku Heisei ERA w <xref:System.Globalization.JapaneseCalendar> .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Jeśli takie zachowanie jest niepożądane w operacjach formatowania, można przywrócić poprzednie zachowanie, które zawsze przedstawia pierwszy rok oceny era jako "1" zamiast "Gannen", wykonując następujące czynności, w zależności od wersji programu .NET:

- **.NET Core:** Do pliku konfiguracyjnego *. Core. Runtime. JSON* można dodać następujące elementy:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4,6 lub nowszy:** Można ustawić następujący przełącznik AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Nazwa | Switch. System. globalizacja. FormatJapaneseFirstYearAsANumber |
   |Typ | REG_SZ |
   |Wartość | true |

W przypadku wyłączenia obsługi Gannen w operacjach formatowania w poprzednim przykładzie są wyświetlane następujące dane wyjściowe:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

Program .NET został także zaktualizowany tak, aby operacje analizowania daty i godziny obsługiwały ciągi zawierające rok reprezentowane jako "1" lub Gannen. Chociaż nie należy tego robić, można przywrócić poprzednie zachowanie, aby rozpoznawać tylko "1" jako pierwszy rok ERA. Można to zrobić w następujący sposób, w zależności od wersji programu .NET:

- **.NET Core:** Do pliku konfiguracyjnego *. Core. Runtime. JSON* można dodać następujące elementy:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4,6 lub nowszy:** Można ustawić następujący przełącznik AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|  
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Nazwa | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |Typ | REG_SZ |
   |Wartość | true | 

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie dat w kalendarzach innych niż gregoriański](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Northwind Narzędzie zakresu tygodnia kalendarzowego](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Klasa kalendarza](xref:System.Globalization.Calendar)
