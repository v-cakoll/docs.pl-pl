---
title: Ustaw style wierszy przemiennych dla kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b87ad50ef7e5118a95998949bc62299955856b27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747138"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Porady: ustawianie alternatywnych stylów wierszy dla formantu DataGridView formularzy systemu Windows
Dane tabelaryczne są często prezentowane użytkownikom w formacie podobnym do finansów, gdzie przemienne wiersze mają różne kolory tła. Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.  
  
 Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można określić pełne informacje o stylu dla przemiennych wierszy. Dzięki temu można używać cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy.  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zobacz również [instrukcje: Ustawianie przemiennych stylów wierszy dla kontrolki DataGridView Windows Forms przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Aby programowo ustawić style przemiennych wierszy  
  
- Ustaw właściwości obiektów <xref:System.Windows.Forms.DataGridViewCellStyle> zwracanych przez właściwości <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > Style określone za pomocą właściwości <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> przesłaniają style określone na poziomie kolumny i <xref:System.Windows.Forms.DataGridView>, ale są przesłonięte przez style ustawione na poziomie poszczególnych wierszy i komórek. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
