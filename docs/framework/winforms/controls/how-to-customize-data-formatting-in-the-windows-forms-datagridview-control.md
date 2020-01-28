---
title: Dostosowywanie formatowania danych w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746776"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows
Poniższy przykład kodu demonstruje sposób implementacji procedury obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>, które zmienia sposób wyświetlania komórek w zależności od ich kolumn i wartości.  
  
 Komórki w `Balance` kolumnie zawierające liczby ujemne otrzymują czerwone tło. Możesz również sformatować te komórki jako walutę, aby wyświetlić nawiasy wokół wartości ujemnych. Aby uzyskać więcej informacji, zobacz [How to: format data w kontrolce DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 W komórkach w kolumnie `Priority` są wyświetlane obrazy zamiast odpowiednich wartości komórek tekstowych. Właściwość <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> służy do pobierania wartości komórki tekstowej i ustawiania odpowiedniej wartości wyświetlania obrazu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
- <xref:System.Drawing.Bitmap> obrazy o nazwach `highPri.bmp`, `mediumPri.bmp`i `lowPri.bmp` znajdujące się w tym samym katalogu co plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: formatowanie danych w kontrolce DataGridView formularzy Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
