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
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933700"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f111e-102">Instrukcje: pobieranie i ustawianie bieżącej komórki w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f111e-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f111e-103">Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga, aby programowo wykryć, która komórka jest obecnie aktywna.</span><span class="sxs-lookup"><span data-stu-id="f111e-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="f111e-104">Może być również konieczne Zmiana bieżącej komórki.</span><span class="sxs-lookup"><span data-stu-id="f111e-104">You may also need to change the current cell.</span></span> <span data-ttu-id="f111e-105">Te zadania można wykonać przy użyciu <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f111e-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f111e-106">Nie można ustawić bieżącej komórki w wierszu lub kolumnie, która ma <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> `false`ustawioną właściwość.</span><span class="sxs-lookup"><span data-stu-id="f111e-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="f111e-107">W zależności <xref:System.Windows.Forms.DataGridView> od trybu zaznaczania kontrolki Zmiana bieżącej komórki może zmienić zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="f111e-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="f111e-108">Aby uzyskać więcej informacji, zobacz [Tryby wyboru w kontrolce DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f111e-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="f111e-109">Aby programowo pobrać bieżącą komórkę</span><span class="sxs-lookup"><span data-stu-id="f111e-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="f111e-110"><xref:System.Windows.Forms.DataGridView> Użyj właściwości<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f111e-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="f111e-111">Aby programowo ustawić bieżącą komórkę</span><span class="sxs-lookup"><span data-stu-id="f111e-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="f111e-112"><xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Ustaw Właściwość<xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="f111e-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f111e-113">W poniższym przykładzie kodu bieżąca komórka jest ustawiona na wiersz 0, kolumna 1.</span><span class="sxs-lookup"><span data-stu-id="f111e-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f111e-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f111e-114">Compiling the Code</span></span>  
 <span data-ttu-id="f111e-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f111e-115">This example requires:</span></span>  
  
- <span data-ttu-id="f111e-116"><xref:System.Windows.Forms.Button>kontrolki `getCurrentCellButton` nazwane `setCurrentCellButton`i.</span><span class="sxs-lookup"><span data-stu-id="f111e-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="f111e-117">W wizualizacji C#, należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f111e-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="f111e-118">Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="f111e-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f111e-119">Odwołania do <xref:System?displayProperty=nameWithType> zestawów i <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f111e-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f111e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f111e-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f111e-121">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f111e-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="f111e-122">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f111e-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
