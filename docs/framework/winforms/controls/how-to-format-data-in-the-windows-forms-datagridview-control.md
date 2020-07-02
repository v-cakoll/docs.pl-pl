---
title: Formatowanie danych w formancie DataGridView
description: Dowiedz się, jak sformatować wartości komórek przy użyciu Windows Forms właściwości DefaultCellStyle kontrolki DataGridView i określonych kolumn w kontrolce.
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622812"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Porady: formatowanie danych w formancie DataGridView formularzy systemu Windows
W poniższych procedurach przedstawiono podstawowe formatowanie wartości komórek przy użyciu <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> właściwości <xref:System.Windows.Forms.DataGridView> kontrolki i określonych kolumn w kontrolce. Aby uzyskać informacje o zaawansowanym formatowaniu danych, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Aby sformatować wartości walutowe i daty  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwość obiektu <xref:System.Windows.Forms.DataGridViewCellStyle> . Poniższy przykład kodu ustawia format dla konkretnych kolumn przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości kolumn. Wartości w `UnitPrice` kolumnie są wyświetlane w bieżącym formacie waluty specyficznej dla kultury, z wartościami ujemnymi otoczonymi nawiasami. Wartości w `ShipDate` kolumnie są wyświetlane w bieżącym formacie daty krótkiej specyficznej dla kultury. Aby uzyskać więcej informacji o <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> wartościach, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Aby dostosować wyświetlanie wartości null bazy danych  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> właściwość obiektu <xref:System.Windows.Forms.DataGridViewCellStyle> . Poniższy przykład kodu używa <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości do wyświetlania "No entry" we wszystkich komórkach zawierających wartości równe <xref:System.DBNull.Value?displayProperty=nameWithType> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Aby włączyć WordWrap w komórkach tekstowych  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> Właściwość a <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z <xref:System.Windows.Forms.DataGridViewTriState> wartości wyliczenia. Poniższy przykład kodu używa właściwości, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> Aby ustawić tryb zawijania dla całej kontrolki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>Aby określić wyrównanie tekstu dla komórek DataGridView  
  
- Ustaw <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> Właściwość a <xref:System.Windows.Forms.DataGridViewCellStyle> na jedną z <xref:System.Windows.Forms.DataGridViewContentAlignment> wartości wyliczenia. Poniższy przykład kodu ustawia wyrównanie dla określonej kolumny przy użyciu <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> Właściwości kolumny.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Te przykłady wymagają:  
  
- <xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie, `dataGridView1` która zawiera kolumnę o nazwie `UnitPrice` , kolumnę o nazwie `ShipDate` i kolumnę o nazwie `CustomerName` .  
  
- Odwołania do <xref:System?displayProperty=nameWithType> zestawów, <xref:System.Drawing?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby uzyskać maksymalną skalowalność, należy udostępnić <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty w wielu wierszach, kolumnach lub komórkach, które używają tych samych stylów zamiast ustawiania właściwości stylu dla każdego elementu osobno. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
