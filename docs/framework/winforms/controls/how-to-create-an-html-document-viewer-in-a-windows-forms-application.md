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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="5203a-102">Instrukcje: Tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5203a-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="5203a-103">Możesz użyć <xref:System.Windows.Forms.WebBrowser> sterowania do wyświetlania i drukowanie dokumentów HTML bez zapewnienia pełnej funkcjonalności przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5203a-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="5203a-104">Jest to przydatne, gdy chcesz korzystać z zalet możliwości formatowania kodu HTML, ale nie mają użytkownicy do załadowania dowolnych stron sieci Web, które mogą zawierać niezaufanych kontrolki sieci Web lub kod potencjalnie złośliwy skrypt.</span><span class="sxs-lookup"><span data-stu-id="5203a-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="5203a-105">Możesz chcieć ograniczyć możliwości <xref:System.Windows.Forms.WebBrowser> kontrolować w ten sposób, na przykład użyć go jako podgląd wiadomości e-mail HTML lub zapewnianie pomocy formacie HTML w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5203a-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="5203a-106">Aby utworzyć przeglądarki dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="5203a-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="5203a-107">Ustaw <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> właściwości `false` zapobiegające <xref:System.Windows.Forms.WebBrowser> kontroli otwieranie plików upuszczone na go.</span><span class="sxs-lookup"><span data-stu-id="5203a-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="5203a-108">Ustaw <xref:System.Windows.Forms.WebBrowser.Url%2A> lokalizacja początkowa plik, aby wyświetlić właściwości.</span><span class="sxs-lookup"><span data-stu-id="5203a-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5203a-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5203a-109">Compiling the Code</span></span>  
 <span data-ttu-id="5203a-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5203a-110">This example requires:</span></span>  
  
-   <span data-ttu-id="5203a-111">A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="5203a-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="5203a-112">Odwołuje się do `System` i `System.Windows.Forms` zestawów.</span><span class="sxs-lookup"><span data-stu-id="5203a-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5203a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5203a-113">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="5203a-114">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5203a-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="5203a-115">Zabezpieczenia WebBrowser</span><span class="sxs-lookup"><span data-stu-id="5203a-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)
- [<span data-ttu-id="5203a-116">Instrukcje: Przejdź do adresu URL za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="5203a-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="5203a-117">Instrukcje: Drukowanie za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="5203a-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
