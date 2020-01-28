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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="0c59a-102">Porady: tworzenie przeglądarki dokumentów HTML w aplikacji formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0c59a-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="0c59a-103">Za pomocą kontrolki <xref:System.Windows.Forms.WebBrowser> można wyświetlać i drukować dokumenty HTML bez podawania pełnej funkcjonalności przeglądarki internetowej.</span><span class="sxs-lookup"><span data-stu-id="0c59a-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="0c59a-104">Jest to przydatne, gdy chcesz korzystać z funkcji formatowania HTML, ale nie chcesz, aby użytkownicy ładowały dowolne strony sieci Web, które mogą zawierać niezaufane formanty sieci Web lub potencjalnie złośliwy kod skryptu.</span><span class="sxs-lookup"><span data-stu-id="0c59a-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="0c59a-105">Może zajść potrzeba ograniczenia możliwości kontroli <xref:System.Windows.Forms.WebBrowser> w ten sposób, na przykład w celu użycia jej jako przeglądarki poczty e-mail w formacie HTML lub zapewnienia pomocy w formacie HTML w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c59a-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="0c59a-106">Aby utworzyć przeglądarkę dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="0c59a-106">To create an HTML document viewer</span></span>  
  
1. <span data-ttu-id="0c59a-107">Ustaw właściwość <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> na `false`, aby uniemożliwić otwieranie plików przez kontrolkę <xref:System.Windows.Forms.WebBrowser>.</span><span class="sxs-lookup"><span data-stu-id="0c59a-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <span data-ttu-id="0c59a-108">Ustaw właściwość <xref:System.Windows.Forms.WebBrowser.Url%2A> na lokalizację początkowego pliku do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="0c59a-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c59a-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0c59a-109">Compiling the Code</span></span>  
 <span data-ttu-id="0c59a-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0c59a-110">This example requires:</span></span>  
  
- <span data-ttu-id="0c59a-111">Kontrolka <xref:System.Windows.Forms.WebBrowser> o nazwie `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="0c59a-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="0c59a-112">Odwołania do zestawów `System` i `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="0c59a-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c59a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c59a-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="0c59a-114">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c59a-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="0c59a-115">Zabezpieczenia WebBrowser</span><span class="sxs-lookup"><span data-stu-id="0c59a-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="0c59a-116">Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="0c59a-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="0c59a-117">Instrukcje: drukowanie za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="0c59a-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
