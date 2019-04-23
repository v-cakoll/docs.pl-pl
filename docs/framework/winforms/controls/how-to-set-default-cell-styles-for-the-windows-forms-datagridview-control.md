---
title: 'Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: e52729a4ff5b95cd45a970068f1874ad77f8ce35
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319199"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Instrukcje: ustawianie domyślnych stylów komórki dla kontrolki DataGridView formularzy systemu Windows
Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić domyślnych stylów komórki dla całego kontroli i określonych kolumn i wierszy. Te ustawienia domyślne odfiltrować z poziomu kontroli na poziomie kolumny, a następnie na poziomie wiersza, a następnie na poziomie komórki. Jeśli konkretny <xref:System.Windows.Forms.DataGridViewCellStyle> właściwość nie jest ustawiona na poziomie komórki, używane jest domyślne ustawienie właściwości na poziomie wiersza. Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest domyślne ustawienie kolumny. Na koniec Jeśli właściwość również nie jest ustawiony na poziomie kolumny, a wartość domyślna <xref:System.Windows.Forms.DataGridView> ustawienie jest używane. To ustawienie można uniknąć konieczności duplikowania ustawienia właściwości na różnych poziomach. Na każdym poziomie wystarczy określić style, które różnią się od poziomami wyższymi. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  Zobacz też [jak: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView, które przy użyciu narzędzia Projektant formularzy Windows](default-cell-styles-datagridview.md).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Aby ustawić wartości domyślne style komórki programowe  
  
1. Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane w drodze <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. Utwórz i zainicjuj nowe <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty do użycia przez wiele wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. Ustaw `DefaultCellStyle` właściwości określonych wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby osiągnąć maksymalną skalowalność podczas pracy z bardzo dużych zestawów danych, powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które za pomocą tego samego stylów, zamiast ponownego obliczenia właściwości stylu dla poszczególnych elementów osobno. Ponadto należy utworzyć udostępnione wiersze i uzyskiwać do nich dostęp za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
