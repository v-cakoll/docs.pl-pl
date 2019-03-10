---
title: 'Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: a0ef450559a1106de635c6d3b16891c23c41b050
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725054"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2ae57-102">Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ae57-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2ae57-103">W <xref:System.Windows.Forms.DataGridView> kontrolka, tekst pola kolumny używać automatycznego sortowania domyślnie, podczas gdy inne typy kolumn nie są sortowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2ae57-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="2ae57-104">Czasami chcesz przesłonić te ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="2ae57-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="2ae57-105">Na przykład można wyświetlić obrazów zamiast tekstu, liczby lub wartości komórki wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2ae57-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="2ae57-106">Gdy obrazy nie można sortować, podstawowej wartości, które reprezentują one można sortować.</span><span class="sxs-lookup"><span data-stu-id="2ae57-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="2ae57-107">W <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> wartość właściwości kolumny określa jego zachowanie sortowania.</span><span class="sxs-lookup"><span data-stu-id="2ae57-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="2ae57-108">Poniższej procedury `Priority` kolumny z [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ae57-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="2ae57-109">Ta kolumna jest kolumną obrazu i nie jest sortowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="2ae57-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="2ae57-110">Zawiera wartości rzeczywiste komórki, które są ciągami, jednak, więc może być sortowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2ae57-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="2ae57-111">Aby ustawić tryb sortowania dla kolumny</span><span class="sxs-lookup"><span data-stu-id="2ae57-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="2ae57-112">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ae57-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ae57-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2ae57-113">Compiling the Code</span></span>  
 <span data-ttu-id="2ae57-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2ae57-114">This example requires:</span></span>  
  
-   <span data-ttu-id="2ae57-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="2ae57-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="2ae57-116">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="2ae57-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae57-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ae57-117">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2ae57-118">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ae57-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ae57-119">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ae57-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ae57-120">Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ae57-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
