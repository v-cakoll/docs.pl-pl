---
title: Dostosowywanie sortowania w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743181"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="720f3-102">Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="720f3-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="720f3-103">Formant <xref:System.Windows.Forms.DataGridView> zapewnia automatyczne sortowanie, ale w zależności od potrzeb może być konieczne dostosowanie operacji sortowania.</span><span class="sxs-lookup"><span data-stu-id="720f3-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="720f3-104">Można na przykład użyć sortowania programistycznego, aby utworzyć alternatywny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="720f3-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="720f3-105">Alternatywnie można obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.SortCompare> lub wywoływać `Sort(IComparer)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A> w celu uzyskania większej elastyczności sortowania, takiej jak sortowanie wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="720f3-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="720f3-106">Poniższe przykłady kodu przedstawiają te trzy podejścia do sortowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="720f3-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="720f3-107">Aby uzyskać więcej informacji, zobacz [tryby sortowania kolumn w kontrolce DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="720f3-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="720f3-108">Sortowanie programistyczne</span><span class="sxs-lookup"><span data-stu-id="720f3-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="720f3-109">Poniższy przykład kodu demonstruje programistyczne sortowanie przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A>, aby określić kierunek sortowania i Właściwość <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A>, aby ręcznie ustawić Symbol sortowania.</span><span class="sxs-lookup"><span data-stu-id="720f3-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="720f3-110">`Sort(DataGridViewColumn,ListSortDirection)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A> jest używane do sortowania danych tylko w jednej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="720f3-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="720f3-111">Sortowanie niestandardowe przy użyciu zdarzenia SortCompare</span><span class="sxs-lookup"><span data-stu-id="720f3-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="720f3-112">Poniższy przykład kodu demonstruje niestandardowe sortowanie przy użyciu programu obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.SortCompare>.</span><span class="sxs-lookup"><span data-stu-id="720f3-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="720f3-113">Wybrany <xref:System.Windows.Forms.DataGridViewColumn> jest sortowany i, jeśli w kolumnie znajdują się zduplikowane wartości, kolumna ID jest używana do określenia kolejności końcowej.</span><span class="sxs-lookup"><span data-stu-id="720f3-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="720f3-114">Sortowanie niestandardowe przy użyciu interfejsu IComparer</span><span class="sxs-lookup"><span data-stu-id="720f3-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="720f3-115">Poniższy przykład kodu demonstruje niestandardowe sortowanie przy użyciu `Sort(IComparer)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A>, która pobiera implementację interfejsu <xref:System.Collections.IComparer> do wykonywania sortowania wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="720f3-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="720f3-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="720f3-116">Compiling the Code</span></span>  
 <span data-ttu-id="720f3-117">Te przykłady wymagają:</span><span class="sxs-lookup"><span data-stu-id="720f3-117">These examples require:</span></span>  
  
- <span data-ttu-id="720f3-118">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="720f3-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720f3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="720f3-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="720f3-120">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="720f3-120">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="720f3-121">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="720f3-121">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="720f3-122">Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="720f3-122">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
