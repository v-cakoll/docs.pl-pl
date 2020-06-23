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
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows
Możesz pobrać zaznaczone komórki, wiersze lub kolumny z <xref:System.Windows.Forms.DataGridView> kontrolki, używając odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> , i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> . W poniższych procedurach zostaną wyświetlone zaznaczone komórki i zostanie wyświetlony indeks wierszy i kolumn <xref:System.Windows.Forms.MessageBox> .  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Aby pobrać zaznaczone komórki w formancie DataGridView  
  
- Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.  
  
    > [!NOTE]
    > Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody, aby uniknąć wyświetlania potencjalnie dużej liczby komórek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Aby pobrać wybrane wiersze w formancie DataGridView  
  
- Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości. Aby umożliwić użytkownikom Zaznaczanie wierszy, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> Właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Aby pobrać wybrane kolumny w formancie DataGridView  
  
- Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości. Aby umożliwić użytkownikom Wybieranie kolumn, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> Właściwość na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- <xref:System.Windows.Forms.Button>kontrolki o nazwach `selectedCellsButton` , `selectedRowsButton` i `selectedColumnsButton` , każdy z obsługą <xref:System.Windows.Forms.Control.Click> zdarzenia.  
  
- <xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie `dataGridView1` .  
  
- Odwołania do <xref:System?displayProperty=nameWithType> zestawów, <xref:System.Windows.Forms?displayProperty=nameWithType> i <xref:System.Text?displayProperty=nameWithType> .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kolekcje opisane w tym temacie nie działają efektywnie w przypadku wybrania dużej liczby komórek, wierszy lub kolumn. Aby uzyskać więcej informacji na temat używania tych kolekcji z dużymi ilościami danych, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
