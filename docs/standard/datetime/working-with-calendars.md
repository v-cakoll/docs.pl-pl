---
title: Praca z kalendarzami
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3a54d5222edca0b42f30c33584f0f62aa96f9e2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-calendars"></a>Praca z kalendarzami

Wartość daty i godziny reprezentuje moment w czasie, ale jej reprezentacja w postaci ciągu jest zależna od kultury, ponieważ zależy zarówno od konwencji używanych do wyświetlania wartości daty i godziny obowiązujących w danej kulturze, jak i od kalendarza używanego w tej kulturze. W tym temacie Eksploruje obsługę kalendarzy programu .NET i omówiono używanie klasy kalendarza podczas pracy z wartości daty.

## <a name="calendars-in-net"></a>Kalendarze w .NET

Wszystkie kalendarze w .NET pochodzi od <xref:System.Globalization.Calendar?displayProperty=nameWithType> klasy, która dostarcza implementację kalendarza podstawowego. Jedną z klas, które dziedziczy <xref:System.Globalization.Calendar> jest klasa <xref:System.Globalization.EastAsianLunisolarCalendar> klasy, która jest klasa podstawowa dla wszystkich księżycowo-słoneczny kalendarzy. .NET zawiera następujące implementacje kalendarza:

* <xref:System.Globalization.ChineseLunisolarCalendar>, reprezentuje Chiński księżycowo-słoneczny kalendarza.

* <xref:System.Globalization.GregorianCalendar>, która reprezentuje kalendarza gregoriańskiego. Tego kalendarza jest podzielono na podtypów (np. arabski i francuskim Bliski Wschód), które są zdefiniowane przez <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> wyliczenia. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Właściwość określa podtyp kalendarza gregoriańskiego.

* <xref:System.Globalization.HebrewCalendar>, która reprezentuje Kalendarz hebrajski.

* <xref:System.Globalization.HijriCalendar>, która reprezentuje kalendarza Hijri.

* <xref:System.Globalization.JapaneseCalendar>, reprezentuje kalendarza japońskiego.

* <xref:System.Globalization.JapaneseLunisolarCalendar>, reprezentuje japoński księżycowo-słoneczny kalendarza.

* <xref:System.Globalization.JulianCalendar>, która reprezentuje kalendarz juliański.

* <xref:System.Globalization.KoreanCalendar>, reprezentuje koreański kalendarza.

* <xref:System.Globalization.KoreanLunisolarCalendar>, reprezentuje Koreański księżycowo-słoneczny kalendarza.

* <xref:System.Globalization.PersianCalendar>, reprezentuje perska kalendarza.

* <xref:System.Globalization.TaiwanCalendar>, reprezentuje Kalendarz tajski.

* <xref:System.Globalization.TaiwanLunisolarCalendar>, która reprezentuje Tajwański księżycowo-słoneczny.

* <xref:System.Globalization.ThaiBuddhistCalendar>, reprezentuje tajski buddyjski kalendarza.

* <xref:System.Globalization.UmAlQuraCalendar>, który reprezentuje kalendarz Um Al Qura.

Kalendarza można używać na jeden z dwóch sposobów:

* Jako kalendarz używany przez określoną kulturę. Każdy <xref:System.Globalization.CultureInfo> obiekt ma bieżącego kalendarza jest kalendarza, obiekt jest aktualnie używany. Reprezentacje wszystkich wartości daty i godziny w formacie ciągu automatycznie odzwierciedlają bieżącą kulturę i jej bieżący kalendarz. Zazwyczaj bieżącym kalendarzem jest kalendarz domyślny kultury. <xref:System.Globalization.CultureInfo>obiekty mają również opcjonalne kalendarzy, które obejmują dodatkowe kalendarzy, które mogą używać tej kultury.

* Jako kalendarz autonomiczny, niezależny od określonej kultury. W takim przypadku <xref:System.Globalization.Calendar> metody są używane do express dat jako wartości, które odzwierciedlać kalendarza.

Należy pamiętać, że sześć kalendarza klasy — <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>, i <xref:System.Globalization.TaiwanLunisolarCalendar> — mogą być używane tylko jako autonomiczny kalendarzy. Nie są one używane przez żadną kulturę ani jako kalendarz domyślny, ani jako kalendarz opcjonalny.

## <a name="calendars-and-cultures"></a>Kalendarze i kultur

Każdy kulturę kalendarz domyślny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Właściwość zwraca tablicę <xref:System.Globalization.Calendar> obiektów, które określa wszystkich kalendarzy obsługiwane przez określonej kultury, łącznie z tym kultury domyślnej kalendarza.

