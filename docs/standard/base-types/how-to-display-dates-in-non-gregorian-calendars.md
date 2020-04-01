---
title: 'Instrukcje: Wyświetlanie dat w kalendarzach innych niż gregoriański'
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
ms.openlocfilehash: 8d02b74f63ec5b6260679ae4cea04791681ec238
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523928"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Instrukcje: Wyświetlanie dat w kalendarzach innych niż gregoriański
I <xref:System.DateTime> <xref:System.DateTimeOffset> typy używają kalendarza gregoriańskiego jako kalendarza domyślnego. Oznacza to, że wywołanie metody `ToString` wartości daty i godziny wyświetla reprezentację ciągu tej daty i godziny w kalendarzu gregoriańskim, nawet jeśli ta data i godzina została utworzona przy użyciu innego kalendarza. Jest to zilustrowane w poniższym przykładzie, który używa dwóch różnych sposobów, aby utworzyć wartość daty i godziny z kalendarzem <xref:System.DateTime.ToString%2A> perskim, ale nadal wyświetla te wartości daty i godziny w kalendarzu gregoriańskim, gdy wywołuje metodę. W tym przykładzie odzwierciedla dwa powszechnie używane, ale niepoprawne techniki wyświetlania daty w określonym kalendarzu.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dwie różne techniki mogą być używane do wyświetlania daty w określonym kalendarzu. Pierwszy wymaga, aby kalendarz był domyślnym kalendarzem dla określonej kultury. Drugi może być używany z dowolnym kalendarzem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1. Tworzenie wystąpienia obiektu kalendarza pochodzącego <xref:System.Globalization.Calendar> z klasy reprezentującej kalendarz, który ma być używany.  
  
2. Tworzenie wystąpienia <xref:System.Globalization.CultureInfo> obiektu reprezentującego kulturę, której formatowanie będzie używane do wyświetlania daty.  
  
3. Wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, aby ustalić, czy obiekt kalendarza <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> jest członkiem tablicy zwróconej przez właściwość. Oznacza to, że kalendarz może służyć jako <xref:System.Globalization.CultureInfo> domyślny kalendarz dla obiektu. Jeśli nie jest członkiem tablicy, postępuj zgodnie z instrukcjami w sekcji "Aby wyświetlić datę w dowolnym kalendarzu".  
  
4. Przypisz obiekt kalendarza <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> do <xref:System.Globalization.DateTimeFormatInfo> właściwości obiektu <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> zwróconego przez właściwość.  
  
    > [!NOTE]
    > Klasa <xref:System.Globalization.CultureInfo> posiada również <xref:System.Globalization.CultureInfo.Calendar%2A> właściwość. Jednak jest tylko do odczytu i stała; nie zmienia się, aby odzwierciedlić nowy kalendarz domyślny przypisany <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> do właściwości.  
  
5. Wywołaj <xref:System.DateTime.ToString%2A> metodę lub <xref:System.DateTime.ToString%2A> metodę i przekaż <xref:System.Globalization.CultureInfo> ją obiektowi, którego domyślny kalendarz został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1. Tworzenie wystąpienia obiektu kalendarza pochodzącego <xref:System.Globalization.Calendar> z klasy reprezentującej kalendarz, który ma być używany.  
  
2. Określ, które elementy daty i godziny powinny być wyświetlane w reprezentacji ciągu wartości daty i godziny.  
  
3. Dla każdego elementu daty i godziny, który chcesz `Get`wyświetlić, wywołaj obiekt kalendarza ... Metoda. Dostępne są następujące metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlić rok w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąc w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, aby wyświetlić minuty w godzinie w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, aby wyświetlić sekundy w minucie w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, aby wyświetlić milisekundy w drugim w odpowiednim kalendarzu.  
  
## <a name="example"></a>Przykład  
 W przykładzie jest wyświetlana data przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarza Hidżry jako domyślnego kalendarza dla kultury ar-JO i wyświetla datę przy użyciu kalendarza perskiego, który nie jest obsługiwany jako kalendarz opcjonalny przez kulturę fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy <xref:System.Globalization.CultureInfo> obiekt może obsługiwać jeden lub więcej kalendarzy, które są wskazywane przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> właściwość. Jeden z nich jest wyznaczony jako kalendarz domyślny kultury i <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> jest zwracany przez właściwość tylko do odczytu. Inny z kalendarzy opcjonalnych można wyznaczyć jako <xref:System.Globalization.Calendar> domyślny, przypisując <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> obiekt, który <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> reprezentuje ten kalendarz do właściwości zwróconej przez właściwość. Jednak niektóre kalendarze, takie jak kalendarz perski reprezentowany przez <xref:System.Globalization.PersianCalendar> klasę, nie służą jako kalendarze opcjonalne dla żadnej kultury.  
  
 W przykładzie definiuje klasy narzędzia kalendarza wielokrotnego użycia, `CalendarUtility`do obsługi wielu szczegółów generowania reprezentacji ciągu daty przy użyciu określonego kalendarza. Klasa `CalendarUtility` ma następujące elementy członkowskie:  
  
- Sparametryzowany konstruktor, <xref:System.Globalization.Calendar> którego pojedynczy parametr jest obiektem, w którym ma być reprezentowana data. Jest to przypisane do prywatnego pola klasy.  
  
- `CalendarExists`, metoda prywatna, która zwraca wartość logiczną wskazującą, czy kalendarz reprezentowany przez `CalendarUtility` obiekt jest obsługiwany przez <xref:System.Globalization.CultureInfo> obiekt, który jest przekazywany do metody jako parametr. Metoda zawija wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, do której <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> przekazuje tablicę.  
  
- `HasSameName`, prywatna metoda przypisana do delegata, <xref:System.Predicate%601> który <xref:System.Array.Exists%2A?displayProperty=nameWithType> jest przekazywany jako parametr do metody. Każdy element członkowski tablicy jest przekazywany do metody, dopóki metoda nie zwróci `true`. Metoda określa, czy nazwa kalendarza opcjonalnego jest taka sama `CalendarUtility` jak kalendarz reprezentowany przez obiekt.  
  
- `DisplayDate`, przeciążona metoda publiczna, która jest <xref:System.DateTime> przekazywana dwa parametry: lub <xref:System.DateTimeOffset> `CalendarUtility` wartość do wyrażenia w kalendarzu reprezentowanym przez obiekt; i kultury, której reguły formatowania mają być używane. Jego zachowanie podczas zwracania reprezentacji ciągu daty zależy od tego, czy kalendarz docelowy jest obsługiwany przez kulturę, której reguły formatowania mają być używane.  
  
 Niezależnie od kalendarza używanego <xref:System.DateTime> <xref:System.DateTimeOffset> do tworzenia lub wartości w tym przykładzie, ta wartość jest zazwyczaj wyrażona jako data gregoriańska. Dzieje się <xref:System.DateTime> tak, ponieważ i <xref:System.DateTimeOffset> typy nie zachowują żadnych informacji kalendarza. Wewnętrznie są one reprezentowane jako liczba kleszczy, które upłynęły od północy 1 stycznia 0001. Interpretacja tego numeru zależy od kalendarza. Dla większości kultur kalendarzem domyślnym jest kalendarz gregoriański.
