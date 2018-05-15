---
title: Sortowanie danych w formancie DataGridView formularzy systemu Windows
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1cbfb4a19e9bb0db5cbb595a91a254a3a8e3f309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d30d8-102">Sortowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d30d8-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="d30d8-103">Domyślnie użytkownicy będą mogli sortować dane w <xref:System.Windows.Forms.DataGridView> kontroli przez kliknięcie nagłówka kolumny pola tekstowego (lub naciskając klawisz F3, gdy komórka pole tekstowe koncentruje się na .NET Framework 4.7.2 i nowszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="d30d8-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="d30d8-104">Można zmodyfikować <xref:System.Windows.Forms.DataGridViewColumn.SortMode> właściwości określonych kolumn, aby umożliwić użytkownikom sortowanie według innych typów kolumn, gdy warto to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d30d8-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="d30d8-105">Można również sortować dane programowo według dowolnej kolumny lub wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="d30d8-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d30d8-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d30d8-106">In this section</span></span>

[<span data-ttu-id="d30d8-107">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d30d8-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d30d8-108">Opisuje opcje sortowania danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="d30d8-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="d30d8-109">Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d30d8-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="d30d8-110">Opisuje sposób użytkownicy mogli sortować według kolumn, które nie są domyślnie sortowania.</span><span class="sxs-lookup"><span data-stu-id="d30d8-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="d30d8-111">Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d30d8-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d30d8-112">Opisuje programowane sortowanie danych oraz dostosowywanie sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> zdarzenia lub implementując <xref:System.Collections.IComparer> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d30d8-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="d30d8-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d30d8-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="d30d8-114">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="d30d8-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="d30d8-115">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d30d8-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="d30d8-116">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d30d8-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="d30d8-117">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewColumnSortMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d30d8-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d30d8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d30d8-118">See also</span></span>

[<span data-ttu-id="d30d8-119">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d30d8-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
[<span data-ttu-id="d30d8-120">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d30d8-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  