---
title: 'Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 415cf18aa4cf01b151a414dbc26609af638a7af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011475"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a6e43-102">Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a6e43-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a6e43-103">Można dostosować wygląd dowolną komórkę, obsługując <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.CellPainting> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6e43-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="a6e43-104">Można wyodrębnić <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Drawing.Graphics> z <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="a6e43-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="a6e43-105">Dzięki temu <xref:System.Drawing.Graphics>, może mieć wpływ na wygląd całą <xref:System.Windows.Forms.DataGridView> kontroli, ale zazwyczaj można wpłynąć na wygląd komórkę, która jest obecnie malowany.</span><span class="sxs-lookup"><span data-stu-id="a6e43-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="a6e43-106"><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Właściwość <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umożliwiają ograniczenie do komórki, która jest obecnie malowany operacji malowania.</span><span class="sxs-lookup"><span data-stu-id="a6e43-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="a6e43-107">W poniższym przykładzie kodu namaluje wszystkie komórki w `ContactName` przy użyciu kolumny <xref:System.Windows.Forms.DataGridView> schemat kolorów formantu.</span><span class="sxs-lookup"><span data-stu-id="a6e43-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="a6e43-108">Zawartość tekstowa każda komórka jest malowane w <xref:System.Drawing.Color.Crimson%2A>, i prostokąt wstawki jest rysowana w taki sam jak kolor <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.GridColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6e43-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6e43-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6e43-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6e43-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a6e43-110">Compiling the Code</span></span>  
 <span data-ttu-id="a6e43-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a6e43-111">This example requires:</span></span>  
  
- <span data-ttu-id="a6e43-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` z `ContactName` kolumny, takiego jak w tabeli Klienci w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a6e43-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="a6e43-113">Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms i System.Drawing.</span><span class="sxs-lookup"><span data-stu-id="a6e43-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e43-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6e43-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="a6e43-115">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6e43-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
