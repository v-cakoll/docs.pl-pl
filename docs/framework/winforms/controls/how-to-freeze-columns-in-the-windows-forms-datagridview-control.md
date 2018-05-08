---
title: 'Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6eb6fab4b147365221ba79a682c4eaf744d24b25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows
Gdy użytkownicy wyświetlać dane wyświetlane w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli, czasami muszą odwoływać się do jednej kolumny lub zestaw kolumn często. Na przykład podczas wyświetlania informacji klienta, który zawiera wiele kolumn tabeli, jest przydatne do wyświetlenia nazwy klienta przez cały czas podczas włączania obsługi innych kolumn przewinięcia poza region widoczny.  
  
 Aby osiągnąć ten problem, można zablokować kolumn w formancie. Po zablokowaniu kolumny zablokowanych również wszystkich kolumn po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej). Zablokowane kolumny pozostają bez zmian, gdy mogą być przewijane w innych kolumn.  
  
> [!NOTE]
>  Jeśli włączono zmiany układu kolumn zablokowane kolumny są traktowane jako grupę różne od kolumny. Użytkownicy można zmienić kolumny w każdej grupie, ale nie może przenieść kolumny z jednej grupy, do drugiego.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Właściwość kolumny określa, czy kolumna jest zawsze widocznych w siatce.  
  
 Brak obsługi dla tego zadania w programie Visual Studio.  Zobacz też [porady: blokowanie kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Aby zablokować kolumnę programowo  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> właściwości `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `AddToCartButton`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
