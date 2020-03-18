---
title: 'Porady: wyświetlanie dat w kalendarzach innych niż gregoriański'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
ms.openlocfilehash: 455996d091f92367667e7077a4524898cd8face6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138756"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Porady: wyświetlanie dat w kalendarzach innych niż gregoriański
<xref:System.DateTimeOffset> I <xref:System.DateTime> typy używają kalendarza gregoriańskiego jako kalendarza domyślnego. Oznacza to, że wywołanie `ToString` metody wartości daty i godziny wyświetla reprezentację ciągu tej daty i godziny w kalendarzu gregoriańskim, nawet jeśli ta data i godzina została utworzona przy użyciu innego kalendarza. Jest to zilustrowane w poniższym przykładzie, który używa dwóch różnych sposobów tworzenia wartości daty i godziny z kalendarzem perskim, ale <xref:System.DateTime.ToString%2A> nadal wyświetla te wartości daty i godziny w kalendarzu gregoriańskim podczas wywoływania metody. W tym przykładzie przedstawiono dwie powszechnie używane, ale niepoprawne techniki wyświetlania daty w określonym kalendarzu.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dwie różne techniki mogą być używane do wyświetlania daty w określonym kalendarzu. Pierwszy wymaga, aby kalendarz był domyślnym kalendarzem dla określonej kultury. Drugi może być używany z dowolnym kalendarzem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1. Tworzenie wystąpienia obiektu kalendarza pochodzącego <xref:System.Globalization.Calendar> z klasy, która reprezentuje kalendarz, który ma być używany.  
  
2. Utworzyć wystąpienia <xref:System.Globalization.CultureInfo> obiektu reprezentującego kulturę, którego formatowanie będzie używane do wyświetlania daty.  
  
3. Wywołaj <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodę, aby ustalić, czy obiekt kalendarza jest <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> członkiem tablicy zwracanej przez właściwość. Oznacza to, że kalendarz może służyć <xref:System.Globalization.CultureInfo> jako domyślny kalendarz obiektu. Jeśli nie jest członkiem tablicy, postępuj zgodnie z instrukcjami w sekcji "Aby wyświetlić datę w dowolnym kalendarzu".  
  
4. Przypisz obiekt kalendarza <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> do <xref:System.Globalization.DateTimeFormatInfo> właściwości obiektu <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> zwróconego przez właściwość.  
  
    > [!NOTE]
    > Klasa <xref:System.Globalization.CultureInfo> posiada również <xref:System.Globalization.CultureInfo.Calendar%2A> właściwość. Jednak jest tylko do odczytu i stała; nie zmienia się w celu odzwierciedlenia nowego kalendarza domyślnego przypisanego <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> do właściwości.  
  
5. Wywołaj <xref:System.DateTime.ToString%2A> <xref:System.DateTime.ToString%2A> lub metody i przekazać <xref:System.Globalization.CultureInfo> go obiekt, którego domyślny kalendarz został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1. Tworzenie wystąpienia obiektu kalendarza pochodzącego <xref:System.Globalization.Calendar> z klasy, która reprezentuje kalendarz, który ma być używany.  
  
2. Określ, które elementy daty i godziny powinny pojawić się w reprezentacji ciągu wartości daty i godziny.  
  
3. Dla każdego elementu daty i godziny, który chcesz wyświetlić, wywołaj obiekt kalendarza `Get`... Metoda. Dostępne są następujące metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlić rok w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąc w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, aby wyświetlić minuty w godzinie w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, aby wyświetlić sekundy w minucie w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, aby wyświetlić milisekundy w drugim w odpowiednim kalendarzu.  
  
## <a name="example"></a>Przykład  
 W przykładzie wyświetla datę przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarza Hidżry jako kalendarza domyślnego dla kultury ar-JO i wyświetla datę przy użyciu kalendarza perskiego, który nie jest obsługiwany jako opcjonalny kalendarz przez kulturę fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy <xref:System.Globalization.CultureInfo> obiekt może obsługiwać jeden lub więcej kalendarzy, które są oznaczone przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> właściwość. Jeden z nich jest oznaczony jako domyślny kalendarz kultury i jest <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> zwracany przez właściwość tylko do odczytu. Inny z opcjonalnych kalendarzy można wyznaczyć jako <xref:System.Globalization.Calendar> domyślny, przypisując obiekt, który reprezentuje ten kalendarz do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości zwróconej <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> przez właściwość. Jednak niektóre kalendarze, takie jak kalendarz perski <xref:System.Globalization.PersianCalendar> reprezentowany przez klasę, nie służą jako opcjonalne kalendarze dla żadnej kultury.  
  
 W przykładzie definiuje klasę narzędzia kalendarza `CalendarUtility`wielokrotnego użytku, aby obsłużyć wiele szczegółów generowania reprezentacji ciągu daty przy użyciu określonego kalendarza. Klasa `CalendarUtility` ma następujące elementy członkowskie:  
  
- Sparametryzowany konstruktor, <xref:System.Globalization.Calendar> którego pojedynczy parametr jest obiektem, w którym ma być reprezentowana data. Jest to przypisane do prywatnego pola klasy.  
  
- `CalendarExists`, metoda prywatna, która zwraca wartość logiczną wskazującą, czy kalendarz reprezentowany przez `CalendarUtility` obiekt jest obsługiwany przez <xref:System.Globalization.CultureInfo> obiekt, który jest przekazywany do metody jako parametr. Metoda otacza wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, do której przekazuje <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> tablicy.  
  
- `HasSameName`, prywatną metodę przypisaną <xref:System.Predicate%601> do pełnomocnika, <xref:System.Array.Exists%2A?displayProperty=nameWithType> która jest przekazywana jako parametr do metody. Każdy element członkowski tablicy jest przekazywany do metody, dopóki metoda nie zwróci . `true` Metoda określa, czy nazwa kalendarza opcjonalnego jest taka sama `CalendarUtility` jak kalendarz reprezentowany przez obiekt.  
  
- `DisplayDate`, przeciążeni metody publicznej, która jest <xref:System.DateTime> przekazywana dwa parametry: a <xref:System.DateTimeOffset> lub `CalendarUtility` wartość do wyrażenia w kalendarzu reprezentowanym przez obiekt; i kultury, której mają być używane reguły formatowania. Jego zachowanie w zwracaniu reprezentacji ciągu daty zależy od tego, czy kalendarz docelowy jest obsługiwany przez kulturę, której reguły formatowania mają być używane.  
  
 Niezależnie od kalendarza użytego <xref:System.DateTime> <xref:System.DateTimeOffset> do utworzenia lub wartości w tym przykładzie ta wartość jest zwykle wyrażana jako data gregoriana. Dzieje się <xref:System.DateTime> tak, ponieważ typy i <xref:System.DateTimeOffset> typy nie zachowują żadnych informacji kalendarza. Wewnętrznie są one reprezentowane jako liczba kleszczy, które upłynęły od północy 1 stycznia 0001. Interpretacja tej liczby zależy od kalendarza. W przypadku większości kultur domyślnym kalendarzem jest kalendarz gregoriański.  
  
## <a name="see-also"></a>Zobacz też

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
