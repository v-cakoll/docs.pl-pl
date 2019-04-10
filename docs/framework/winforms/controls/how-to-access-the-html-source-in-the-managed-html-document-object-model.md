---
title: 'Instrukcje: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: f2306e3405aa0ff37060d987bdc82b58fbaa7784
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345563"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="a2b7c-102">Instrukcje: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="a2b7c-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="a2b7c-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> właściwości <xref:System.Windows.Forms.WebBrowser> kontrola zwraca kod HTML w bieżącym dokumencie, jaka istniała podczas najpierw został wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="a2b7c-104">Jednak w przypadku zmodyfikowania strony przy użyciu wywołania metod i właściwości, takich jak <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> i <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, te zmiany nie pojawią się po wywołaniu <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> i <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="a2b7c-105">Aby uzyskać najbardziej aktualne źródło HTML dla modelu DOM, należy wywołać <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> właściwość elementu HTML.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="a2b7c-106">Poniższa procedura pokazuje, jak pobrać źródło dynamiczne i wyświetlania ich w menu skrótów oddzielne.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="a2b7c-107">Trwa pobieranie źródło dynamiczne z właściwością zewnętrzny kod HTML</span><span class="sxs-lookup"><span data-stu-id="a2b7c-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1. <span data-ttu-id="a2b7c-108">Tworzenie nowej aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="a2b7c-109">Rozpoczynać znakiem pojedynczego <xref:System.Windows.Forms.Form>, a następnie wywołaj ją `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2. <span data-ttu-id="a2b7c-110">Host <xref:System.Windows.Forms.WebBrowser> kontrolkę w aplikacji Windows Forms i nadaj mu nazwę `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="a2b7c-111">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie funkcji przeglądarki sieci Web do aplikacji programu Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="a2b7c-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3. <span data-ttu-id="a2b7c-112">Utwórz drugi <xref:System.Windows.Forms.Form> w aplikacji o nazwie `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4. <span data-ttu-id="a2b7c-113">Dodaj <xref:System.Windows.Forms.RichTextBox> kontrolę `CodeForm` i ustaw jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość `Fill`.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5. <span data-ttu-id="a2b7c-114">Utwórz właściwość publiczną na `CodeForm` o nazwie `Code`.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6. <span data-ttu-id="a2b7c-115">Dodaj <xref:System.Windows.Forms.Button> formantu o nazwie `Button1` do Twojej <xref:System.Windows.Forms.Form>i Monitoruj <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="a2b7c-116">Aby uzyskać więcej informacji na temat monitorowania zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2b7c-116">For details on monitoring events, see [Events](../../../standard/events/index.md).</span></span>  
  
7. <span data-ttu-id="a2b7c-117">Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a2b7c-118">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a2b7c-118">Robust Programming</span></span>  
 <span data-ttu-id="a2b7c-119">Należy zawsze przetestować wartość <xref:System.Windows.Forms.WebBrowser.Document%2A> przed podjęciem próby pobrania go.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="a2b7c-120">Jeśli bieżąca strona nie jest zakończony podczas ładowania, <xref:System.Windows.Forms.WebBrowser.Document%2A> lub nie można zainicjować co najmniej jeden z jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b7c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2b7c-121">See also</span></span>

- [<span data-ttu-id="a2b7c-122">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="a2b7c-122">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
- [<span data-ttu-id="a2b7c-123">WebBrowser — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="a2b7c-123">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
