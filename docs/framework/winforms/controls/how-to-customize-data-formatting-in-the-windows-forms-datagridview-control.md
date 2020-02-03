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
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f740a-102">Porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f740a-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f740a-103">Poniższy przykład kodu demonstruje sposób implementacji procedury obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>, które zmienia sposób wyświetlania komórek w zależności od ich kolumn i wartości.</span><span class="sxs-lookup"><span data-stu-id="f740a-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="f740a-104">Komórki w `Balance` kolumnie zawierające liczby ujemne otrzymują czerwone tło.</span><span class="sxs-lookup"><span data-stu-id="f740a-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="f740a-105">Możesz również sformatować te komórki jako walutę, aby wyświetlić nawiasy wokół wartości ujemnych.</span><span class="sxs-lookup"><span data-stu-id="f740a-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="f740a-106">Aby uzyskać więcej informacji, zobacz [How to: format data w kontrolce DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f740a-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f740a-107">W komórkach w kolumnie `Priority` są wyświetlane obrazy zamiast odpowiednich wartości komórek tekstowych.</span><span class="sxs-lookup"><span data-stu-id="f740a-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="f740a-108">Właściwość <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> służy do pobierania wartości komórki tekstowej i ustawiania odpowiedniej wartości wyświetlania obrazu.</span><span class="sxs-lookup"><span data-stu-id="f740a-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f740a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f740a-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f740a-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f740a-110">Compiling the Code</span></span>  
 <span data-ttu-id="f740a-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f740a-111">This example requires:</span></span>  
  
- <span data-ttu-id="f740a-112">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="f740a-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="f740a-113"><xref:System.Drawing.Bitmap> obrazy o nazwach `highPri.bmp`, `mediumPri.bmp`i `lowPri.bmp` znajdujące się w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="f740a-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f740a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f740a-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="f740a-115">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f740a-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f740a-116">Instrukcje: formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f740a-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f740a-117">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f740a-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f740a-118">Formatowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f740a-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
