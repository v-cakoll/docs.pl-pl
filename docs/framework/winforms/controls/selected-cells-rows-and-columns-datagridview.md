---
title: 'Instrukcje: pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960516"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="46088-102">Instrukcje: pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="46088-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="46088-103">Możesz pobrać zaznaczone komórki, <xref:System.Windows.Forms.DataGridView> wiersze lub kolumny z kontrolki, używając odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="46088-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="46088-104">W poniższych procedurach zostaną wyświetlone zaznaczone komórki i zostanie wyświetlony indeks <xref:System.Windows.Forms.MessageBox>wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="46088-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="46088-105">Aby pobrać zaznaczone komórki w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="46088-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="46088-106"><xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Użyj właściwości.</span><span class="sxs-lookup"><span data-stu-id="46088-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="46088-107">Użyj metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> , aby uniknąć wyświetlania potencjalnie dużej liczby komórek.</span><span class="sxs-lookup"><span data-stu-id="46088-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="46088-108">Aby pobrać wybrane wiersze w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="46088-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="46088-109"><xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Użyj właściwości.</span><span class="sxs-lookup"><span data-stu-id="46088-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="46088-110">Aby umożliwić użytkownikom Zaznaczanie wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="46088-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="46088-111">Aby pobrać wybrane kolumny w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="46088-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="46088-112"><xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> Użyj właściwości.</span><span class="sxs-lookup"><span data-stu-id="46088-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="46088-113">Aby umożliwić użytkownikom Wybieranie kolumn, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="46088-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46088-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="46088-114">Compiling the Code</span></span>  
 <span data-ttu-id="46088-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="46088-115">This example requires:</span></span>  
  
- <span data-ttu-id="46088-116"><xref:System.Windows.Forms.Button>kontrolki `selectedCellsButton`o `selectedRowsButton`nazwach `selectedColumnsButton`, i, każdy z obsługą <xref:System.Windows.Forms.Control.Click> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="46088-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="46088-117">Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="46088-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="46088-118">Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Windows.Forms?displayProperty=nameWithType>i. <xref:System.Text?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="46088-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="46088-119">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="46088-119">Robust Programming</span></span>  
 <span data-ttu-id="46088-120">Kolekcje opisane w tym temacie nie działają efektywnie w przypadku wybrania dużej liczby komórek, wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="46088-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="46088-121">Aby uzyskać więcej informacji na temat używania tych kolekcji z dużymi ilościami danych, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="46088-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46088-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46088-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="46088-123">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46088-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
