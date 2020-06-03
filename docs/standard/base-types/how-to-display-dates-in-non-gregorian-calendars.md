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
<xref:System.DateTime>Typy i <xref:System.DateTimeOffset> używają kalendarza gregoriańskiego jako kalendarza domyślnego. Oznacza to, że wywołanie metody daty i godziny `ToString` powoduje wyświetlenie ciągu reprezentującego datę i godzinę w kalendarzu gregoriańskim, nawet jeśli ta data i godzina zostały utworzone przy użyciu innego kalendarza. Jest to zilustrowane w poniższym przykładzie, który używa dwóch różnych sposobów tworzenia wartości daty i godziny w kalendarzu perski, ale nadal wyświetla te wartości daty i godziny w kalendarzu gregoriańskim, gdy wywołuje <xref:System.DateTime.ToString%2A> metodę. W tym przykładzie przedstawiono dwa często używane, ale nieprawidłowe techniki wyświetlania daty w określonym kalendarzu.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Do wyświetlania daty w określonym kalendarzu można użyć dwóch różnych technik. Pierwszy wymaga, aby kalendarz był kalendarzem domyślnym dla określonej kultury. Drugi może być używany z dowolnym kalendarzem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1. Utwórz wystąpienie obiektu kalendarza pochodnego od <xref:System.Globalization.Calendar> klasy, która reprezentuje kalendarz do użycia.  
  
2. Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiektu reprezentującego kulturę, której formatowanie będzie używane do wyświetlania daty.  
  
3. Wywołaj <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodę, aby określić, czy obiekt Calendar jest elementem członkowskim tablicy zwracanej przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Właściwość. Oznacza to, że kalendarz może być używany jako domyślny kalendarz dla <xref:System.Globalization.CultureInfo> obiektu. Jeśli nie jest elementem członkowskim tablicy, postępuj zgodnie z instrukcjami w sekcji "aby wyświetlić datę w dowolnym kalendarzu".  
  
4. Przypisz obiekt Calendar do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> właściwości <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Właściwość.  
  
    > [!NOTE]
    > <xref:System.Globalization.CultureInfo>Klasa ma również <xref:System.Globalization.CultureInfo.Calendar%2A> Właściwość. Jest to jednak tylko do odczytu i stała; nie zmienia się w celu odzwierciedlenia nowego domyślnego kalendarza przypisanego do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości.  
  
5. Wywołaj albo <xref:System.DateTime.ToString%2A> <xref:System.DateTime.ToString%2A> metodę, a następnie przekaż ją do <xref:System.Globalization.CultureInfo> obiektu, którego domyślny kalendarz został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1. Utwórz wystąpienie obiektu kalendarza pochodnego od <xref:System.Globalization.Calendar> klasy, która reprezentuje kalendarz do użycia.  
  
2. Określ, które elementy daty i godziny mają być wyświetlane w ciągu reprezentującym wartość daty i godziny.  
  
3. Dla każdego elementu daty i godziny, który chcesz wyświetlić, wywołaj obiekt Calendar.. `Get` . Method. Dostępne są następujące metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlić rok w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąc w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, aby wyświetlić minuty w ciągu godziny w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, aby wyświetlić sekundy (w minutach) w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, aby wyświetlić milisekundy w drugim w odpowiednim kalendarzu.  
  
## <a name="example"></a>Przykład  
 Przykład wyświetla datę przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarza Hidżry jako kalendarz domyślny dla kultury AR-JO i wyświetla datę przy użyciu kalendarza perskiego, który nie jest obsługiwany jako opcjonalny Kalendarz przez kulturę FA-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy <xref:System.Globalization.CultureInfo> obiekt może obsługiwać jeden lub więcej kalendarzy, które są wskazywane przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> Właściwość. Jedna z nich jest oznaczona jako domyślny kalendarz kultury i zwracana przez właściwość tylko do odczytu <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> . Kolejne kalendarze opcjonalne można wyznaczyć jako domyślne, przypisując <xref:System.Globalization.Calendar> obiekt reprezentujący ten kalendarz do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> Właściwości zwróconej przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Właściwość. Niektóre kalendarze, takie jak kalendarz Perski przedstawiony przez klasę, nie są jednak załączane <xref:System.Globalization.PersianCalendar> jako opcjonalne kalendarze dla żadnej kultury.  
  
 W przykładzie zdefiniowano klasę narzędzia kalendarza wielokrotnego użytku, `CalendarUtility` , która obsługuje wiele szczegółów generowania ciągu reprezentującego datę przy użyciu określonego kalendarza. `CalendarUtility`Klasa ma następujących członków:  
  
- Sparametryzowany Konstruktor, którego pojedynczy parametr to <xref:System.Globalization.Calendar> obiekt, w którym ma być reprezentowana Data. Jest to przypisane do prywatnego pola klasy.  
  
- `CalendarExists`Metoda prywatna zwracająca wartość logiczną, wskazującą, czy Kalendarz reprezentowany przez `CalendarUtility` obiekt jest obsługiwany przez <xref:System.Globalization.CultureInfo> obiekt, który jest przesyłany do metody jako parametr. Metoda otacza wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, do której przeszedł <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> tablicę.  
  
- `HasSameName`Metoda prywatna przypisana do <xref:System.Predicate%601> delegata, który jest przekazaniem jako parametr do <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody. Każdy element członkowski tablicy jest przenoszona do metody do momentu, aż Metoda zwróci metodę `true` . Metoda określa, czy nazwa opcjonalnego kalendarza jest taka sama jak kalendarz reprezentowany przez `CalendarUtility` obiekt.  
  
- `DisplayDate`, przeciążona metoda publiczna przekazała dwa parametry: albo <xref:System.DateTime> <xref:System.DateTimeOffset> wartość w kalendarzu reprezentowanego przez `CalendarUtility` obiekt; oraz kulturę, której reguły formatowania mają być używane. Zachowanie w celu zwrócenia ciągu reprezentującego datę jest zależne od tego, czy Kalendarz docelowy jest obsługiwany przez kulturę, której reguły formatowania mają być używane.  
  
 Bez względu na kalendarz używany do utworzenia <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości w tym przykładzie ta wartość jest zwykle wyrażona jako data gregoriański. Dzieje się tak, <xref:System.DateTime> ponieważ <xref:System.DateTimeOffset> typy i nie zachowują żadnych informacji o kalendarzu. Wewnętrznie są one reprezentowane jako liczba taktów, które upłynęły od północy 1 stycznia 0,001. Interpretacja tego numeru zależy od kalendarza. W przypadku większości kultur domyślnym kalendarzem jest kalendarz gregoriański.