Poniższy przykład przedstawia <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Tworzy `CultureInfo` obiektów na tajski (Tajlandia) i kultur japoński (Japonia) i wyświetla domyślne i opcjonalne kalendarzy. Należy pamiętać, że w obu przypadkach kultury domyślnej kalendarza dołączony jest również <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekcji.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendarza obecnie używanymi przez określonego <xref:System.Globalization.CultureInfo> obiektu jest zdefiniowana przez kultury <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Kultura <xref:System.Globalization.DateTimeFormatInfo> obiekt jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Po utworzeniu kultury, jego wartość domyślna jest taka sama jak wartość <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Jednak zmienić kulturę bieżącego kalendarza do dowolnego kalendarza zawartych w tablicy zwracanej przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Jeśli spróbujesz ustawić bieżącego kalendarza do kalendarza, które nie są uwzględnione w <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> wartość właściwości <xref:System.ArgumentException> jest generowany.

W poniższym przykładzie jest zmieniany kalendarz używany przez kulturę Arabski (Arabia Saudyjska). Najpierw tworzy <xref:System.DateTime> wartości i wyświetla je przy użyciu bieżącej kultury — które w tym przypadku jest angielski (Stany Zjednoczone) - i kalendarza bieżącej kultury, (czyli, w tym przypadku kalendarza gregoriańskiego). Następnie bieżąca kultura jest zmieniana na Arabski (Arabia Saudyjska) i data jest wyświetlana przy użyciu domyślnego kalendarza tej kultury, czyli Um Al-Qura. Następnie wywołuje `CalendarExists` metodę, aby określić, czy kalendarza Hijri jest obsługiwane przez kultury arabski (Arabia Saudyjska). Ten kalendarz jest obsługiwany, więc bieżący kalendarz jest zmieniany na kalendarz Hidżry i ponownie jest wyświetlana data. Należy zauważyć, że w każdym przypadku data jest wyświetlana przy użyciu bieżącego kalendarza bieżącej kultury.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Daty i kalendarzy

Z wyjątkiem konstruktorów, które obejmują parametr typu <xref:System.Globalization.Calendar> i umożliwić elementy daty (oznacza to, miesiąc, dzień i rok) do wartości w kalendarzu wyznaczonych zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są zawsze oparte na kalendarza gregoriańskiego. Oznacza to, na przykład, że <xref:System.DateTime.Year%2A?displayProperty=nameWithType> właściwość zwraca rok kalendarza gregoriańskiego i <xref:System.DateTime.Day%2A?displayProperty=nameWithType> właściwości Zwraca dzień miesiąca kalendarza gregoriańskiego.

> [!IMPORTANT]
> Ważne jest, aby pamiętać o różnicy między wartością daty a jej reprezentacją w formacie ciągu. Pierwsza jest oparta na kalendarzu gregoriańskim, a druga na bieżącym kalendarzu określonej kultury.

Poniższy przykład przedstawia tej różnicy między <xref:System.DateTime> właściwości i odpowiadające <xref:System.Globalization.Calendar> metody. W tym przykładzie bieżącą kulturą jest Arabski (Egipt), a bieżącym kalendarzem jest Um Al Qura. A <xref:System.DateTime> wartość jest równa 15 dnia miesiąca siódmego 2011. Jest jasne, czy to jest interpretowana jako data gregoriańska, ponieważ te same wartości są zwracane przez <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody, gdy używa konwencji Niezmienna kultura. Reprezentacja tej daty w formacie ciągu, która jest formatowana z użyciem konwencji bieżącej kultury, to 14/08/32, co odpowiada dacie w kalendarzu Um Al Qura. Następnie członkami `DateTime` i `Calendar` są używane do zwrócenia dzień, miesiąc i rok <xref:System.DateTime> wartość. W każdym przypadku wartości zwracane przez <xref:System.DateTime> członków odzwierciedlają wartości kalendarza gregoriańskiego, natomiast wartości zwracane przez <xref:System.Globalization.UmAlQuraCalendar> członków odzwierciedlają wartości w kalendarzu al Qura Uum.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Tworzenie wystąpień dat na podstawie kalendarza

Ponieważ <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są oparte na kalendarza gregoriańskiego, należy wywołać przeciążonego konstruktora, który zawiera parametr typu <xref:System.Globalization.Calendar> można utworzyć wartości daty, jeśli chcesz użyć wartości dnia, miesiąca lub roku z inny kalendarz. Można również wywołać jednego z przeciążeń szczególne kalendarza <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metody tworzenia wystąpienia <xref:System.DateTime> obiekt na podstawie wartości określonego kalendarza.

Poniższy przykład tworzy jeden <xref:System.DateTime> wartości przez przekazanie <xref:System.Globalization.HebrewCalendar> do obiektu <xref:System.DateTime> konstruktora i tworzy drugi <xref:System.DateTime> wartości przez wywołanie metody <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody. Ponieważ te dwie wartości są tworzone z identycznymi wartościami z hebrajski kalendarza, wywołanie <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> metoda zawiera dwa <xref:System.DateTime> wartości są równe.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Reprezentujący dat w bieżącym kalendarza

