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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3da8a524af872a724ee6cbe206912572d6338624
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Porady: wyświetlanie dat w kalendarzach innych niż gregoriański
<xref:System.DateTime> i <xref:System.DateTimeOffset> typy używany kalendarz gregoriański jako ich kalendarz domyślny. Oznacza to, że wywołanie wartość daty i godziny `ToString` metoda Wyświetla reprezentację ciągu tego daty i czasu w kalendarza gregoriańskiego, nawet jeśli ta data i godzina został utworzony przy użyciu innego. Jest to zilustrowane w poniższym przykładzie, który wykorzystuje dwa różne sposoby, można utworzyć wartości daty i godziny z kalendarzem perska, ale nadal wyświetla te wartości daty i godziny w kalendarza gregoriańskiego, gdy wywołuje <xref:System.DateTime.ToString%2A> metody. W tym przykładzie odzwierciedla dwa najczęściej używane, ale niepoprawne techniki wyświetlanie daty w szczególności kalendarza.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dwóch różnych technik może służyć do wyświetlania w kalendarzu określonej daty. Pierwszy wymaga kalendarza kalendarz domyślny dla określonej kultury. Drugi służy z żadnym z kalendarzem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1.  Utwórz wystąpienie obiektu kalendarza pochodzące z <xref:System.Globalization.Calendar> klasa, która reprezentuje kalendarza ma być używany.  
  
2.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt reprezentujący kultury, którego formatowanie będzie używany do wyświetlania daty.  
  
3.  Wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodę, aby ustalić, czy obiekt kalendarza jest członkiem tablica zwrócona przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Oznacza to, że kalendarz może służyć jako domyślny kalendarz dla <xref:System.Globalization.CultureInfo> obiektu. Jeśli nie jest członkiem tablicy, postępuj zgodnie z instrukcjami w sekcji "Do wyświetlania daty w dowolny kalendarz".  
  
4.  Przypisz obiekt kalendarza do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> właściwość <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Klasa ma również <xref:System.Globalization.CultureInfo.Calendar%2A> właściwości. Jednak jest tylko do odczytu i stałej; nie zmienia się na nowy kalendarz domyślne przypisane do uwzględnienia <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości.  
  
5.  Wywołaj albo <xref:System.DateTime.ToString%2A> lub <xref:System.DateTime.ToString%2A> metody i przekaż go <xref:System.Globalization.CultureInfo> obiektu, którego domyślna kalendarz został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1.  Utwórz wystąpienie obiektu kalendarza pochodzące z <xref:System.Globalization.Calendar> klasa, która reprezentuje kalendarza ma być używany.  
  
2.  Określić, które daty i czasu elementów powinny być wyświetlane w reprezentację ciągu wartość daty i godziny.  
  
3.  Dla każdego elementu datę i godzinę, która ma być wyświetlany wywołania obiektu kalendarza `Get`... Metoda. Dostępne są następujące metody:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlić roku w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąca w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w odpowiedni kalendarz.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, można wyświetlić minut w ciągu godziny w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, do wyświetlenia w ciągu minuty w kalendarzu odpowiednie sekund.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> , do wyświetlenia w ciągu sekundy w kalendarzu odpowiednie milisekund.  
  
## <a name="example"></a>Przykład  
 W przykładzie przedstawiono datę przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarza Hijri jako domyślny kalendarz dla kultury ar JO i wyświetla datę perska kalendarza, który jako opcjonalnego kalendarza kultury fa-IR nie jest obsługiwany.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy <xref:System.Globalization.CultureInfo> obiektu może obsługiwać jeden lub więcej kalendarzy, które są oznaczone <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> właściwości. Jeden z nich jest oznaczony jako kultury domyślnej kalendarza i zwraca tylko do odczytu <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Inny opcjonalne kalendarzy może zostać wyznaczony jako domyślne, przypisując <xref:System.Globalization.Calendar> obiekt, który reprezentuje tego kalendarza <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości zwróconej przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Jednak niektóre kalendarzy, takich jak perska kalendarza reprezentowany przez <xref:System.Globalization.PersianCalendar> klasa, nie stanowią kalendarzy opcjonalne dla dowolnego kultury.  
  
 W przykładzie zdefiniowano klasę narzędzia do ponownego użycia kalendarza `CalendarUtility`, do obsługi wielu szczegółów generowania reprezentację ciągu daty przy użyciu określonego kalendarza. `CalendarUtility` Klasa ma następujące elementy:  
  
-   Parametryzowanym konstruktorem, w których pojedynczy parametr jest <xref:System.Globalization.Calendar> obiektu, w którym ma być reprezentowane daty. To jest przypisany do pola prywatne klasy.  
  
-   `CalendarExists`, metody prywatnej, która zwraca wartość logiczną wskazującą, czy kalendarza reprezentowany przez `CalendarUtility` obiekt jest obsługiwany przez <xref:System.Globalization.CultureInfo> obiekt, który jest przekazywany do metody jako parametr. Metoda opakowuje wywołanie <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, która przekazuje <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> tablicy.  
  
-   `HasSameName`, Metoda prywatna przypisane do <xref:System.Predicate%601> delegata, który jest przekazywany jako parametr <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody. Każdy element członkowski tablicy jest przekazywany do metody do momentu metoda zwraca `true`. Metoda określa, czy nazwa opcjonalnego kalendarza jest taka sama jak kalendarza reprezentowany przez `CalendarUtility` obiektu.  
  
-   `DisplayDate`, przeciążonej metodę publiczną, która została przekazana dwa parametry: albo <xref:System.DateTime> lub <xref:System.DateTimeOffset> express w kalendarzu reprezentowany przez wartość `CalendarUtility` obiekt; i kultury reguły formatowania, które mają być używane. Jego zachowania w reprezentację ciągu daty zwracanie zależy od tego, czy docelowy kalendarza jest obsługiwana przez kultury reguły formatowania, które mają być używane.  
  
 Niezależnie od tego kalendarza, używany do tworzenia <xref:System.DateTime> lub <xref:System.DateTimeOffset> w tym przykładzie, czy wartość jest zazwyczaj podawana jako data gregoriańska wartość. Jest to spowodowane <xref:System.DateTime> i <xref:System.DateTimeOffset> typów nie zachowuje żadnych informacji kalendarza. Wewnętrznie są one reprezentowane jako liczbę znaczników, które upłynęły od północy 1 stycznia 0001. Interpretacja tego numeru zależą od kalendarza. Dla większości kultur kalendarz domyślny jest kalendarza gregoriańskiego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do System.Core.dll.  
  
 Skompiluj kod w wierszu polecenia za pomocą csc.exe lub vb.exe. Aby skompilować kod w programie Visual Studio, umieść ją w szablonu projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
