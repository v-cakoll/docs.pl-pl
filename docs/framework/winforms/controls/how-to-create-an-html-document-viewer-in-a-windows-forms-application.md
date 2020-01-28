---
title: Tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732847"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Porady: tworzenie przeglądarki dokumentów HTML w aplikacji formularzy systemu Windows
Za pomocą kontrolki <xref:System.Windows.Forms.WebBrowser> można wyświetlać i drukować dokumenty HTML bez podawania pełnej funkcjonalności przeglądarki internetowej. Jest to przydatne, gdy chcesz korzystać z funkcji formatowania HTML, ale nie chcesz, aby użytkownicy ładowały dowolne strony sieci Web, które mogą zawierać niezaufane formanty sieci Web lub potencjalnie złośliwy kod skryptu. Może zajść potrzeba ograniczenia możliwości kontroli <xref:System.Windows.Forms.WebBrowser> w ten sposób, na przykład w celu użycia jej jako przeglądarki poczty e-mail w formacie HTML lub zapewnienia pomocy w formacie HTML w aplikacji.  
  
### <a name="to-create-an-html-document-viewer"></a>Aby utworzyć przeglądarkę dokumentów HTML  
  
1. Ustaw właściwość <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> na `false`, aby uniemożliwić otwieranie plików przez kontrolkę <xref:System.Windows.Forms.WebBrowser>.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. Ustaw właściwość <xref:System.Windows.Forms.WebBrowser.Url%2A> na lokalizację początkowego pliku do wyświetlenia.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.WebBrowser> o nazwie `webBrowser1`.  
  
- Odwołania do zestawów `System` i `System.Windows.Forms`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser, kontrolka — omówienie](webbrowser-control-overview.md)
- [Zabezpieczenia WebBrowser](webbrowser-security.md)
- [Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Instrukcje: drukowanie za pomocą kontrolki WebBrowser](how-to-print-with-a-webbrowser-control.md)
