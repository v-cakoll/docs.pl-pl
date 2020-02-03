---
title: Włączanie zmiany kolejności kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 681489cdb874677079e2577140040921e587d21e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745500"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Porady: włączanie zmiany układu kolumn w formancie DataGridView formularzy systemu Windows
Po włączeniu zmiany kolejności kolumn w kontrolce <xref:System.Windows.Forms.DataGridView> użytkownicy mogą przenieść kolumnę do nowej pozycji, przeciągając nagłówek kolumny za pomocą myszy. W kontrolce <xref:System.Windows.Forms.DataGridView> wartość właściwości <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> określa, czy użytkownicy mogą przenosić kolumny do różnych pozycji.  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zobacz również [instrukcje: Włączanie zmiany kolejności kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Aby programowo włączyć zmianę kolejności kolumn  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> na `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
