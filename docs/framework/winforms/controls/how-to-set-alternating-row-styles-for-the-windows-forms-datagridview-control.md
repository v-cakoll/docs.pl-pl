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
ms.openlocfilehash: 06b93a756b351213a87e1f52bc691aaa27558ac4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078593"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Instrukcje: ustawianie alternatywnych stylów wierszy dla kontrolki DataGridView formularzy systemu Windows
Dane tabelaryczne często jest przesyłany do użytkowników w postaci księgi, gdzie przemienne wiersze mają różnych kolorów tła. Ten format ułatwia użytkownikom Poinformuj komórki, które są w każdym wierszu, szczególnie w przypadku szerokich tabel, które mają wiele kolumn.  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolę, można określić dotycząca pełną styl naprzemiennych wierszach. Dzięki temu możesz użyć właściwości stylu, takich jak kolor pierwszego planu i czcionki, oprócz kolor tła do odróżnienia przemienne wiersze.  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: Ustawianie przemiennych wierszy dla formantu DataGridView, które przy użyciu narzędzia Projektant formularzy Windows](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Aby ustawić programowo alternatywnych stylów wierszy  
  
-   Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów zwróconych przez <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Style określony za pomocą <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości przesłaniają style określone na podstawie kolumny i <xref:System.Windows.Forms.DataGridView> poziomu, ale są zastępowane przez style ustawić na poziomie wierszy i komórek. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W przypadku maksymalnej skalowalności powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style, zamiast oddzielnie ustawienie ponownego obliczenia właściwości stylu dla każdego elementu. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w formancie DataGridView formularzy systemu Windows](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie stylów czcionek i koloru w kontrolce DataGridView formularzy systemu Windows](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
