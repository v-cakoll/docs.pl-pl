---
title: Wykonaj akcję niestandardową na podstawie zmian w komórce kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: a809134b0a79bc9685c5b84acce58b4c61b5c526
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744284"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>Porady: wykonywanie niestandardowej akcji na podstawie zmian w komórce formantu DataGridView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.DataGridView> ma wiele zdarzeń, których można użyć do wykrywania zmian w stanie <xref:System.Windows.Forms.DataGridView> komórek. Dwa najczęściej używane są zdarzeniami <xref:System.Windows.Forms.DataGridView.CellValueChanged> i <xref:System.Windows.Forms.DataGridView.CellStateChanged>.  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a>Aby wykryć zmiany wartości w komórkach DataGridView  
  
- Napisz procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValueChanged>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a>Aby wykryć zmiany w Stanach komórek DataGridView  
  
- Napisz procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellStateChanged>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`. W C#przypadku programu programy obsługi zdarzeń muszą być połączone z odpowiednimi zdarzeniami.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
