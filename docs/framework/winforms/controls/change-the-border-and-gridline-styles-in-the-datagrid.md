---
title: 'Instrukcje: zmienianie stylów obramowania i linii siatki w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917673"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Instrukcje: zmienianie stylów obramowania i linii siatki w kontrolce DataGridView formularzy systemu Windows
Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można dostosować wygląd obramowania i linii siatki kontrolki w celu ulepszenia środowiska użytkownika. Oprócz stylów obramowania komórek w kontrolce, można zmodyfikować kolor linii siatki i styl obramowania kontrolki. Można również zastosować różne style obramowania komórek dla zwykłych komórek, komórek nagłówka wiersza i komórek nagłówka kolumny.  
  
> [!NOTE]
> Kolor linii siatki jest używany tylko z <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>wartościami <xref:System.Windows.Forms.DataGridViewCellBorderStyle> wyliczenia i <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> wartością <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> wyliczenia. Pozostałe wartości tych wyliczeń używają kolorów określonych przez system operacyjny. Ponadto, gdy style wizualizacji są włączone w systemie Windows XP i w rodzinie systemu Windows Server <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 2003 za pomocą <xref:System.Windows.Forms.DataGridView.GridColor%2A> metody, wartość właściwości nie jest używana.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Aby zmienić kolor linii siatki programowo  
  
- <xref:System.Windows.Forms.DataGridView.GridColor%2A> Ustaw właściwość.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Aby zmienić styl obramowania całego formantu DataGridView  
  
- Ustaw właściwość na jedną z wartości <xref:System.Windows.Forms.BorderStyle> wyliczenia. <xref:System.Windows.Forms.DataGridView.BorderStyle%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Aby programowo zmienić style obramowania dla komórek DataGridView  
  
- Ustaw właściwości <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>i <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView>  
  
- Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Windows.Forms?displayProperty=nameWithType>i. <xref:System.Drawing?displayProperty=nameWithType>  
  
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
