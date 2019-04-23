---
title: 'Instrukcje: formatowanie danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 62701edfdb3cf2729cb401ad12a12ee4f524287b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221303"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Instrukcje: formatowanie danych w kontrolce DataGridView formularzy systemu Windows
Poniższe procedury przedstawiają podstawowe formatowanie wartości komórki za pomocą <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwość <xref:System.Windows.Forms.DataGridView> kontroli i określonych kolumn w formancie. Informacje na temat zaawansowanych danych formatowania, zobacz [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Formatowanie waluty i wartości daty  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>. Poniższy przykład kodu ustawia format dla określonych kolumn przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumn. Wartości w `UnitPrice` kolumna jest wyświetlana w bieżącym formacie waluty specyficzny dla kultury za pomocą wartości ujemnych, ujęte w nawiasy. Wartości w `ShipDate` kolumna jest wyświetlana w formacie bieżącej daty krótkiej dla kultury. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartości, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Aby dostosować wyświetlanie wartości null bazy danych  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle>. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwość, aby wyświetlić "puste" we wszystkich komórkach zawiera wartości równą <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Aby włączyć wordwrap komórek na podstawie tekstu  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewTriState> wartości wyliczenia. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości, aby ustawić tryb zawijania dla całego formantu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>Aby określić wyrównanie tekstu w komórkach kontrolki DataGridView  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> do jednego z <xref:System.Windows.Forms.DataGridViewContentAlignment> wartości wyliczenia. Poniższy przykład kodu Ustawia wyrównanie dla określonej kolumny za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumny.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj tych przykładach:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `UnitPrice`, kolumna o nazwie `ShipDate`, a kolumna o nazwie `CustomerName`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W przypadku maksymalnej skalowalności powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki, które używają tego samego style, zamiast oddzielnie ustawienie ponownego obliczenia właściwości stylu dla każdego elementu. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
