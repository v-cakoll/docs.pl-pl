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
ms.openlocfilehash: de8e5a03c769a22f3320c7785706555898bf8c1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400590"
---
# <a name="work-with-calendars"></a>Praca z kalendarzami

Wartość daty i godziny reprezentuje moment w czasie, ale jej reprezentacja w postaci ciągu jest zależna od kultury, ponieważ zależy zarówno od konwencji używanych do wyświetlania wartości daty i godziny obowiązujących w danej kulturze, jak i od kalendarza używanego w tej kulturze. W tym temacie omówiono obsługę kalendarzy w .NET i omówiono użycie klas kalendarza podczas pracy z wartościami daty.

## <a name="calendars-in-net"></a>Kalendarze w .NET

Wszystkie kalendarze w .NET <xref:System.Globalization.Calendar?displayProperty=nameWithType> pochodzą od klasy, która zapewnia implementację kalendarza podstawowego. Jedną z klas, która <xref:System.Globalization.Calendar> dziedziczy <xref:System.Globalization.EastAsianLunisolarCalendar> z klasy jest klasa, która jest klasą podstawową dla wszystkich kalendarzy lunisolar. .NET zawiera następujące implementacje kalendarza:

- <xref:System.Globalization.ChineseLunisolarCalendar>, który reprezentuje chiński kalendarz lunisolar.

- <xref:System.Globalization.GregorianCalendar>, który reprezentuje kalendarz gregoriański. Ten kalendarz jest dalej podzielony na podtypy (takie jak arabski i <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> bliskowschodni francuski), które są zdefiniowane przez wyliczenie. Właściwość <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> określa podtyp kalendarza gregoriańskiego.

- <xref:System.Globalization.HebrewCalendar>, który reprezentuje kalendarz hebrajski.

- <xref:System.Globalization.HijriCalendar>, który reprezentuje kalendarz Hidżry.

- <xref:System.Globalization.JapaneseCalendar>, który reprezentuje kalendarz japoński.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, który reprezentuje japoński kalendarz lunisolar.

- <xref:System.Globalization.JulianCalendar>, który reprezentuje kalendarz juliański.

- <xref:System.Globalization.KoreanCalendar>, który reprezentuje kalendarz koreański.

- <xref:System.Globalization.KoreanLunisolarCalendar>, który reprezentuje koreański kalendarz lunisolar.

- <xref:System.Globalization.PersianCalendar>, który reprezentuje kalendarz perski.

- <xref:System.Globalization.TaiwanCalendar>, który reprezentuje kalendarz Tajwanu.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, który reprezentuje kalendarz lunisolar Tajwanu.

- <xref:System.Globalization.ThaiBuddhistCalendar>, który reprezentuje tajski kalendarz buddyjski.

- <xref:System.Globalization.UmAlQuraCalendar>, który reprezentuje kalendarz Um Al Qura.

Kalendarza można używać na jeden z dwóch sposobów:

- Jako kalendarz używany przez określoną kulturę. Każdy <xref:System.Globalization.CultureInfo> obiekt ma bieżący kalendarz, który jest kalendarzem, który jest aktualnie używany przez obiekt. Reprezentacje wszystkich wartości daty i godziny w formacie ciągu automatycznie odzwierciedlają bieżącą kulturę i jej bieżący kalendarz. Zazwyczaj bieżącym kalendarzem jest kalendarz domyślny kultury. <xref:System.Globalization.CultureInfo>obiekty mają również opcjonalne kalendarze, które zawierają dodatkowe kalendarze, które kultury można używać.

- Jako kalendarz autonomiczny, niezależny od określonej kultury. W takim <xref:System.Globalization.Calendar> przypadku metody są używane do wyrażania dat jako wartości, które odzwierciedlają kalendarz.

