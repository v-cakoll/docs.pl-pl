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
dev_langs:
- csharp
- vb
ms.openlocfilehash: 51142a168aba4408e6ce550a032960c4df6c3ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138732"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Porady: wyświetlanie zlokalizowanych informacji daty i godziny dla użytkowników sieci Web
Ze względu na to, że strona sieci Web może być wyświetlana w dowolnym miejscu na świecie, operacje, które analizują i sformatują wartości daty i godziny nie mogą opierać się na domyślnym formacie (najczęściej jest to format kultury lokalnej serwera sieci Web) podczas współpracy z użytkownikiem. Zamiast tego formularze sieci Web, które obsługują dane daty i godziny przez użytkownika, powinny analizować ciągi przy użyciu preferowanej kultury użytkownika. Podobnie dane daty i godziny powinny być wyświetlane użytkownikowi w formacie, który jest zgodny z kulturą użytkownika. W tym temacie pokazano, jak to zrobić.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Aby przeanalizować ciągi daty i godziny wprowadzane przez użytkownika  
  
1. Ustal, czy tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> jest wypełniana. Jeśli tak nie jest, przejdź do kroku 6.  
  
2. Jeśli zostanie wypełniona tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>, pobierz jej pierwszy element. Pierwszy element wskazuje domyślny lub preferowany język i region użytkownika.  
  
3. Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę preferowaną przez użytkownika przez wywołanie konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Wywołaj `TryParse` lub metodę `Parse` typu <xref:System.DateTime> lub <xref:System.DateTimeOffset>, aby wypróbować konwersję. Użyj przeciążenia `TryParse` lub metody `Parse` z parametrem `provider` i przekaż go jedną z następujących czynności:  
  
    - Obiekt <xref:System.Globalization.CultureInfo> utworzony w kroku 3.  
  
    - Obiekt <xref:System.Globalization.DateTimeFormatInfo>, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> obiektu <xref:System.Globalization.CultureInfo> utworzonego w kroku 3.  
  
5. Jeśli konwersja nie powiedzie się, powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwracanej przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Jeśli konwersja nadal kończy się niepowodzeniem lub jeśli tablica ciągów zwracana przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A> jest pusta, Przeanalizuj ciąg przy użyciu niezmiennej kultury, która jest zwracana przez właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Aby przeanalizować lokalną datę i godzinę żądania użytkownika  
  
1. Dodaj kontrolkę <xref:System.Web.UI.WebControls.HiddenField> do formularza sieci Web.  
  
2. Utwórz funkcję języka JavaScript, która obsługuje zdarzenie `onClick` przycisku `Submit` przez zapisanie bieżącej daty i godziny i przesunięcia lokalnej strefy czasowej od skoordynowanego czasu uniwersalnego (UTC) do właściwości <xref:System.Web.UI.WebControls.HiddenField.Value%2A>. Użyj ogranicznika (takiego jak średnik), aby oddzielić dwa składniki ciągu.  
  
3. Użyj zdarzenia <xref:System.Web.UI.Control.PreRender> formularza sieci Web, aby wstrzyknąć funkcję do strumienia wyjściowego HTML przez przekazanie tekstu skryptu do metody <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Połącz procedurę obsługi zdarzeń ze zdarzeniem `onClick` `Submit` przycisku, podając nazwę funkcji JavaScript do atrybutu `OnClientClick` przycisku `Submit`.  
  
5. Utwórz procedurę obsługi dla zdarzenia <xref:System.Web.UI.WebControls.Button.Click> `Submit` przycisku.  
  
6. W programie obsługi zdarzeń Ustal, czy tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> jest wypełniana. Jeśli tak nie jest, przejdź do kroku 14.  
  
7. Jeśli zostanie wypełniona tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>, pobierz jej pierwszy element. Pierwszy element wskazuje domyślny lub preferowany język i region użytkownika.  
  
8. Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę preferowaną przez użytkownika przez wywołanie konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
9. Przekaż ciąg przypisany do właściwości <xref:System.Web.UI.WebControls.HiddenField.Value%2A> do metody <xref:System.String.Split%2A>, aby przechowywać ciąg reprezentujący lokalną datę i godzinę użytkownika oraz ciąg reprezentujący przesunięcia lokalnej strefy czasowej użytkownika w oddzielnych elementach tablicy.  
  
10. Wywołaj metodę <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType>, aby skonwertować datę i godzinę żądania użytkownika do wartości <xref:System.DateTime>. Użyj przeciążenia metody z parametrem `provider` i przekaż go jedną z następujących wartości:  
  
    - Obiekt <xref:System.Globalization.CultureInfo> utworzony w kroku 8.  
  
    - Obiekt <xref:System.Globalization.DateTimeFormatInfo>, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> obiektu <xref:System.Globalization.CultureInfo> utworzonego w kroku 8.  
  
11. Jeśli operacja analizy w kroku 10 zakończy się niepowodzeniem, przejdź do kroku 13. W przeciwnym razie Wywołaj metodę <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType>, aby przekonwertować ciąg reprezentujący przesunięcia strefy czasowej użytkownika na liczbę całkowitą.  
  
12. Utwórz wystąpienie <xref:System.DateTimeOffset>, które reprezentuje czas lokalny użytkownika przez wywołanie konstruktora <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>.  
  
