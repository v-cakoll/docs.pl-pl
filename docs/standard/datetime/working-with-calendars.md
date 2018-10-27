---
title: Praca z kalendarzami
ms.date: 03/30/2017
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
ms.openlocfilehash: 055c7db652426651dd3c2a74825a11e305d939f1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183909"
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

Dwóch <xref:System.Globalization.Calendar> klasy, które obsługują wiele er, datę, która składa się z danego roku, miesiąc i dzień miesiąca może być niejednoznaczna, na przykład wszystkie cztery ery kalendarza <xref:System.Globalization.JapaneseCalendar> zawierają lata o numerach od 1 do 15. Normalnie, jeśli era nie jest określona, metody daty i godziny oraz kalendarza zakładają, że wartości należą do bieżącej ery. Aby jawnie określić erę podczas tworzenia wystąpienia daty dla <xref:System.Globalization.Calendar> klasę, która obsługuje wiele er, można wywołać <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody. Ta metoda umożliwia jawne określenie ery wraz z rokiem, miesiącem, dniem, godziną, minutą, sekundą i milisekundą w kalendarzu.

W poniższym przykładzie użyto <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienia tego samego dnia, miesiąca od pierwszego dnia drugiego roku, w każdej erze obsługiwanej przez <xref:System.Globalization.JapaneseCalendar> klasy. Następnie data jest wyświetlana z użyciem kalendarza japońskiego i gregoriańskiego. Wzywa także <xref:System.DateTime> konstruktora, aby zilustrować, że metody tworzące wartości danych bez określania ery tworzą daty w bieżącej ery.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Przedstawianie dat w kalendarzach z erami

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

## <a name="see-also"></a>Zobacz także

* [Porady: wyświetlanie dat w kalendarzach innych niż gregoriański](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
* [Przykład: Tygodnia w kalendarzu zakresu narzędzia](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
