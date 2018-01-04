---
title: "Porady: wyświetlanie zlokalizowanych informacji daty i godziny dla użytkowników sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6c68ddd29b8221a073b00ade87e3b9d3dc870b8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Porady: wyświetlanie zlokalizowanych informacji daty i godziny dla użytkowników sieci Web
Ponieważ strony sieci Web mogą być wyświetlane w dowolnym miejscu w świecie, operacje przeanalizować i sformatować wartości daty i godziny nie należy polegać na domyślnym formacie (która jest najczęściej format kultury lokalnego serwera sieci Web) po interakcji z użytkownikiem. Zamiast tego formularzy sieci Web, które obsługują daty i czasu ciągi wprowadzane przez użytkownika należy przeanalizować ciągów, za pomocą preferowanej kultury użytkownika. Podobnie danych daty i godziny powinna być wyświetlana użytkownikowi w formacie, który odpowiada kulturę użytkownika. W tym temacie pokazano, jak to zrobić.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Ciągi wprowadzane przez użytkownika, można przeanalizować daty i godziny  
  
1.  Określić, czy tablicy ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwości jest wypełnione. Jeśli nie, przejdź do kroku 6.  
  
2.  Jeśli zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość zostanie wypełnione, pobrać pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowany język i regionu użytkownika.  
  
3.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowana przez kultury wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
4.  Wywołaj albo `TryParse` lub `Parse` metody <xref:System.DateTime> lub <xref:System.DateTimeOffset> typu próby konwersji. Użyj przeciążenia `TryParse` lub `Parse` metody z `provider` parametru, a następnie przekaż jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiektu utworzonego w kroku 3.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiektu utworzonego w kroku 3.  
  
5.  W przypadku niepowodzenia konwersji Powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
6.  Jeśli nadal niepowodzenia konwersji lub zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu Niezmienna kultura, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Można przeanalizować lokalnego Data i godzina żądanie użytkownika  
  
1.  Dodaj <xref:System.Web.UI.WebControls.HiddenField> sterowania do formularza sieci Web.  
  
2.  Tworzenie funkcji JavaScript, która obsługuje `onClick` zdarzenie `Submit` przycisk pisząc bieżącej daty i godziny oraz przesunięcia lokalnej strefy czasowej z uniwersalnego czasu koordynowanego (UTC) do <xref:System.Web.UI.WebControls.HiddenField.Value%2A> właściwości. Użyj ogranicznik (na przykład średnikami) do oddzielania dwa składniki ciągu.  
  
3.  Za pomocą formularza sieci Web <xref:System.Web.UI.Control.PreRender> zdarzeń można wstawić funkcji do HTML output strumienia przez przekazanie tekst skrypt <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> metody.  
  
4.  Połącz program obsługi zdarzeń do `Submit` przycisku `onClick` zdarzeń, podając nazwę funkcji JavaScript do `OnClientClick` atrybutu `Submit` przycisku.  
  
5.  Utwórz program obsługi `Submit` przycisku <xref:System.Web.UI.WebControls.Button.Click> zdarzeń.  
  
6.  Program obsługi zdarzeń, określ, czy tablicy ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwości jest wypełnione. Jeśli nie, przejdź do kroku 14.  
  
7.  Jeśli zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość zostanie wypełnione, pobrać pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowany język i regionu użytkownika.  
  
8.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowana przez kultury wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
9. Przekazać ciąg przypisane do <xref:System.Web.UI.WebControls.HiddenField.Value%2A> właściwości <xref:System.String.Split%2A> metodę reprezentację ciągu użytkownika lokalnego daty i godziny oraz reprezentację ciągu przesunięcie strefy czasu lokalnego użytkownika są przechowywane w oddzielnych tablicy elementów.  
  
10. Wywołaj albo <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> metodę, aby przekonwertować datę i godzinę żądanie użytkownika <xref:System.DateTime> wartość. Użyj przeciążenia metody `provider` parametr, a następnie przekaż jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiektu utworzonego w kroku 8.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiektu utworzonego w kroku 8.  
  
11. W przypadku niepowodzenia operacji analizy w kroku 10, przejdź do kroku 13. W przeciwnym razie wywołać <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> do przekonwertowania na liczbę całkowitą reprezentację ciągu przesunięcia strefy czasowej użytkownika.  
  
12. Utwórz wystąpienie <xref:System.DateTimeOffset> reprezentujący czasu lokalnego użytkownika, wywołując <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktora.  
  
