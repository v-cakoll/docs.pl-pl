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
ms.openlocfilehash: d24adb98c339f911d6bea0312bce4d4b4f198a61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224997"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Instrukcje: zmienianie stylów obramowania i linii siatki w kontrolce DataGridView formularzy systemu Windows
Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki, można dostosować wygląd obramowania formantu i linie siatki, aby ulepszyć środowisko użytkownika. Możesz zmodyfikować kolor linii siatki i styl obramowania kontrolki, oprócz style obramowania komórek w kontrolce. Można także zastosować inną komórkę style obramowania dla zwykłych komórek, komórki nagłówka wiersza i komórki nagłówka kolumny.  
  
> [!NOTE]
>  Kolor linii siatki jest używany tylko z <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, i <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> wartości <xref:System.Windows.Forms.DataGridViewCellBorderStyle> wyliczenie i <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> wartość <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> wyliczenia. Wartości te wyliczenia Użyj kolorów, określona przez system operacyjny. Ponadto, jeżeli style wizualne są włączone w systemach Windows i z rodziny Windows Server 2003 za pośrednictwem <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> nie jest używana wartość właściwości.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Aby programowo zmienić kolor linii siatki  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.GridColor%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Aby zmienić styl obramowania formantu DataGridView całego programowe  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> jedną z właściwości <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Aby programowo zmienić styl komórek DataGridView  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, i <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
