---
title: "Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8506df062729a98adc1aa1e0dcb524aa4ec812c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="aeb0c-102">Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="aeb0c-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="aeb0c-103">Istnieje wiele wartości opóźnienia, które można ustawić dla formularzy systemu Windows <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="aeb0c-104">Jednostka miary tych właściwości to milisekund.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="aeb0c-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Właściwość określa, jak długo użytkownik musi wskazywać na skojarzonym formancie ciągu etykietki narzędzia i pojawienie się.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="aeb0c-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Właściwość ustawia liczbę milisekund zajmuje kolejnych ciągów ToolTip są wyświetlane jako wskaźnik myszy są przenoszone z jednego formantu ToolTip skojarzonych na inny.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="aeb0c-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Właściwość określa długość czasu jest wyświetlany ciąg etykietki narzędzia.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="aeb0c-108">Wartości te można ustawiać indywidualnie lub przez ustawienie wartości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości; opóźnienie, na wartość przypisana do właściwości są ustawione na podstawie <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="aeb0c-109">Na przykład, jeśli <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> ma ustawioną wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> ma ustawioną wartość N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> ma ustawioną wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielony przez pięć (lub N/5) i <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> ma ustawioną wartość, która jest pięć razy wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości (lub 5 n).</span><span class="sxs-lookup"><span data-stu-id="aeb0c-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="aeb0c-110">Aby ustawić opóźnienie</span><span class="sxs-lookup"><span data-stu-id="aeb0c-110">To set the delay</span></span>  
  
1.  <span data-ttu-id="aeb0c-111">Ustaw następujące właściwości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="aeb0c-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aeb0c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aeb0c-112">See Also</span></span>  
 [<span data-ttu-id="aeb0c-113">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="aeb0c-113">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="aeb0c-114">Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="aeb0c-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="aeb0c-115">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="aeb0c-115">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
