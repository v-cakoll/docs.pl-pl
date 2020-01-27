---
title: Dostosowywanie sortowania w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743181"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> zapewnia automatyczne sortowanie, ale w zależności od potrzeb może być konieczne dostosowanie operacji sortowania. Można na przykład użyć sortowania programistycznego, aby utworzyć alternatywny interfejs użytkownika. Alternatywnie można obsłużyć zdarzenie <xref:System.Windows.Forms.DataGridView.SortCompare> lub wywoływać `Sort(IComparer)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A> w celu uzyskania większej elastyczności sortowania, takiej jak sortowanie wielu kolumn.  
  
 Poniższe przykłady kodu przedstawiają te trzy podejścia do sortowania niestandardowego. Aby uzyskać więcej informacji, zobacz [tryby sortowania kolumn w kontrolce DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Sortowanie programistyczne  
 Poniższy przykład kodu demonstruje programistyczne sortowanie przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A>, aby określić kierunek sortowania i Właściwość <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A>, aby ręcznie ustawić Symbol sortowania. `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A> jest używane do sortowania danych tylko w jednej kolumnie.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Sortowanie niestandardowe przy użyciu zdarzenia SortCompare  
 Poniższy przykład kodu demonstruje niestandardowe sortowanie przy użyciu programu obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.SortCompare>. Wybrany <xref:System.Windows.Forms.DataGridViewColumn> jest sortowany i, jeśli w kolumnie znajdują się zduplikowane wartości, kolumna ID jest używana do określenia kolejności końcowej.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Sortowanie niestandardowe przy użyciu interfejsu IComparer  
 Poniższy przykład kodu demonstruje niestandardowe sortowanie przy użyciu `Sort(IComparer)` Przeciążenie metody <xref:System.Windows.Forms.DataGridView.Sort%2A>, która pobiera implementację interfejsu <xref:System.Collections.IComparer> do wykonywania sortowania wielu kolumn.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Te przykłady wymagają:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
