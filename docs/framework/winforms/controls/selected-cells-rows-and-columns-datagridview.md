---
title: 'Instrukcje: Pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 95229f1915b25962a700a7d6aced0a012bbe6657
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626917"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d05f1-102">Instrukcje: Pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05f1-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d05f1-103">Możesz uzyskać zaznaczonych komórek, wierszy i kolumn z <xref:System.Windows.Forms.DataGridView> sterowania za pomocą odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="d05f1-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="d05f1-104">W poniższych procedurach spowoduje pobieranie wybranych komórek i wyświetlania ich indeksów wierszy i kolumn w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d05f1-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="d05f1-105">Aby uzyskać zaznaczonych komórek w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="d05f1-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="d05f1-106">Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d05f1-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d05f1-107">Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metodę, aby uniknąć wyświetlania potencjalnie dużą liczbę komórek.</span><span class="sxs-lookup"><span data-stu-id="d05f1-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="d05f1-108">Aby uzyskać wybranych wierszy w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="d05f1-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="d05f1-109">Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d05f1-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="d05f1-110">Aby umożliwić użytkownikom w celu wybrania wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="d05f1-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="d05f1-111">Aby uzyskać wybranych kolumn w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="d05f1-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="d05f1-112">Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d05f1-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="d05f1-113">Aby umożliwić użytkownikom wybrać kolumny, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="d05f1-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d05f1-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d05f1-114">Compiling the Code</span></span>  
 <span data-ttu-id="d05f1-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d05f1-115">This example requires:</span></span>  
  
-   <span data-ttu-id="d05f1-116"><xref:System.Windows.Forms.Button> kontrolki o nazwie `selectedCellsButton`, `selectedRowsButton`, i `selectedColumnsButton`, każdy z obsługi <xref:System.Windows.Forms.Control.Click> dołączone zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d05f1-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="d05f1-117">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="d05f1-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="d05f1-118">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Text?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="d05f1-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d05f1-119">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d05f1-119">Robust Programming</span></span>  
 <span data-ttu-id="d05f1-120">Kolekcje opisane w tym temacie należy wykonywać efektywne, gdy wybrano dużą liczbę komórek, wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="d05f1-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="d05f1-121">Aby uzyskać więcej informacji o używaniu tych kolekcji zawierających duże ilości danych, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d05f1-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05f1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d05f1-122">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="d05f1-123">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05f1-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
