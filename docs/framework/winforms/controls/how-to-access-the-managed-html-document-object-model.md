---
title: 'Instrukcje: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 2a195dc6583d5a0a72bd08b66f8933f4002e879a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487271"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="34b01-102">Instrukcje: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="34b01-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="34b01-103">Dostęp z zarządzanego HTML Document Object Model (DOM), spośród dwóch rodzajów aplikacji:</span><span class="sxs-lookup"><span data-stu-id="34b01-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
- <span data-ttu-id="34b01-104">Aplikacji Windows Forms (.exe), która obsługiwana zarządzanej <xref:System.Windows.Forms.WebBrowser> kontroli.</span><span class="sxs-lookup"><span data-stu-id="34b01-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="34b01-105">Te dwie technologie wzajemnie się uzupełniają, za pomocą <xref:System.Windows.Forms.WebBrowser> kontroli stroną dla użytkownika i HTML DOM reprezentującej strukturę logiczną dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34b01-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
- <span data-ttu-id="34b01-106">Formularze Windows <xref:System.Windows.Forms.UserControl> hostowany w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="34b01-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="34b01-107">Możesz uzyskać dostęp DOM HTML reprezentujący stronę, na którym Twojej <xref:System.Windows.Forms.UserControl> znajduje się w celu zmiany struktury dokumentu lub Otwórz modalnych okien dialogowych, wśród wielu innych możliwości.</span><span class="sxs-lookup"><span data-stu-id="34b01-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="34b01-108">Aby uzyskać dostęp do modelu DOM z aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34b01-108">To access DOM from a Windows Forms application</span></span>  
  
1. <span data-ttu-id="34b01-109">Host <xref:System.Windows.Forms.WebBrowser> kontrolki w aplikacji Windows Forms i Monitoruj <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="34b01-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="34b01-110">Szczegółowe informacje na temat kontrolki hostingu i monitorowania zdarzeń, [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="34b01-110">For details on hosting controls and monitoring for events, see [Events](../../../standard/events/index.md).</span></span>  
  
2. <span data-ttu-id="34b01-111">Pobieranie <xref:System.Windows.Forms.HtmlDocument> dla bieżącej strony, uzyskując dostęp do <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> kontroli.</span><span class="sxs-lookup"><span data-stu-id="34b01-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="34b01-112">Dostęp do modelu DOM z elementu UserControl hostowanych w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="34b01-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1. <span data-ttu-id="34b01-113">Utwórz własne niestandardowe klasy pochodnej <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="34b01-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="34b01-114">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie kontrolek złożonych](how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="34b01-114">For more information, see [How to: Author Composite Controls](how-to-author-composite-controls.md).</span></span>  
  
2. <span data-ttu-id="34b01-115">Umieść następujący kod wewnątrz procedury obsługi zdarzenia obciążenia dla swojej <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="34b01-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="34b01-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="34b01-116">Robust Programming</span></span>  
  
1. <span data-ttu-id="34b01-117">Podczas korzystania z modelu DOM przy użyciu <xref:System.Windows.Forms.WebBrowser> kontrolki, należy zawsze poczekać aż <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> wystąpi zdarzenie przed podjęciem próby uzyskania dostępu <xref:System.Windows.Forms.WebBrowser.Document%2A> właściwość <xref:System.Windows.Forms.WebBrowser> kontroli.</span><span class="sxs-lookup"><span data-stu-id="34b01-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="34b01-118"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Zdarzenie jest wywoływane po załadowaniu całego dokumentu; Jeśli używasz modelu DOM przed tym dniem, istnieje ryzyko powoduje wyjątek czasu wykonywania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34b01-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="34b01-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="34b01-119">.NET Framework Security</span></span>  
  
1. <span data-ttu-id="34b01-120">Aplikacja lub <xref:System.Windows.Forms.UserControl> będzie wymagać pełnego zaufania w celu uzyskania dostępu do zarządzanego kodu HTML DOM.</span><span class="sxs-lookup"><span data-stu-id="34b01-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="34b01-121">Jeśli wdrażasz aplikację Windows Forms przy użyciu aplikacji ClickOnce, możesz poprosić o pełnego zaufania za pomocą podnoszenia poziomu uprawnień lub zaufanego wdrożenia aplikacji; zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications) Aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="34b01-121">If you are deploying a Windows Forms application using ClickOnce, you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b01-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34b01-122">See also</span></span>

- [<span data-ttu-id="34b01-123">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="34b01-123">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
