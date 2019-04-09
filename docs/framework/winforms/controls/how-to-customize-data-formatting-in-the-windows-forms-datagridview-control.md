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
ms.openlocfilehash: 5ce43054130db88792acab852b1e886285ff34d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116054"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="68f99-102">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68f99-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="68f99-103">Poniższy przykład kodu demonstruje sposób implementacji programu obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenia, które zmieniają się, jak komórki są wyświetlane w zależności od ich kolumny i wartości.</span><span class="sxs-lookup"><span data-stu-id="68f99-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="68f99-104">Komórek w `Balance` kolumny, która zawiera wartości ujemne są podane czerwone tło.</span><span class="sxs-lookup"><span data-stu-id="68f99-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="68f99-105">Możesz również sformatować te komórki jako walutę, aby wyświetlić nawiasów wokół wartości ujemnych.</span><span class="sxs-lookup"><span data-stu-id="68f99-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="68f99-106">Aby uzyskać więcej informacji, zobacz [jak: Formatowanie danych w Windows formantu DataGridView formularzy](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="68f99-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="68f99-107">Komórek w `Priority` kolumny wyświetlanie obrazów zamiast odpowiadających tekstowej komórek wartości.</span><span class="sxs-lookup"><span data-stu-id="68f99-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="68f99-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> jest używana do uzyskania wartości tekstowej komórki i ustaw odpowiednie wartości wyświetlania obrazu.</span><span class="sxs-lookup"><span data-stu-id="68f99-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f99-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f99-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68f99-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="68f99-110">Compiling the Code</span></span>  
 <span data-ttu-id="68f99-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="68f99-111">This example requires:</span></span>  
  
-   <span data-ttu-id="68f99-112">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="68f99-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <xref:System.Drawing.Bitmap> <span data-ttu-id="68f99-113">obrazy o nazwie `highPri.bmp`, `mediumPri.bmp`, i `lowPri.bmp` znajdujących się w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="68f99-113">images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="68f99-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="68f99-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="68f99-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="68f99-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f99-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68f99-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="68f99-117">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68f99-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="68f99-118">Instrukcje: formatowanie danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68f99-118">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="68f99-119">Style komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68f99-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="68f99-120">Formatowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68f99-120">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
