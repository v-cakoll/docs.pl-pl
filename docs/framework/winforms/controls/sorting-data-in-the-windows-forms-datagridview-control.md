---
title: Sortowanie danych w formancie DataGridView formularzy Windows
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 588678b3ba0d75fea58709c1969a3e276d65439e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688288"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2120d-102">Sortowanie danych w formancie DataGridView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="2120d-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="2120d-103">Domyślnie użytkownicy mogą sortować dane w <xref:System.Windows.Forms.DataGridView> formantu przez kliknięcie nagłówka kolumny pola tekstowego (lub, naciskając klawisz F3, gdy komórka pole tekstowe koncentruje się na .NET Framework 4.7.2 i nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="2120d-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="2120d-104">Możesz zmodyfikować <xref:System.Windows.Forms.DataGridViewColumn.SortMode> właściwości określone kolumny, aby zezwolić użytkownikom na sortowanie według innych typów kolumn, gdy warto to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2120d-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="2120d-105">Można również sortować dane programowo według dowolnej kolumny lub przez wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="2120d-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2120d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2120d-106">In this section</span></span>

[<span data-ttu-id="2120d-107">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2120d-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="2120d-108">W tym artykule opisano opcje sortowania danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="2120d-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="2120d-109">Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2120d-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="2120d-110">W tym artykule opisano, jak umożliwić użytkownikom sortować według kolumn, które nie są sortowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="2120d-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="2120d-111">Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2120d-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="2120d-112">W tym artykule opisano sposób programowe sortowanie danych oraz dostosowywanie sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> zdarzeń lub poprzez implementację <xref:System.Collections.IComparer> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2120d-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="2120d-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2120d-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="2120d-114">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2120d-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="2120d-115">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2120d-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="2120d-116">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2120d-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="2120d-117">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumnSortMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2120d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="2120d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2120d-118">See also</span></span>

- [<span data-ttu-id="2120d-119">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="2120d-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="2120d-120">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2120d-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