Należy pamiętać, że <xref:System.Globalization.ChineseLunisolarCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar>sześć <xref:System.Globalization.JulianCalendar> <xref:System.Globalization.KoreanLunisolarCalendar>klas <xref:System.Globalization.PersianCalendar>kalendarza – , , , , i <xref:System.Globalization.TaiwanLunisolarCalendar> – mogą być używane tylko jako samodzielne kalendarze. Nie są one używane przez żadną kulturę ani jako kalendarz domyślny, ani jako kalendarz opcjonalny.

## <a name="calendars-and-cultures"></a>Kalendarze i kultury

Każda kultura ma domyślny kalendarz, który <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> jest zdefiniowany przez właściwość. Właściwość <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> zwraca tablicy <xref:System.Globalization.Calendar> obiektów, który określa wszystkie kalendarze obsługiwane przez określoną kulturę, w tym kalendarza domyślnego tej kultury.

W poniższym przykładzie <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> przedstawiono i właściwości. Tworzy `CultureInfo` obiekty dla tajlandzkich (Tajlandia) i japońskich (Japonia) kultur i wyświetla ich kalendarze domyślne i opcjonalne. Należy zauważyć, że w obu przypadkach domyślny kalendarz <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kultury jest również uwzględniony w kolekcji.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendarz aktualnie używany przez <xref:System.Globalization.CultureInfo> określony obiekt jest zdefiniowany przez <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwość kultury. <xref:System.Globalization.DateTimeFormatInfo> Obiekt kultury jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwość. Po utworzeniu kultury, jego wartość domyślna jest taka <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> sama jak wartość właściwości. Można jednak zmienić bieżący kalendarz kultury na dowolny kalendarz zawarty <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> w tablicy zwróconej przez właściwość. Jeśli spróbujesz ustawić bieżący kalendarz na kalendarz, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> który nie <xref:System.ArgumentException> jest uwzględniony w wartości właściwości, zostanie wydyłany.

W poniższym przykładzie jest zmieniany kalendarz używany przez kulturę Arabski (Arabia Saudyjska). Najpierw tworzy <xref:System.DateTime> wartość i wyświetla ją przy użyciu bieżącej kultury - która w tym przypadku jest angielska (Stany Zjednoczone) - i kalendarzem bieżącej kultury (który w tym przypadku jest kalendarzem gregoriańskim). Następnie bieżąca kultura jest zmieniana na Arabski (Arabia Saudyjska) i data jest wyświetlana przy użyciu domyślnego kalendarza tej kultury, czyli Um Al-Qura. Następnie wywołuje `CalendarExists` metodę, aby ustalić, czy kalendarz Hidżry jest obsługiwany przez kulturę arabską (Arabia Saudyjska). Ten kalendarz jest obsługiwany, więc bieżący kalendarz jest zmieniany na kalendarz Hidżry i ponownie jest wyświetlana data. Należy zauważyć, że w każdym przypadku data jest wyświetlana przy użyciu bieżącego kalendarza bieżącej kultury.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Daty i kalendarze

Z wyjątkiem konstruktorów, które zawierają <xref:System.Globalization.Calendar> parametr typu i pozwalają elementy daty (czyli miesiąc, dzień i rok) do odzwierciedlenia wartości w wyznaczonym kalendarzu, zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są zawsze oparte na kalendarzu gregoriańskim. Oznacza to na przykład, <xref:System.DateTime.Year%2A?displayProperty=nameWithType> że właściwość zwraca rok w kalendarzu <xref:System.DateTime.Day%2A?displayProperty=nameWithType> gregoriańskim, a właściwość zwraca dzień miesiąca w kalendarzu gregoriańskim.

> [!IMPORTANT]
> Ważne jest, aby pamiętać o różnicy między wartością daty a jej reprezentacją w formacie ciągu. Pierwsza jest oparta na kalendarzu gregoriańskim, a druga na bieżącym kalendarzu określonej kultury.

