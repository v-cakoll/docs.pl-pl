---
title: Ustawianie trybów sortowania kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742996"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a9b3b-102">Porady: ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a9b3b-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a9b3b-103">W kontrolce <xref:System.Windows.Forms.DataGridView> kolumny pól tekstowych używają automatycznego sortowania domyślnie, natomiast inne typy kolumn nie są sortowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="a9b3b-104">Czasami chcesz zastąpić te ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="a9b3b-105">Na przykład można wyświetlić obrazy zamiast tekstu, liczb lub wartości komórek wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="a9b3b-106">Gdy obrazy nie mogą być sortowane, podstawowe wartości, które reprezentują, mogą być sortowane.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="a9b3b-107">W formancie <xref:System.Windows.Forms.DataGridView> wartość właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> kolumny określa zachowanie sortowania.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="a9b3b-108">Poniższa procedura przedstawia `Priority` kolumnie z [: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a9b3b-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="a9b3b-109">Ta kolumna jest kolumną obrazu i domyślnie nie jest sortowany.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="a9b3b-110">Zawiera rzeczywiste wartości komórek, które są ciągami, jednak można je posortować automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="a9b3b-111">Aby ustawić tryb sortowania dla kolumny</span><span class="sxs-lookup"><span data-stu-id="a9b3b-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="a9b3b-112">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9b3b-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a9b3b-113">Compiling the Code</span></span>  
 <span data-ttu-id="a9b3b-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a9b3b-114">This example requires:</span></span>  
  
- <span data-ttu-id="a9b3b-115">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="a9b3b-116">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9b3b-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b3b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9b3b-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a9b3b-118">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9b3b-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9b3b-119">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9b3b-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9b3b-120">Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9b3b-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
