---
title: 'Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962277"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy systemu Windows
Dane tabelaryczne są często prezentowane użytkownikom w formacie podobnym do finansów, gdzie przemienne wiersze mają różne kolory tła. Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można określić pełne informacje o stylu dla przemiennych wierszy. Dzięki temu można używać cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy.  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zapoznaj [się również z tematem: Ustaw style przemiennych wierszy dla kontrolki DataGridView Windows Forms przy użyciu](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)narzędzia Projektant.  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Aby programowo ustawić style przemiennych wierszy  
  
- Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów zwracanych <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> przez i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > Style określone za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości zastępują style określone w kolumnie i <xref:System.Windows.Forms.DataGridView> na poziomie, ale są przesłonięte przez style ustawione na poziomie poszczególnych wierszy i komórek. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka o `dataGridView1`nazwie. <xref:System.Windows.Forms.DataGridView>  
  
- Odwołania do <xref:System?displayProperty=nameWithType>zestawów, <xref:System.Drawing?displayProperty=nameWithType>i. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby uzyskać maksymalną skalowalność, należy <xref:System.Windows.Forms.DataGridViewCellStyle> udostępnić obiekty w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiania właściwości stylu dla każdego elementu osobno. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie stylów czcionek i kolorów w kontrolce DataGridView Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
