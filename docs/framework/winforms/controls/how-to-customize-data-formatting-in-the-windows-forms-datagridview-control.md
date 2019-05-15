---
title: 'Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 948e9bf485b42b445491a4da9f8de7ae7974075c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592826"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy systemu Windows
Poniższy przykład kodu demonstruje sposób implementacji programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenia, które zmieniają się, jak komórki są wyświetlane w zależności od ich kolumny i wartości.  
  
 Komórek w `Balance` kolumny, która zawiera wartości ujemne są podane czerwone tło. Możesz również sformatować te komórki jako walutę, aby wyświetlić nawiasów wokół wartości ujemnych. Aby uzyskać więcej informacji, zobacz [jak: Formatowanie danych w Windows formantu DataGridView formularzy](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 Komórek w `Priority` kolumny wyświetlanie obrazów zamiast odpowiadających tekstowej komórek wartości. <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> jest używana do uzyskania wartości tekstowej komórki i ustaw odpowiednie wartości wyświetlania obrazu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
- <xref:System.Drawing.Bitmap> obrazy o nazwie `highPri.bmp`, `mediumPri.bmp`, i `lowPri.bmp` znajdujących się w tym samym katalogu co plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Formatowanie danych w Windows formantu DataGridView formularzy](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
