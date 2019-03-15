---
title: Praca z kalendarzami
ms.date: 02/23/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET Framework], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bc41f6881c8a876e77ac385c715a5517b95842c
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845989"
---
# <a name="working-with-calendars"></a>Praca z kalendarzami

Wartość daty i godziny reprezentuje moment w czasie, ale jej reprezentacja w postaci ciągu jest zależna od kultury, ponieważ zależy zarówno od konwencji używanych do wyświetlania wartości daty i godziny obowiązujących w danej kulturze, jak i od kalendarza używanego w tej kulturze. W tym temacie opisano obsługę kalendarzy w programie .NET i w tym artykule omówiono użycie klas kalendarza podczas pracy z wartości daty.

## <a name="calendars-in-net"></a>Kalendarze w programie .NET

Wszystkie kalendarze w programie .NET pochodzić od <xref:System.Globalization.Calendar?displayProperty=nameWithType> klasy, która dostarcza podstawową implementację kalendarza. Jedną z klas dziedziczących z klasy <xref:System.Globalization.Calendar> klasa jest <xref:System.Globalization.EastAsianLunisolarCalendar> klasy, która jest klasą bazową wszystkich kalendarzy księżycowo-słoneczny. .NET zawiera następujące implementacje kalendarza:

* <xref:System.Globalization.ChineseLunisolarCalendar>, która reprezentuje Chiński kalendarz księżycowo-słoneczny.

* <xref:System.Globalization.GregorianCalendar>, która reprezentuje kalendarz gregoriański. Ten kalendarz jest dalej dzielony na podtypy (takie jak arabski i francuski Bliski Wschód), które są definiowane przez <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> wyliczenia. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Właściwość określa podtyp kalendarza gregoriańskiego.

* <xref:System.Globalization.HebrewCalendar>, która reprezentuje Kalendarz hebrajski.

* <xref:System.Globalization.HijriCalendar>, która reprezentuje kalendarz Hidżry.

* <xref:System.Globalization.JapaneseCalendar>, która reprezentuje Kalendarz japoński.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, która reprezentuje japoński kalendarz księżycowo-słoneczny.

* <xref:System.Globalization.JulianCalendar>, która reprezentuje kalendarz juliański.

* <xref:System.Globalization.KoreanCalendar>, która reprezentuje Kalendarz koreański.

* <xref:System.Globalization.KoreanLunisolarCalendar>, która reprezentuje koreański kalendarz księżycowo-słoneczny.

* <xref:System.Globalization.PersianCalendar>, która reprezentuje kalendarz perski.

* <xref:System.Globalization.TaiwanCalendar>, która reprezentuje kalendarz tajwański.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, która reprezentuje tajwański kalendarz księżycowo-słoneczny.

* <xref:System.Globalization.ThaiBuddhistCalendar>, która reprezentuje tajski kalendarz buddyjski.

* <xref:System.Globalization.UmAlQuraCalendar>, która reprezentuje kalendarz Um Al Qura.

Kalendarza można używać na jeden z dwóch sposobów:

* Jako kalendarz używany przez określoną kulturę. Każdy <xref:System.Globalization.CultureInfo> obiekt ma bieżącym kalendarzem jest kalendarz aktualnie używany obiekt. Reprezentacje wszystkich wartości daty i godziny w formacie ciągu automatycznie odzwierciedlają bieżącą kulturę i jej bieżący kalendarz. Zazwyczaj bieżącym kalendarzem jest kalendarz domyślny kultury. <xref:System.Globalization.CultureInfo> obiekty mają także opcjonalne kalendarze, w tym dodatkowe kalendarze, których można użyć kultury.

* Jako kalendarz autonomiczny, niezależny od określonej kultury. W tym przypadku <xref:System.Globalization.Calendar> metody są używane do wyrażania dat jako wartości odzwierciedlających kalendarz.

Należy pamiętać, że sześciu klas kalendarza — <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, i <xref:System.Globalization.TaiwanLunisolarCalendar> — mogą być używane tylko jako kalendarzy autonomicznych. Nie są one używane przez żadną kulturę ani jako kalendarz domyślny, ani jako kalendarz opcjonalny.

