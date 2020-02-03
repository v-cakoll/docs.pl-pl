---
title: Zdarzenia w kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745757"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="14c47-102">Zdarzenia w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="14c47-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="14c47-103">Formant Windows Forms dziedziczy więcej niż 60 zdarzeń z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14c47-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="14c47-104">Obejmują one zdarzenie <xref:System.Windows.Forms.Control.Paint>, które powoduje narysowanie kontrolki, zdarzenia związane z wyświetlaniem okna, takie jak zdarzenia <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> oraz zdarzenia myszy i klawiatury niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="14c47-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="14c47-105">Niektóre zdarzenia niskiego poziomu są syntezą <xref:System.Windows.Forms.Control> do zdarzeń semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="14c47-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="14c47-106">Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczonych, zobacz <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="14c47-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="14c47-107">Jeśli kontrolka niestandardowa musi przesłonić funkcję dziedziczonego zdarzenia, Przesłoń dziedziczonej metody `On`*EventName* zamiast dołączać delegata.</span><span class="sxs-lookup"><span data-stu-id="14c47-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="14c47-108">Jeśli nie znasz modelu zdarzeń w .NET Framework, zobacz Wywoływanie [zdarzeń ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="14c47-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c47-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14c47-109">See also</span></span>

- [<span data-ttu-id="14c47-110">Przesłanianie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="14c47-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="14c47-111">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="14c47-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="14c47-112">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="14c47-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="14c47-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="14c47-113">Events</span></span>](../../../standard/events/index.md)
