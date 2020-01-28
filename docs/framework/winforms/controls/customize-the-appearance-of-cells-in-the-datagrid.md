---
title: Dostosowywanie wyglądu komórek w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744051"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Porady: dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows
Możesz dostosować wygląd dowolnej komórki, obsługując zdarzenie <xref:System.Windows.Forms.DataGridView.CellPainting> formantu <xref:System.Windows.Forms.DataGridView>. <xref:System.Drawing.Graphics> formantu <xref:System.Windows.Forms.DataGridView> można wyodrębnić z właściwości <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Dzięki temu <xref:System.Drawing.Graphics>można mieć wpływ na wygląd całej kontrolki <xref:System.Windows.Forms.DataGridView>, ale zazwyczaj chcesz mieć wpływ tylko na wygląd komórki, która jest aktualnie namalowana. Właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umożliwia ograniczenie operacji malowania do komórki, która jest aktualnie namalowana.  
  
 W poniższym przykładzie kodu zobaczysz wszystkie komórki w `ContactName` kolumnie przy użyciu schematu kolorów kontrolki <xref:System.Windows.Forms.DataGridView>. Zawartość tekstowa każdej komórki jest malowana w <xref:System.Drawing.Color.Crimson%2A>, a prostokąt marginesu jest rysowany w tym samym kolorze co Właściwość <xref:System.Windows.Forms.DataGridView.GridColor%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1` z kolumną `ContactName` taką jak jedna w tabeli Customers w przykładowej bazie danych Northwind.  
  
- Odwołania do zestawów system, system. Windows. Forms i system. Drawing.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