Poniższy przykład ilustruje <xref:System.DateTime> tę różnicę <xref:System.Globalization.Calendar> między właściwościami i ich odpowiednich metod. W tym przykładzie bieżącą kulturą jest Arabski (Egipt), a bieżącym kalendarzem jest Um Al Qura. Wartość <xref:System.DateTime> jest ustawiona na piętnasty dzień siódmego miesiąca 2011 roku. Jest oczywiste, że jest to interpretowane jako data gregoriańska, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ponieważ te same wartości są zwracane przez metodę, gdy używa konwencji kultury niezmiennej. Reprezentacja tej daty w formacie ciągu, która jest formatowana z użyciem konwencji bieżącej kultury, to 14/08/32, co odpowiada dacie w kalendarzu Um Al Qura. Następnie członkowie `DateTime` i `Calendar` są używane do zwracania dnia, miesiąca <xref:System.DateTime> i roku wartości. W każdym przypadku wartości zwracane przez <xref:System.DateTime> elementy członkowskie odzwierciedlają wartości w kalendarzu <xref:System.Globalization.UmAlQuraCalendar> gregoriańskim, podczas gdy wartości zwracane przez elementy członkowskie odzwierciedlają wartości w kalendarzu Uum al-Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Tworzenie sulatkowego przekazywania dat na podstawie kalendarza

Ponieważ <xref:System.DateTime> <xref:System.DateTimeOffset> i wartości są oparte na kalendarzu gregoriańskim, należy wywołać <xref:System.Globalization.Calendar> przeciążony konstruktor, który zawiera parametr typu, aby utworzyć wystąpienie wartości daty, jeśli chcesz użyć wartości dnia, miesiąca lub roku z innego kalendarza. Można również wywołać jeden z przeciążeń <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metody określonego kalendarza, <xref:System.DateTime> aby utworzyć wystąpienia obiektu na podstawie wartości określonego kalendarza.

Poniższy <xref:System.DateTime> przykład tworzy jedną wartość, przekazując <xref:System.Globalization.HebrewCalendar> obiekt <xref:System.DateTime> do konstruktora i <xref:System.DateTime> tworzy drugą <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> wartość, wywołując metodę. Ponieważ dwie wartości są tworzone z identycznymi wartościami z <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> kalendarza hebrajskiego, wywołanie metody pokazuje, że dwie <xref:System.DateTime> wartości są równe.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Reprezentowanie dat w bieżącym kalendarzu

Metody formatowania daty i godziny zawsze używają bieżącego kalendarza podczas konwertowania dat na ciągi. Oznacza to, że reprezentacja roku, miesiąca i dnia miesiąca w formacie ciągu odzwierciedla bieżący kalendarz i nie musi to być kalendarz gregoriański.

W poniższym przykładzie pokazano, jak bieżący kalendarz wpływa na reprezentację daty w formacie ciągu. Bieżąca kultura jest zmieniana na Chiński (tradycyjny, Tajwan) i jest tworzone wystąpienie wartości daty. Następnie wyświetla bieżący kalendarz i datę, zmienia <xref:System.Globalization.TaiwanCalendar>bieżący kalendarz na , i wyświetla bieżący kalendarz i datę po raz kolejny. Gdy data jest wyświetlana po raz pierwszy, jest przedstawiana jako data w kalendarzu gregoriańskim. Gdy data jest wyświetlana po raz drugi, jest przedstawiana jako data w kalendarzu tajwańskim.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Reprezentowanie dat w niebieżącym kalendarzu

Aby reprezentować datę przy użyciu kalendarza, który nie jest bieżącym <xref:System.Globalization.Calendar> kalendarzem określonej kultury, należy wywołać metody tego obiektu. Na przykład <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody konwertują rok, miesiąc i dzień na wartości, które odzwierciedlają określony kalendarz.

> [!WARNING]
> Niektóre kalendarze nie są opcjonalnymi kalendarzami żadnej kultury, więc przedstawianie dat za pomocą tych kalendarzy zawsze wymaga wywołania metod kalendarza. Dotyczy to wszystkich kalendarzy, które <xref:System.Globalization.EastAsianLunisolarCalendar>wynikają <xref:System.Globalization.JulianCalendar>z <xref:System.Globalization.PersianCalendar> , i klas.

