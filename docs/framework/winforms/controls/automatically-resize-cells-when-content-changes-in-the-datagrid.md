---
title: 'Instrukcje: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 7acd7777ede726b9dfed2b821e4248a0ebf7797f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182497"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="86918-102">Instrukcje: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="86918-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="86918-103">Można skonfigurować <xref:System.Windows.Forms.DataGridView> kontrolować zmiany rozmiaru jego wiersze, kolumny i nagłówki automatycznie zawsze, gdy zmian zawartości, tak aby komórek są zawsze wystarczająco duży, aby wyświetlić ich wartości bez przycinania.</span><span class="sxs-lookup"><span data-stu-id="86918-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="86918-104">Masz wiele opcji, aby ograniczyć komórki, które są używane do określania nowe rozmiary.</span><span class="sxs-lookup"><span data-stu-id="86918-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="86918-105">Na przykład można skonfigurować formant Aby automatycznie zmieniać rozmiar szerokość kolumn tylko na podstawie wartości w wierszach, które są obecnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="86918-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="86918-106">Dzięki temu można uniknąć dotyczące nieefektywności podczas pracy z dużą liczbę wierszy, mimo że w tym przypadku warto użyć metod zmiany rozmiaru, takich jak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> dostosowania rozmiarów czasami wybrane.</span><span class="sxs-lookup"><span data-stu-id="86918-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="86918-107">Aby uzyskać więcej informacji na temat automatycznej zmiany rozmiaru, zobacz [opcje ustalania rozmiaru w formancie DataGridView formularzy Windows](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="86918-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="86918-108">Poniższy przykład kodu demonstruje opcjami dostępnymi na potrzeby automatycznej zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="86918-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86918-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="86918-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86918-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86918-110">Compiling the Code</span></span>  
 <span data-ttu-id="86918-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="86918-111">This example requires:</span></span>  
  
-   <span data-ttu-id="86918-112">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="86918-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="86918-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="86918-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="86918-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="86918-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="86918-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86918-115">See also</span></span>

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
- [<span data-ttu-id="86918-116">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86918-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="86918-117">Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86918-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="86918-118">Instrukcje: Programowe zmienianie rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86918-118">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
