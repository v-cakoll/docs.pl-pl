---
title: Zmienianie stylów obramowania i linii siatki w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744699"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Porady: zmienianie stylów obramowania i linii siatki w formancie DataGridView formularzy systemu Windows
Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować wygląd obramowania i linii siatki kontrolki w celu ulepszenia środowiska użytkownika. Oprócz stylów obramowania komórek w kontrolce, można zmodyfikować kolor linii siatki i styl obramowania kontrolki. Można również zastosować różne style obramowania komórek dla zwykłych komórek, komórek nagłówka wiersza i komórek nagłówka kolumny.  
  
> [!NOTE]
> Kolor linii siatki jest używany tylko z wartościami <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>i <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> wyliczenia <xref:System.Windows.Forms.DataGridViewCellBorderStyle> i <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> wartości wyliczenia <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>. Pozostałe wartości tych wyliczeń używają kolorów określonych przez system operacyjny. Ponadto, gdy style wizualizacji są włączone w systemie Windows XP i w rodzinie systemu Windows Server 2003 za pomocą metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>, wartość właściwości <xref:System.Windows.Forms.DataGridView.GridColor%2A> nie jest używana.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Aby zmienić kolor linii siatki programowo  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Aby zmienić styl obramowania całego formantu DataGridView  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> na jedną z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Aby programowo zmienić style obramowania dla komórek DataGridView  
  
- Ustaw właściwości <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>i <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>i <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
