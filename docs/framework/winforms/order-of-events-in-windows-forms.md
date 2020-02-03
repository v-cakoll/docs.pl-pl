---
title: Kolejność zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734860"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="6af54-102">Kolejność zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6af54-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="6af54-103">Kolejność, w której zdarzenia są zgłaszane w Windows Forms aplikacji, jest szczególnie interesująca dla deweloperów, którzy z kolei obsługują każde z tych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6af54-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="6af54-104">Gdy sytuacja wywołuje dokładnych obsługi zdarzeń, na przykład podczas ponownego rysowania części formularza, należy zapoznać się z dokładną kolejnością, w której zdarzenia są zgłaszane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6af54-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="6af54-105">Ten temat zawiera pewne szczegóły dotyczące kolejności zdarzeń w kilku ważnych etapach w okresie istnienia aplikacji i kontroli.</span><span class="sxs-lookup"><span data-stu-id="6af54-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="6af54-106">Aby uzyskać szczegółowe informacje na temat kolejności zdarzeń wejściowych myszy, zobacz [zdarzenia myszy w Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6af54-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="6af54-107">Aby zapoznać się z omówieniem zdarzeń w Windows Forms, zobacz [Omówienie zdarzeń](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6af54-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="6af54-108">Aby uzyskać szczegółowe informacje na temat korzeń programów obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6af54-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="6af54-109">Zdarzenia uruchamiania i zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="6af54-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="6af54-110">Klasy <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> uwidaczniają zestaw zdarzeń związanych z uruchamianiem i wyłączaniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6af54-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="6af54-111">Po uruchomieniu aplikacji Windows Forms zdarzenia uruchamiania głównego formularza są zgłaszane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6af54-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="6af54-112">Po zamknięciu aplikacji zdarzenia zamknięcia głównego formularza są zgłaszane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6af54-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="6af54-113">Zdarzenie <xref:System.Windows.Forms.Application.ApplicationExit> klasy <xref:System.Windows.Forms.Application> jest wywoływane po zdarzeniach zamknięcia głównego formularza.</span><span class="sxs-lookup"><span data-stu-id="6af54-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6af54-114">Visual Basic 2005 zawiera dodatkowe zdarzenia aplikacji, takie jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6af54-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="6af54-115">Zdarzenia fokusu i walidacji</span><span class="sxs-lookup"><span data-stu-id="6af54-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="6af54-116">Gdy zmienisz fokus przy użyciu klawiatury (TAB, SHIFT + TAB itd.), wywołując metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> lub ustawiając właściwość <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> na bieżącą formę, zdarzenia fokusu klasy <xref:System.Windows.Forms.Control> są wykonywane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6af54-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="6af54-117">Gdy zmienisz fokus przy użyciu myszy lub wywołując metodę <xref:System.Windows.Forms.Control.Focus%2A>, zdarzenia fokusu klasy <xref:System.Windows.Forms.Control> są wykonywane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6af54-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="6af54-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6af54-118">See also</span></span>

- [<span data-ttu-id="6af54-119">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6af54-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
