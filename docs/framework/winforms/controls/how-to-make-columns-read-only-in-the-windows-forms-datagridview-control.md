---
title: "Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fb80b5baeafff53781cb1ff430ad05dd93f2ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="509f2-102">Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="509f2-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="509f2-103">Nie wszystkie dane są przeznaczone do edycji.</span><span class="sxs-lookup"><span data-stu-id="509f2-103">Not all data is meant for editing.</span></span> <span data-ttu-id="509f2-104">W <xref:System.Windows.Forms.DataGridView> kontrolować kolumny <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości wartość określa, czy użytkownicy mogą edytować komórki w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="509f2-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="509f2-105">Aby uzyskać informacje o sposobie tworzenia kontrolki całkowicie tylko do odczytu, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="509f2-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="509f2-106">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="509f2-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="509f2-107">Zobacz też [jak: utworzyć tylko do odczytu w kolumnach w Windows Forms DataGridView formantu przy użyciu projektanta](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="509f2-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="509f2-108">Aby kolumnę tylko do odczytu programowo</span><span class="sxs-lookup"><span data-stu-id="509f2-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="509f2-109">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="509f2-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="509f2-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="509f2-110">Compiling the Code</span></span>  
 <span data-ttu-id="509f2-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="509f2-111">This example requires:</span></span>  
  
-   <span data-ttu-id="509f2-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` z kolumny o nazwie `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="509f2-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="509f2-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="509f2-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509f2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="509f2-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="509f2-115">Wierszy i kolumn podstawowe funkcje komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="509f2-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="509f2-116">Porady: Zapobieganie dodawaniu i usuwaniu w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="509f2-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
