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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 224e8e82b7e71d7efbfdf0ce26cc4bd783cce3c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313310"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Instrukcje: Wyświetlanie dat w kalendarzach innych niż gregoriański
<xref:System.DateTime> i <xref:System.DateTimeOffset> typy pełnić ich kalendarza domyślnego kalendarza gregoriańskiego. Oznacza to, że wywołanie wartości daty i godziny `ToString` metoda Wyświetla reprezentację ciągu tego dnia i godzina w kalendarzu gregoriańskim, nawet jeśli ta data i godzina utworzenia przy użyciu innego kalendarza. Jest to zilustrowane w poniższym przykładzie, który używa dwa różne sposoby tworzenia wartości daty i godziny przy użyciu kalendarz perski, ale nadal wyświetlana tych wartości daty i godziny w kalendarzu gregoriańskim, gdy wywołuje <xref:System.DateTime.ToString%2A> metody. W tym przykładzie odzwierciedla dwie techniki często używane, ale niepoprawny do wyświetlania datę w określonym kalendarzu.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dwóch różnych technik może służyć do wyświetlania datę w kalendarzu określonej. Pierwszy wymaga kalendarza kalendarz domyślny dla określonej kultury. Drugi można używać z dowolnym kalendarzu.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Aby wyświetlić datę domyślnego kalendarza kultury  
  
1. Tworzenie wystąpień obiektów kalendarza pochodną <xref:System.Globalization.Calendar> klasę, która reprezentuje kalendarz, który ma być używany.  
  
2. Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt reprezentujący kulturę, której formatowanie będzie służyć do wyświetlania daty.  
  
3. Wywołaj <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodę pozwala ustalić, czy obiekt Kalendarz jest elementem członkowskim tablicy zwracane przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> właściwości. Oznacza to, że kalendarz może służyć jako kalendarz domyślny dla <xref:System.Globalization.CultureInfo> obiektu. Jeśli nie jest elementem członkowskim tablicy, postępuj zgodnie z instrukcjami w sekcji "Do wyświetlania datę w dowolny kalendarz".  
  
4. Przypisz obiekt kalendarza do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> właściwość <xref:System.Globalization.DateTimeFormatInfo> obiektu zwróconego przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Ma również klasy <xref:System.Globalization.CultureInfo.Calendar%2A> właściwości. Jednak jest tylko do odczytu i stałe; nie zmienia się w celu odzwierciedlenia nowego kalendarz domyślny przypisany do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości.  
  
5. Wywołaj opcję <xref:System.DateTime.ToString%2A> lub <xref:System.DateTime.ToString%2A> metody i przekazać go <xref:System.Globalization.CultureInfo> obiektu, którego kalendarz domyślny został zmodyfikowany w poprzednim kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Aby wyświetlić datę w dowolnym kalendarzu  
  
1. Tworzenie wystąpień obiektów kalendarza pochodną <xref:System.Globalization.Calendar> klasę, która reprezentuje kalendarz, który ma być używany.  
  
2. Określić, które daty i czasu elementy powinien pojawić się w ciąg reprezentujący wartość daty i godziny.  
  
3. Dla każdego elementu daty i godziny, który chcesz wyświetlić, należy wywołać obiekt kalendarza `Get`... Metoda. Dostępne są następujące metody:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, aby wyświetlać rok w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, aby wyświetlić miesiąca w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, aby wyświetlić numer dnia miesiąca w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, aby wyświetlić godzinę dnia w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, aby wyświetlić minuty w ciągu godziny w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, aby wyświetlić sekund w ciągu minuty w kalendarzu odpowiednie.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> , do wyświetlenia milisekund w ciągu sekundy w kalendarzu odpowiednie.  
  
## <a name="example"></a>Przykład  
 W przykładzie wyświetlono datę przy użyciu dwóch różnych kalendarzy. Wyświetla datę po zdefiniowaniu kalendarz Hidżry jako kalendarz domyślny kultury ar JO i wyświetla datę przy użyciu kalendarz perski, który nie jest obsługiwany przez kulturę fa-IR jako kalendarz opcjonalny.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Każdy <xref:System.Globalization.CultureInfo> obiektu może obsługiwać jednego lub wielu kalendarzy, które są wskazywane przez <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> właściwości. Jedną z tych nazw jest wyznaczony jako kalendarz domyślny kultury i zwraca tylko do odczytu <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> właściwości. Inny opcjonalnymi kalendarzami może być wyznaczony jako domyślne, przypisując <xref:System.Globalization.Calendar> obiekt, który reprezentuje kalendarza do <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> właściwości zwróconej przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Jednak niektóre kalendarze, takich jak kalendarz perski reprezentowany przez <xref:System.Globalization.PersianCalendar> klasy, nie stanowić opcjonalnymi kalendarzami dla żadnej kultury.  
  
 W przykładzie zdefiniowano klasę użytkową wielokrotnego użytku kalendarza `CalendarUtility`, aby obsługiwać wiele szczegółów generowania ciąg reprezentujący datę przy użyciu określonego kalendarza. `CalendarUtility` Klasy ma następujące składowe:  
  
-   Którego pojedynczy parametr w to sparametryzowania konstruktora <xref:System.Globalization.Calendar> obiekt, w którym ma być reprezentowane wartość typu date. To jest przypisany do pola prywatnego klasy.  
  
-   `CalendarExists`, metody prywatnej, która zwraca wartość logiczną wskazującą, czy kalendarz reprezentowany przez `CalendarUtility` obiekt jest obsługiwany przez <xref:System.Globalization.CultureInfo> obiekt, który jest przekazywany do metody jako parametr. Metoda zawija wywołanie do <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, która przekazuje <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> tablicy.  
  
-   `HasSameName`, przypisany do metody prywatnej <xref:System.Predicate%601> delegata, który jest przekazywany jako parametr do <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody. Każdy element członkowski tablicy jest przekazywany do metody, dopóki metoda zwraca `true`. Metoda określa, czy nazwa kalendarz opcjonalny jest taka sama jak kalendarz, reprezentowane przez `CalendarUtility` obiektu.  
  
-   `DisplayDate`, przeciążona metoda publiczny, który jest przekazywany dwa parametry: albo <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości wyrażenia w kalendarzu, reprezentowane przez `CalendarUtility` obiektu; i kulturę, której reguły formatowania mają zostać użyte. Jego zachowanie w powrocie reprezentacją ciągu daty, zależy od tego, czy kalendarz docelowy jest obsługiwany przez kulturę, której reguły formatowania mają zostać użyte.  
  
 Niezależnie od tego, kalendarz, użyty do utworzenia <xref:System.DateTime> lub <xref:System.DateTimeOffset> w tym przykładzie, że wartość jest zwykle wyrażona jako data gregoriańska wartość. Jest to spowodowane <xref:System.DateTime> i <xref:System.DateTimeOffset> typów nie zachowuje żadnych informacji kalendarza. Wewnętrznie są one reprezentowane jako liczbę znaczników, które upłynęły od północy 1 stycznia 0001. Interpretacja tego numeru, zależy od kalendarza. W przypadku większości kultur kalendarz domyślny jest kalendarz gregoriański.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do System.Core.dll.  
  
 Skompiluj kod w wierszu polecenia za pomocą csc.exe lub vb.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
