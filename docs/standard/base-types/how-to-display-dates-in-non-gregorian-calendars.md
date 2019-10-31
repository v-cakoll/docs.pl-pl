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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138756"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Porady: wyświetlanie dat w kalendarzach innych niż gregoriański
Typy <xref:System.DateTime> i <xref:System.DateTimeOffset> używają kalendarza gregoriańskiego jako kalendarza domyślnego. Oznacza to, że wywołanie metody `ToString` wartości daty i godziny powoduje wyświetlenie ciągu reprezentującego datę i godzinę w kalendarzu gregoriańskim, nawet jeśli ta data i godzina zostały utworzone przy użyciu innego kalendarza. Jest to zilustrowane w poniższym przykładzie, który używa dwóch różnych sposobów tworzenia wartości daty i godziny w kalendarzu perski, ale nadal wyświetla te wartości daty i godziny w kalendarzu gregoriańskim, gdy wywołuje metodę <xref:System.DateTime.ToString%2A>. W tym przykładzie przedstawiono dwa często używane, ale nieprawidłowe techniki wyświetlania daty w określonym kalendarzu.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Do wyświetlania daty w określonym kalendarzu można użyć dwóch różnych technik. Pierwszy wymaga, aby kalendarz był kalendarzem domyślnym dla określonej kultury. Drugi może być używany z dowolnym kalendarzem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1. Utwórz wystąpienie obiektu Calendar pochodnego od klasy <xref:System.Globalization.Calendar>, która reprezentuje kalendarz do użycia.  
  
2. Utworzenie wystąpienia obiektu <xref:System.Globalization.CultureInfo> reprezentującego kulturę, której formatowanie będzie używane do wyświetlania daty.  
  
3. Wywołaj metodę <xref:System.Array.Exists%2A?displayProperty=nameWithType>, aby określić, czy obiekt Calendar jest elementem członkowskim tablicy zwracanej przez właściwość <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Oznacza to, że kalendarz może obsłużyć jako domyślny kalendarz dla obiektu <xref:System.Globalization.CultureInfo>. Jeśli nie jest elementem członkowskim tablicy, postępuj zgodnie z instrukcjami w sekcji "aby wyświetlić datę w dowolnym kalendarzu".  
  
4. Przypisz obiekt Calendar do właściwości <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> obiektu <xref:System.Globalization.DateTimeFormatInfo> zwróconego przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > Klasa <xref:System.Globalization.CultureInfo> ma również właściwość <xref:System.Globalization.CultureInfo.Calendar%2A>. Jest to jednak tylko do odczytu i stała; nie zmienia się w celu odzwierciedlenia nowego domyślnego kalendarza przypisanego do właściwości <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>.  
  
5. Wywołaj metodę <xref:System.DateTime.ToString%2A> lub <xref:System.DateTime.ToString%2A> i przekaż ją do obiektu <xref:System.Globalization.CultureInfo>, którego domyślny kalendarz został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1. Utwórz wystąpienie obiektu Calendar pochodnego od klasy <xref:System.Globalization.Calendar>, która reprezentuje kalendarz do użycia.  
  
2. Określ, które elementy daty i godziny mają być wyświetlane w ciągu reprezentującym wartość daty i godziny.  
  
3. Dla każdego elementu daty i godziny, który chcesz wyświetlić, wywołaj `Get`obiektu kalendarza... Method. Dostępne są następujące metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlić rok w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąc w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, aby wyświetlić minuty w ciągu godziny w odpowiednim kalendarzu.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, aby wyświetlić sekundy w odpowiednim kalendarzu w ciągu minuty.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, aby wyświetlić milisekundy w drugim w odpowiednim kalendarzu.  
  
## <a name="example"></a>Przykład  
 Przykład wyświetla datę przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarza Hidżry jako kalendarz domyślny dla kultury AR-JO i wyświetla datę przy użyciu kalendarza perskiego, który nie jest obsługiwany jako opcjonalny Kalendarz przez kulturę FA-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy obiekt <xref:System.Globalization.CultureInfo> może obsługiwać jeden lub więcej kalendarzy, które są wskazywane przez właściwość <xref:System.Globalization.CultureInfo.OptionalCalendars%2A>. Jedna z nich jest oznaczona jako domyślny kalendarz kultury i zwracana przez właściwość <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> tylko do odczytu. Kolejne kalendarze opcjonalne można wyznaczyć jako domyślne, przypisując <xref:System.Globalization.Calendar> obiekt, który reprezentuje ten kalendarz do właściwości <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> zwróconej przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Jednak niektóre kalendarze, takie jak kalendarz Perski przedstawiony przez klasę <xref:System.Globalization.PersianCalendar>, nie są jako opcjonalne kalendarze dla żadnej kultury.  
  
 W przykładzie zdefiniowano klasę narzędzia kalendarza wielokrotnego użytku, `CalendarUtility`, aby obsłużyć wiele szczegółów generowania ciągu reprezentującego datę przy użyciu określonego kalendarza. Klasa `CalendarUtility` ma następujących członków:  
  
- Sparametryzowany Konstruktor, którego pojedynczy parametr jest obiektem <xref:System.Globalization.Calendar>, w którym ma być reprezentowana Data. Jest to przypisane do prywatnego pola klasy.  
  
- `CalendarExists`, Metoda prywatna zwracająca wartość logiczną wskazującą, czy Kalendarz reprezentowany przez obiekt `CalendarUtility` jest obsługiwany przez obiekt <xref:System.Globalization.CultureInfo>, który jest przesyłany do metody jako parametr. Metoda otacza wywołanie metody <xref:System.Array.Exists%2A?displayProperty=nameWithType>, do której przekazuje tablicę <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.  
  
- `HasSameName`, prywatna Metoda przypisana do <xref:System.Predicate%601> delegata, który jest przesyłany jako parametr do metody <xref:System.Array.Exists%2A?displayProperty=nameWithType>. Każdy element członkowski tablicy jest przenoszona do metody do momentu, gdy metoda zwróci wartość `true`. Metoda określa, czy nazwa opcjonalnego kalendarza jest taka sama jak kalendarz reprezentowany przez obiekt `CalendarUtility`.  
  
- `DisplayDate`, przeciążona metoda publiczna, która przekazała dwa parametry: <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartość w kalendarzu reprezentowanego przez obiekt `CalendarUtility`; i kulturę, której reguły formatowania mają być używane. Zachowanie w celu zwrócenia ciągu reprezentującego datę jest zależne od tego, czy Kalendarz docelowy jest obsługiwany przez kulturę, której reguły formatowania mają być używane.  
  
 Bez względu na kalendarz używany do tworzenia <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości w tym przykładzie ta wartość jest zwykle wyrażona jako data gregoriański. Dzieje się tak, ponieważ typy <xref:System.DateTime> i <xref:System.DateTimeOffset> nie zachowują żadnych informacji o kalendarzu. Wewnętrznie są one reprezentowane jako liczba taktów, które upłynęły od północy 1 stycznia 0,001. Interpretacja tego numeru zależy od kalendarza. W przypadku większości kultur domyślnym kalendarzem jest kalendarz gregoriański.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
