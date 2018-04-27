---
title: 'Porady: pobieranie i ustawianie bieżącej komórki w formancie DataGridView formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b53d135a1d019ce20dfc8c5c2c1ba59e5968306e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4542c-102">Porady: pobieranie i ustawianie bieżącej komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4542c-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4542c-103">Interakcja z <xref:System.Windows.Forms.DataGridView> często wymaga się, że programowo odkrywasz komórki, która jest obecnie aktywny.</span><span class="sxs-lookup"><span data-stu-id="4542c-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="4542c-104">Ponadto może być konieczna zmiana bieżącej komórki.</span><span class="sxs-lookup"><span data-stu-id="4542c-104">You may also need to change the current cell.</span></span> <span data-ttu-id="4542c-105">Można wykonać te zadania z <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4542c-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4542c-106">Nie można ustawić bieżącej komórki w wiersz lub kolumnę, która ma jego <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> ustawioną właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="4542c-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="4542c-107">W zależności od <xref:System.Windows.Forms.DataGridView> tryb zaznaczania formantu, zmiana bieżącej komórki można zmienić zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="4542c-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="4542c-108">Aby uzyskać więcej informacji, zobacz [tryby wyboru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="4542c-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="4542c-109">Aby programowo pobieranie bieżącej komórki</span><span class="sxs-lookup"><span data-stu-id="4542c-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="4542c-110">Użyj <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4542c-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="4542c-111">Aby programowo Ustawianie bieżącej komórki</span><span class="sxs-lookup"><span data-stu-id="4542c-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="4542c-112">Ustaw <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> właściwość <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="4542c-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4542c-113">W poniższym przykładzie kodu bieżącej komórki jest równa 0, kolumna 1 wiersz.</span><span class="sxs-lookup"><span data-stu-id="4542c-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4542c-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4542c-114">Compiling the Code</span></span>  
 <span data-ttu-id="4542c-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4542c-115">This example requires:</span></span>  
  
-   <span data-ttu-id="4542c-116"><xref:System.Windows.Forms.Button> formanty o nazwie `getCurrentCellButton` i `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="4542c-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="4542c-117">W środowisku Visual C#, należy dołączyć <xref:System.Windows.Forms.Control.Click> zdarzeń dla każdego przycisku do skojarzonego programu obsługi zdarzeń w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4542c-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="4542c-118">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="4542c-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="4542c-119">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="4542c-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4542c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4542c-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4542c-121">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4542c-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="4542c-122">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4542c-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
