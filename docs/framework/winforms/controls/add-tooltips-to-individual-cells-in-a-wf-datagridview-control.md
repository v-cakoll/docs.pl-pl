---
title: 'Instrukcje: Dodawanie elementu ToolTips do pojedynczych komórek w kontrolce DataGridView formularzy Windows Forms'
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
ms.openlocfilehash: 5198bec11142e31d60f9127ecebc4ffc8ee8b8ec
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717417"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="fb084-102">Instrukcje: Dodawanie elementu ToolTips do pojedynczych komórek w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb084-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fb084-103">Domyślnie, etykietki narzędzi są używane do wyświetlania wartości <xref:System.Windows.Forms.DataGridView> komórki, które są zbyt małe, aby wyświetlić jego całą zawartość.</span><span class="sxs-lookup"><span data-stu-id="fb084-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="fb084-104">Można jednak zmienić to zachowanie, można ustawić wartości tekst etykietki narzędzia dla poszczególnych komórek.</span><span class="sxs-lookup"><span data-stu-id="fb084-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="fb084-105">Jest to przydatne, mają być wyświetlane użytkownikom dodatkowe informacje na temat komórki lub w celu zapewnienia użytkownikom alternatywny opis zawartości komórki.</span><span class="sxs-lookup"><span data-stu-id="fb084-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="fb084-106">Na przykład w przypadku wiersza, który wyświetla ikony stanu może być zapewnienie tekst wyjaśnienia przy użyciu etykietek narzędzi.</span><span class="sxs-lookup"><span data-stu-id="fb084-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="fb084-107">Wyświetlanie etykietek narzędzi w komórce poziomu można również wyłączyć, ustawiając <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="fb084-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="fb084-108">Aby dodać etykietka narzędzia komórki</span><span class="sxs-lookup"><span data-stu-id="fb084-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="fb084-109">Ustaw <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fb084-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb084-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fb084-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="fb084-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fb084-111">This example requires:</span></span>  
  
-   <span data-ttu-id="fb084-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `Rating` do wyświetlania wartości ciągu o jeden przez cztery gwiazdki ("\*") symboli.</span><span class="sxs-lookup"><span data-stu-id="fb084-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="fb084-113"><xref:System.Windows.Forms.DataGridView.CellFormatting> Zdarzeń formantu musi być skojarzony z metody obsługi zdarzeń, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fb084-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="fb084-114">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="fb084-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fb084-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fb084-115">Robust Programming</span></span>  
 <span data-ttu-id="fb084-116">Po powiązaniu <xref:System.Windows.Forms.DataGridView> sterowania do zewnętrznego źródła danych lub zapewnić źródła danych, implementowanie trybu wirtualnego, mogą wystąpić problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="fb084-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="fb084-117">Aby uniknąć spadek wydajności, podczas pracy z dużymi ilościami danych, obsługa <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> zdarzeń, a nie ustawienie <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwości wielu komórek.</span><span class="sxs-lookup"><span data-stu-id="fb084-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="fb084-118">Podczas obsługi tego zdarzenia pobierania wartości komórki <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> właściwość wywołuje zdarzenie i zwraca wartość <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> właściwość jako określonych w zdarzeniu programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="fb084-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb084-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb084-119">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fb084-120">Programowanie przy użyciu komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb084-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
