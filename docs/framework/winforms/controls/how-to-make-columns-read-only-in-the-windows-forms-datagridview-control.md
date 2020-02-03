---
title: Określanie kolumn jako tylko do odczytu w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736182"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="cfd33-102">Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cfd33-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cfd33-103">Nie wszystkie dane są przeznaczone do edycji.</span><span class="sxs-lookup"><span data-stu-id="cfd33-103">Not all data is meant for editing.</span></span> <span data-ttu-id="cfd33-104">W kontrolce <xref:System.Windows.Forms.DataGridView> kolumna <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> wartość określa, czy użytkownicy mogą edytować komórki w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="cfd33-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="cfd33-105">Aby uzyskać informacje dotyczące sposobu, w jaki formant ma być całkowicie tylko do odczytu, zobacz [How to: zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="cfd33-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="cfd33-106">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfd33-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="cfd33-107">Zobacz również [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="cfd33-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="cfd33-108">Aby uczynić kolumnę tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cfd33-108">To make a column read-only programmatically</span></span>  
  
- <span data-ttu-id="cfd33-109">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="cfd33-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cfd33-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cfd33-110">Compiling the Code</span></span>  
 <span data-ttu-id="cfd33-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="cfd33-111">This example requires:</span></span>  
  
- <span data-ttu-id="cfd33-112">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1` z kolumną o nazwie `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="cfd33-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
- <span data-ttu-id="cfd33-113">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cfd33-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd33-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfd33-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cfd33-115">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cfd33-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="cfd33-116">Instrukcje: zapobieganie dodawaniu i usuwaniu wierszy dla kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cfd33-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
