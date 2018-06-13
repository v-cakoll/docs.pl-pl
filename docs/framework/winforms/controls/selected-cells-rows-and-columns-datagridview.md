---
title: 'Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: a1d2338250abbced89ef7821d02edc654d26d7fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539109"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows
Można uzyskać zaznaczonych komórek, wierszy i kolumn z <xref:System.Windows.Forms.DataGridView> formantu przy użyciu odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. W poniższych procedurach, będzie pobrać zaznaczonych komórek i wyświetlić ich indeksy wierszy i kolumn w <xref:System.Windows.Forms.MessageBox>.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Aby uzyskać zaznaczonych komórek w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.  
  
    > [!NOTE]
    >  Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metodę, aby uniknąć wyświetlania potencjalnie dużą liczbę komórek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Aby uzyskać wybranych wierszy w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości. Aby umożliwić użytkownikom wybierz wiersze, musisz ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Aby uzyskać wybranych kolumn w formancie DataGridView  
  
-   Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości. Aby umożliwić użytkownikom zaznaczyć kolumny, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   <xref:System.Windows.Forms.Button> formanty o nazwie `selectedCellsButton`, `selectedRowsButton`, i `selectedColumnsButton`, każde z nich obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń dołączony.  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Text?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kolekcje opisanych w tym temacie należy wykonywać wydajnie, jeśli wybrano dużą liczbę komórek, wierszy lub kolumn. Aby uzyskać więcej informacji o korzystaniu z tych kolekcji z dużych ilości danych, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
