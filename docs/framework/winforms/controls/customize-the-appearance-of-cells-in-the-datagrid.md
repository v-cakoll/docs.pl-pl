---
title: 'Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: add865eedc54253ad257e0e142e555da52f341dd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703351"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms
Można dostosować wygląd dowolną komórkę, obsługując <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń. Można wyodrębnić <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Drawing.Graphics> z <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Dzięki temu <xref:System.Drawing.Graphics>, może mieć wpływ na wygląd całą <xref:System.Windows.Forms.DataGridView> kontroli, ale zazwyczaj można wpłynąć na wygląd komórkę, która jest obecnie malowany. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umożliwiają ograniczenie do komórki, która jest obecnie malowany operacji malowania.  
  
 W poniższym przykładzie kodu namaluje wszystkie komórki w `ContactName` przy użyciu kolumny <xref:System.Windows.Forms.DataGridView> schemat kolorów formantu. Zawartość tekstowa każda komórka jest malowane w <xref:System.Drawing.Color.Crimson%2A>, i prostokąt wstawki jest rysowana w taki sam jak kolor <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.GridColor%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` z `ContactName` kolumny, takiego jak w tabeli Klienci w bazie danych Northwind.  
  
-   Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms i System.Drawing.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
