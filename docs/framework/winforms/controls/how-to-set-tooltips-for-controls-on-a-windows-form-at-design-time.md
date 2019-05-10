---
title: 'Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211684"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="c1355-102">Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c1355-102">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="c1355-103">Możesz ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie lub w programie Windows Forms Designer w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1355-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="c1355-104">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [— informacje o składniku ToolTip](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c1355-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="c1355-105">Programowe Ustawianie etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="c1355-105">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="c1355-106">Dodaj kontrolkę która będzie wyświetlana etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c1355-106">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="c1355-107">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="c1355-107">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="c1355-108">Ustawić etykietkę narzędzi w Projektancie</span><span class="sxs-lookup"><span data-stu-id="c1355-108">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="c1355-109">W programie Visual Studio, należy dodać <xref:System.Windows.Forms.ToolTip> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="c1355-109">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="c1355-110">Wybierz kontrolkę która będzie wyświetlić wskazówkę, albo dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="c1355-110">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="c1355-111">W **właściwości** oknie **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="c1355-111">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="c1355-112">Aby usunąć etykietka narzędzia programistyczne</span><span class="sxs-lookup"><span data-stu-id="c1355-112">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="c1355-113">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="c1355-113">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="c1355-114">Usuń etykietkę narzędzia w Projektancie</span><span class="sxs-lookup"><span data-stu-id="c1355-114">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="c1355-115">W programie Visual Studio wybierz kontrolkę która jest wyświetlana etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c1355-115">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="c1355-116">W **właściwości** oknie Usuwanie tekstu z **etykietki narzędzia w ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="c1355-116">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1355-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1355-117">See also</span></span>

- [<span data-ttu-id="c1355-118">ToolTip, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="c1355-118">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="c1355-119">Instrukcje: Zmienianie opóźnienia składnika ToolTip formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="c1355-119">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="c1355-120">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="c1355-120">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
