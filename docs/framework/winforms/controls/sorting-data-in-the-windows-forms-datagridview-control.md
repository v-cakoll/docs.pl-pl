---
title: Sortowanie danych w formancie DataGridView formularzy Windows
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012155"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="eddab-102">Sortowanie danych w formancie DataGridView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="eddab-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="eddab-103">Domyślnie użytkownicy mogą sortować dane w <xref:System.Windows.Forms.DataGridView> formantu przez kliknięcie nagłówka kolumny pola tekstowego (lub, naciskając klawisz F3, gdy komórka pole tekstowe koncentruje się na .NET Framework 4.7.2 i nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="eddab-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="eddab-104">Możesz zmodyfikować <xref:System.Windows.Forms.DataGridViewColumn.SortMode> właściwości określone kolumny, aby zezwolić użytkownikom na sortowanie według innych typów kolumn, gdy warto to zrobić.</span><span class="sxs-lookup"><span data-stu-id="eddab-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="eddab-105">Można również sortować dane programowo według dowolnej kolumny lub przez wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="eddab-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="eddab-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="eddab-106">In this section</span></span>

[<span data-ttu-id="eddab-107">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eddab-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="eddab-108">W tym artykule opisano opcje sortowania danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="eddab-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="eddab-109">Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eddab-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="eddab-110">W tym artykule opisano, jak umożliwić użytkownikom sortować według kolumn, które nie są sortowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="eddab-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="eddab-111">Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eddab-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="eddab-112">W tym artykule opisano sposób programowe sortowanie danych oraz dostosowywanie sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> zdarzeń lub poprzez implementację <xref:System.Collections.IComparer> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="eddab-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="eddab-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="eddab-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="eddab-114">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eddab-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="eddab-115">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="eddab-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="eddab-116">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eddab-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="eddab-117">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewColumnSortMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="eddab-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="eddab-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eddab-118">See also</span></span>

- [<span data-ttu-id="eddab-119">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eddab-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="eddab-120">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eddab-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