13. Jeśli konwersja w kroku 10 nie powiedzie się, powtórz kroki od 7 do 12 dla każdego pozostałego elementu w tablicy ciągów zwracanej przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
14. Jeśli konwersja nadal kończy się niepowodzeniem lub jeśli tablica ciągów zwracana przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A> jest pusta, Przeanalizuj ciąg przy użyciu niezmiennej kultury, która jest zwracana przez właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Następnie powtórz kroki od 7 do 12.  
  
 Wynik jest obiektem <xref:System.DateTimeOffset>, który reprezentuje czas lokalny użytkownika strony sieci Web. Następnie można określić odpowiedni czas UTC, wywołując metodę <xref:System.DateTimeOffset.ToUniversalTime%2A>. Możesz również określić równoważną datę i godzinę na serwerze sieci Web, wywołując metodę <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> i przekazując wartość <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jako strefę czasową do przekonwertowania czasu na.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera zarówno źródło HTML, jak i kod formularza sieci Web ASP.NET, który prosi użytkownika o wprowadzenie wartości daty i godziny. Skrypt po stronie klienta zapisuje również informacje o lokalnej dacie i godzinie żądania użytkownika oraz o przesunięciu strefy czasowej użytkownika z czasu UTC do ukrytego pola. Te informacje są następnie analizowane przez serwer, który zwraca stronę sieci Web, która wyświetla dane wejściowe użytkownika. Wyświetla również datę i godzinę żądania użytkownika przy użyciu czasu lokalnego użytkownika, godziny na serwerze i czasu UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Skrypt po stronie klienta wywołuje metodę `toLocaleString` JavaScript. Spowoduje to utworzenie ciągu zgodnego z konwencjami formatowania ustawień regionalnych użytkownika, co jest bardziej podobne do pomyślnego przeanalizowania na serwerze.  
  
 Właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> jest wypełniana nazwami kultur, które znajdują się w `Accept-Language` nagłówkach zawartych w żądaniu HTTP. Jednak nie wszystkie przeglądarki zawierają nagłówki `Accept-Language` w swoich żądaniach, a użytkownicy mogą również całkowicie pominąć nagłówki. Sprawia to, że ważne jest kulturę rezerwową podczas analizowania danych wejściowych użytkownika. Zwykle kultura powrotu jest kulturą niezmienną zwracaną przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy mogą również udostępnić program Internet Explorer z nazwami kultur, które są wprowadzane w polu tekstowym, co tworzy możliwość, że nazwy kultur mogą być nieprawidłowe. Jest to ważne, aby używać obsługi wyjątków podczas tworzenia wystąpienia obiektu <xref:System.Globalization.CultureInfo>.  
  
 Po pobraniu z żądania HTTP przesłanego przez Internet Explorer, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablica jest wypełniana według preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę głównej kultury/regionu użytkownika. Jeśli tablica zawiera jakiekolwiek dodatkowe elementy, program Internet Explorer arbitralnie przypisze im specyfikator jakości, który jest rozdzielany od nazwy kultury średnikami. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołuje konstruktora <xref:System.Globalization.CultureInfo.%23ctor%2A> z jego parametrem `useUserOverride` ustawionym na `false`, aby utworzyć nowy obiekt <xref:System.Globalization.CultureInfo>. Gwarantuje to, że jeśli nazwa kultury jest domyślną nazwą kultury na serwerze, nowy obiekt <xref:System.Globalization.CultureInfo> utworzony przez konstruktora klasy zawiera domyślne ustawienia kultury i nie uwzględnia żadnych ustawień przesłoniętych przez użycie **regionalnego serwera i Aplikacja opcji języka** . Wartości z dowolnych przesłoniętych ustawień na serwerze prawdopodobnie nie istnieją w systemie użytkownika lub zostaną odzwierciedlone w danych wejściowych użytkownika.  
  
 Ponieważ ten przykład analizuje dwie reprezentacje ciągów daty i godziny (jedno dane wejściowe przez użytkownika, drugie przechowywane do pola ukrytego), definiuje możliwe <xref:System.Globalization.CultureInfo> obiektów, które mogą być wymagane z góry. Tworzy tablicę <xref:System.Globalization.CultureInfo> obiektów, która jest większa niż liczba elementów zwracanych przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Następnie tworzy wystąpienie obiektu <xref:System.Globalization.CultureInfo> dla każdego ciągu języka/regionu, a także tworzy wystąpienie <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Kod może wywoływać <xref:System.DateTime.Parse%2A> lub metodę <xref:System.DateTime.TryParse%2A>, aby przekonwertować ciąg reprezentujący datę i godzinę użytkownika na wartość <xref:System.DateTime>. Do pojedynczej operacji analizowania mogą być wymagane powtórzone wywołania metody Parse. W efekcie Metoda <xref:System.DateTime.TryParse%2A> jest lepsza, ponieważ zwraca `false` w przypadku niepowodzenia operacji analizy. W przeciwieństwie do obsługi powtarzających się wyjątków, które mogą być zgłaszane przez metodę <xref:System.DateTime.Parse%2A> może być bardzo kosztowną pozycją w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, Utwórz stronę sieci Web ASP.NET bez kodu. Następnie skopiuj przykład na stronę sieci Web, aby zastąpić cały istniejący kod. Strona sieci Web ASP.NET powinna zawierać następujące kontrolki:  
  
- Kontrolka <xref:System.Web.UI.WebControls.Label>, do której nie odwołuje się kod. Ustaw jej Właściwość <xref:System.Web.UI.WebControls.TextBox.Text%2A> na wartość "Wprowadź liczbę:".  
  
- Kontrolka <xref:System.Web.UI.WebControls.TextBox> o nazwie `DateString`.  
  
- Kontrolka <xref:System.Web.UI.WebControls.Button> o nazwie `OKButton`. Ustaw jej Właściwość <xref:System.Web.UI.WebControls.Button.Text%2A> na wartość "OK".  
  
- Kontrolka <xref:System.Web.UI.WebControls.HiddenField> o nazwie `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wstrzyknięcie skryptu do strumienia HTML, dane wejściowe użytkownika nigdy nie powinny być przywracane bezpośrednio w odpowiedzi serwera. Zamiast tego należy je zakodować przy użyciu metody <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)
