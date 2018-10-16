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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663f9d88315f396b187cca874c930179f1dea523
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349140"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Porady: konwertowanie liczbowych danych wejściowych użytkownika na liczby w formantach sieci Web
Ponieważ strony sieci Web może być wyświetlany w dowolnym miejscu na świecie, użytkownicy można wpisać dane liczbowe do <xref:System.Web.UI.WebControls.TextBox> formantu w niemal nieograniczoną liczbę formatów. W rezultacie jest bardzo ważne określić ustawienia regionalne i kultury użytkownika strony sieci Web. Podczas analizy danych wejściowych użytkownika, można użyć konwencji formatowania, zdefiniowane przez użytkownika ustawień regionalnych i kultur.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Aby konwertowanie liczbowych danych wejściowych z formantu sieci Web w polu tekstowym na liczbę  
  
1.  Określić, czy tablica ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwość jest wypełnione. Jeśli nie jest, przejdź do kroku 6.  
  
2.  Jeśli ciąg tablica zwrócona przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest wypełniana, pobrać jej pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowanego języka i regionu użytkownika.  
  
3.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowanego kultury poprzez wywołanie <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
4.  Wywołaj opcję `TryParse` lub `Parse` wejściowych do metody typu liczbowego, który chcesz przekonwertować użytkownika. Używanie przeciążenia `TryParse` lub `Parse` metody z `provider` parametru i przekazywać je w jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiekt utworzony w kroku 3.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.NumberFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiekt utworzony w kroku 3.  
  
5.  Jeśli konwersja nie powiedzie się, powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
6.  Jeśli konwersja nadal kończy się niepowodzeniem lub tablicę ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu niezmiennej kultury, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia kompletny osobna strona kodu formularza sieci Web, która prosi użytkownika o podanie wartości numerycznej w <xref:System.Web.UI.WebControls.TextBox> kontroli i konwertuje ją na liczbę. Ta liczba jest następnie dwukrotnie i wyświetlane przy użyciu tego samego reguły formatowania jako oryginalne dane wejściowe.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Właściwość pochodzą z nazwy kultury, które są zawarte w `Accept-Language` nagłówki dołączone w żądaniu HTTP. Jednak nie wszystkie przeglądarki: `Accept-Language` nagłówków żądań i użytkowników można również pominąć nagłówki całkowicie. Dzięki temu istotne dla kultury rezerwowej podczas analizowania danych wejściowych użytkownika. Zazwyczaj rezerwowego kultury jest kulturą niezmienną zwróconą przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy mogą także podać programu Internet Explorer z nazwami kultur ich dane wejściowe w polu tekstowym, co powoduje utworzenie możliwości nazwy kultury jest nieprawidłowy. Dzięki temu można użyć obsługi wyjątków, podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu.  
  
 Podczas pobierania z żądania HTTP przesłane przez program Internet Explorer <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablicy jest wypełniana w kolejności preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę kultury/region podstawowy użytkownika. Jeśli tablica zawiera dodatkowe elementy, Internet Explorer według własnego uznania przypisze je specyfikator jakości jest oddzielone od nazwy kultury średnikiem. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołuje <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktora z jego `useUserOverride` parametr `false` do tworzenia nowego <xref:System.Globalization.CultureInfo> obiektu. Dzięki temu, jeśli nazwa kultury jest domyślną nazwę kultury na serwerze, nowe <xref:System.Globalization.CultureInfo> obiekt utworzony przez konstruktora klasy zawiera ustawienia domyślne, kultury i nie będzie odzwierciedlał wszelkie ustawienia zastąpić przy użyciu serwera  **Regionalne i opcji języka** aplikacji. Wartości z dowolnym zgodnym z przesłoniętą ustawienia na serwerze prawdopodobnie nie istnieje w systemie użytkownika lub zostaną odzwierciedlone w danych wejściowych użytkownika.  
  
 Twój kod może wywołać albo `Parse` lub `TryParse` metody typu liczbowego, który wejściowych użytkownika zostaną przekonwertowane na. Wielokrotnego wywołania metody parse może być wymagane dla pojedynczej operacji analizy. W rezultacie `TryParse` metody jest lepszym rozwiązaniem, ponieważ zwraca `false` w przypadku niepowodzenia operacji analizy. Z kolei obsługi wyjątków dopuszczalnych, które mogą być generowane przez `Parse` metoda może być bardzo kosztowna oferty w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] osobna strona kodu, tak aby znajdował zastępuje istniejący kod. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Strony sieci Web może zawierać następujących formantów:  
  
-   A <xref:System.Web.UI.WebControls.Label> formant, który nie ma odwołania w kodzie. Ustaw jego <xref:System.Web.UI.WebControls.TextBox.Text%2A> właściwość "Wprowadź liczbę:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> formantu o nazwie `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> formantu o nazwie `OKButton`. Ustaw jego <xref:System.Web.UI.WebControls.Button.Text%2A> właściwość "OK".  
  
 Zmień nazwę klasy z `NumericUserInput` na nazwę klasy, która jest zdefiniowana przez `Inherits` atrybutu [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony `Page` dyrektywy. Zmień nazwę `NumericInput` odwołanie do nazwy zdefiniowane przez obiekt `id` atrybutu [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony `form` tagu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wprowadzanie skryptów do strumienia HTML, dane wejściowe użytkownika powinno nigdy nie można bezpośrednio powtarzane w odpowiedzi z serwera. Zamiast tego powinien być kodowany za pomocą <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)
