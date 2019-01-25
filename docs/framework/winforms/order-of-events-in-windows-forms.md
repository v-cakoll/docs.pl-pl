---
title: Kolejność zdarzeń w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 814c788285d974db5a8ef2bbaec1368a860c21d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643965"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="6f1b2-102">Kolejność zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6f1b2-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="6f1b2-103">Kolejność, w której zdarzenia są wywoływane w aplikacjach Windows Forms ma szczególne znaczenie dla deweloperów zaniepokojona obsługi, każde z tych wydarzeń z kolei.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="6f1b2-104">Rozwiązania wymaga dokładnych obsługi zdarzeń, takich jak kiedy są odświeżanie części formularza, niezbędne jest rozpoznawanie dokładne kolejność, w której zdarzenia są wywoływane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="6f1b2-105">Ten temat zawiera kilka szczegółów rzędu kilku zdarzeń kilku etapach ważne w okresie istnienia aplikacji i formantów.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="6f1b2-106">Aby uzyskać szczegółowe informacje na temat kolejności zdarzeń wejściowych myszy zobacz [zdarzeń myszy w formularzach Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6f1b2-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="6f1b2-107">Aby uzyskać przegląd zdarzeń w formularzach Windows Forms, zobacz [Przegląd zdarzeń](../../../docs/framework/winforms/events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6f1b2-107">For an overview of events in Windows Forms, see [Events Overview](../../../docs/framework/winforms/events-overview-windows-forms.md).</span></span> <span data-ttu-id="6f1b2-108">Aby uzyskać szczegółowe informacje o korzeń procedury obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6f1b2-108">For details about the makeup of event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="6f1b2-109">Uruchamianie aplikacji i zamykania</span><span class="sxs-lookup"><span data-stu-id="6f1b2-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="6f1b2-110"><xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> klasy udostępnić zestaw zdarzeń związanych z aplikacji, uruchamiania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="6f1b2-111">Po uruchomieniu aplikacji Windows Forms zdarzenia uruchamiania formularza głównego są wywoływane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6f1b2-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="6f1b2-112">Po zakończeniu działania aplikacji, zdarzeń zamknięcia formularza głównego są wywoływane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6f1b2-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="6f1b2-113"><xref:System.Windows.Forms.Application.ApplicationExit> Zdarzenia <xref:System.Windows.Forms.Application> klasy jest wywoływane po wykonaniu zdarzeń zamknięcia formularza głównego.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f1b2-114">Visual Basic 2005 zawiera zdarzenia dodatkowych aplikacji, takich jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f1b2-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="6f1b2-115">Fokus i zdarzenia walidacji</span><span class="sxs-lookup"><span data-stu-id="6f1b2-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="6f1b2-116">Po zmianie fokusu przy użyciu klawiatury (karty, SHIFT + TAB i tak dalej), przez wywołanie metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> metod, lub poprzez skonfigurowanie <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwości bieżącego formularza zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy zachodzą w następującej kolejności :</span><span class="sxs-lookup"><span data-stu-id="6f1b2-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="6f1b2-117">Po zmianie fokusu przy użyciu myszy lub przez wywołanie <xref:System.Windows.Forms.Control.Focus%2A> metody, zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy zachodzą w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6f1b2-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="6f1b2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f1b2-118">See also</span></span>
- [<span data-ttu-id="6f1b2-119">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f1b2-119">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
