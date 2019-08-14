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
ms.openlocfilehash: 45df54b3a590078eff6ddc1197db5b0124663cf5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971922"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML a kodem aplikacji klienta

Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki można dodać istniejący kod aplikacji sieci Web (DHTML) do Windows Forms aplikacji klienckich. Jest to przydatne, gdy zainwestowano znaczący czas projektowania podczas tworzenia formantów opartych na języku DHTML i chcesz korzystać z zaawansowanych możliwości interfejsu użytkownika Windows Forms bez konieczności ponownego zapisywania istniejącego kodu.

Kontrolka umożliwia zaimplementowanie dwukierunkowej komunikacji między kodem aplikacji klienta i kodem skryptowym strony sieci Web <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> za pomocą <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwości i. <xref:System.Windows.Forms.WebBrowser> Ponadto można skonfigurować <xref:System.Windows.Forms.WebBrowser> kontrolkę tak, aby kontrolki sieci Web bezproblemowo mieszają się z innymi kontrolkami w formularzu aplikacji, ukrywając ich implementację DHTML. Aby bezproblemowo mieszać kontrolki, sformatuj wyświetlaną stronę tak, aby jej kolor tła i styl wizualny odpowiadały pozostałej części formularza <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>i Użyj <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwości, i, aby wyłączyć standardowe funkcje przeglądarki.

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Aby osadzić DHTML w aplikacji Windows Forms

1. <xref:System.Windows.Forms.WebBrowser> Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> Właściwośćkontrolki`false` na, aby uniemożliwić kontrolowanie<xref:System.Windows.Forms.WebBrowser> otwierania plików.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. Ustaw <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> właściwość kontrolki na `false` , aby zapobiec <xref:System.Windows.Forms.WebBrowser> wyświetlaniu menu skrótów przez formant po kliknięciu go prawym przyciskiem myszy.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. Ustaw <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> właściwość kontrolki na `false` , aby uniemożliwić <xref:System.Windows.Forms.WebBrowser> sterowanie odpowiedzią na skróty klawiaturowe.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. Ustaw właściwość w Konstruktorze formularza <xref:System.Windows.Forms.Form.Load> lub programie obsługi zdarzeń. <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>

     Poniższy kod używa samej klasy form dla obiektu Scripting.

    > [!NOTE]
    >  Component Object Model (COM) musi być w stanie uzyskać dostęp do obiektu skryptów. Aby formularz był widoczny dla modelu COM, Dodaj <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut do klasy formularza.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. Implementowanie publicznych właściwości lub metod w kodzie aplikacji, który będzie używany przez kod skryptu.

     Na przykład, jeśli używasz klasy form dla obiektu Scripting, Dodaj następujący kod do klasy formularza.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. `window.external` Użyj obiektu w kodzie skryptów, aby uzyskać dostęp do publicznych właściwości i metod określonego obiektu.

     Poniższy kod HTML demonstruje sposób wywołania metody dla obiektu skryptu z kliknięcia przycisku. Skopiuj ten kod do elementu body dokumentu HTML, który jest ładowany przy użyciu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody kontrolki lub przypisanej do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości kontrolki.

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. Zaimplementuj funkcje w kodzie skryptu, który będzie używany przez kod aplikacji.

     Poniższy element skryptu HTML zawiera przykład funkcji. Skopiuj ten kod do elementu nagłówkowego dokumentu HTML, który jest ładowany przy użyciu <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody kontrolki lub przypisanej do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości kontrolki.

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. <xref:System.Windows.Forms.WebBrowser.Document%2A> Użyj właściwości, aby uzyskać dostęp do kodu skryptu z kodu aplikacji klienckiej.

     Na przykład Dodaj następujący kod do programu obsługi zdarzeń przycisku <xref:System.Windows.Forms.Control.Click> .

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. Po zakończeniu debugowania kodu DHTML Ustaw <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> właściwość kontrolki na `true` , aby zapobiec <xref:System.Windows.Forms.WebBrowser> wyświetlaniu przez formant komunikatów o błędach w przypadku problemów z kodem skryptu.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>Przykład

Poniższy pełny kod zawiera przykładową aplikację, której można użyć do zrozumienia tej funkcji. Kod HTML jest ładowany do <xref:System.Windows.Forms.WebBrowser> kontrolki <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> za pośrednictwem właściwości zamiast ładowania z oddzielnego pliku HTML.

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten kod wymaga:

- Odwołania do zestawów system i system. Windows. Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
