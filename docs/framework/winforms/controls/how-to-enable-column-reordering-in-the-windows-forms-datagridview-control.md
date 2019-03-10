---
title: 'Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: c34807cc1d2a569068ba82479e3a2bf230f4f2c5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704416"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="198e6-102">Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="198e6-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="198e6-103">Po włączeniu zmiany układu kolumn w <xref:System.Windows.Forms.DataGridView> kontrolki, użytkownicy mogą przechodzić kolumnę w nowe położenie przez przeciągnięcie nagłówka kolumny za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="198e6-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="198e6-104">W <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> wartość właściwości określa, czy użytkownicy mogą przechodzić do innej pozycji kolumn.</span><span class="sxs-lookup"><span data-stu-id="198e6-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="198e6-105">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="198e6-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="198e6-106">Zobacz też [jak: Włącz w Windows zmiany układu kolumn do formantu DataGridView przy użyciu narzędzia Projektant formularzy](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="198e6-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="198e6-107">Aby włączyć programowe Zmienianie kolejności kolumn</span><span class="sxs-lookup"><span data-stu-id="198e6-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="198e6-108">Ustaw <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="198e6-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="198e6-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="198e6-109">Compiling the Code</span></span>  
 <span data-ttu-id="198e6-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="198e6-110">This example requires:</span></span>  
  
-   <span data-ttu-id="198e6-111">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="198e6-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="198e6-112">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="198e6-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198e6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="198e6-113">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="198e6-114">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="198e6-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="198e6-115">Instrukcje: Zablokuj kolumny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="198e6-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
