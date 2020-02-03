---
title: Automatycznie zmieniaj rozmiar komórek, gdy zmienia się zawartość w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 86e3bce993aa06546e301c6d7a7e03a31013c337
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732065"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="667b3-102">Porady: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="667b3-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="667b3-103">Można skonfigurować kontrolkę <xref:System.Windows.Forms.DataGridView>, aby zmienić rozmiar swoich wierszy, kolumn i nagłówków automatycznie przy każdej zmianie zawartości, dzięki czemu komórki są zawsze wystarczająco duże, aby wyświetlić ich wartości bez obcinania.</span><span class="sxs-lookup"><span data-stu-id="667b3-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="667b3-104">Istnieje wiele opcji ograniczających, które komórki są używane do określania nowych rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="667b3-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="667b3-105">Na przykład można skonfigurować kontrolkę tak, aby automatycznie zmieniała szerokość kolumn na podstawie wartości w wierszach, które są aktualnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="667b3-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="667b3-106">Dzięki temu można uniknąć nieefektywności podczas pracy z dużymi liczbami wierszy, chociaż w tym przypadku można użyć metod ustalania rozmiaru, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>, aby dostosować rozmiary w miarę dokonania wyboru.</span><span class="sxs-lookup"><span data-stu-id="667b3-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="667b3-107">Aby uzyskać więcej informacji na temat automatycznej zmiany rozmiarów, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="667b3-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="667b3-108">Poniższy przykład kodu demonstruje opcje dostępne dla automatycznej zmiany rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="667b3-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="667b3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="667b3-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="667b3-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="667b3-110">Compiling the Code</span></span>  
 <span data-ttu-id="667b3-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="667b3-111">This example requires:</span></span>  
  
- <span data-ttu-id="667b3-112">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="667b3-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667b3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="667b3-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="667b3-114">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="667b3-114">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="667b3-115">Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="667b3-115">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="667b3-116">Instrukcje: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="667b3-116">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