W poniższym <xref:System.Globalization.JulianCalendar> przykładzie użyto obiektu do utworzenia wystąpienia daty, 9 stycznia 1905 r., w kalendarzu juliańskim. Gdy ta data jest wyświetlana przy użyciu kalendarza domyślnego (gregoriańskiego), jest przedstawiana jako 22 stycznia 1905 roku. Wywołania <xref:System.Globalization.JulianCalendar> poszczególnych metod umożliwiają reprezentowanie daty w kalendarzu juliańskim.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendarze i zakresy dat

Najwcześniejsza data obsługiwana przez kalendarz jest <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> wskazywana przez właściwość tego kalendarza. Dla <xref:System.Globalization.GregorianCalendar> klasy ta data to 1 stycznia 0001 C.E. Większość innych kalendarzy w .NET obsługuje późniejszą datę. Próba pracy z wartością daty i godziny, która poprzedza najwcześniejszą obsługiwaną datę kalendarza, <xref:System.ArgumentOutOfRangeException> zgłasza wyjątek.

Istnieje jednak jeden ważny wyjątek. Domyślna (niezainicjowana) wartość <xref:System.DateTime> obiektu <xref:System.DateTimeOffset> i obiektu jest <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> równa wartości. Jeśli spróbujesz sformatować tę datę w kalendarzu, który nie obsługuje 1 stycznia 0001 C.E. i nie należy podawać specyfikatorformatu, metoda formatowania używa specyfikatora formatu "s" (sortable date/time pattern) zamiast specyfikatora formatu "G" (ogólny wzorzec daty/godziny). W rezultacie operacja formatowania nie zgłasza <xref:System.ArgumentOutOfRangeException> wyjątku. W zamian zwróci nieobsługiwaną datę. Jest to zilustrowane w poniższym przykładzie, <xref:System.DateTime.MinValue?displayProperty=nameWithType> który wyświetla wartość, gdy bieżąca kultura jest ustawiona na japoński (Japonia) z kalendarzem japońskim i arabski (Egipt) z kalendarzem Um Al Qura. Ustawia również bieżącą kulturę na angielski (Stany Zjednoczone) i wywołuje <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metodę z każdym z tych <xref:System.Globalization.CultureInfo> obiektów. W każdym przypadku data jest wyświetlana z użyciem wzorca sortowalnej daty/godziny.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Praca z epokami

Daty w kalendarzach są zazwyczaj dzielone na ery. Jednak <xref:System.Globalization.Calendar> klasy w .NET nie obsługują każdej ery zdefiniowanej przez <xref:System.Globalization.Calendar> kalendarz, a większość klas obsługuje tylko jedną erę. Tylko <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar> klasy obsługują wiele epok.

> [!IMPORTANT]
> Era Reiwy, nowa era <xref:System.Globalization.JapaneseCalendar> w <xref:System.Globalization.JapaneseLunisolarCalendar>i , zaczyna się 1 maja 2019. Ta zmiana dotyczy wszystkich aplikacji, które używają tych kalendarzy. Więcej informacji można znaleźć w następujących artykułach:
>
> - [Obsługa nowej ery w kalendarzu japońskim w .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), która dokumentuje funkcje dodane do platformy .NET w celu obsługi kalendarzy z wieloma epokami i omówiono najlepsze rozwiązania używane podczas obsługi kalendarzy wieloeryjnych.
> - [Przygotuj aplikację do zmiany ery japońskiej,](/windows/uwp/design/globalizing/japanese-era-change)która zawiera informacje na temat testowania aplikacji w systemie Windows, aby zapewnić ich gotowość do zmiany ery.
> - [Podsumowanie nowych aktualizacji ery japońskiej dla programu .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), który zawiera listę aktualizacji .NET Framework dla poszczególnych wersji systemu Windows, które są związane z nową erą kalendarza japońskiego, zauważa nowe funkcje .NET Framework dla obsługi wielu ery i zawiera rzeczy, których należy szukać podczas testowania aplikacji.

