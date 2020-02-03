---
title: Dostosowywanie wyglądu komórek w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744051"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="80292-102">Porady: dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80292-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="80292-103">Możesz dostosować wygląd dowolnej komórki, obsługując zdarzenie <xref:System.Windows.Forms.DataGridView.CellPainting> formantu <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="80292-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="80292-104"><xref:System.Drawing.Graphics> formantu <xref:System.Windows.Forms.DataGridView> można wyodrębnić z właściwości <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="80292-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="80292-105">Dzięki temu <xref:System.Drawing.Graphics>można mieć wpływ na wygląd całej kontrolki <xref:System.Windows.Forms.DataGridView>, ale zazwyczaj chcesz mieć wpływ tylko na wygląd komórki, która jest aktualnie namalowana.</span><span class="sxs-lookup"><span data-stu-id="80292-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="80292-106">Właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umożliwia ograniczenie operacji malowania do komórki, która jest aktualnie namalowana.</span><span class="sxs-lookup"><span data-stu-id="80292-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="80292-107">W poniższym przykładzie kodu zobaczysz wszystkie komórki w `ContactName` kolumnie przy użyciu schematu kolorów kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="80292-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="80292-108">Zawartość tekstowa każdej komórki jest malowana w <xref:System.Drawing.Color.Crimson%2A>, a prostokąt marginesu jest rysowany w tym samym kolorze co Właściwość <xref:System.Windows.Forms.DataGridView.GridColor%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="80292-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80292-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="80292-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80292-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80292-110">Compiling the Code</span></span>  
 <span data-ttu-id="80292-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="80292-111">This example requires:</span></span>  
  
- <span data-ttu-id="80292-112">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1` z kolumną `ContactName` taką jak jedna w tabeli Customers w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="80292-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="80292-113">Odwołania do zestawów system, system. Windows. Forms i system. Drawing.</span><span class="sxs-lookup"><span data-stu-id="80292-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80292-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80292-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="80292-115">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80292-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
