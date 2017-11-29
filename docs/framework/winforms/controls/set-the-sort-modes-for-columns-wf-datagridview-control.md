---
title: "Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows"
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
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1c5b0447895b0ca5c67fff054d88da0d0107c5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bec55-102">Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bec55-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bec55-103">W <xref:System.Windows.Forms.DataGridView> kolumny pole tekstowe kontroli, użyj automatyczne sortowanie domyślne, podczas gdy inne typy kolumn nie są automatycznie sortowane.</span><span class="sxs-lookup"><span data-stu-id="bec55-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="bec55-104">Czasami można przesłonić te ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="bec55-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="bec55-105">Na przykład można wyświetlić obrazy zamiast tekstu, liczby lub wartości wyliczenia komórki.</span><span class="sxs-lookup"><span data-stu-id="bec55-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="bec55-106">Gdy nie można sortować obrazy, wartości podstawowych, które reprezentują można sortować.</span><span class="sxs-lookup"><span data-stu-id="bec55-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="bec55-107">W <xref:System.Windows.Forms.DataGridView> kontroli, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości kolumny określa zachowanie sortowania.</span><span class="sxs-lookup"><span data-stu-id="bec55-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="bec55-108">Poniżej przedstawiono procedurę `Priority` kolumny z [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bec55-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="bec55-109">Ta kolumna jest kolumną obrazu i nie jest sortowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="bec55-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="bec55-110">Zawiera wartości rzeczywistych komórek, które są ciągami, jednak, mogą być sortowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="bec55-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="bec55-111">Aby ustawić tryb sortowania kolumny</span><span class="sxs-lookup"><span data-stu-id="bec55-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="bec55-112">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bec55-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bec55-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bec55-113">Compiling the Code</span></span>  
 <span data-ttu-id="bec55-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="bec55-114">This example requires:</span></span>  
  
-   <span data-ttu-id="bec55-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="bec55-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="bec55-116">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="bec55-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec55-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bec55-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="bec55-118">Sortowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bec55-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="bec55-119">Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bec55-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="bec55-120">Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bec55-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
