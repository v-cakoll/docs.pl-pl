---
title: 'Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 4e4623c1c0fe7d082e4d1a1f404ddaa94e79fc2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533633"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="24aeb-102">Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="24aeb-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="24aeb-103">Można ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie, lub w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="24aeb-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="24aeb-104">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="24aeb-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24aeb-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="24aeb-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="24aeb-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="24aeb-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="24aeb-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="24aeb-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="24aeb-108">Aby ustawić programowo etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="24aeb-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="24aeb-109">Dodaj kontrolkę, która będzie wyświetlana etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="24aeb-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="24aeb-110">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="24aeb-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="24aeb-111">Aby ustawić etykietka narzędzia w Projektancie</span><span class="sxs-lookup"><span data-stu-id="24aeb-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="24aeb-112">Dodaj <xref:System.Windows.Forms.ToolTip> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="24aeb-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="24aeb-113">Wybierz kontrolkę, która będzie wyświetlenia wskazówki lub dodanie go do formularza.</span><span class="sxs-lookup"><span data-stu-id="24aeb-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="24aeb-114">W **właściwości** ustaw **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstu.</span><span class="sxs-lookup"><span data-stu-id="24aeb-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24aeb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24aeb-115">See Also</span></span>  
 [<span data-ttu-id="24aeb-116">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="24aeb-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="24aeb-117">Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24aeb-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="24aeb-118">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="24aeb-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
