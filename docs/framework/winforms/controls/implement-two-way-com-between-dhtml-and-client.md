---
title: 'Porady: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta'
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
ms.openlocfilehash: 90f4f4500514e2e3d7a231861c0cf4b3d453a4c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Porady: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta
Można użyć <xref:System.Windows.Forms.WebBrowser> formantu, aby dodać istniejące dynamiczny kod aplikacji sieci Web HTML (DHTML) aplikacjom klienckim formularzy systemu Windows. Jest to przydatne, gdy zainwestowały czasu znaczących programowania do tworzenia opartych na DHTML — formanty i chcesz korzystać z funkcji interfejsu użytkownika sformatowanego formularzy systemu Windows bez konieczności ponownego zapisania istniejącego kodu.  
  
 <xref:System.Windows.Forms.WebBrowser> Kontrola umożliwia Implementowanie dwukierunkowej komunikacji między kod klienta aplikacji i skryptów kodu strony sieci Web za pomocą <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> i <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości. Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> , aby formantów sieci Web programu blend bezproblemowo z innych kontrolek w formularzu aplikacji, ukrywanie ich realizacji DHTML. Na bezproblemowo blend formantów, formatu strony wyświetlany tak, aby jego kolor tła i styl wizualny zgodne pozostałej części formularza i użyj <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, i <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, aby wyłączyć funkcje standardowej przeglądarki.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Aby osadzić w aplikacji Windows Forms DHTML  
  
1.  Ustaw <xref:System.Windows.Forms.WebBrowser> formantu <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików na go.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlanie menu skrótów po kliknięciu go.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> formantu z odpowiada klawiszy skrótu.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Ustaw <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> właściwości w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.  
  
     W poniższym kodzie użyto samej klasy formularza dla obiekt skryptów.  
  
    > [!NOTE]
    >  Składnik modelu COM (Object) musi mieć możliwość dostępu do obiektu skryptów. Aby formularz był widoczny dla modelu COM, należy dodać <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu do własnej klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Implementuje publicznej właściwości i metody w kodzie aplikacji, który będzie używany przez kod skryptu.  
  
     Na przykład jeśli używasz klasy formularza dla obiekt skryptów, Dodaj następujący kod do klasy formularza.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Użyj `window.external` obiektu w kodzie skryptu dostęp do publicznej właściwości i metod określonego obiektu.  
  
     Poniższy kod HTML pokazano, jak wywołać metody dla obiekt skryptów w kliknij przycisk. Skopiuj ten kod do elementu BODY dokumentu HTML, które zostały załadowane, za pomocą formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  Implementowanie funkcji w kodzie skryptu, który będzie używany przez kod aplikacji.  
  
     Następujący element HTML skryptu zawiera funkcję przykład. Skopiuj ten kod do elementu HEAD dokumentu HTML, które zostały załadowane, za pomocą formantu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody lub przypisać formantu <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Użyj <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości dostępu do kodu skryptu w kodzie aplikacji klienta.  
  
     Na przykład, Dodaj następujący kod do przycisku <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Po zakończeniu debugowania programu DHTML Ustawianie formantu <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwości `true` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli przy wyświetlaniu komunikatów o błędach dla problemów kodu skryptu.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompletny kod zawiera aplikacji demonstracyjnej, która służy do zrozumienia tej funkcji. Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolować za pośrednictwem <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości zamiast ładowana z pliku HTML.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten kod wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [WebBrowser, kontrolka](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