## <a name="calendars-and-cultures"></a>Kalendarze i kultury

Każda kultura ma kalendarz domyślny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Właściwość zwraca tablicę <xref:System.Globalization.Calendar> obiektów, które określa wszystkie kalendarze obsługiwane przez daną kulturę, w tym kalendarz domyślny tej kultury.

W poniższym przykładzie pokazano <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Tworzy `CultureInfo` obiektów tajski (Tajlandia) i kultur japoński (Japonia) i wyświetla ich kalendarze domyślne oraz opcjonalne. Należy pamiętać, że w obu przypadkach kalendarz domyślny kultury wchodzi też w <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekcji.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendarz aktualnie używany przez dany <xref:System.Globalization.CultureInfo> obiekt jest zdefiniowany przez kulturę <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Kultury <xref:System.Globalization.DateTimeFormatInfo> obiekt jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Po utworzeniu kultury jego wartość domyślna jest taka sama jak wartość <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Jednak zmienić bieżący kalendarz kultury na dowolny kalendarz zawarty w tablicy zwracanej przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Jeśli zostanie podjęta próba ustawienia jako bieżącego kalendarza kalendarza, który nie jest uwzględniony w <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> wartość właściwości <xref:System.ArgumentException> zgłaszany.

W poniższym przykładzie jest zmieniany kalendarz używany przez kulturę Arabski (Arabia Saudyjska). Najpierw tworzone jest wystąpienie <xref:System.DateTime> wartość i wyświetla je przy użyciu bieżącej kultury, — czyli, w tym przypadku języka angielskiego (Stany Zjednoczone) — i bieżącego kalendarza kultury (czyli, w tym przypadku kalendarza gregoriańskiego). Następnie bieżąca kultura jest zmieniana na Arabski (Arabia Saudyjska) i data jest wyświetlana przy użyciu domyślnego kalendarza tej kultury, czyli Um Al-Qura. Następnie wywołuje `CalendarExists` metodę pozwala ustalić, czy kalendarz Hidżry jest obsługiwany przez kulturę arabski (Arabia Saudyjska). Ten kalendarz jest obsługiwany, więc bieżący kalendarz jest zmieniany na kalendarz Hidżry i ponownie jest wyświetlana data. Należy zauważyć, że w każdym przypadku data jest wyświetlana przy użyciu bieżącego kalendarza bieżącej kultury.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Daty i kalendarze

Z wyjątkiem konstruktorów, które zawierają parametr typu <xref:System.Globalization.Calendar> i zezwalają elementom daty (oznacza to, miesiąc, dzień i rok) odzwierciedlać wartości w wyznaczonym kalendarzu, zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są zawsze oparte na kalendarzu gregoriańskim. Oznacza to, na przykład, który <xref:System.DateTime.Year%2A?displayProperty=nameWithType> właściwość zwraca rok w kalendarzu gregoriańskim, a <xref:System.DateTime.Day%2A?displayProperty=nameWithType> właściwość zwraca dzień miesiąca w kalendarzu gregoriańskim.

> [!IMPORTANT]
> Ważne jest, aby pamiętać o różnicy między wartością daty a jej reprezentacją w formacie ciągu. Pierwsza jest oparta na kalendarzu gregoriańskim, a druga na bieżącym kalendarzu określonej kultury.

Poniższy przykład ilustruje różnicę między <xref:System.DateTime> właściwości i odpowiadające im <xref:System.Globalization.Calendar> metody. W tym przykładzie bieżącą kulturą jest Arabski (Egipt), a bieżącym kalendarzem jest Um Al Qura. A <xref:System.DateTime> wartość ustawiono piętnasty dzień siódmego miesiąca 2011 roku. To oczywiste, że jest interpretowana jako data gregoriańska, ponieważ te same wartości są zwracane przez <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody, gdy używa ona Konwencji niezmiennej kultury. Reprezentacja tej daty w formacie ciągu, która jest formatowana z użyciem konwencji bieżącej kultury, to 14/08/32, co odpowiada dacie w kalendarzu Um Al Qura. Następnie elementy członkowskie `DateTime` i `Calendar` są używane do zwrócenia dnia, miesiąca i roku <xref:System.DateTime> wartość. W każdym przypadku wartości zwracane przez <xref:System.DateTime> odzwierciedlają wartości z kalendarza gregoriańskiego, podczas gdy wartości zwracane przez <xref:System.Globalization.UmAlQuraCalendar> odzwierciedlają wartości kalendarza kalendarza Uum al-Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Tworzenie wystąpień dat na podstawie kalendarza

