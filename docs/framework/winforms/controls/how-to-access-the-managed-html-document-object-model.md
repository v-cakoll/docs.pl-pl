---
title: 'Porady: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 175a29322fe2af13992e267b3fc3308b70212272
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="bbeee-102">Porady: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="bbeee-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="bbeee-103">Zarządzany HTML modelu DOM (Document Object) mogą korzystać z dwóch typów aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bbeee-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="bbeee-104">Aplikacji formularzy systemu Windows (.exe), który hostował zarządzanej <xref:System.Windows.Forms.WebBrowser> formantu.</span><span class="sxs-lookup"><span data-stu-id="bbeee-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="bbeee-105">Te dwie technologie uzupełnić, <xref:System.Windows.Forms.WebBrowser> kontroli wyświetlania strony do modelu DOM kodu HTML reprezentujący struktury logicznej dokumentu i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bbeee-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="bbeee-106">Formularze systemu Windows <xref:System.Windows.Forms.UserControl> hostowanej w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="bbeee-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="bbeee-107">Można uzyskać dostępu do modelu DOM kodu HTML reprezentujący strony, na której Twojej <xref:System.Windows.Forms.UserControl> znajduje się w celu zmiany struktury dokumentu lub Otwórz modalnych okien dialogowych, wśród innych możliwości.</span><span class="sxs-lookup"><span data-stu-id="bbeee-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="bbeee-108">Dostępu do modelu DOM w aplikacji formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bbeee-108">To access DOM from a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="bbeee-109">Host <xref:System.Windows.Forms.WebBrowser> kontroli w aplikacji formularzy systemu Windows oraz monitorować <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bbeee-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="bbeee-110">Szczegółowe informacje o kontrole hostingu i monitorowanie zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbeee-110">For details on hosting controls and monitoring for events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
2.  <span data-ttu-id="bbeee-111">Pobrać <xref:System.Windows.Forms.HtmlDocument> dla bieżącej strony, uzyskując dostęp do <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> formantu.</span><span class="sxs-lookup"><span data-stu-id="bbeee-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="bbeee-112">Dostęp do modelu DOM z elementu UserControl hostowanej w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="bbeee-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="bbeee-113">Tworzenie własnych niestandardowych klasy pochodnej <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbeee-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="bbeee-114">Aby uzyskać więcej informacji, zobacz [porady: formanty złożone autora](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bbeee-114">For more information, see [How to: Author Composite Controls](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span></span>  
  
2.  <span data-ttu-id="bbeee-115">Umieść następujący kod wewnątrz obsługi zdarzenia obciążenia dla Twojego <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="bbeee-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bbeee-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="bbeee-116">Robust Programming</span></span>  
  
1.  <span data-ttu-id="bbeee-117">Korzystając z modelu DOM za pośrednictwem <xref:System.Windows.Forms.WebBrowser> kontroli, użytkownik powinien zawsze czekać <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie przed podjęciem próby uzyskania dostępu <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> formantu.</span><span class="sxs-lookup"><span data-stu-id="bbeee-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="bbeee-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Zdarzenie jest wywoływane po załadowaniu całego dokumentu; Jeśli używasz modelu DOM przed upływem, istnieje ryzyko spowodować wyjątek czasu wykonywania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbeee-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bbeee-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bbeee-119">.NET Framework Security</span></span>  
  
1.  <span data-ttu-id="bbeee-120">Aplikacja lub <xref:System.Windows.Forms.UserControl> będzie wymagają pełnego zaufania, aby uzyskać dostęp do zarządzany HTML DOM</span><span class="sxs-lookup"><span data-stu-id="bbeee-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="bbeee-121">Jeśli wdrażasz aplikacji formularzy systemu Windows przy użyciu [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], możesz poprosić o pełnego zaufania przy użyciu podniesienia uprawnień lub zaufanych wdrożenia aplikacji, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="bbeee-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbeee-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbeee-122">See Also</span></span>  
 [<span data-ttu-id="bbeee-123">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="bbeee-123">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