Metody formatowania daty i godziny zawsze używają bieżącego kalendarza podczas konwertowania dat na ciągi. Oznacza to, że reprezentacja roku, miesiąca i dnia miesiąca w formacie ciągu odzwierciedla bieżący kalendarz i nie musi to być kalendarz gregoriański.

W poniższym przykładzie pokazano, jak bieżący kalendarz wpływa na reprezentację daty w formacie ciągu. Bieżąca kultura jest zmieniana na Chiński (tradycyjny, Tajwan) i jest tworzone wystąpienie wartości daty. Go następnie wyświetla bieżącego kalendarza i daty, zmiany bieżącego kalendarza <xref:System.Globalization.TaiwanCalendar>i ponownie Wyświetla bieżącego kalendarza i daty. Gdy data jest wyświetlana po raz pierwszy, jest przedstawiana jako data w kalendarzu gregoriańskim. Gdy data jest wyświetlana po raz drugi, jest przedstawiana jako data w kalendarzu tajwańskim.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Reprezentujących daty w kalendarzu długoterminowe

Do reprezentowania datę przy użyciu kalendarza, który nie jest bieżący kalendarz określonej kultury, należy wywołać metody, która <xref:System.Globalization.Calendar> obiektu. Na przykład <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody Konwertuj rok, miesiąc i dzień na wartości, które odzwierciedlać określonego kalendarza.

> [!WARNING]
> Niektóre kalendarze nie są opcjonalnymi kalendarzami żadnej kultury, więc przedstawianie dat za pomocą tych kalendarzy zawsze wymaga wywołania metod kalendarza. Dotyczy to wszystkich kalendarzy, które pochodzą z <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, i <xref:System.Globalization.PersianCalendar> klasy.

W poniższym przykładzie użyto <xref:System.Globalization.JulianCalendar> obiektu można utworzyć wystąpienia typu date 9 stycznia 1905 w kalendarz juliański. Gdy ta data jest wyświetlana przy użyciu kalendarza domyślnego (gregoriańskiego), jest przedstawiana jako 22 stycznia 1905 roku. Wywołuje do poszczególnych <xref:System.Globalization.JulianCalendar> metody włączyć dat być reprezentowane w kalendarz juliański.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendarze i zakres dat

Najwcześniejsza data obsługiwane przez kalendarza jest określane przez tego kalendarza <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> właściwości. Aby uzyskać <xref:System.Globalization.GregorianCalendar> klasy, czy data jest 1 stycznia 0001 r. Większość innych kalendarzy .NET obsługuje późniejszym terminie. W trakcie pracy z wartości daty i godziny poprzedzający kalendarza tak szybko, jak jego obsługiwane zgłasza data <xref:System.ArgumentOutOfRangeException> wyjątku.

Istnieje jednak jeden ważny wyjątek. Wartość domyślna (niezainicjowane) <xref:System.DateTime> obiektu i <xref:System.DateTimeOffset> obiekt jest taki sam <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> wartość. Jeśli spróbujesz format tego datę w kalendarzu, która nie obsługuje 1 stycznia 0001 r. N.E. specyfikator formatu nie zostanie określona, formatowania metoda używa specyfikator formatu "s" (można sortować daty/godziny wzorzec) zamiast specyfikator formatu "G" (ogólne daty/godziny wzorzec). W związku z tym nie zgłasza operacji formatowania <xref:System.ArgumentOutOfRangeException> wyjątku. W zamian zwróci nieobsługiwaną datę. Jest to zilustrowane w poniższym przykładzie, który zawiera wartość <xref:System.DateTime.MinValue?displayProperty=nameWithType> podczas bieżącej kultury ustawiono japoński (Japonia) z kalendarzem japońskich i arabski (Egipt) z kalendarzem Um Al Qura. Ustawia również bieżącej kultury angielski (Stany Zjednoczone) i wywołania <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metody z każdej z tych <xref:System.Globalization.CultureInfo> obiektów. W każdym przypadku data jest wyświetlana z użyciem wzorca sortowalnej daty/godziny.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Praca z Arial

Daty w kalendarzach są zazwyczaj dzielone na ery. Jednak <xref:System.Globalization.Calendar> klas programu .NET nie obsługują era, co wynika z kalendarza oraz większość <xref:System.Globalization.Calendar> klasy obsługuje tylko jeden ery. Tylko <xref:System.Globalization.JapaneseCalendar> i <xref:System.Globalization.JapaneseLunisolarCalendar> klasy obsługuje wiele Arial.

### <a name="eras-and-era-names"></a>Arial i nazwy era

