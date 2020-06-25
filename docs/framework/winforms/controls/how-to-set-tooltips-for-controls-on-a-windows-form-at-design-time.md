---
title: 'Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania'
description: Dowiedz się, jak ustawić etykietki narzędzi dla formantów programowo lub w Projektant formularzy systemu Windows w programie Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325972"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="6eb2c-103">Porady: Ustawianie etykietek narzędzi dla kontrolek w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6eb2c-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="6eb2c-104">Można ustawić <xref:System.Windows.Forms.ToolTip> ciąg w kodzie lub w Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="6eb2c-105">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składnika, zobacz [Omówienie składnika etykietki narzędzia](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6eb2c-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="6eb2c-106">Programistyczne Ustawianie etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="6eb2c-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="6eb2c-107">Dodaj kontrolkę, która będzie wyświetlać etykietkę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="6eb2c-108">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="6eb2c-109">Ustawianie etykietki narzędzia w projektancie</span><span class="sxs-lookup"><span data-stu-id="6eb2c-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="6eb2c-110">W programie Visual Studio Dodaj <xref:System.Windows.Forms.ToolTip> składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="6eb2c-111">Wybierz kontrolkę, która będzie wyświetlać etykietkę narzędzia, lub Dodaj ją do formularza.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="6eb2c-112">W oknie **Właściwości** Ustaw **etykietkę narzędzia dla wartości ToolTip1** na odpowiedni ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="6eb2c-113">Aby programowo usunąć etykietkę narzędzia</span><span class="sxs-lookup"><span data-stu-id="6eb2c-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="6eb2c-114">Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

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

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="6eb2c-115">Usuwanie etykietki narzędzia w projektancie</span><span class="sxs-lookup"><span data-stu-id="6eb2c-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="6eb2c-116">W programie Visual Studio Wybierz kontrolkę wyświetlającą etykietkę narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="6eb2c-117">W oknie **Właściwości** Usuń tekst w **etykietce narzędzia ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="6eb2c-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb2c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6eb2c-118">See also</span></span>

- [<span data-ttu-id="6eb2c-119">ToolTip — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="6eb2c-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="6eb2c-120">Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6eb2c-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="6eb2c-121">ToolTip, składnik</span><span class="sxs-lookup"><span data-stu-id="6eb2c-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
