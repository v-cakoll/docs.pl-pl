---
title: "Porady: tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e06fbfde68c0d02a94f8c7e4657e2907cd3fa7eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Porady: tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms
Można użyć <xref:System.Windows.Forms.WebBrowser> formantu do wyświetlania i drukowania dokumentów HTML bez podawania z pełnej funkcjonalności przeglądarki sieci Web. Jest to przydatne, jeśli chcesz skorzystać z możliwości formatowania kodu HTML, ale nie ma użytkowników, aby załadować dowolnego stron sieci Web, które mogą zawierać niezaufanych formantów sieci Web lub kod potencjalnie złośliwy skrypt. Możesz chcieć ograniczyć możliwości <xref:System.Windows.Forms.WebBrowser> kontroli w ten sposób, na przykład, aby używać go jako HTML Podgląd wiadomości e-mail lub w celu zapewnienia pomocy formacie HTML w aplikacji.  
  
### <a name="to-create-an-html-document-viewer"></a>Aby tworzenie przeglądarki dokumentów HTML  
  
1.  Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików na go.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Ustaw <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości do lokalizacji pliku początkowej do wyświetlenia.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.  
  
-   Odwołuje się do `System` i `System.Windows.Forms` zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [Informacje o formancie WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [Zabezpieczenia WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Porady: drukowanie za pomocą formantu WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
