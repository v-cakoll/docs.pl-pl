---
title: Pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView
description: Dowiedz się, jak pobrać zaznaczone komórki, wiersze lub kolumny z kontrolki DataGridView przy użyciu odpowiednich właściwości.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904172"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="41559-103">Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="41559-103">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="41559-104">Możesz pobrać zaznaczone komórki, wiersze lub kolumny z <xref:System.Windows.Forms.DataGridView> kontrolki, używając odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> , i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> .</span><span class="sxs-lookup"><span data-stu-id="41559-104">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="41559-105">W poniższych procedurach zostaną wyświetlone zaznaczone komórki i zostanie wyświetlony indeks wierszy i kolumn <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="41559-105">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="41559-106">Aby pobrać zaznaczone komórki w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="41559-106">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="41559-107">Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="41559-107">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="41559-108">Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody, aby uniknąć wyświetlania potencjalnie dużej liczby komórek.</span><span class="sxs-lookup"><span data-stu-id="41559-108">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="41559-109">Aby pobrać wybrane wiersze w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="41559-109">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="41559-110">Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="41559-110">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="41559-111">Aby umożliwić użytkownikom Zaznaczanie wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> Właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="41559-111">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="41559-112">Aby pobrać wybrane kolumny w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="41559-112">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="41559-113">Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="41559-113">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="41559-114">Aby umożliwić użytkownikom Wybieranie kolumn, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> Właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="41559-114">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41559-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="41559-115">Compiling the Code</span></span>  
 <span data-ttu-id="41559-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="41559-116">This example requires:</span></span>  
  
- <span data-ttu-id="41559-117"><xref:System.Windows.Forms.Button>kontrolki o nazwach `selectedCellsButton` , `selectedRowsButton` i `selectedColumnsButton` , każdy z obsługą <xref:System.Windows.Forms.Control.Click> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="41559-117"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="41559-118"><xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie `dataGridView1` .</span><span class="sxs-lookup"><span data-stu-id="41559-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="41559-119">Odwołania do <xref:System?displayProperty=nameWithType> zestawów, <xref:System.Windows.Forms?displayProperty=nameWithType> i <xref:System.Text?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="41559-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41559-120">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="41559-120">Robust Programming</span></span>  
 <span data-ttu-id="41559-121">Kolekcje opisane w tym temacie nie działają efektywnie w przypadku wybrania dużej liczby komórek, wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="41559-121">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="41559-122">Aby uzyskać więcej informacji na temat używania tych kolekcji z dużymi ilościami danych, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="41559-122">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41559-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41559-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="41559-124">Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41559-124">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
