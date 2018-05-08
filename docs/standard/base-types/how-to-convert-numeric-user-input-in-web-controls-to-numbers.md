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
ms.openlocfilehash: 24016ea68e17aa66432928c43d1de970fc13a55b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Porady: konwertowanie liczbowych danych wejściowych użytkownika na liczby w formantach sieci Web
Ponieważ strony sieci Web mogą być wyświetlane w dowolnym miejscu w świecie, użytkowników można wprowadzić dane liczbowe w <xref:System.Web.UI.WebControls.TextBox> formantu w praktycznie nieograniczoną liczbę formatów. W związku z tym jest bardzo ważne, aby określić ustawienia regionalne i kultury użytkownika strony sieci Web. Podczas analizy danych wejściowych użytkownika, aby potem stosować Konwencji formatowania zdefiniowany przez użytkownika ustawień regionalnych i kultur.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Aby przekonwertować liczbowa na wejściu za pomocą formantu TextBox sieci Web na liczbę  
  
1.  Określić, czy tablicy ciągów zwracane przez <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> właściwości jest wypełnione. Jeśli nie, przejdź do kroku 6.  
  
2.  Jeśli zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość zostanie wypełnione, pobrać pierwszego elementu. Pierwszy element wskazuje domyślną lub preferowany język i regionu użytkownika.  
  
3.  Utwórz wystąpienie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje użytkownika preferowana przez kultury wywołując <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora.  
  
4.  Wywołaj albo `TryParse` lub `Parse` wejściowych do metody typu liczbowego, który ma zostać przekonwertowany użytkownika. Użyj przeciążenia `TryParse` lub `Parse` metody z `provider` parametru, a następnie przekaż jednej z następujących pozycji:  
  
    -   <xref:System.Globalization.CultureInfo> Obiektu utworzonego w kroku 3.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.NumberFormat%2A> właściwość <xref:System.Globalization.CultureInfo> obiektu utworzonego w kroku 3.  
  
5.  W przypadku niepowodzenia konwersji Powtórz kroki od 2 do 4 dla każdego pozostałego elementu w tablicy ciągów zwrócony przez <xref:System.Web.HttpRequest.UserLanguages%2A> właściwości.  
  
6.  Jeśli nadal niepowodzenia konwersji lub zwrócił tablicę ciągów <xref:System.Web.HttpRequest.UserLanguages%2A> właściwość jest pusta, przeanalizować składni ciągu przy użyciu Niezmienna kultura, która jest zwracana przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest to strona ukończenia kodem formularza sieci Web, z prośbą o wprowadzenie wartości numerycznej w <xref:System.Web.UI.WebControls.TextBox> kontroli i konwertuje ją na liczbę. Ten numer następnie podwójny i wyświetlić przy użyciu tej samej reguły formatowania jako oryginalne dane wejściowe.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Właściwości pochodzą z nazwy kultury, które są zawarte w `Accept-Language` nagłówki uwzględnione w żądaniu HTTP. Jednak nie wszystkie przeglądarki: `Accept-Language` nagłówków żądań i użytkowników można również pominąć nagłówki całkowicie. Dzięki temu należy mieć rezerwowej kultury podczas analizowania danych wejściowych użytkownika. Zazwyczaj rezerwowej kultury jest kulturą niezmienną zwrócony przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Użytkownicy może także udostępnić programu Internet Explorer nazwy kultury one danych wejściowych w polu tekstowym, który tworzy możliwości nazwy kultury jest nieprawidłowy. Dzięki temu można użyć obsługi wyjątków, podczas tworzenia wystąpienia <xref:System.Globalization.CultureInfo> obiektu.  
  
 Po pobraniu z żądania HTTP przesłane przez program Internet Explorer <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tablicy jest wypełniana w kolejności preferencji użytkownika. Pierwszy element w tablicy zawiera nazwę kultury/regionie podstawowym użytkownika. Jeśli tablica zawiera dodatkowe elementy, Internet Explorer arbitralnie przypisze specyfikator jakości Rozdzielana średnikami z nazwy kultury. Na przykład wpis dla kultury fr-FR może mieć postać `fr-FR;q=0.7`.  
  
 Przykład wywołania <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktora z jego `useUserOverride` ustawiona `false` do tworzenia nowego <xref:System.Globalization.CultureInfo> obiektu. Dzięki temu, jeśli nazwa kultury jest domyślną nazwę kultury na serwerze, nowe <xref:System.Globalization.CultureInfo> obiektu utworzonego przez konstruktora klasy zawiera ustawienia domyślne, kultury i nie odzwierciedla żadnych ustawień zastąpiona przy użyciu serwera  **Regionalne i opcje języka** aplikacji. Wartości z wszelkich przesłoniętych ustawienia na serwerze prawdopodobnie nie istnieje w systemie lub w danych wejściowych użytkownika.  
  
 Kod może wywoływać albo `Parse` lub `TryParse` metody typu liczbowego danych wejściowych użytkownika zostanie przekonwertowany na. Powtarzane wywołania metody parse może być wymagane dla pojedynczej operacji analizy. W związku z tym `TryParse` metoda jest lepsze, ponieważ zwraca ono `false` Jeśli operacja analizy nie powiedzie się. Z kolei obsługi powtarzane wyjątki, które mogą być zgłaszany przez `Parse` metoda może być bardzo kosztowna oferty w aplikacji sieci Web.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] CodeBehind strony, którego nie zastępuje istniejący kod. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Strona sieci Web powinna zawierać następujące sterowniki:  
  
-   A <xref:System.Web.UI.WebControls.Label> kontroli, która nie odwołuje się do kodu. Ustaw jego <xref:System.Web.UI.WebControls.TextBox.Text%2A> dla właściwości "Wprowadź liczbę z zakresu:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> formantu o nazwie `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> formantu o nazwie `OKButton`. Ustaw jego <xref:System.Web.UI.WebControls.Button.Text%2A> dla właściwości "OK".  
  
 Zmień nazwę klasy z `NumericUserInput` na nazwę klasy, która jest zdefiniowana przez `Inherits` atrybutu [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony `Page` dyrektywy. Zmień nazwę `NumericInput` odwołanie do nazwy zdefiniowane przez obiekt `id` atrybutu [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony `form` tagu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uniemożliwić użytkownikowi wstrzykiwania skryptu do strumienia HTML, dane wejściowe użytkownika powinien nigdy nie należy bezpośrednio powtarzana w odpowiedzi serwera. Zamiast tego, powinny zostać zakodowany przy użyciu <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)
