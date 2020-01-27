---
title: Pobieranie i Ustawianie bieżącej komórki w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745664"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="de3dc-102">Porady: pobieranie i ustawianie bieżącej komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="de3dc-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="de3dc-103">Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga, aby można było programowo wykryć, która komórka jest obecnie aktywna.</span><span class="sxs-lookup"><span data-stu-id="de3dc-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="de3dc-104">Może być również konieczne Zmiana bieżącej komórki.</span><span class="sxs-lookup"><span data-stu-id="de3dc-104">You may also need to change the current cell.</span></span> <span data-ttu-id="de3dc-105">Te zadania można wykonać za pomocą właściwości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.</span><span class="sxs-lookup"><span data-stu-id="de3dc-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de3dc-106">Nie można ustawić bieżącej komórki w wierszu lub kolumnie, która ma właściwość <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> ustawioną na `false`.</span><span class="sxs-lookup"><span data-stu-id="de3dc-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="de3dc-107">W zależności od trybu zaznaczania kontrolki <xref:System.Windows.Forms.DataGridView>, zmiana bieżącej komórki może zmienić zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="de3dc-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="de3dc-108">Aby uzyskać więcej informacji, zobacz [Tryby wyboru w kontrolce DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="de3dc-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="de3dc-109">Aby programowo pobrać bieżącą komórkę</span><span class="sxs-lookup"><span data-stu-id="de3dc-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="de3dc-110">Użyj właściwości <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="de3dc-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="de3dc-111">Aby programowo ustawić bieżącą komórkę</span><span class="sxs-lookup"><span data-stu-id="de3dc-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="de3dc-112">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="de3dc-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="de3dc-113">W poniższym przykładzie kodu bieżąca komórka jest ustawiona na wiersz 0, kolumna 1.</span><span class="sxs-lookup"><span data-stu-id="de3dc-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de3dc-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="de3dc-114">Compiling the Code</span></span>  
 <span data-ttu-id="de3dc-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="de3dc-115">This example requires:</span></span>  
  
- <span data-ttu-id="de3dc-116"><xref:System.Windows.Forms.Button> kontrolki o nazwach `getCurrentCellButton` i `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="de3dc-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="de3dc-117">W wizualizacji C#należy dołączyć zdarzenia <xref:System.Windows.Forms.Control.Click> dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="de3dc-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="de3dc-118">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="de3dc-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="de3dc-119">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de3dc-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3dc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de3dc-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="de3dc-121">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de3dc-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="de3dc-122">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de3dc-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
