---
title: Zdarzenia w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 5d51b6a71bffb546c85ba253181453f6deecfa64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="5908e-102">Zdarzenia w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5908e-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="5908e-103">Formant formularzy systemu Windows dziedziczy więcej niż 60 zdarzeń z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5908e-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5908e-104">Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzeń, co powoduje, że formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takich jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzenia i niskiego poziomu zdarzeń myszy i klawiatury.</span><span class="sxs-lookup"><span data-stu-id="5908e-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="5908e-105">Niektóre zdarzenia niskiego poziomu są syntezatora przez <xref:System.Windows.Forms.Control> do semantycznego zdarzenia, takie jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="5908e-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="5908e-106">Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="5908e-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="5908e-107">Jeśli formant niestandardowy musi przesłonić odziedziczonego zdarzeń funkcji, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączanie delegata.</span><span class="sxs-lookup"><span data-stu-id="5908e-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="5908e-108">Jeśli nie masz doświadczenia w obsłudze zdarzeń modelu w programie .NET Framework, zobacz [wywoływanie zdarzeń od składnika](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="5908e-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5908e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5908e-109">See Also</span></span>  
 [<span data-ttu-id="5908e-110">Przesłanianie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="5908e-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="5908e-111">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="5908e-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="5908e-112">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5908e-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="5908e-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5908e-113">Events</span></span>](../../../../docs/standard/events/index.md)
