---
title: Ustaw domyślne style komórek dla kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744868"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows
Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można określić domyślne style komórek dla całej kontrolki i dla konkretnych kolumn i wierszy. Te wartości domyślne są filtrowane z poziomu formantu do poziomu kolumny, a następnie do poziomu wiersza, a następnie do poziomu komórki. Jeśli określona właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> nie jest ustawiona na poziomie komórki, zostanie użyta wartość domyślna ustawienia właściwości na poziomie wiersza. Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest ustawienie domyślne kolumny. Na koniec, jeśli właściwość nie jest również ustawiona na poziomie kolumny, używane jest domyślne ustawienie <xref:System.Windows.Forms.DataGridView>. Przy użyciu tego ustawienia można uniknąć duplikowania ustawień właściwości na wielu poziomach. Na każdym poziomie wystarczy określić style, które różnią się od poziomów powyżej. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  Zobacz również [instrukcje: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView Windows Forms przy użyciu narzędzia Projektant](default-cell-styles-datagridview.md).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Aby programowo ustawić domyślne style komórek  
  
1. Ustaw właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane za pomocą właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. Utwórz i zainicjuj nowe obiekty <xref:System.Windows.Forms.DataGridViewCellStyle> do użycia przez wiele wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. Ustaw właściwość `DefaultCellStyle` określonych wierszy i kolumn.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby osiągnąć maksymalną skalowalność podczas pracy z bardzo dużymi zestawami danych, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów, zamiast ustawiać właściwości stylu poszczególnych elementów osobno. Ponadto należy utworzyć wiersze udostępnione i uzyskać do nich dostęp przy użyciu właściwości <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy Windows Forms](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
