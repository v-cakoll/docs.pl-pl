---
title: "Porady: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML"
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
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ef9839029e1c60cbc0d713e8982baa5708a281f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Porady: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości <xref:System.Windows.Forms.WebBrowser> kontroli zwracać bieżącego dokumentu HTML, który istniał, gdy najpierw została wyświetlona. Jednak jeśli można modyfikować przy użyciu wywołania metod i właściwości, takich jak <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> i <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, zmiany te nie będą wyświetlane po wywołaniu <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Aby uzyskać najbardziej aktualne źródła HTML dla modelu DOM, należy wywołać <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> właściwości w elemencie HTML.  
  
 Poniższa procedura pokazuje, jak pobrać źródło dynamiczne i wyświetlić je w menu skrótów oddzielne.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Trwa pobieranie źródło dynamiczne razem z właściwością OuterHtml  
  
1.  Tworzenie nowej aplikacji formularzy systemu Windows. Uruchom za pomocą jednej <xref:System.Windows.Forms.Form>i nadaj mu `Form1`.  
  
2.  Host <xref:System.Windows.Forms.WebBrowser> kontroli w aplikacji formularzy systemu Windows i nadaj mu nazwę `WebBrowser1`. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Tworzenie drugiej <xref:System.Windows.Forms.Form> w aplikacji o nazwie `CodeForm`.  
  
4.  Dodaj <xref:System.Windows.Forms.RichTextBox> formant `CodeForm` i ustawić jej <xref:System.Windows.Forms.Control.Dock%2A> właściwości `Fill`.  
  
5.  Utwórz właściwość publiczna na `CodeForm` o nazwie `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Dodaj <xref:System.Windows.Forms.Button> formantu o nazwie `Button1` do Twojej <xref:System.Windows.Forms.Form>i monitorować <xref:System.Windows.Forms.Control.Click> zdarzeń. Aby uzyskać szczegółowe informacje dotyczące monitorowania zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).  
  
7.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy zawsze przetestować wartość <xref:System.Windows.Forms.WebBrowser.Document%2A> przed próbą ich pobrania. Jeśli bieżąca strona nie jest ukończone ładowania, <xref:System.Windows.Forms.WebBrowser.Document%2A> lub nie można zainicjować co najmniej jeden z jego obiektów podrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą modelu obiektów zarządzanych dokumentów HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [Informacje o formancie WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
