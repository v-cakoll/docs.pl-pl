---
title: Określanie kolumn jako tylko do odczytu w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736182"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows
Nie wszystkie dane są przeznaczone do edycji. W kontrolce <xref:System.Windows.Forms.DataGridView> kolumna <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> wartość określa, czy użytkownicy mogą edytować komórki w tej kolumnie. Aby uzyskać informacje dotyczące sposobu, w jaki formant ma być całkowicie tylko do odczytu, zobacz [How to: zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms](prevent-row-addition-and-deletion-datagridview.md).  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zobacz również [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](make-columns-read-only-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Aby uczynić kolumnę tylko do odczytu  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwość `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1` z kolumną o nazwie `CompanyName`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy dla kontrolki DataGridView formularzy Windows Forms](prevent-row-addition-and-deletion-datagridview.md)