13. Jeśli w kroku 10 konwersji nie powiedzie się, powtórz kroki od 7 do 12 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
14. Jeśli nadal niepowodzenia konwersji lub zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu Niezmienna kultura, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Następnie powtórz kroki od 7 do 12.  
  
 W rezultacie <xref:System.DateTimeOffset> obiekt, który reprezentuje czas lokalny użytkownika strony sieci Web. Następnie można określić równoważne UTC przez wywołanie metody <xref:System.DateTimeOffset.ToUniversalTime%2A> metody. Można także określić równoważne Data i godzina na serwerze sieci Web przez wywołanie metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> — metoda i przekazywanie wartości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jako strefa czasowa można przekonwertować czasu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera źródła HTML i kodu formularza sieci Web ASP.NET, które pyta użytkownika, aby wprowadzić wartość daty i godziny. Skrypt po stronie klienta również zapisuje informacje o lokalnych Data i godzina żądanie użytkownika i przesunięcie strefy czasowej użytkownika z UTC ukryte pole. Te informacje jest następnie przeanalizować przez serwer, który zwraca stronę sieci Web, który wyświetla danych wejściowych użytkownika. Wyświetla także data i godzina żądanie użytkownika przy użyciu czasu lokalnego użytkownika, czas na serwerze, a czasem UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Skrypt po stronie klienta wywołuje JavaScript `toLocaleString` metody. Daje to ciąg formatowania konwencjami ustawień regionalnych użytkownika, który jest bardziej prawdopodobne, że można pomyślnie przeanalizować na serwerze.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Właściwości pochodzą z nazwy kultury, które są zawarte w `Accept-Language` nagłówki uwzględnione w żądaniu HTTP. Jednak nie wszystkie przeglądarki: `Accept-Language` nagłówków żądań i użytkowników można również pominąć nagłówki całkowicie. Dzięki temu należy mieć rezerwowej kultury podczas analizowania danych wejściowych użytkownika. Zazwyczaj rezerwowej kultury jest kulturą niezmienną zwrócony przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy może także udostępnić programu Internet Explorer nazwy kultury one danych wejściowych w polu tekstowym, który tworzy możliwości nazwy kultury jest nieprawidłowy. Dzięki temu można użyć obsługi wyjątków, podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu.  
  
 Po pobraniu z żądania HTTP przesłane przez program Internet Explorer <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablicy jest wypełniana w kolejności preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę kultury/regionie podstawowym użytkownika. Jeśli tablica zawiera dodatkowe elementy, Internet Explorer arbitralnie przypisze specyfikator jakości Rozdzielana średnikami z nazwy kultury. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołania <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktora z jego `useUserOverride` ustawiona `false` do tworzenia nowego <xref:System.Globalization.CultureInfo> obiektu. Dzięki temu, jeśli nazwa kultury jest domyślną nazwę kultury na serwerze, nowe <xref:System.Globalization.CultureInfo> obiektu utworzonego przez konstruktora klasy zawiera ustawienia domyślne, kultury i nie odzwierciedla żadnych ustawień zastąpiona przy użyciu serwera  **Regionalne i opcje języka** aplikacji. Wartości z wszelkich przesłoniętych ustawienia na serwerze prawdopodobnie nie istnieje w systemie lub w danych wejściowych użytkownika.  
  
 Ponieważ w tym przykładzie analizuje dwóch reprezentacji ciągu daty i godziny (co wprowadzane przez użytkownika, innych przechowywane do pola ukryte), definiuje możliwe <xref:System.Globalization.CultureInfo> obiektów, które mogą być wymagane z wyprzedzeniem. Tworzy tablicę <xref:System.Globalization.CultureInfo> obiektów, które jest większa niż liczba elementów zwracanych przez jedną <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwości. Następnie tworzy <xref:System.Globalization.CultureInfo> obiekt dla każdego języka i regionu ciągu, a także tworzy <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Kod może wywoływać albo <xref:System.DateTime.Parse%2A> lub <xref:System.DateTime.TryParse%2A> metodę, aby przekonwertować użytkownika reprezentacji ciągu daty i godziny do <xref:System.DateTime> wartości. Powtarzane wywołania metody parse może być wymagane dla pojedynczej operacji analizy. W związku z tym <xref:System.DateTime.TryParse%2A> lepszym rozwiązaniem jest użycie, ponieważ zwraca ono `false` Jeśli operacja analizy nie powiedzie się. Z kolei obsługi powtarzane wyjątki, które mogą być zgłaszany przez <xref:System.DateTime.Parse%2A> metoda może być bardzo kosztowna oferty w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, należy utworzyć [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony sieci Web bez CodeBehind. Następnie skopiuj przykładzie do strony sieci Web, dzięki czemu zastępuje istniejący kod. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Strona sieci Web powinna zawierać następujące sterowniki:  
  
-   A <xref:System.Web.UI.WebControls.Label> kontroli, która nie odwołuje się do kodu. Ustaw jego <xref:System.Web.UI.WebControls.TextBox.Text%2A> dla właściwości "Wprowadź liczbę z zakresu:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> formantu o nazwie `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> formantu o nazwie `OKButton`. Ustaw jego <xref:System.Web.UI.WebControls.Button.Text%2A> dla właściwości "OK".  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> formantu o nazwie `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wstrzykiwania skryptu do strumienia HTML, dane wejściowe użytkownika powinien nigdy nie należy bezpośrednio powtarzana w odpowiedzi serwera. Zamiast tego, powinny zostać zakodowany przy użyciu <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)