Era w większości kalendarzy oznacza bardzo długi okres czasu. Na przykład w kalendarzu gregoriańskim bieżąca era obejmuje więcej niż dwa tysiąclecia. Dla <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar>, dwa kalendarze, które obsługują wiele epok, nie jest to przypadek. Epoka odpowiada okresowi panowania cesarza. Wsparcie dla wielu epok, zwłaszcza gdy górna granica obecnej epoki jest nieznana, stanowi szczególne wyzwanie.

### <a name="eras-and-era-names"></a>Nazwy epok i epok

W .NET liczby całkowite reprezentujące epok obsługiwanych przez określoną implementację <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> kalendarza są przechowywane w odwrotnej kolejności w tablicy. Bieżąca era (czyli era z najnowszym zakresem czasu) jest <xref:System.Globalization.Calendar> na poziomie zero indeksu, a dla klas obsługujących wiele epok każdy kolejny indeks odzwierciedla poprzednią erę. Właściwość <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> statyczna definiuje indeks bieżącej ery <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> w tablicy; jest to stała, której wartość jest zawsze zerowa. Poszczególne <xref:System.Globalization.Calendar> klasy zawierają również pola statyczne, które zwracają wartość bieżącej ery. Zostały one wymienione w poniższej tabeli.

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

Nazwę, która odpowiada określonej liczby ery można pobrać przez przekazanie <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> numeru <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> ery do lub metody. Poniższy przykład wywołuje te metody, aby pobrać <xref:System.Globalization.GregorianCalendar> informacje o obsłudze ery w klasie. Wyświetla gregoriańskiej daty kalendarza, która odpowiada 1 stycznia drugiego roku bieżącej ery, a także gregoriańskiej daty kalendarza, która odpowiada 1 stycznia drugiego roku każdego obsługiwanej ery kalendarza japońskiego.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Ponadto niestandardowy format daty i godziny „g” dołącza nazwę ery kalendarza do reprezentacji daty i godziny w formacie ciągu. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatu daty i godziny](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Tworzenie wystąpienia daty z epoką

Dla dwóch <xref:System.Globalization.Calendar> klas, które obsługują wiele epok, data, która składa się z określonego roku, miesiąca i dnia wartości miesiąca może być niejednoznaczna. Na przykład wszystkie epoki <xref:System.Globalization.JapaneseCalendar> obsługiwane przez lata, których liczba wynosi 1. Normalnie, jeśli era nie jest określona, metody daty i godziny oraz kalendarza zakładają, że wartości należą do bieżącej ery. Dotyczy to <xref:System.DateTime.%23ctor%2A> i <xref:System.DateTimeOffset.%23ctor%2A> konstruktorów, które zawierają <xref:System.Globalization.Calendar>parametry typu, a także [japanesecalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) i [JapaneseLunisolarCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) metody. Poniższy przykład tworzy datę, która reprezentuje 1 stycznia drugiego roku nieokreślonej ery. Jeśli wykonasz przykład, gdy era Reiwa jest bieżącą erą, data jest interpretowana jako drugi rok ery Reiwy. Era, japonka, poprzedza rok w <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> ciągu zwrócony m.in. (Era Reiwy rozpoczyna się w roku 2019 kalendarza gregoriańskiego.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Jednak jeśli era uulega zmianie, intencji tego kodu staje się niejednoznaczne. Czy data ma reprezentować drugi rok obecnej ery, czy też ma reprezentować drugi rok ery Heisei? Istnieją dwa sposoby, aby uniknąć tej dwuznaczności:

- Tworzenie wystąpienia wartości daty i godziny <xref:System.Globalization.GregorianCalendar> przy użyciu klasy domyślnej. Następnie można użyć kalendarza japońskiego lub japońskiego kalendarza lunisolar dla reprezentacji ciągów dat, jak pokazano w poniższym przykładzie.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Wywołaj metodę daty i godziny, która jawnie określa epokę. Obejmuje to następujące metody:

  - Metoda <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> <xref:System.Globalization.JapaneseCalendar> lub <xref:System.Globalization.JapaneseLunisolarCalendar> klasy.

  - A <xref:System.DateTime> <xref:System.DateTimeOffset> lub metody analizy, <xref:System.DateTime.Parse%2A>takich <xref:System.DateTime.TryParse%2A> <xref:System.DateTime.ParseExact%2A>jak <xref:System.DateTime.TryParseExact%2A>, , , lub , który zawiera <xref:System.Globalization.DateTimeStyles> ciąg do analizy i opcjonalnie argument, jeśli bieżąca kultura jest japoński-Japonia ("ja-JP") i że kultura kalendarz jest <xref:System.Globalization.JapaneseCalendar>. Ciąg do przeanalizowania musi zawierać epokę.

  - A <xref:System.DateTime> <xref:System.DateTimeOffset> lub metoda analizy, `provider` która zawiera <xref:System.IFormatProvider>parametr typu . `provider`musi być <xref:System.Globalization.CultureInfo> obiektem reprezentującym kulturę japońsko-japońską ("ja-JP"), <xref:System.Globalization.DateTimeFormatInfo> której <xref:System.Globalization.DateTimeFormatInfo.Calendar> bieżącym <xref:System.Globalization.JapaneseCalendar>kalendarzem jest <xref:System.Globalization.JapaneseCalendar> lub obiektem, którego właściwością jest . Ciąg do przeanalizowania musi zawierać epokę.

  Poniższy przykład wykorzystuje trzy z tych metod, aby utworzyć datę i godzinę w erze Meiji, która rozpoczęła się 8 września 1868 roku i zakończyła się 29 lipca 1912 roku.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Podczas pracy z kalendarzami obsługującymi wiele epok *należy zawsze* używać daty gregoriańskiej do tworzenia wystąpienia daty lub określać epokę wystąpienia daty i godziny na podstawie tego kalendarza.

Określając era do <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metody, należy podać indeks ery we właściwości <xref:System.Globalization.Calendar.Eras> kalendarza. W przypadku kalendarzy, których epoki mogą ulec zmianie, indeksy te nie są jednak wartościami stałymi; obecna era jest na indeksie 0, a `Eras.Length - 1`najstarsza era jest w indeksie . Po dodaniu nowej ery do kalendarza indeksy poprzednich epok zwiększają się o jeden. Można podać odpowiedni indeks ery w następujący sposób:

- W przypadku dat w bieżącej erze <xref:System.Globalization.Calendar.CurrentEra> zawsze należy używać właściwości kalendarza.

- Dla dat w określonej erze <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> użyj metody, aby pobrać indeks, który odpowiada określonej nazwie ery. Wymaga to, <xref:System.Globalization.JapaneseCalendar> że być bieżący <xref:System.Globalization.CultureInfo> kalendarz obiektu, który reprezentuje kultury ja-JP.  (Ta technika <xref:System.Globalization.JapaneseLunisolarCalendar> działa również dla, ponieważ obsługuje te <xref:System.Globalization.JapaneseCalendar>same epoki co .) Poprzedni przykład ilustruje to podejście.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendarze, epoki i zakresy dat: złagodzone kontrole zakresu

Podobnie jak poszczególne kalendarze obsługują zakresy dat, epok w <xref:System.Globalization.JapaneseCalendar> klasach i <xref:System.Globalization.JapaneseLunisolarCalendar> mają również obsługiwane zakresy. Wcześniej .NET używane ścisłe kontrole zakresu ery, aby upewnić się, że data specyficzne dla ery był w zakresie tej ery. Oznacza to, że jeśli data znajduje się poza zakresem określonej <xref:System.ArgumentOutOfRangeException>ery, metoda wyrzuci plik . Obecnie .NET domyślnie używa swobodnego sprawdzania dystansowego. Aktualizacje do wszystkich wersji .NET wprowadzono kontrole zakres epoki złagodzone; próba utworzenia wystąpienia daty specyficznej dla ery, która znajduje się poza zakresem określonej ery "przepełnia" do następnej ery i nie jest zgłaszany wyjątek.

Poniższy przykład próbuje utworzyć datę w 65 roku ery Showa, która rozpoczęła się 25 grudnia 1926 roku i zakończyła się 7 stycznia 1989 roku. Data ta odpowiada 9 stycznia 1990 roku, który jest poza zakresem ery Showa w <xref:System.Globalization.JapaneseCalendar>. Jak wynika z przykładu ilustruje, data wyświetlana przez przykład jest 9 stycznia 1990, w drugim roku ery Heisei.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Jeśli kontrole zakresu złagodzone są niepożądane, można przywrócić rygorystyczne kontrole zakresu na wiele sposobów, w zależności od wersji .NET, na której aplikacja jest uruchomiona:

- **Program .NET Core:** Dodaj następujące elementy do pliku konfiguracyjnego *.netcore.runtime.json:*

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4.6 lub nowszy:** Ustaw następujący przełącznik AppContext w pliku *app.config:*

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Ustaw następującą wartość rejestru:

   |  |  |
   |--|--|
   | **Klucz** | **HKEY_LOCAL_MACHINE\Oprogramowanie\Microsoft\\. NETFramework\Kontekst aplikacji** |
   | **Nazwa** | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   | **Typ** | REG_SZ |
   | **Wartość** | true |

Po włączeniu ścisłych kontroli zakresu poprzedni <xref:System.ArgumentOutOfRangeException> przykład zgłasza i wyświetla następujące dane wyjściowe:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Przedstawiaj daty w kalendarzach z wieloma epokami

Jeśli <xref:System.Globalization.Calendar> obiekt obsługuje epoki i jest bieżącym <xref:System.Globalization.CultureInfo> kalendarzem obiektu, era jest uwzględniana w reprezentacji ciągu wartości daty i godziny dla pełnych wzorców daty i godziny, daty długiej i krótkiej daty. W poniższym przykładzie są wyświetlane te wzorce, gdy bieżącą kulturą jest Japonia (Japoński), a bieżącym kalendarzem jest kalendarz japoński.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Klasa <xref:System.Globalization.JapaneseCalendar> jest jedyną klasą kalendarza w .NET, która obsługuje daty w więcej <xref:System.Globalization.CultureInfo> niż jednej erze <xref:System.Globalization.CultureInfo> i która może być bieżącym kalendarzem obiektu — w szczególności obiektu reprezentującego kulturę japońską (Japonia).

Specyfikator formatu niestandardowego „g” dołącza erę do ciągu wynikowego dla każdego kalendarza. W poniższym przykładzie użyto ciągu formatu niestandardowego „MM-dd-yyyy g” w celu dołączenia ery do ciągu wynikowego, gdy bieżącym kalendarzem jest kalendarz gregoriański.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

W przypadkach, gdy reprezentacja ciągu daty jest wyrażona w kalendarzu, który <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> nie jest bieżącym kalendarzem, <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> <xref:System.Globalization.Calendar> klasa zawiera metodę, która może być używana wraz z <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>i metody jednoznacznie wskazują datę, a także epokę, do której należy. W poniższym <xref:System.Globalization.JapaneseLunisolarCalendar> przykładzie użyto klasy, aby zapewnić ilustrację. Należy jednak pamiętać, że w tym znaczącej nazwy lub skrótu zamiast liczby całkowitej dla ery w <xref:System.Globalization.DateTimeFormatInfo> ciągu <xref:System.Globalization.JapaneseCalendar> wynik wymaga wystąpienia obiektu i dokonać jego bieżącego kalendarza. (Kalendarz <xref:System.Globalization.JapaneseLunisolarCalendar> nie może być bieżącym kalendarzem żadnej kultury, ale w tym przypadku oba kalendarze mają te same epoki).

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

W kalendarzach japońskich pierwszy rok ery nazywa się Gannen (jap. 大中). Na przykład, zamiast Heisei 1, pierwszy rok ery Heisei można opisać jako Heisei Gannen. .NET przyjmuje tę konwencję w operacjach formatowania dla dat i godzin sformatowanych za pomocą <xref:System.Globalization.CultureInfo> następujących standardowych lub niestandardowych ciągów formatu daty i <xref:System.Globalization.JapaneseCalendar> godziny, gdy są one używane z obiektem reprezentującym kulturę japońsko-japońską ("ja-JP") z klasą:

- [Wzór daty długiej](../base-types/standard-date-and-time-format-strings.md#LongDate), oznaczony przez standardowy ciąg formatu daty i godziny "D".
- [Pełny wzór długiego czasu daty](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), wskazany przez standardowy ciąg formatu daty i godziny "F".
- [Pełny wzór krótkiego czasu daty,](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)wskazany przez standardowy ciąg formatu daty i godziny "f".
- [Wzór roku/miesiąca](../base-types/standard-date-and-time-format-strings.md#YearMonth), wskazany przez standardowy ciąg formatu daty i godziny Y.
- [[Niestandardowy ciąg formatu daty i godziny](../base-types/custom-date-and-time-format-strings.md)"ggy'ju" lub "ggy中".

Na przykład w poniższym przykładzie wyświetla datę w pierwszym roku <xref:System.Globalization.JapaneseCalendar>ery Heisei w .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Jeśli to zachowanie jest niepożądane w operacjach formatowania, można przywrócić poprzednie zachowanie, które zawsze reprezentuje pierwszy rok ery jako "1", a nie "Gannen", wykonując następujące czynności, w zależności od wersji .NET:

- **Program .NET Core:** Dodaj następujące elementy do pliku konfiguracyjnego *.netcore.runtime.json:*

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4.6 lub nowszy:** Ustaw następujący przełącznik AppContext w pliku *app.config:*

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Ustaw następującą wartość rejestru:

   |  |  |
   |--|--|
   | **Klucz** | **HKEY_LOCAL_MACHINE\Oprogramowanie\Microsoft\\. NETFramework\Kontekst aplikacji** |
   | **Nazwa** | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   | **Typ** | REG_SZ |
   | **Wartość** | true |

W przypadku wyłączonej obsługi gannen w operacjach formatowania w poprzednim przykładzie wyświetlane są następujące dane wyjściowe:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET został również zaktualizowany, tak aby data i godzina analizowania operacji obsługiwały ciągi, które zawierają rok reprezentowany jako "1" lub Gannen. Chociaż nie należy tego robić, można przywrócić poprzednie zachowanie, aby rozpoznawać tylko "1" jako pierwszy rok ery. Można to zrobić w następujący sposób, w zależności od wersji .NET:

- **Program .NET Core:** Dodaj następujące elementy do pliku konfiguracyjnego *.netcore.runtime.json:*

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4.6 lub nowszy:** Ustaw następujący przełącznik AppContext w pliku *app.config:*

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 lub wcześniejszy:** Ustaw następującą wartość rejestru:

   |  |  |
   |--|--|
   | **Klucz** | **HKEY_LOCAL_MACHINE\Oprogramowanie\Microsoft\\. NETFramework\Kontekst aplikacji** |
   | **Nazwa** | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   | **Typ** | REG_SZ |
   | **Wartość** | true |

## <a name="see-also"></a>Zobacz też

- [Jak: Wyświetlanie dat w kalendarzach innych niż gregorianie](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Przykład: Narzędzie zakres tygodnia kalendarzowego](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Klasa kalendarza](xref:System.Globalization.Calendar)
