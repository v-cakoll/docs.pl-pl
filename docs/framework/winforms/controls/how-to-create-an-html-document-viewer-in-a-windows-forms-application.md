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
ms.workload: dotnet
ms.openlocfilehash: 00be8ca2e4e227b6e4593b0a9e32172ecb9457f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="1ce07-102">Porady: tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ce07-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="1ce07-103">Można użyć <xref:System.Windows.Forms.WebBrowser> formantu do wyświetlania i drukowania dokumentów HTML bez podawania z pełnej funkcjonalności przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ce07-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="1ce07-104">Jest to przydatne, jeśli chcesz skorzystać z możliwości formatowania kodu HTML, ale nie ma użytkowników, aby załadować dowolnego stron sieci Web, które mogą zawierać niezaufanych formantów sieci Web lub kod potencjalnie złośliwy skrypt.</span><span class="sxs-lookup"><span data-stu-id="1ce07-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="1ce07-105">Możesz chcieć ograniczyć możliwości <xref:System.Windows.Forms.WebBrowser> kontroli w ten sposób, na przykład, aby używać go jako HTML Podgląd wiadomości e-mail lub w celu zapewnienia pomocy formacie HTML w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1ce07-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML e-mail viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="1ce07-106">Aby tworzenie przeglądarki dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="1ce07-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="1ce07-107">Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików na go.</span><span class="sxs-lookup"><span data-stu-id="1ce07-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="1ce07-108">Ustaw <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości do lokalizacji pliku początkowej do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="1ce07-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ce07-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1ce07-109">Compiling the Code</span></span>  
 <span data-ttu-id="1ce07-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1ce07-110">This example requires:</span></span>  
  
-   <span data-ttu-id="1ce07-111">A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="1ce07-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="1ce07-112">Odwołuje się do `System` i `System.Windows.Forms` zestawów.</span><span class="sxs-lookup"><span data-stu-id="1ce07-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce07-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ce07-113">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [<span data-ttu-id="1ce07-114">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1ce07-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="1ce07-115">Zabezpieczenia WebBrowser</span><span class="sxs-lookup"><span data-stu-id="1ce07-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [<span data-ttu-id="1ce07-116">Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="1ce07-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [<span data-ttu-id="1ce07-117">Instrukcje: drukowanie za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="1ce07-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
