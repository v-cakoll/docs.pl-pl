---
title: 'Porady: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 49a50bdf5ea0f24d712458c739b7829ee73d157a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="43187-102">Porady: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="43187-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="43187-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości <xref:System.Windows.Forms.WebBrowser> kontroli zwracać bieżącego dokumentu HTML, który istniał, gdy najpierw została wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="43187-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="43187-104">Jednak jeśli można modyfikować przy użyciu wywołania metod i właściwości, takich jak <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> i <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, zmiany te nie będą wyświetlane po wywołaniu <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="43187-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="43187-105">Aby uzyskać najbardziej aktualne źródła HTML dla modelu DOM, należy wywołać <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> właściwości w elemencie HTML.</span><span class="sxs-lookup"><span data-stu-id="43187-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="43187-106">Poniższa procedura pokazuje, jak pobrać źródło dynamiczne i wyświetlić je w menu skrótów oddzielne.</span><span class="sxs-lookup"><span data-stu-id="43187-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="43187-107">Trwa pobieranie źródło dynamiczne razem z właściwością OuterHtml</span><span class="sxs-lookup"><span data-stu-id="43187-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="43187-108">Tworzenie nowej aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="43187-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="43187-109">Uruchom za pomocą jednej <xref:System.Windows.Forms.Form>i nadaj mu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="43187-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="43187-110">Host <xref:System.Windows.Forms.WebBrowser> kontroli w aplikacji formularzy systemu Windows i nadaj mu nazwę `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="43187-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="43187-111">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="43187-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="43187-112">Tworzenie drugiej <xref:System.Windows.Forms.Form> w aplikacji o nazwie `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="43187-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="43187-113">Dodaj <xref:System.Windows.Forms.RichTextBox> formant `CodeForm` i ustawić jej <xref:System.Windows.Forms.Control.Dock%2A> właściwości `Fill`.</span><span class="sxs-lookup"><span data-stu-id="43187-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="43187-114">Utwórz właściwość publiczna na `CodeForm` o nazwie `Code`.</span><span class="sxs-lookup"><span data-stu-id="43187-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="43187-115">Dodaj <xref:System.Windows.Forms.Button> formantu o nazwie `Button1` do Twojej <xref:System.Windows.Forms.Form>i monitorować <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="43187-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="43187-116">Aby uzyskać szczegółowe informacje dotyczące monitorowania zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="43187-116">For details on monitoring events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="43187-117">Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="43187-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="43187-118">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="43187-118">Robust Programming</span></span>  
 <span data-ttu-id="43187-119">Należy zawsze przetestować wartość <xref:System.Windows.Forms.WebBrowser.Document%2A> przed próbą ich pobrania.</span><span class="sxs-lookup"><span data-stu-id="43187-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="43187-120">Jeśli bieżąca strona nie jest ukończone ładowania, <xref:System.Windows.Forms.WebBrowser.Document%2A> lub nie można zainicjować co najmniej jeden z jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="43187-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43187-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43187-121">See Also</span></span>  
 [<span data-ttu-id="43187-122">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="43187-122">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [<span data-ttu-id="43187-123">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="43187-123">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
