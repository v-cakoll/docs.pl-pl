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
ms.openlocfilehash: 689b06e8fbebe490f79ab6c12f144546472a95ff
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087222"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="91365-102">Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="91365-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="91365-103">Możesz ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie lub w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="91365-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="91365-104">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [— informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="91365-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91365-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="91365-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="91365-106">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="91365-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="91365-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="91365-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="91365-108">Aby programowo ustawić etykietkę narzędzia</span><span class="sxs-lookup"><span data-stu-id="91365-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="91365-109">Dodaj kontrolkę która będzie wyświetlana etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="91365-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="91365-110">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="91365-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="91365-111">Aby ustawić etykietkę narzędzi w Projektancie</span><span class="sxs-lookup"><span data-stu-id="91365-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="91365-112">Dodaj <xref:System.Windows.Forms.ToolTip> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="91365-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="91365-113">Wybierz kontrolkę która będzie wyświetlić wskazówkę, albo dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="91365-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="91365-114">W **właściwości** oknie **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="91365-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="91365-115">Aby usunąć etykietka narzędzia programistyczne</span><span class="sxs-lookup"><span data-stu-id="91365-115">To remove a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="91365-116">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="91365-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="91365-117">Aby usunąć etykietki narzędzia w Projektancie</span><span class="sxs-lookup"><span data-stu-id="91365-117">To remove a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="91365-118">Wybierz kontrolkę która jest wyświetlana etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="91365-118">Select the control that is displaying the ToolTip.</span></span>  
  
2.  <span data-ttu-id="91365-119">W **właściwości** oknie Usuwanie tekstu z **etykietki narzędzia w ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="91365-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="91365-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91365-120">See Also</span></span>  
- [<span data-ttu-id="91365-121">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="91365-121">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
- [<span data-ttu-id="91365-122">Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91365-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
- [<span data-ttu-id="91365-123">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="91365-123">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
