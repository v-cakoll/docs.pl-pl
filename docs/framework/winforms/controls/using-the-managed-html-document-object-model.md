---
title: Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML
ms.date: 03/30/2017
helpviewer_keywords:
- managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
ms.openlocfilehash: 7800311895d1c0fac43577076226a68712164f60
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47081763"
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="d7e6b-102">Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="d7e6b-103">HTML zarządzanych document object model (DOM) zapewnia otoki, na podstawie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dla klas kodu HTML, udostępnianych przez program Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="d7e6b-104">Korzystając z tych klas do manipulowania strony HTML, hostowana w <xref:System.Windows.Forms.WebBrowser> kontroli, lub tworzyć nowe strony, od początku.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7e6b-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d7e6b-105">In This Section</span></span>  
 [<span data-ttu-id="d7e6b-106">Instrukcje: uzyskiwanie dostępu do modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="d7e6b-107">W tym artykule opisano sposób uzyskiwania poprawne wystąpienie <xref:System.Windows.Forms.HtmlDocument> z aplikacji Windows Forms lub <xref:System.Windows.Forms.UserControl> hostowanych w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="d7e6b-108">Instrukcje: uzyskiwanie dostępu do źródła HTML w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="d7e6b-109">W tym artykule opisano sposób uzyskiwania źródła HTML oryginalne, niezmodyfikowanego i sposobie uzyskania źródła "na żywo", który reprezentuje bieżący stan DOM.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="d7e6b-110">Instrukcje: zmienianie stylu elementu w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="d7e6b-111">Opisuje sposób modyfikowania style, które są używane do kontrolowania wyświetlania elementów.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="d7e6b-112">Uzyskiwanie dostępu do ramek w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="d7e6b-113">W tym artykule opisano, jakie ramek i zestawu ramek i jak uzyskać dostęp do modelu DOM ramki.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="d7e6b-114">Uzyskiwanie dostępu do nieujawnionych elementów w modelu DOM (Document Object Model) zarządzanych dokumentów HTML</span><span class="sxs-lookup"><span data-stu-id="d7e6b-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="d7e6b-115">Opisuje sposób dostęp do elementów członkowskich podstawowego modelu DOM, które nie mają odpowiednika zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d7e6b-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d7e6b-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d7e6b-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="d7e6b-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d7e6b-117">Related Sections</span></span>  
 [<span data-ttu-id="d7e6b-118">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d7e6b-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7e6b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7e6b-119">See Also</span></span>  
 [<span data-ttu-id="d7e6b-120">Model obiektowy DHTML — informacje</span><span class="sxs-lookup"><span data-stu-id="d7e6b-120">About the DHTML Object Model</span></span>](https://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