Ponieważ <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są oparte na kalendarzu gregoriańskim, trzeba wywołać przeciążonego konstruktora zawierającego parametr typu <xref:System.Globalization.Calendar> do utworzenia wystąpienia wartości daty, jeśli chcesz użyć wartości dnia, miesiąca lub roku z innego kalendarza. Można także wywołać jedno z przeciążeń określonym kalendarzu <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie <xref:System.DateTime> obiektu na podstawie wartości określonego kalendarza.

Poniższym przykładzie jedno wystąpienie <xref:System.DateTime> wartość przez przekazanie <xref:System.Globalization.HebrewCalendar> obiekt <xref:System.DateTime> konstruktora, a drugie wystąpienie <xref:System.DateTime> wartość przez wywołanie metody <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody. Ponieważ dwie wartości są tworzone za pomocą identycznych wartości z hebrajskiego kalendarza, wywołanie <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> metoda pokaże, iż dwie <xref:System.DateTime> wartości są równe.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Przedstawianie dat w bieżącym kalendarzu

Metody formatowania daty i godziny zawsze używają bieżącego kalendarza podczas konwertowania dat na ciągi. Oznacza to, że reprezentacja roku, miesiąca i dnia miesiąca w formacie ciągu odzwierciedla bieżący kalendarz i nie musi to być kalendarz gregoriański.

W poniższym przykładzie pokazano, jak bieżący kalendarz wpływa na reprezentację daty w formacie ciągu. Bieżąca kultura jest zmieniana na Chiński (tradycyjny, Tajwan) i jest tworzone wystąpienie wartości daty. Go następnie wyświetla bieżący kalendarz i Data, bieżący kalendarz do <xref:System.Globalization.TaiwanCalendar>i wyświetla bieżący kalendarz oraz Data jeszcze raz. Gdy data jest wyświetlana po raz pierwszy, jest przedstawiana jako data w kalendarzu gregoriańskim. Gdy data jest wyświetlana po raz drugi, jest przedstawiana jako data w kalendarzu tajwańskim.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Przedstawianie dat w kalendarzu innym niż bieżący

Aby przedstawić datę przy użyciu kalendarza, który nie jest bieżącym kalendarzem danej kultury, należy wywołać metody tego <xref:System.Globalization.Calendar> obiektu. Na przykład <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> konwertują rok, miesiąc i dzień na wartości odzwierciedlające określony kalendarz.

> [!WARNING]
> Niektóre kalendarze nie są opcjonalnymi kalendarzami żadnej kultury, więc przedstawianie dat za pomocą tych kalendarzy zawsze wymaga wywołania metod kalendarza. Dotyczy to wszystkich kalendarzy dziedziczących z <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, i <xref:System.Globalization.PersianCalendar> klasy.

W poniższym przykładzie użyto <xref:System.Globalization.JulianCalendar> obiektu do utworzenia wystąpienia daty 9 stycznia 1905 roku w kalendarzu juliańskim. Gdy ta data jest wyświetlana przy użyciu kalendarza domyślnego (gregoriańskiego), jest przedstawiana jako 22 stycznia 1905 roku. Wywołania pojedynczych <xref:System.Globalization.JulianCalendar> metody umożliwiają przedstawienie daty w kalendarzu juliańskim.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendarze i zakresy dat

Najwcześniejsza data obsługiwana przez kalendarz jest wskazywana przez ten kalendarz <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> właściwości. Aby uzyskać <xref:System.Globalization.GregorianCalendar> klasy, że data to 1 stycznia 0001 r Większość innych kalendarzy w programie .NET obsługuje późniejszą datę. Próba wartości daty i godziny, kalendarz użytkownika Najwcześniejsza data obsługiwana <xref:System.ArgumentOutOfRangeException> wyjątku.

