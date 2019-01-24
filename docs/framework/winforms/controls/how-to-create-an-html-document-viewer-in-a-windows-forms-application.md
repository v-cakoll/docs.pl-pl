---
title: 'Instrukcje: Tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 83a29af28f5e58b75377805e443eb92cee39e272
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643705"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Instrukcje: Tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms
Możesz użyć <xref:System.Windows.Forms.WebBrowser> sterowania do wyświetlania i drukowanie dokumentów HTML bez zapewnienia pełnej funkcjonalności przeglądarki sieci Web. Jest to przydatne, gdy chcesz korzystać z zalet możliwości formatowania kodu HTML, ale nie mają użytkownicy do załadowania dowolnych stron sieci Web, które mogą zawierać niezaufanych kontrolki sieci Web lub kod potencjalnie złośliwy skrypt. Możesz chcieć ograniczyć możliwości <xref:System.Windows.Forms.WebBrowser> kontrolować w ten sposób, na przykład użyć go jako podgląd wiadomości e-mail HTML lub zapewnianie pomocy formacie HTML w aplikacji.  
  
### <a name="to-create-an-html-document-viewer"></a>Aby utworzyć przeglądarki dokumentów HTML  
  
1.  Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików upuszczone na go.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Ustaw <xref:System.Windows.Forms.WebBrowser.Url%2A> lokalizacja początkowa plik, aby wyświetlić właściwości.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.  
  
-   Odwołuje się do `System` i `System.Windows.Forms` zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser, kontrolka — omówienie](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [Zabezpieczenia WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)
- [Instrukcje: Przejdź do adresu URL za pomocą formantu WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Instrukcje: Drukowanie za pomocą formantu WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
