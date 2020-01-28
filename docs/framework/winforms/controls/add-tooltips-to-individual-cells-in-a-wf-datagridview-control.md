---
title: Dodaj etykietki narzędzi do poszczególnych komórek w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732183"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="529af-102">Porady: dodawanie elementu ToolTips do pojedynczych komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="529af-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="529af-103">Domyślnie etykietki narzędzi są używane do wyświetlania wartości <xref:System.Windows.Forms.DataGridView> komórek, które są zbyt małe, aby wyświetlić całą zawartość.</span><span class="sxs-lookup"><span data-stu-id="529af-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="529af-104">Można jednak zastąpić to zachowanie, aby ustawić wartości tekstowe etykietki narzędzia dla poszczególnych komórek.</span><span class="sxs-lookup"><span data-stu-id="529af-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="529af-105">Jest to przydatne w przypadku wyświetlania użytkownikom dodatkowych informacji o komórce lub zapewnienia użytkownikom alternatywnego opisu zawartości komórki.</span><span class="sxs-lookup"><span data-stu-id="529af-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="529af-106">Na przykład jeśli masz wiersz, w którym są wyświetlane ikony stanu, możesz podać wyjaśnienie tekstu przy użyciu etykietek narzędzi.</span><span class="sxs-lookup"><span data-stu-id="529af-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="529af-107">Możesz również wyłączyć wyświetlanie etykietek na poziomie komórki, ustawiając właściwość <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="529af-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="529af-108">Aby dodać etykietkę narzędzia do komórki</span><span class="sxs-lookup"><span data-stu-id="529af-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="529af-109">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="529af-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="529af-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="529af-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="529af-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="529af-111">This example requires:</span></span>  
  
- <span data-ttu-id="529af-112">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `Rating` do wyświetlania wartości ciągów jednego z czterech gwiazdek ("\*").</span><span class="sxs-lookup"><span data-stu-id="529af-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="529af-113">Zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting> formantu musi być skojarzone z metodą obsługi zdarzeń pokazaną w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="529af-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="529af-114">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="529af-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="529af-115">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="529af-115">Robust Programming</span></span>  
 <span data-ttu-id="529af-116">Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> z zewnętrznym źródłem danych lub udostępnieniu własnego źródła danych przez implementację trybu wirtualnego mogą wystąpić problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="529af-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="529af-117">Aby uniknąć pogorszenia wydajności podczas pracy z dużymi ilościami danych, należy obsłużyć <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> zdarzenia zamiast ustawiania właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> wielu komórek.</span><span class="sxs-lookup"><span data-stu-id="529af-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="529af-118">Podczas obsługi tego zdarzenia pobieranie wartości właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> komórki wywołuje zdarzenie i zwraca wartość właściwości <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>, jak określono w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="529af-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529af-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="529af-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="529af-120">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="529af-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
