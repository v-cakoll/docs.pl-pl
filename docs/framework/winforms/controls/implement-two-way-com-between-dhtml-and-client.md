---
title: 'Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: cf1391e88c03095e0851d75ae6d50f8e809d13e9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295617"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta
Możesz użyć <xref:System.Windows.Forms.WebBrowser> formantu, aby dodać istniejący dynamiczny kod aplikacji sieci Web HTML (DHTML) do aplikacji klienta Windows Forms. Jest to przydatne, gdy zainwestowali czas opracowywania znaczące w tworzeniu kontrolek na podstawie DHTML i chcesz korzystać z zalet użytkownikowi możliwości interfejsu Windows Forms bez konieczności ponownego zapisania istniejącego kodu.  
  
 <xref:System.Windows.Forms.WebBrowser> Kontrola umożliwia Implementowanie dwukierunkowej komunikacji między kodu aplikacji klienckich i skryptów kodu strony sieci Web za pomocą <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> i <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości. Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> kontrolki formantów sieci Web programu blend bezproblemowo z innymi formantami na formularzu aplikacji ukrywanie ich implementacji DHTML. Aby dopasować bezproblemowo formanty, formatowanie stronę wyświetlaną, aby jej kolor tła i stylu wizualnego dopasowania pozostałej części formularza i używać <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, i <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, aby wyłączyć funkcje standardową przeglądarką.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Aby osadzić DHTML w aplikacji Windows Forms  
  
1. Ustaw <xref:System.Windows.Forms.WebBrowser> kontrolki <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` aby zapobiec <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików upuszczone na go.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2. Ustaw dla formantu <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie jego menu skrótów, gdy użytkownik kliknie prawym przyciskiem myszy go.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3. Ustaw dla formantu <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli ją klawiszy skrótów.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4. Ustaw <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> właściwość w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.  
  
     W poniższym kodzie użyto samej klasy formularza dla skryptów obiektu.  
  
    > [!NOTE]
    >  Component Object Model (COM) musi mieć możliwość dostępu do obiektu skryptów. Aby formularz był widoczny dla modelu COM, należy dodać <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów do klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5. Implementuje właściwości publiczne lub metody w kodzie aplikacji, która będzie używana w kodzie skryptu.  
  
     Na przykład jeśli używasz klasy formularza dla skryptów obiektu, Dodaj następujący kod do klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6. Użyj `window.external` obiektu w kodzie skryptu do publicznej właściwości i metody określonego obiektu.  
  
     Poniższy kod HTML przedstawia sposób wywołania metody wobec obiektu skryptów od kliknięcia przycisku. Skopiuj ten kod do elementu BODY dokumentu HTML, który należy załadować przy użyciu formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7. Implementowanie funkcji w kodzie skryptu, który będzie używany w kodzie aplikacji.  
  
     Następujący element HTML skrypt zawiera przykład funkcja. Skopiuj ten kod w element główny dokumentu HTML, który należy załadować przy użyciu formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8. Użyj <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości dostępu do kodu skryptu w kodzie aplikacji klienta.  
  
     Na przykład, Dodaj następujący kod do przycisku <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Po zakończeniu debugowania usługi DHTML ustawić <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwości `true` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie komunikatów o błędach dla problemów kodu skryptu.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompletny kod zapewnia aplikacji demonstracyjnych, która umożliwia zrozumienie tej funkcji. Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolować za pośrednictwem <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości zamiast ładowana z pliku HTML.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten kod wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [WebBrowser — Formant](webbrowser-control-windows-forms.md)
