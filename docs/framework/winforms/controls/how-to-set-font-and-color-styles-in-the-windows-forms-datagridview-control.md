---
title: Ustawianie stylów czcionek i kolorów w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746761"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Porady: ustawianie stylów czcionek i koloru w formancie DataGridView formularzy systemu Windows
Aby określić wygląd komórek w kontrolce <xref:System.Windows.Forms.DataGridView>, należy ustawić właściwości klasy <xref:System.Windows.Forms.DataGridViewCellStyle>. Można pobrać wystąpienia tej klasy z różnych właściwości klasy <xref:System.Windows.Forms.DataGridView> i jej klas towarzyszących lub można utworzyć wystąpienia obiektów <xref:System.Windows.Forms.DataGridViewCellStyle> do przypisywania do tych właściwości.  
  
 W poniższych procedurach przedstawiono podstawowe dostosowanie wyglądu komórki przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Każda komórka w kontrolce dziedziczy style określone za pomocą tej właściwości, chyba że zostaną zastąpione na poziomie kolumny, wiersza lub komórki. Aby zapoznać się z przykładem dziedziczenia stylu, zobacz [jak: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Aby uzyskać informacje o dodatkowych zastosowaniach klasy <xref:System.Windows.Forms.DataGridViewCellStyle>, zobacz tematy wymienione w sekcji Zobacz też.  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  Zobacz również [instrukcje: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView Windows Forms przy użyciu narzędzia Projektant](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>Aby określić czcionkę używaną przez komórki DataGridView  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> do ustawiania czcionki dla całej kontrolki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>Aby określić kolory pierwszego planu i tła dla komórek DataGridView  
  
- Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, aby ustawić te style dla całej kontrolki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Aby określić kolory pierwszego planu i tła wybranych komórek DataGridView  
  
- Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> i <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Poniższy przykład kodu używa właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>, aby ustawić te style dla całej kontrolki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
