---
title: 'Instrukcje: wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013403"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="be639-102">Instrukcje: wyświetlanie obrazów w komórkach kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="be639-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="be639-103">Obraz lub element graficzny jest jedną z wartości, które można wyświetlić w wierszu danych.</span><span class="sxs-lookup"><span data-stu-id="be639-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="be639-104">Często te grafiki formę fotografii pracownika lub logo firmy.</span><span class="sxs-lookup"><span data-stu-id="be639-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="be639-105">Dołączanie obrazów jest proste, podczas wyświetlania danych w ramach <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="be639-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="be639-106"><xref:System.Windows.Forms.DataGridView> Kontroli natywnie obsługuje format obrazu, wszystkie obsługiwane przez <xref:System.Drawing.Image> klasy, a także OLE obraz format używany przez niektóre bazy danych.</span><span class="sxs-lookup"><span data-stu-id="be639-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="be639-107">Jeśli <xref:System.Windows.Forms.DataGridView> swojego źródła danych zawiera kolumnę obrazów, zostaną one wyświetlone automatycznie przez <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="be639-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="be639-108">Poniższy przykład kodu demonstruje sposób wyodrębniania ikony z zasobu osadzonego i przekonwertować go do mapy bitowej do wyświetlenia w każdej komórce kolumny obrazu.</span><span class="sxs-lookup"><span data-stu-id="be639-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="be639-109">Inny przykład zastępuje wartości tekstowej komórek przy użyciu odpowiedniego obrazów, zobacz [jak: Dostosowywanie formatowania danych w formancie DataGridView formularzy Windows](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="be639-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be639-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="be639-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be639-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="be639-111">Compiling the Code</span></span>  
 <span data-ttu-id="be639-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="be639-112">This example requires:</span></span>  
  
- <span data-ttu-id="be639-113">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="be639-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="be639-114">Zasób osadzony ikony o nazwie `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="be639-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="be639-115">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="be639-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be639-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be639-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="be639-117">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be639-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="be639-118">Instrukcje: Dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be639-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
