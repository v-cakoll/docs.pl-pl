---
title: Programistyczne Zmienianie rozmiaru komórek w celu dopasowania do zawartości w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: df3b378a8ba358fa0bfe549a7901b3d59d53f556
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742448"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="35ef1-102">Porady: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35ef1-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="35ef1-103">Można użyć metod kontroli <xref:System.Windows.Forms.DataGridView>, aby zmienić rozmiar wierszy, kolumn i nagłówków, tak aby wyświetlały ich całe wartości bez obcinania.</span><span class="sxs-lookup"><span data-stu-id="35ef1-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="35ef1-104">Za pomocą tych metod można zmieniać rozmiar <xref:System.Windows.Forms.DataGridView> elementów w miarę dokonania wyboru.</span><span class="sxs-lookup"><span data-stu-id="35ef1-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="35ef1-105">Alternatywnie można skonfigurować kontrolkę do automatycznego zmieniania rozmiaru tych elementów przy każdej zmianie zawartości.</span><span class="sxs-lookup"><span data-stu-id="35ef1-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="35ef1-106">Może to być niewydajne, jednak gdy pracujesz z dużymi zestawami danych lub często zmieniają się dane.</span><span class="sxs-lookup"><span data-stu-id="35ef1-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="35ef1-107">Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="35ef1-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="35ef1-108">Zwykle program programowo dostosowuje elementy <xref:System.Windows.Forms.DataGridView>, aby dopasować ich zawartość tylko podczas ładowania nowych danych ze źródła danych lub podczas edytowania wartości przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35ef1-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="35ef1-109">Jest to przydatne w celu optymalizacji wydajności, ale jest również przydatne, gdy chcesz umożliwić użytkownikom ręczne zmienianie rozmiaru wierszy i kolumn za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="35ef1-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="35ef1-110">Poniższy przykład kodu demonstruje dostępne opcje umożliwiające programistyczne zmienianie rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="35ef1-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ef1-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="35ef1-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35ef1-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35ef1-112">Compiling the Code</span></span>  
 <span data-ttu-id="35ef1-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="35ef1-113">This example requires:</span></span>  
  
- <span data-ttu-id="35ef1-114">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="35ef1-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ef1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ef1-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="35ef1-116">Zmiana rozmiaru wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35ef1-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="35ef1-117">Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35ef1-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="35ef1-118">Instrukcje: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35ef1-118">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
