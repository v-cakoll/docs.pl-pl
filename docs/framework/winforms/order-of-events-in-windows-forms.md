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
ms.openlocfilehash: 10a6451827a16605ba738cf74b7f684b69adb5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538479"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="cc27f-102">Kolejność zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc27f-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="cc27f-103">Kolejność, w której zdarzenia są generowane w aplikacjach formularzy systemu Windows ma szczególne znaczenie dla deweloperów związane z obsługi każdego z tych zdarzeń z kolei.</span><span class="sxs-lookup"><span data-stu-id="cc27f-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="cc27f-104">Rozwiązania wymaga dokładnych obsługi zdarzenia, na przykład gdy są ponownego narysowania części formularza, konieczne jest świadomości dokładne kolejności, w której zdarzenia są generowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cc27f-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="cc27f-105">Ten temat zawiera pewne szczegóły rzędu zdarzenia podczas kilka ważnych etapach cykl życia aplikacji i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="cc27f-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="cc27f-106">Aby uzyskać szczegółowe informacje o zamówieniu myszy zdarzenia wejściowe, zobacz [zdarzenia myszy w formularzach systemu Windows](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cc27f-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="cc27f-107">Przegląd zdarzeń w formularzach systemu Windows, temacie [Przegląd zdarzeń](../../../docs/framework/winforms/events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cc27f-107">For an overview of events in Windows Forms, see [Events Overview](../../../docs/framework/winforms/events-overview-windows-forms.md).</span></span> <span data-ttu-id="cc27f-108">Aby uzyskać więcej informacji o w skład programów obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cc27f-108">For details about the makeup of event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="cc27f-109">Uruchamianie aplikacji i zdarzeń zamknięcia systemu</span><span class="sxs-lookup"><span data-stu-id="cc27f-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="cc27f-110"><xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> klasy ujawnia zestaw zdarzeń związanych z aplikacji uruchamiania i wyłączania.</span><span class="sxs-lookup"><span data-stu-id="cc27f-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="cc27f-111">Po uruchomieniu aplikacji formularzy systemu Windows zdarzenia uruchamiania formularza głównego pojawienia się w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="cc27f-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="cc27f-112">Po zamknięciu aplikacji, zdarzenia zamknięcia formularza głównego pojawienia się w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="cc27f-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="cc27f-113"><xref:System.Windows.Forms.Application.ApplicationExit> Zdarzenie <xref:System.Windows.Forms.Application> klasy jest wywoływane po wykonaniu zdarzeń zamknięcia formularza głównego.</span><span class="sxs-lookup"><span data-stu-id="cc27f-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc27f-114">Visual Basic 2005 zawiera zdarzenia dodatkowych aplikacji, takich jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cc27f-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="cc27f-115">Fokus i zdarzenia walidacji</span><span class="sxs-lookup"><span data-stu-id="cc27f-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="cc27f-116">Po zmianie fokusu przy użyciu klawiatury (TAB, SHIFT + TAB i tak dalej), przez wywołanie metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> metody, lub przez ustawienie <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwości do bieżącego formularza zdarzenia fokus <xref:System.Windows.Forms.Control> klasy występują w następującej kolejności :</span><span class="sxs-lookup"><span data-stu-id="cc27f-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="cc27f-117">Po zmianie fokusu za pomocą myszy lub poprzez wywołanie <xref:System.Windows.Forms.Control.Focus%2A> metody, zdarzenia fokus <xref:System.Windows.Forms.Control> klasy występują w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="cc27f-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="cc27f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc27f-118">See Also</span></span>  
 [<span data-ttu-id="cc27f-119">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc27f-119">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
