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
ms.openlocfilehash: cd3e88b5b01b67f677fbe203a0db9c4de7fe67ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160553"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy systemu Windows
Możesz uzyskać zaznaczonych komórek, wierszy i kolumn z <xref:System.Windows.Forms.DataGridView> sterowania za pomocą odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. W poniższych procedurach spowoduje pobieranie wybranych komórek i wyświetlania ich indeksów wierszy i kolumn w <xref:System.Windows.Forms.MessageBox>.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Aby uzyskać zaznaczonych komórek w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.  
  
    > [!NOTE]
    >  Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metodę, aby uniknąć wyświetlania potencjalnie dużą liczbę komórek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Aby uzyskać wybranych wierszy w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości. Aby umożliwić użytkownikom w celu wybrania wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Aby uzyskać wybranych kolumn w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości. Aby umożliwić użytkownikom wybrać kolumny, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   <xref:System.Windows.Forms.Button> kontrolki o nazwie `selectedCellsButton`, `selectedRowsButton`, i `selectedColumnsButton`, każdy z obsługi <xref:System.Windows.Forms.Control.Click> dołączone zdarzenia.  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Text?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kolekcje opisane w tym temacie należy wykonywać efektywne, gdy wybrano dużą liczbę komórek, wierszy lub kolumn. Aby uzyskać więcej informacji o używaniu tych kolekcji zawierających duże ilości danych, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Wybór i używanie schowka za pomocą składnika DataGridView formularzy systemu Windows](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