W środowisku .NET, liczby całkowite będące Arial obsługiwana przez implementację kalendarza są przechowywane w odwrotnej kolejności w <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tablicy. Bieżący ery jest o indeksie zero, a także <xref:System.Globalization.Calendar> klas, które obsługują wiele Arial, każdy indeks kolejnych odzwierciedla poprzedniej ery. Statycznych <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> właściwość definiuje indeks bieżącego ery w <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> tablicy; jest stałą, której wartość jest zawsze zero. Poszczególne <xref:System.Globalization.Calendar> obejmować pól statycznych, które zwracają wartość ery bieżącej klasy. Zostały one wymienione w poniższej tabeli.

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

Można pobrać nazwę, która odpowiada numerowi ery określonego przez przekazanie numer ery <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> lub <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metody. Poniższy przykład wywołania tych metod można pobrać informacji o obsłudze ery w <xref:System.Globalization.GregorianCalendar> klasy.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

Ponadto niestandardowy format daty i godziny „g” dołącza nazwę ery kalendarza do reprezentacji daty i godziny w formacie ciągu. Aby uzyskać więcej informacji, zobacz [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Utworzenie wystąpienia typu date z ery

Dla dwóch <xref:System.Globalization.Calendar> klas, które obsługują wiele Arial, datę, która składa się z danego roku, miesiąc i dzień miesiąca wartość może być niejednoznaczna, na przykład wszystkie cztery Arial z <xref:System.Globalization.JapaneseCalendar> ma lat ponumerowane od 1 do 15. Normalnie, jeśli era nie jest określona, metody daty i godziny oraz kalendarza zakładają, że wartości należą do bieżącej ery. Aby jawnie określić era podczas tworzenia wystąpienia daty <xref:System.Globalization.Calendar> klasy, która obsługuje wiele Arial, można wywołać <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody. Ta metoda umożliwia jawne określenie ery wraz z rokiem, miesiącem, dniem, godziną, minutą, sekundą i milisekundą w kalendarzu.

W poniższym przykładzie użyto <xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody tworzenia wystąpienia tego samego dnia, miesiąca od pierwszego dnia roku drugiego, w każdej ery obsługiwane przez <xref:System.Globalization.JapaneseCalendar> klasy. Następnie data jest wyświetlana z użyciem kalendarza japońskiego i gregoriańskiego. Wywołuje również <xref:System.DateTime> konstruktora, aby zilustrować, metody, które utworzyć wartości daty bez określania ery utworzyć dat w bieżącym ery.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>Reprezentujący dat w kalendarzach z Arial

Jeśli <xref:System.Globalization.Calendar> obiekt obsługuje Arial i bieżącego kalendarza <xref:System.Globalization.CultureInfo> obiekt era znajduje się w ciągu reprezentującego wartość daty i godziny dla pełnej daty i godziny, Data długa oraz wzorców daty krótkiej. W poniższym przykładzie są wyświetlane te wzorce, gdy bieżącą kulturą jest Japonia (Japoński), a bieżącym kalendarzem jest kalendarz japoński.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar> Klasy jest to jedyna klasa kalendarza w środowisku .NET, które obu obsługuje dat w więcej niż jeden era, które mogą być bieżącego kalendarza <xref:System.Globalization.CultureInfo> obiektów — w szczególności z <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury japoński (Japonia).

Specyfikator formatu niestandardowego „g” dołącza erę do ciągu wynikowego dla każdego kalendarza. W poniższym przykładzie użyto ciągu formatu niestandardowego „MM-dd-yyyy g” w celu dołączenia ery do ciągu wynikowego, gdy bieżącym kalendarzem jest kalendarz gregoriański.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

W przypadkach, gdzie reprezentacji ciągu daty jest wyrażone w kalendarzu, który nie jest bieżący kalendarz <xref:System.Globalization.Calendar> klasa zawiera <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> metodę, która może być używany wraz z <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>, i <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody jednoznacznie wskazywać datę, a także era, do którego on należy. W poniższym przykładzie użyto <xref:System.Globalization.JapaneseLunisolarCalendar> klasy zapewnienie ilustracji. Pamiętaj jednak, tym takich jak opisową nazwę lub skrót zamiast całkowitą ery w ciągu wyników wymaga czy wystąpienia <xref:System.Globalization.DateTimeFormatInfo> obiektu i wprowadzić <xref:System.Globalization.JapaneseCalendar> jej bieżącego kalendarza. ( <xref:System.Globalization.JapaneseLunisolarCalendar> Kalendarza nie może być bieżącego kalendarza żadnych kultury, ale w takim przypadku obu kalendarzy udostępnianie tego samego Arial.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>Zobacz także

[Porady: wyświetlanie dat w kalendarzach innych niż gregoriański](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
[próbki: narzędzie zakresu tydzień kalendarza](http://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
