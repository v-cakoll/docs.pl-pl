---
title: 'Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 2a4ca0a718373c56f77e8f3c45a9d6ee6d76a081
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171928"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4c38d-102">Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c38d-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4c38d-103">Nie wszystkie dane, jest przeznaczona do edycji.</span><span class="sxs-lookup"><span data-stu-id="4c38d-103">Not all data is meant for editing.</span></span> <span data-ttu-id="4c38d-104">W <xref:System.Windows.Forms.DataGridView> kontrolować kolumny <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> wartość właściwości określa, czy użytkownicy mogą edytować komórek w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="4c38d-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="4c38d-105">Aby dowiedzieć się, jak sprawić, że formant całkowicie tylko do odczytu, zobacz [jak: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="4c38d-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="4c38d-106">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4c38d-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="4c38d-107">Zobacz też [jak: Określanie kolumn jako tylko do odczytu w Windows Forms formantu DataGridView za pomocą projektanta](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4c38d-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="4c38d-108">Aby kolumnę tylko do odczytu programowe</span><span class="sxs-lookup"><span data-stu-id="4c38d-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="4c38d-109">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="4c38d-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c38d-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4c38d-110">Compiling the Code</span></span>  
 <span data-ttu-id="4c38d-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4c38d-111">This example requires:</span></span>  
  
-   <span data-ttu-id="4c38d-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` kolumnę o nazwie `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="4c38d-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="4c38d-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="4c38d-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c38d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c38d-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4c38d-115">Podstawowe funkcje komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c38d-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="4c38d-116">Instrukcje: zapobieganie dodawaniu i usuwaniu rzędów do kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c38d-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
