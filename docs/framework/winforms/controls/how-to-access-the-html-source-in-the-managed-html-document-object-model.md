---
title: 'Instrukcje: Uzyskiwanie dostępu do źródła HTML w modelu obiektów zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 310af03adf38339dd13a5095546391d4bfecac05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674953"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Instrukcje: Uzyskiwanie dostępu do źródła HTML w modelu obiektów zarządzanych dokumentów HTML
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości <xref:System.Windows.Forms.WebBrowser> kontrola zwraca kod HTML w bieżącym dokumencie, jaka istniała podczas najpierw został wyświetlony. Jednak w przypadku zmodyfikowania strony przy użyciu wywołania metod i właściwości, takich jak <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> i <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, te zmiany nie pojawią się po wywołaniu <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Aby uzyskać najbardziej aktualne źródło HTML dla modelu DOM, należy wywołać <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> właściwość elementu HTML.  
  
 Poniższa procedura pokazuje, jak pobrać źródło dynamiczne i wyświetlania ich w menu skrótów oddzielne.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Trwa pobieranie źródło dynamiczne z właściwością zewnętrzny kod HTML  
  
1.  Tworzenie nowej aplikacji Windows Forms. Rozpoczynać znakiem pojedynczego <xref:System.Windows.Forms.Form>, a następnie wywołaj ją `Form1`.  
  
2.  Host <xref:System.Windows.Forms.WebBrowser> kontrolkę w aplikacji Windows Forms i nadaj mu nazwę `WebBrowser1`. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie funkcji przeglądarki sieci Web do aplikacji programu Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Utwórz drugi <xref:System.Windows.Forms.Form> w aplikacji o nazwie `CodeForm`.  
  
4.  Dodaj <xref:System.Windows.Forms.RichTextBox> kontrolę `CodeForm` i ustaw jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość `Fill`.  
  
5.  Utwórz właściwość publiczną na `CodeForm` o nazwie `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Dodaj <xref:System.Windows.Forms.Button> formantu o nazwie `Button1` do Twojej <xref:System.Windows.Forms.Form>i Monitoruj <xref:System.Windows.Forms.Control.Click> zdarzeń. Aby uzyskać więcej informacji na temat monitorowania zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).  
  
7.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy zawsze przetestować wartość <xref:System.Windows.Forms.WebBrowser.Document%2A> przed podjęciem próby pobrania go. Jeśli bieżąca strona nie jest zakończony podczas ładowania, <xref:System.Windows.Forms.WebBrowser.Document%2A> lub nie można zainicjować co najmniej jeden z jego obiektów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
- [WebBrowser, kontrolka — omówienie](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