Istnieje jednak jeden ważny wyjątek. Wartość domyślna (niezainicjowana) <xref:System.DateTime> obiektu i <xref:System.DateTimeOffset> obiekt jest równy <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> wartość. Jeśli zostanie podjęta próba sformatowania tej daty w kalendarzu, który nie obsługuje 1 stycznia 0001 r specyfikator formatu nie zostanie określona, metoda formatowania użyje specyfikatora formatu "s" (wzorzec sortowalnej daty/godziny), zamiast specyfikatora formatu "G" (wzorzec ogólnej daty/godziny). W wyniku operacji formatowania nie zgłasza <xref:System.ArgumentOutOfRangeException> wyjątku. W zamian zwróci nieobsługiwaną datę. Jest to zilustrowane w poniższym przykładzie, wyświetlana jest wartość <xref:System.DateTime.MinValue?displayProperty=nameWithType> gdy bieżącą kulturę ustawiono japoński (Japonia) za pomocą kalendarza japońskiego i arabski (Egipt) za pomocą kalendarza Um Al Qura. Ustawia również bieżącej kultury angielski (Stany Zjednoczone) i wywołuje <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metody z każdym z tych <xref:System.Globalization.CultureInfo> obiektów. W każdym przypadku data jest wyświetlana z użyciem wzorca sortowalnej daty/godziny.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Praca z erami

Daty w kalendarzach są zazwyczaj dzielone na ery. Jednak <xref:System.Globalization.Calendar> klas na platformie .NET nie obsługują każdej ery zdefiniowanej w kalendarzu, a większość <xref:System.Globalization.Calendar> klasy obsługuje tylko jedną erę. Tylko <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar> klasy obsługują wiele er.

> [!IMPORTANT]
>  W nowej ery usług w <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar> zaczyna się od 1 maja 2019 r. Ta zmiana ma wpływ na wszystkie aplikacje, które używają tych kalendarzy. Zobacz [obsługi nowej ery usług w kalendarza japońskiego na platformie .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/) uzyskać więcej informacji, jak i do określenia aplikacji, których dotyczy problem. Zobacz [przygotowanie aplikacji w taki sposób, aby ta zmiana era japoński](/windows/uwp/design/globalizing/japanese-era-change) instrukcje dotyczące testowania aplikacji na Windows w celu zapewnienia ich gotowości, aby ta zmiana era.

Ery w większości kalendarzy wskazuje, że okres bardzo dużo czasu. W kalendarzu gregoriańskim na przykład bieżącej ery obejmuje więcej niż dwóch millenia. Aby uzyskać <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar>dwa kalendarze, które obsługują wiele er, nie jest to wymagane. Ery odnosi się do okresu emperor reign. Obsługa wiele er, szczególnie w przypadku, gdy górny limit bieżącej ery jest nieznany, stanowią szczególne wyzwanie. 

### <a name="eras-and-era-names"></a>Ery i nazwy er

Na platformie .NET, liczby całkowite reprezentujące ery obsługiwane przez określoną implementację kalendarza są przechowywane w odwrotnej kolejności w <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tablicy. Bieżąca era ma indeks zero, a dla <xref:System.Globalization.Calendar> klasy, które obsługują wiele er, każdy kolejny indeks odzwierciedla poprzednią erę. Statyczne <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> właściwość definiuje indeks bieżącej ery w <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tablicy; jest stałą, której wartość jest zawsze zero. Poszczególne <xref:System.Globalization.Calendar> klasy zawierają także pola statyczne, które zwracają wartość bieżącej ery. Zostały one wymienione w poniższej tabeli.

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

