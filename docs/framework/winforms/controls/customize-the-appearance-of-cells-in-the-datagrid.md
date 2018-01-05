---
title: "Porady: dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows"
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
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b2a39943dfca412afa4b66265aabbf65b9ccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d018d-102">Porady: dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d018d-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d018d-103">Obsługa można dostosować wygląd dowolną komórkę <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d018d-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="d018d-104">Można wyodrębnić <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Drawing.Graphics> z <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d018d-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="d018d-105">Z tym <xref:System.Drawing.Graphics>, mogą wpływać na wygląd całą <xref:System.Windows.Forms.DataGridView> sterowania, ale zazwyczaj można wpływają na wygląd komórek, który jest obecnie rysowane.</span><span class="sxs-lookup"><span data-stu-id="d018d-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="d018d-106"><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> pozwala ograniczyć do komórek, która jest obecnie rysowane operacje rysowania.</span><span class="sxs-lookup"><span data-stu-id="d018d-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="d018d-107">W poniższym przykładzie kodu namaluje wszystkie komórki w `ContactName` przy użyciu kolumny <xref:System.Windows.Forms.DataGridView> schemat kolorów formantu.</span><span class="sxs-lookup"><span data-stu-id="d018d-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="d018d-108">Zawartość tekstu każdej komórki jest rysowane w <xref:System.Drawing.Color.Crimson%2A>, i krawędzi prostokąta jest rysowana w taki sam jak kolor <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.GridColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d018d-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d018d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d018d-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d018d-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d018d-110">Compiling the Code</span></span>  
 <span data-ttu-id="d018d-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d018d-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d018d-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` z `ContactName` kolumny znajdującego się w tabeli Klienci w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d018d-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="d018d-113">Odwołania do zestawów systemu, System.Windows.Forms i System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="d018d-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d018d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d018d-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [<span data-ttu-id="d018d-115">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d018d-115">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
