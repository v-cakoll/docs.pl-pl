---
title: 'Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: fb71a6e3259d3007e11f528377c95a9c4cbeb023
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096982"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="db126-102">Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="db126-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="db126-103">Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga się, że programowo odkryjesz komórki, która jest obecnie aktywna.</span><span class="sxs-lookup"><span data-stu-id="db126-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="db126-104">Również może być konieczna zmiana bieżącej komórki.</span><span class="sxs-lookup"><span data-stu-id="db126-104">You may also need to change the current cell.</span></span> <span data-ttu-id="db126-105">Możesz wykonywać te zadania za pomocą <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="db126-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db126-106">Nie można ustawić bieżącej komórki w wierszu lub kolumnie, który ma jej <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="db126-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="db126-107">W zależności od <xref:System.Windows.Forms.DataGridView> trybu zaznaczania kontrolki, zmieniania bieżącej komórki dokonać zmian.</span><span class="sxs-lookup"><span data-stu-id="db126-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="db126-108">Aby uzyskać więcej informacji, zobacz [tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="db126-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="db126-109">Aby programowo uzyskać bieżącej komórki</span><span class="sxs-lookup"><span data-stu-id="db126-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="db126-110">Użyj <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="db126-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="db126-111">Aby programowo ustawić bieżącej komórki</span><span class="sxs-lookup"><span data-stu-id="db126-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="db126-112">Ustaw <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwość <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="db126-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="db126-113">W poniższym przykładzie kodu bieżącej komórki jest równa 0, kolumna 1 wiersz.</span><span class="sxs-lookup"><span data-stu-id="db126-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db126-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="db126-114">Compiling the Code</span></span>  
 <span data-ttu-id="db126-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="db126-115">This example requires:</span></span>  
  
-   <span data-ttu-id="db126-116"><xref:System.Windows.Forms.Button> kontrolki o nazwie `getCurrentCellButton` i `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="db126-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="db126-117">W elemencie wizualnym C#, należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla każdego przycisku do obsługi skojarzone ze zdarzeniem w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="db126-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="db126-118">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="db126-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="db126-119">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="db126-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db126-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db126-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="db126-121">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db126-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="db126-122">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db126-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