Nazwa, która odpowiada numerowi ery można pobrać, przekazując numer ery do <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metody. Poniższy przykład wywołuje te metody do pobierania informacji dotyczących obsługi er w <xref:System.Globalization.GregorianCalendar> klasy.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Ponadto niestandardowy format daty i godziny „g” dołącza nazwę ery kalendarza do reprezentacji daty i godziny w formacie ciągu. Aby uzyskać więcej informacji, zobacz [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Tworzenie wystąpienia daty z erą

Dwóch <xref:System.Globalization.Calendar> klas, które obsługują wiele er, datę, która składa się z danego roku, miesiąc i dzień miesiąca wartość może być niejednoznaczna. Na przykład wszystkie ery obsługiwane przez <xref:System.Globalization.JapaneseCalendar> zawierają lata, w których liczba to 1. Normalnie, jeśli era nie jest określona, metody daty i godziny oraz kalendarza zakładają, że wartości należą do bieżącej ery. Dotyczy to <xref:System.DateTime.%23ctor%2A> i <xref:System.DateTimeOffset.%23ctor%2A> konstruktorów, które zawierają parametry typu <xref:System.Globalization.Calendar>, jak również [JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) i [JapaneseLunisolarCalendar.ToDateTime ](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) metody. Poniższy przykład tworzy wystąpienie daty, która reprezentuje 1 stycznia drugi rok z erą nieokreślony. Jak wynika z w przykładzie pokazano Data jest interpretowany jako drugiego roku era Heisei, bieżącej ery w czasie, który został wykonany w tym przykładzie. Ery 平成, poprzedza rok w ciągu zwracanego przez <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> metody i odnosi się do 1 stycznia 1990 r. w kalendarzu gregoriańskim. (Zakres ery Heisei jest od 1989 2019 w kalendarzu gregoriańskim.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Jednak zmiana era celem tego kodu staje się niejednoznaczne. Data ma na celu reprezentowania drugiego roku bieżącej ery, czy jest przeznaczona do reprezentowania drugiego roku ery Heisei? Istnieją dwa sposoby, aby uniknąć niejednoznaczności, to:

- Utwórz wystąpienie wartości daty i godziny przy użyciu domyślnego <xref:System.Globalization.GregorianCalendar> klasy. Można następnie użyć Kalendarz japoński lub Kalendarz japoński księżycowo-słoneczny reprezentacji ciągu daty, co ilustruje poniższy przykład.

   [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
   [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Wywołaj metodę daty i godziny, który jawnie określa ery. Obejmuje to następujące metody:

   - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Metody <xref:System.Globalization.JapaneseCalendar> lub <xref:System.Globalization.JapaneseLunisolarCalendar> klasy.

   - A <xref:System.DateTime> lub <xref:System.DateTimeOffset> analizy metody, takie jak <xref:System.DateTime.Parse%2A>, <xref:System.DateTime.TryParse%2A>, <xref:System.DateTime.ParseExact%2A>, lub <xref:System.DateTime.TryParseExact%2A>, który zawiera ciąg, który ma być analizowany i opcjonalnie <xref:System.Globalization.DateTimeStyles> argumentu, jeśli bieżącą kulturą jest Japonia japoński (" ja-JP") i kalendarza tej kultury <xref:System.Globalization.JapaneseCalendar>. Ciąg, który ma być analizowany, musi zawierać ery.

   - A <xref:System.DateTime> lub <xref:System.DateTimeOffset> analizy metody, która obejmuje `provider` parametr typu <xref:System.IFormatProvider>. `provider` musi być albo <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę Japoński — Japonia ("ja-JP"), którego bieżącym kalendarzem jest <xref:System.Globalization.JapaneseCalendar> lub <xref:System.Globalization.DateTimeFormatInfo> którego <xref:System.Globalization.DateTimeFormatInfo.Calendar> właściwość <xref:System.Globalization.JapaneseCalendar>. Ciąg, który ma być analizowany, musi zawierać ery.

   W poniższym przykładzie użyto trzech z następujących metod do utworzenia wystąpienia daty i godziny w erze Meiji, który rozpoczął się na 8 września 1868 i zakończył się 29 lipca 1912. 

   [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
   [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Podczas pracy z kalendarze, które obsługują wiele er *zawsze* Użyj data gregoriańska, aby utworzyć datę lub określić erę podczas tworzenia wystąpienia daty i godziny na podstawie tego kalendarza.

Podczas określania ery do <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metody, należy podać indeks ery kalendarza <xref:System.Globalization.Calendar.Eras> właściwości. Kalendarzy, w których ery mogą ulec zmianie jednak te indeksy nie są wartościami stałymi; Bieżąca era ma pod indeksem 0, a najstarsza era ma pod indeksem `Eras.Length - 1`. Po dodaniu nowej ery usług do kalendarza indeksy poprzedniego ery zwiększyć o jeden. Możesz podać indeksu odpowiednie ery w następujący sposób:

- Daty w bieżącej ery, zawsze używaj kalendarza <xref:System.Globalization.Calendar.CurrentEra> właściwości.

- Dla dat w erze określonego, użyj <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metodę, która pobierze indeksu, który odpowiada nazwie określonej ery. Takie rozwiązanie wymaga <xref:System.Globalization.JapaneseCalendar> być bieżącym kalendarzem obiektu <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury ja-JP.  (Ta metoda działa w przypadku <xref:System.Globalization.JapaneseLunisolarCalendar> tak dobrze, ponieważ obsługuje te same ery jako <xref:System.Globalization.JapaneseCalendar>.) To podejście pokazano w poprzednim przykładzie.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendarze, ery i zakresy dat: Swobodna zakresu kontroli

Bardzo tak jak poszczególne kalendarze mają obsługiwane zakresów dat ery w <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar> klasy również mieć obsługiwane zakresów. Wcześniej .NET używać strict ery, który sprawdza zakres, aby upewnić się, że datę ery należała do zakresu tej ery. Data spoza zakresu powodowało zgłoszenie .NET Framework używa swobodna ranged sprawdzanie domyślnie. Oznacza to, jeśli wartość typu date znajduje się poza zakresem określonym ery, metoda zgłasza <xref:System.ArgumentOutOfRangeException>. Aktualizacje do wszystkich wersji programu .NET Framework, wprowadzono złagodzone ery zakresu kontroli. próbie utworzenia wystąpienia datę właściwą dla ery, który znajduje się poza zakresem określonym ery "overflow" następujące ery i żaden wyjątek jest zgłaszany.

Poniższy przykład podejmie próbę utworzenia wystąpienia daty w roku 65 ery Showa, która rozpoczęło się w dniu 25 grudnia 1926 i zakończył się 7 stycznia 1989 roku. Ta data odnosi się do 9 stycznia 1990 r., który jest poza zakresem ery Showa <xref:System.Globalization.JapaneseCalendar>. Tak jak pokazano w danych wyjściowych z przykładu, Data, w przykładzie jest wyświetlana 9 stycznia 1990 r. w drugim roku ery Heisei.

   [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
   [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

W przypadku niepożądanych swobodna zakresu kontroli można przywrócić zakres ścisłych testy na wiele sposobów, w zależności od wersji programu .NET, na którym działa aplikacja:

- **.NET Core:** Można dodać następujące polecenie, aby *. netcore.runtime.json* pliku konfiguracji:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
      } 
   }
   ```

- **.NET framework 4.6 lub nowszy:** Można ustawić następującego przełącznika AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 lub wcześniej:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Nazwa | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |Typ | REG_SZ |
   |Wartość | 1 |

Za pomocą kontroli zakresu strict włączona, zgłasza poprzedni przykład <xref:System.ArgumentOutOfRangeException> i wyświetla następujące dane wyjściowe:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Przedstawianie dat w kalendarzach z erami wielu

Jeśli <xref:System.Globalization.Calendar> obiekt obsługuje ery i jest bieżącym kalendarzem obiektu <xref:System.Globalization.CultureInfo> obiektu, era jest dołączana w ciąg reprezentujący wartość daty i godziny dla pełnej daty i godziny, daty długiej i wzorców daty krótkiej. W poniższym przykładzie są wyświetlane te wzorce, gdy bieżącą kulturą jest Japonia (Japoński), a bieżącym kalendarzem jest kalendarz japoński.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> Klasa to jedyna klasa kalendarza w programie .NET, która obsługująca daty z więcej niż jeden ery i który może być bieżącym kalendarzem obiektu <xref:System.Globalization.CultureInfo> obiektu — w szczególności z <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę japoński (Japonia).

Specyfikator formatu niestandardowego „g” dołącza erę do ciągu wynikowego dla każdego kalendarza. W poniższym przykładzie użyto ciągu formatu niestandardowego „MM-dd-yyyy g” w celu dołączenia ery do ciągu wynikowego, gdy bieżącym kalendarzem jest kalendarz gregoriański.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

W przypadkach, gdzie reprezentacją ciągu daty jest wyrażone w kalendarzu, który nie jest bieżącym kalendarzem <xref:System.Globalization.Calendar> klasa zawiera <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> metodę, która może być używany wraz z <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody jednoznacznie wskazywać datę, a także ery, do której należy. W poniższym przykładzie użyto <xref:System.Globalization.JapaneseLunisolarCalendar> Aby klasa zapewniała ilustrację. Pamiętaj jednak, tego w tym nazwę lub skrót, a nie liczby całkowitej ery do ciągu wynikowego wymaga, że wystąpienia <xref:System.Globalization.DateTimeFormatInfo> i określić obiekt <xref:System.Globalization.JapaneseCalendar> jego bieżący kalendarz. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Kalendarza nie może być bieżącym kalendarzem żadnej kultury, ale w tym przypadku oba te kalendarze mają te same ery.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

W japońskich kalendarzach przez pierwszy rok ery nosi nazwę Gannen (元年). Na przykład zamiast Heisei 1 przez pierwszy rok ery Heisei można określić jako Heisei Gannen. .NET przyjmuje niniejszej Konwencji formatowania operacje dotyczące daty i godziny sformatowane przy użyciu następujących standardowy lub niestandardowy format daty i godziny ciągi, jeśli są używane z <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę Japoński — Japonia ("ja-JP"), za pomocą <xref:System.Globalization.JapaneseCalendar> klasy:

- [Wzorzec daty długiej](../base-types/standard-date-and-time-format-strings.md#LongDate), wskazane przez "D" Standardowa Data i godzina w ciągu formatu.
- [Wzorzec pełnej daty godzina długa](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), wskazane przez "F" Standardowa Data i godzina w ciągu formatu.
- [Wzorzec godziny krótkiej pełnej daty](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), wskazane przez "f" Standardowa Data i godzina w ciągu formatu.
- [Wzorzec roku i miesiąca](../base-types/standard-date-and-time-format-strings.md#YearMonth), wskazane przez Y "lub"y"Standardowa Data i godzina ciąg formatu.
- ["Ggy"年"" lub "ggy年" [niestandardowa data i godzina ciąg formatu](../base-types/custom-date-and-time-format-strings.md).

Na przykład, poniższy przykład data jest wyświetlana w pierwszym roku ery Heisei <xref:System.Globalization.JapaneseCalendar> .

   [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
   [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Jeśli to zachowanie jest niepożądanych w operacjach formatowania, można przywrócić poprzednie zachowanie, które zawsze odzwierciedla przez pierwszy rok ery jako "1" zamiast "Gannen", wykonując następujące polecenie, w zależności od wersji programu .NET:

- **.NET Core:** Można dodać następujące polecenie, aby *. netcore.runtime.json* pliku konfiguracji:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
      } 
   }
   ```

- **.NET framework 4.6 lub nowszy:** Można ustawić następującego przełącznika AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 lub wcześniej:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Nazwa | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   |Typ | REG_SZ |
   |Wartość | 1 |

Dzięki obsłudze gannen w operacjach wyłączone formatowania poprzedni przykład wyświetla następujące dane wyjściowe:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET został także zaktualizowany tak, że data i godzina operacji analizowania obsługuje ciągi zawierające roku reprezentowane jako "1" lub Gannen. Mimo że nie należy to zrobić, można przywrócić poprzednie zachowanie można tylko "1" jest rozpoznawany jako pierwszy rok ery. Można to zrobić w następujący sposób, w zależności od wersji programu .NET:

- **.NET Core:** Można dodać następujące polecenie, aby *. netcore.runtime.json* pliku konfiguracji:

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
      } 
   }
   ```

- **.NET framework 4.6 lub nowszy:** Można ustawić następującego przełącznika AppContext:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 lub wcześniej:** Można ustawić następującą wartość rejestru:

   |  |  |
   |--|--|  
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |Nazwa | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |Typ | REG_SZ |
   |Wartość | 1 | 

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie dat w kalendarzach innych niż gregoriański](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Przykład: Narzędzie zakresu tydzień kalendarza](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
