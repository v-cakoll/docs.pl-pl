---
title: Grupowanie kontrolek z kontrolką panelu przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745652"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="a3bc9-102">Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a3bc9-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="a3bc9-103">Kontrolki <xref:System.Windows.Forms.Panel> Windows Forms są używane do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="a3bc9-104">Istnieją trzy powody, dla których należy grupować formanty.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-104">There are three reasons to group controls.</span></span> <span data-ttu-id="a3bc9-105">Jednym z nich jest wizualne grupowanie elementów formularza dla czystego interfejsu użytkownika; innym jest programistyczne Grupowanie przycisków radiowych na przykład; ostatnim jest do przesuwania kontrolek jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="a3bc9-106">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="a3bc9-106">To create a group of controls</span></span>

1. <span data-ttu-id="a3bc9-107">Przeciągnij kontrolkę <xref:System.Windows.Forms.Panel> z karty **Windows Forms** przybornika na formularz.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="a3bc9-108">Dodaj inne kontrolki do panelu, rysując każdy wewnątrz panelu.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="a3bc9-109">Jeśli masz istniejące kontrolki, które chcesz umieścić w panelu, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, wybrać kontrolkę <xref:System.Windows.Forms.Panel>, a następnie wkleić ją do panelu.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="a3bc9-110">Możesz również przeciągnąć je do panelu.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="a3bc9-111">Obowiązkowe Jeśli chcesz dodać obramowanie do panelu, ustaw jego właściwość <xref:System.Windows.Forms.BorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="a3bc9-112">Dostępne są trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>i <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="a3bc9-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3bc9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3bc9-113">See also</span></span>

- [<span data-ttu-id="a3bc9-114">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a3bc9-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="a3bc9-115">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a3bc9-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="a3bc9-116">Instrukcje: ustawianie tła panelu</span><span class="sxs-lookup"><span data-stu-id="a3bc9-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
