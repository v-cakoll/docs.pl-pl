---
title: 'Porady: wyświetlanie zlokalizowanych informacji daty i godziny dla użytkowników sieci Web'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27e9306164e3d0e008f38f2d94e1f9c11c0d7d3d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871715"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Porady: wyświetlanie zlokalizowanych informacji daty i godziny dla użytkowników sieci Web
Ponieważ strony sieci Web może być wyświetlany w dowolnym miejscu na świecie, operacje analizy i formatowanie wartości daty i godziny, nie należy polegać na format domyślny (czyli w większości przypadków format kultury lokalnego serwera sieci Web) podczas interakcji z użytkownikiem. Zamiast tego formularzy sieci Web, Obsługa daty i godziny ciągi wprowadzane przez użytkownika, które należy przeanalizować ciągi przy użyciu preferowanej kultury użytkownika. Podobnie dane daty i godziny, powinna być wyświetlana dla użytkownika w formacie, który jest zgodny z kultury użytkownika. W tym temacie pokazano, jak to zrobić.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Ciągi danych wejściowych przez użytkownika, można przeanalizować daty i godziny  
  
1.  Określić, czy tablica ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwość jest wypełnione. Jeśli nie jest, przejdź do kroku 6.  
  
2.  Jeśli ciąg tablica zwrócona przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest wypełniana, pobrać jej pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowanego języka i regionu użytkownika.  
  
3.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowanego kultury poprzez wywołanie <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
4.  Wywołaj opcję `TryParse` lub `Parse` metody <xref:System.DateTime> lub <xref:System.DateTimeOffset> typu próby konwersji. Używanie przeciążenia `TryParse` lub `Parse` metody z `provider` parametru i przekazywać je w jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiekt utworzony w kroku 3.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiekt utworzony w kroku 3.  
  
5.  Jeśli konwersja nie powiedzie się, powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
6.  Jeśli konwersja nadal kończy się niepowodzeniem lub tablicę ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu niezmiennej kultury, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Aby przeanalizować lokalnego datę i godzinę żądanie użytkownika  
  
1.  Dodaj <xref:System.Web.UI.WebControls.HiddenField> formantu do formularza sieci Web.  
  
2.  Utwórz funkcję języka JavaScript, która obsługuje `onClick` zdarzenia `Submit` przycisku, pisząc bieżącej daty i godziny oraz przesunięcie lokalnej strefy czasowej z uniwersalnego czasu koordynowanego (UTC) do <xref:System.Web.UI.WebControls.HiddenField.Value%2A> właściwości. Użyj ogranicznika (np. średnikiem) do oddzielenia dwa składniki ciągu.  
  
3.  Za pomocą formularza sieci Web <xref:System.Web.UI.Control.PreRender> zdarzenie, aby wstawić funkcji do HTML strumienia wyjściowego, przekazując tekst skryptu <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> metody.  
  
4.  Połącz program obsługi zdarzeń do `Submit` przycisku `onClick` zdarzeń, podając nazwę funkcji JavaScript do `OnClientClick` atrybutu `Submit` przycisku.  
  
5.  Utwórz procedurę obsługi dla `Submit` przycisku <xref:System.Web.UI.WebControls.Button.Click> zdarzeń.  
  
6.  W obsłudze zdarzeń należy określić, czy tablica ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwość jest wypełnione. Jeśli nie jest, przejdź do kroku 14.  
  
7.  Jeśli ciąg tablica zwrócona przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest wypełniana, pobrać jej pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowanego języka i regionu użytkownika.  
  
8.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowanego kultury poprzez wywołanie <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
9. Przekazać ciąg przypisane do <xref:System.Web.UI.WebControls.HiddenField.Value%2A> właściwość <xref:System.String.Split%2A> metodę, aby ciąg reprezentujący użytkownika lokalnego daty i godziny oraz reprezentację ciągu przesunięcie strefy czasu lokalnego użytkownika są przechowywane w osobnej tablicy elementów.  
  
10. Wywołaj opcję <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> metodę, aby przekonwertować datę i godzinę żądanie użytkownika <xref:System.DateTime> wartość. Użyj przeciążenia metody `provider` parametru i przekazywać je w jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiekt utworzony w kroku 8.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiekt utworzony w kroku 8.  
  
11. W przypadku niepowodzenia operacji analizy w kroku 10 przejdź do kroku 13. W przeciwnym razie wywołanie <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> metodę, aby przekonwertować ciąg reprezentujący przesunięcia strefy czasowej użytkownika na liczbę całkowitą.  
  
12. Utwórz wystąpienie <xref:System.DateTimeOffset> reprezentujący czasem lokalnym użytkownika, wywołując <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktora.  
  
