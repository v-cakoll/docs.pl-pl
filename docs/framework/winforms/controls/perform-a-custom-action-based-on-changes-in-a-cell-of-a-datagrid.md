---
title: 'Instrukcje: Wykonywanie niestandardowej akcji na podstawie zmian w komórce formantu DataGridView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: ad1c60c34fc5461de21e2ad5d4d02f5b2abd6dfd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705587"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>Instrukcje: Wykonywanie niestandardowej akcji na podstawie zmian w komórce formantu DataGridView formularzy Windows
<xref:System.Windows.Forms.DataGridView> Kontroli zawiera liczbę zdarzeń, można użyć do wykrywania zmian w stanie <xref:System.Windows.Forms.DataGridView> komórek. Dwa najczęściej używane są <xref:System.Windows.Forms.DataGridView.CellValueChanged> i <xref:System.Windows.Forms.DataGridView.CellStateChanged> zdarzenia.  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a>Aby wykryć zmiany wartości komórek DataGridView  
  
-   Pisanie programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueChanged> zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a>Aby wykryć zmiany w Stanach komórek DataGridView  
  
-   Pisanie programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellStateChanged> zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`. Aby uzyskać C#, programy obsługi zdarzeń musi być podłączony do pokrewnych zdarzeń.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
