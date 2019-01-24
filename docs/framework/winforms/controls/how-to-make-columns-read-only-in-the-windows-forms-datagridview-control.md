---
title: 'Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: e57f926208e67ce894b58bdfaf5d0c3e3815b2ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514884"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7413-102">Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7413-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7413-103">Nie wszystkie dane, jest przeznaczona do edycji.</span><span class="sxs-lookup"><span data-stu-id="c7413-103">Not all data is meant for editing.</span></span> <span data-ttu-id="c7413-104">W <xref:System.Windows.Forms.DataGridView> kontrolować kolumny <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> wartość właściwości określa, czy użytkownicy mogą edytować komórek w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="c7413-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="c7413-105">Aby dowiedzieć się, jak sprawić, że formant całkowicie tylko do odczytu, zobacz [jak: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="c7413-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="c7413-106">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7413-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="c7413-107">Zobacz też [jak: Określanie kolumn jako tylko do odczytu w Windows Forms formantu DataGridView za pomocą projektanta](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c7413-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="c7413-108">Aby kolumnę tylko do odczytu programowe</span><span class="sxs-lookup"><span data-stu-id="c7413-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="c7413-109">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="c7413-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7413-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c7413-110">Compiling the Code</span></span>  
 <span data-ttu-id="c7413-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c7413-111">This example requires:</span></span>  
  
-   <span data-ttu-id="c7413-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` kolumnę o nazwie `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="c7413-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="c7413-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="c7413-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7413-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7413-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c7413-115">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7413-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="c7413-116">Instrukcje: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="c7413-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