13. W przypadku niepowodzenia konwersji w kroku 10, powtórz kroki od 7 do 12 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
14. Jeśli konwersja nadal kończy się niepowodzeniem lub tablicę ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu niezmiennej kultury, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Następnie powtórz kroki od 7 do 12.  
  
 Wynik jest <xref:System.DateTimeOffset> obiekt, który odpowiada czasowi lokalnemu użytkownika strony sieci Web. Następnie możesz określić równoważne UTC, wywołując <xref:System.DateTimeOffset.ToUniversalTime%2A> metody. Możesz również określić równoważne datę i godzinę na serwerze sieci Web, wywołując <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody i przekazywanie wartości elementu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jak dla strefy czasowej można przekonwertować czasu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera zarówno do źródła HTML, jak i kod do formularza sieci Web platformy ASP.NET, które prosi użytkownika o wprowadzanie wartości daty i godziny. Skrypt po stronie klienta zapisuje także informacje na temat lokalne daty i godziny żądanie użytkownika i przesunięcie strefy czasowej użytkownika względem czasu UTC ukryte pole. Te informacje, następnie jest analizowany przez serwer, który zwraca stronę sieci Web, która wyświetla dane wejściowe użytkownika. Wyświetla także data i godzina żądanie użytkownika przy użyciu czasu lokalnego użytkownika, czas na serwerze i czasem UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Skrypt po stronie klienta wywołuje kod JavaScript `toLocaleString` metody. Daje to ciąg, który następuje po Konwencji formatowania ustawień regionalnych użytkownika, który jest bardziej prawdopodobne go pomyślnie przeanalizować na serwerze.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Właściwość pochodzą z nazwy kultury, które są zawarte w `Accept-Language` nagłówki dołączone w żądaniu HTTP. Jednak nie wszystkie przeglądarki: `Accept-Language` nagłówków żądań i użytkowników można również pominąć nagłówki całkowicie. Dzięki temu istotne dla kultury rezerwowej podczas analizowania danych wejściowych użytkownika. Zazwyczaj rezerwowego kultury jest kulturą niezmienną zwróconą przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy mogą także podać programu Internet Explorer z nazwami kultur ich dane wejściowe w polu tekstowym, co powoduje utworzenie możliwości nazwy kultury jest nieprawidłowy. Dzięki temu można użyć obsługi wyjątków, podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu.  
  
 Podczas pobierania z żądania HTTP przesłane przez program Internet Explorer <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablicy jest wypełniana w kolejności preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę kultury/region podstawowy użytkownika. Jeśli tablica zawiera dodatkowe elementy, Internet Explorer według własnego uznania przypisze je specyfikator jakości jest oddzielone od nazwy kultury średnikiem. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołuje <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktora z jego `useUserOverride` parametr `false` do tworzenia nowego <xref:System.Globalization.CultureInfo> obiektu. Dzięki temu, jeśli nazwa kultury jest domyślną nazwę kultury na serwerze, nowe <xref:System.Globalization.CultureInfo> obiekt utworzony przez konstruktora klasy zawiera ustawienia domyślne, kultury i nie będzie odzwierciedlał wszelkie ustawienia zastąpić przy użyciu serwera  **Regionalne i opcji języka** aplikacji. Wartości z dowolnym zgodnym z przesłoniętą ustawienia na serwerze prawdopodobnie nie istnieje w systemie użytkownika lub zostaną odzwierciedlone w danych wejściowych użytkownika.  
  
 Ponieważ w tym przykładzie analizuje dwóch ciągów reprezentujących daty i godziny (jeden zestaw danych wejściowych przez użytkownika, inne przechowywane, aby pole ukryte), definiuje możliwe <xref:System.Globalization.CultureInfo> obiektów, które mogą być wymagane z wyprzedzeniem. Tworzy tablicę <xref:System.Globalization.CultureInfo> obiektów, które jest większa niż liczba elementów zwróconych przez jedną <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwości. Następnie tworzy <xref:System.Globalization.CultureInfo> obiekt dla każdego ciągu język/region, a także tworzy <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Twój kod może wywołać albo <xref:System.DateTime.Parse%2A> lub <xref:System.DateTime.TryParse%2A> metody konwersji użytkownika reprezentacją ciągu daty i czasu <xref:System.DateTime> wartość. Wielokrotnego wywołania metody parse może być wymagane dla pojedynczej operacji analizy. W rezultacie <xref:System.DateTime.TryParse%2A> lepszym rozwiązaniem jest użycie, ponieważ zwraca `false` w przypadku niepowodzenia operacji analizy. Z kolei obsługi wyjątków dopuszczalnych, które mogą być generowane przez <xref:System.DateTime.Parse%2A> metoda może być bardzo kosztowna oferty w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować ten kod, Utwórz [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony sieci Web bez związanym z kodem. Następnie skopiuj przykład do strony sieci Web, dzięki czemu zastępuje istniejący kod. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Strony sieci Web może zawierać następujących formantów:  
  
-   A <xref:System.Web.UI.WebControls.Label> formant, który nie ma odwołania w kodzie. Ustaw jego <xref:System.Web.UI.WebControls.TextBox.Text%2A> właściwość "Wprowadź liczbę:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> formantu o nazwie `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> formantu o nazwie `OKButton`. Ustaw jego <xref:System.Web.UI.WebControls.Button.Text%2A> właściwość "OK".  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> formantu o nazwie `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wprowadzanie skryptów do strumienia HTML, dane wejściowe użytkownika powinno nigdy nie można bezpośrednio powtarzane w odpowiedzi z serwera. Zamiast tego powinien być kodowany za pomocą <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
- [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)
