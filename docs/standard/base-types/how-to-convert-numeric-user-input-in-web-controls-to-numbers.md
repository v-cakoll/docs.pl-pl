---
title: 'Porady: konwertowanie liczbowych danych wejściowych użytkownika na liczby w formantach sieci Web'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
ms.openlocfilehash: 78ba284ad2e75b39c0fb1001b0f65b48c519dbb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140107"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Porady: konwertowanie liczbowych danych wejściowych użytkownika na liczby w formantach sieci Web
Ze względu na to, że strona sieci Web może być wyświetlana w dowolnym miejscu na świecie, użytkownicy mogą wprowadzać dane liczbowe do kontrolki <xref:System.Web.UI.WebControls.TextBox> w prawie nieograniczonej liczbie formatów. W związku z tym ważne jest, aby określić ustawienia regionalne i kulturę użytkownika strony sieci Web. Podczas analizowania danych wejściowych użytkownika można zastosować konwencje formatowania zdefiniowane przez ustawienia regionalne i kulturowe użytkownika.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Aby skonwertować liczbowe dane wejściowe z kontrolki TextBox sieci Web na liczbę  
  
1. Ustal, czy tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> jest wypełniana. Jeśli tak nie jest, przejdź do kroku 6.  
  
2. Jeśli zostanie wypełniona tablica ciągów zwrócona przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>, pobierz jej pierwszy element. Pierwszy element wskazuje domyślny lub preferowany język i region użytkownika.  
  
3. Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę preferowaną przez użytkownika przez wywołanie konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Wywołaj metodę `TryParse` lub `Parse` typu liczbowego, do którego chcesz skonwertować dane wejściowe użytkownika. Użyj przeciążenia `TryParse` lub metody `Parse` z parametrem `provider` i przekaż go jedną z następujących czynności:  
  
    - Obiekt <xref:System.Globalization.CultureInfo> utworzony w kroku 3.  
  
    - Obiekt <xref:System.Globalization.NumberFormatInfo>, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.NumberFormat%2A> obiektu <xref:System.Globalization.CultureInfo> utworzonego w kroku 3.  
  
5. Jeśli konwersja nie powiedzie się, powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwracanej przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Jeśli konwersja nadal kończy się niepowodzeniem lub jeśli tablica ciągów zwracana przez właściwość <xref:System.Web.HttpRequest.UserLanguages%2A> jest pusta, Przeanalizuj ciąg przy użyciu niezmiennej kultury, która jest zwracana przez właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest kompletną stroną z kodem dla formularza sieci Web, który prosi użytkownika o wprowadzenie wartości liczbowej w kontrolce <xref:System.Web.UI.WebControls.TextBox> i konwertuje ją na liczbę. Ten numer jest następnie podwojony i wyświetlany przy użyciu tych samych reguł formatowania co oryginalne dane wejściowe.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 Właściwość <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> jest wypełniana nazwami kultur, które znajdują się w `Accept-Language` nagłówkach zawartych w żądaniu HTTP. Jednak nie wszystkie przeglądarki zawierają nagłówki `Accept-Language` w swoich żądaniach, a użytkownicy mogą również całkowicie pominąć nagłówki. Sprawia to, że ważne jest kulturę rezerwową podczas analizowania danych wejściowych użytkownika. Zwykle kultura rezerwowa jest kulturą niezmienną zwracaną przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy mogą również udostępnić program Internet Explorer z nazwami kultur, które są wprowadzane w polu tekstowym, co tworzy możliwość, że nazwy kultur mogą być nieprawidłowe. Jest to ważne, aby używać obsługi wyjątków podczas tworzenia wystąpienia obiektu <xref:System.Globalization.CultureInfo>.  
  
 Po pobraniu z żądania HTTP przesłanego przez Internet Explorer, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablica jest wypełniana według preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę głównej kultury/regionu użytkownika. Jeśli tablica zawiera jakiekolwiek dodatkowe elementy, program Internet Explorer arbitralnie przypisze im specyfikator jakości, który jest rozdzielany od nazwy kultury średnikami. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołuje konstruktora <xref:System.Globalization.CultureInfo.%23ctor%2A> z jego parametrem `useUserOverride` ustawionym na `false`, aby utworzyć nowy obiekt <xref:System.Globalization.CultureInfo>. Gwarantuje to, że jeśli nazwa kultury jest domyślną nazwą kultury na serwerze, nowy obiekt <xref:System.Globalization.CultureInfo> utworzony przez konstruktora klasy zawiera domyślne ustawienia kultury i nie uwzględnia żadnych ustawień przesłoniętych przez użycie **regionalnego serwera i Aplikacja opcji języka** . Wartości z dowolnych przesłoniętych ustawień na serwerze prawdopodobnie nie istnieją w systemie użytkownika lub zostaną odzwierciedlone w danych wejściowych użytkownika.  
  
 Kod może wywoływać `Parse` lub metodę `TryParse` typu liczbowego, do którego zostanie przekonwertowane dane wejściowe użytkownika. Do pojedynczej operacji analizowania mogą być wymagane powtórzone wywołania metody Parse. W efekcie Metoda `TryParse` jest lepsza, ponieważ zwraca `false` w przypadku niepowodzenia operacji analizy. W przeciwieństwie do obsługi powtarzających się wyjątków, które mogą być zgłaszane przez metodę `Parse` może być bardzo kosztowną pozycją w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go do ASP.NETej strony kodowej, aby zastąpić cały istniejący kod. Strona sieci Web ASP.NET powinna zawierać następujące kontrolki:  
  
- Kontrolka <xref:System.Web.UI.WebControls.Label>, do której nie odwołuje się kod. Ustaw jej Właściwość <xref:System.Web.UI.WebControls.TextBox.Text%2A> na wartość "Wprowadź liczbę:".  
  
- Kontrolka <xref:System.Web.UI.WebControls.TextBox> o nazwie `NumericString`.  
  
- Kontrolka <xref:System.Web.UI.WebControls.Button> o nazwie `OKButton`. Ustaw jej Właściwość <xref:System.Web.UI.WebControls.Button.Text%2A> na wartość "OK".  
  
 Zmień nazwę klasy z `NumericUserInput` na nazwę klasy, która jest zdefiniowana przez atrybut `Inherits` dyrektywy `Page` strony ASP.NET. Zmień nazwę odwołania obiektu `NumericInput` na nazwę zdefiniowaną przez atrybut `id` tagu `form` strony ASP.NET.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wstrzyknięcie skryptu do strumienia HTML, dane wejściowe użytkownika nigdy nie powinny być przywracane bezpośrednio w odpowiedzi serwera. Zamiast tego należy je zakodować przy użyciu metody <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)
