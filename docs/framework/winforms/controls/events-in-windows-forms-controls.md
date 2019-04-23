---
title: Zdarzenia w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215894"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="40933-102">Zdarzenia w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="40933-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="40933-103">Formant programu Windows Forms dziedziczy więcej niż 60 zdarzenia z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40933-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="40933-104">Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzenie, które powoduje formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takie jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzeń i niskiego poziomu zdarzeń myszy i klawiatury.</span><span class="sxs-lookup"><span data-stu-id="40933-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="40933-105">Niektóre zdarzenia niskiego poziomu są przekształcony przez <xref:System.Windows.Forms.Control> zdarzeniach semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="40933-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="40933-106">Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="40933-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="40933-107">Jeśli niestandardową kontrolkę musi zastąpić funkcjonalność zdarzeń dziedziczone, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączając delegata.</span><span class="sxs-lookup"><span data-stu-id="40933-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="40933-108">Jeśli nie znasz modelu zdarzeń w programie .NET Framework, zobacz [Raising Events ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="40933-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40933-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40933-109">See also</span></span>

- [<span data-ttu-id="40933-110">Przesłanianie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="40933-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="40933-111">Obsługa danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="40933-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="40933-112">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="40933-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="40933-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="40933-113">Events</span></span>](../../../standard/events/index.md)
