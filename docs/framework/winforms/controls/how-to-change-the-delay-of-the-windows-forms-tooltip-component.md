---
title: Zmień opóźnienie składnika ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746590"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="c87ca-102">Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c87ca-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="c87ca-103">Istnieje wiele wartości opóźnienia, które można ustawić dla składnika <xref:System.Windows.Forms.ToolTip> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c87ca-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="c87ca-104">Jednostką miary dla wszystkich tych właściwości jest milisekund.</span><span class="sxs-lookup"><span data-stu-id="c87ca-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="c87ca-105">Właściwość <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> określa, jak długo użytkownik musi wskazywać w skojarzonym formancie ciąg etykietki narzędzia do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="c87ca-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="c87ca-106">Właściwość <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> ustawia liczbę milisekund, jaką zajmie kolejny ciąg etykietki narzędzia, gdy wskaźnik myszy zostanie przeniesiony z jednej etykietki narzędzia do innej.</span><span class="sxs-lookup"><span data-stu-id="c87ca-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="c87ca-107">Właściwość <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> określa długość czasu wyświetlania ciągu etykietki narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c87ca-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="c87ca-108">Można ustawić te wartości pojedynczo lub przez ustawienie wartości właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; inne właściwości opóźnienia są ustawiane na podstawie wartości przypisanej do właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>.</span><span class="sxs-lookup"><span data-stu-id="c87ca-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="c87ca-109">Na przykład, gdy <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> jest ustawiona na wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> jest ustawiona na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> jest ustawiona na wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielona przez pięć (lub N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> jest ustawiona na wartość, która jest pięć razy większa niż wartość właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (lub 5N).</span><span class="sxs-lookup"><span data-stu-id="c87ca-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="c87ca-110">Aby ustawić opóźnienie</span><span class="sxs-lookup"><span data-stu-id="c87ca-110">To set the delay</span></span>  
  
1. <span data-ttu-id="c87ca-111">Ustaw następujące właściwości, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c87ca-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c87ca-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c87ca-112">See also</span></span>

- [<span data-ttu-id="c87ca-113">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="c87ca-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="c87ca-114">Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c87ca-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="c87ca-115">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="c87ca-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
