---
title: 'Instrukcje: Zmienianie opóźnienia składnika ToolTip formularzy Windows'
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
ms.openlocfilehash: 494691a6f91a58f2689c1668d95b2df581b76d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593904"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="43031-102">Instrukcje: Zmienianie opóźnienia składnika ToolTip formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="43031-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="43031-103">Istnieje wiele wartości opóźnienia, które można ustawić dla formularzy Windows <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="43031-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="43031-104">Jednostka miary dla tych właściwości jest milisekund.</span><span class="sxs-lookup"><span data-stu-id="43031-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="43031-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Właściwość określa, jak długo użytkownik musi wskazywać na jest skojarzony formant ciąg etykietki narzędzi są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="43031-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="43031-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Właściwość ustawia liczbę milisekund zajmuje kolejne parametry etykietki narzędzia wyświetlany jako myszy przesuwa się z jednego formantu skojarzone ToolTip do innego.</span><span class="sxs-lookup"><span data-stu-id="43031-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="43031-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Właściwość określa długość czasu, jest wyświetlany ciąg etykietki narzędzia.</span><span class="sxs-lookup"><span data-stu-id="43031-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="43031-108">Wartości te można ustawić indywidualnie lub przez ustawienie wartości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości; opóźnienie, właściwości jest ustawiona na podstawie wartości przypisanej do <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="43031-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="43031-109">Na przykład, gdy <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> jest ustawiona na wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> jest równa się N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> jest ustawiona na wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielona przez pięć (lub N na dobę, 5) i <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> jest ustawiona na wartość, która jest pięciokrotnie wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości (lub 5 n).</span><span class="sxs-lookup"><span data-stu-id="43031-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="43031-110">Aby ustawić opóźnienie</span><span class="sxs-lookup"><span data-stu-id="43031-110">To set the delay</span></span>  
  
1.  <span data-ttu-id="43031-111">Ustaw następujące właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="43031-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43031-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43031-112">See also</span></span>
- [<span data-ttu-id="43031-113">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="43031-113">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="43031-114">Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="43031-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="43031-115">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="43031-115">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
