---
title: Wyświetlanie obrazów w komórkach kontrolki DataGridView
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
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740285"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="0fb87-102">Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fb87-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0fb87-103">Obraz lub grafika to jedna z wartości, które można wyświetlić w wierszu danych.</span><span class="sxs-lookup"><span data-stu-id="0fb87-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="0fb87-104">Często te grafiki przyjmują formę Zdjęcia pracownika lub logo firmy.</span><span class="sxs-lookup"><span data-stu-id="0fb87-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="0fb87-105">Dołączanie obrazów jest proste, gdy wyświetlasz dane w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0fb87-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0fb87-106">Formant <xref:System.Windows.Forms.DataGridView> natywnie obsługuje dowolny format obrazu obsługiwany przez klasę <xref:System.Drawing.Image>, a także format obrazu OLE używany przez niektóre bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0fb87-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="0fb87-107">Jeśli źródło danych kontrolki <xref:System.Windows.Forms.DataGridView> ma kolumnę obrazów, zostaną one automatycznie wyświetlone przez kontrolkę <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0fb87-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="0fb87-108">Poniższy przykład kodu demonstruje, jak wyodrębnić ikonę z osadzonego zasobu i przekonwertować ją na mapę bitową do wyświetlania w każdej komórce kolumny obrazu.</span><span class="sxs-lookup"><span data-stu-id="0fb87-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="0fb87-109">Aby uzyskać inny przykład, który zastępuje wartości komórki tekstowej odpowiednimi obrazami, zobacz [How to: Dostosowywanie formatowania danych w kontrolce DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0fb87-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb87-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fb87-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fb87-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0fb87-111">Compiling the Code</span></span>  
 <span data-ttu-id="0fb87-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0fb87-112">This example requires:</span></span>  
  
- <span data-ttu-id="0fb87-113">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="0fb87-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="0fb87-114">Osadzony zasób ikon o nazwie `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="0fb87-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="0fb87-115">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>i <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fb87-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb87-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fb87-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="0fb87-117">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fb87-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="0fb87-118">Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fb87-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
