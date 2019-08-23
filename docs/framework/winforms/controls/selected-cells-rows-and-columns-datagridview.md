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
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy systemu Windows
Możesz pobrać zaznaczone komórki, <xref:System.Windows.Forms.DataGridView> wiersze lub kolumny z kontrolki, używając odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. W poniższych procedurach zostaną wyświetlone zaznaczone komórki i zostanie wyświetlony indeks <xref:System.Windows.Forms.MessageBox>wierszy i kolumn.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Aby pobrać zaznaczone komórki w formancie DataGridView  
  
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Użyj właściwości.  
  
    > [!NOTE]
    > Użyj metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> , aby uniknąć wyświetlania potencjalnie dużej liczby komórek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Aby pobrać wybrane wiersze w formancie DataGridView  
  
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Użyj właściwości. Aby umożliwić użytkownikom Zaznaczanie wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Aby pobrać wybrane kolumny w formancie DataGridView  
  
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> Użyj właściwości. Aby umożliwić użytkownikom Wybieranie kolumn, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button>kontrolki `selectedCellsButton`o `selectedRowsButton`nazwach `selectedColumnsButton`, i, każdy z obsługą <xref:System.Windows.Forms.Control.Click> zdarzenia.  
  
- Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView>  
  
- Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Windows.Forms?displayProperty=nameWithType>i. <xref:System.Text?displayProperty=nameWithType>  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kolekcje opisane w tym temacie nie działają efektywnie w przypadku wybrania dużej liczby komórek, wierszy lub kolumn. Aby uzyskać więcej informacji na temat używania tych kolekcji z dużymi ilościami danych, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
