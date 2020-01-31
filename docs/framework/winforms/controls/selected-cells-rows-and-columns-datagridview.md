---
title: Pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 0079c590ee6e4732523fd50be157bd58ec1bfb1b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743071"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows
Możesz pobrać zaznaczone komórki, wiersze lub kolumny z kontrolki <xref:System.Windows.Forms.DataGridView>, używając odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. W poniższych procedurach zostaną wyświetlone zaznaczone komórki i zostanie wyświetlony indeks wierszy i kolumn w <xref:System.Windows.Forms.MessageBox>.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Aby pobrać zaznaczone komórki w formancie DataGridView  
  
- Użyj właściwości <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.  
  
    > [!NOTE]
    > Użyj metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>, aby uniknąć wyświetlania potencjalnie dużej liczby komórek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Aby pobrać wybrane wiersze w formancie DataGridView  
  
- Użyj właściwości <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Aby umożliwić użytkownikom Zaznaczanie wierszy, należy ustawić właściwość <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Aby pobrać wybrane kolumny w formancie DataGridView  
  
- Użyj właściwości <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Aby umożliwić użytkownikom Wybieranie kolumn, należy ustawić właściwość <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button> kontrolki o nazwach `selectedCellsButton`, `selectedRowsButton`i `selectedColumnsButton`, z których każdy ma programy obsługi dla dołączonego zdarzenia <xref:System.Windows.Forms.Control.Click>.  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>i <xref:System.Text?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Kolekcje opisane w tym temacie nie działają efektywnie w przypadku wybrania dużej liczby komórek, wierszy lub kolumn. Aby uzyskać więcej informacji na temat używania tych kolekcji z dużymi ilościami danych, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
