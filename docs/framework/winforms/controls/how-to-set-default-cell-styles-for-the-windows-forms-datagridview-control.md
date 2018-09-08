---
title: 'Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 072a9ce7e28983683ac1104b70c160cf5eea12b7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130987"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows
Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić domyślnych stylów komórki dla całego kontroli i określonych kolumn i wierszy. Te ustawienia domyślne odfiltrować z poziomu kontroli na poziomie kolumny, a następnie na poziomie wiersza, a następnie na poziomie komórki. Jeśli konkretny <xref:System.Windows.Forms.DataGridViewCellStyle> właściwość nie jest ustawiona na poziomie komórki, używane jest domyślne ustawienie właściwości na poziomie wiersza. Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest domyślne ustawienie kolumny. Na koniec Jeśli właściwość również nie jest ustawiony na poziomie kolumny, a wartość domyślna <xref:System.Windows.Forms.DataGridView> ustawienie jest używane. To ustawienie można uniknąć konieczności duplikowania ustawienia właściwości na różnych poziomach. Na każdym poziomie wystarczy określić style, które różnią się od poziomami wyższymi. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  Zobacz też [jak: Ustaw domyślnych stylów komórek i formatów danych w Windows Forms DataGridView sterowania za pomocą projektanta](https://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Aby ustawić wartości domyślne style komórki programowe  
  
1.  Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane w drodze <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  Utwórz i zainicjuj nowe <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty do użycia przez wiele wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  Ustaw `DefaultCellStyle` właściwości określonych wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby osiągnąć maksymalną skalowalność podczas pracy z bardzo dużych zestawów danych, powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które za pomocą tego samego stylów, zamiast ponownego obliczenia właściwości stylu dla poszczególnych elementów osobno. Ponadto należy utworzyć udostępnione wiersze i uzyskiwać do nich dostęp za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
