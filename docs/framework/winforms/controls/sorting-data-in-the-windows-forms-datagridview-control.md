---
title: Sortowanie danych w formancie DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742945"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7c8a1-102">Sortowanie danych w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c8a1-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="7c8a1-103">Domyślnie użytkownicy mogą sortować dane w kontrolce <xref:System.Windows.Forms.DataGridView>, klikając nagłówek kolumny pola tekstowego (lub naciskając klawisz F3, gdy komórka pola tekstowego koncentruje się na .NET Framework 4.7.2 i nowszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="7c8a1-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="7c8a1-104">Możesz zmodyfikować właściwość <xref:System.Windows.Forms.DataGridViewColumn.SortMode> określonych kolumn, aby umożliwić użytkownikom sortowanie według innych typów kolumn, gdy ma to sens.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="7c8a1-105">Możesz również sortować dane programowo według dowolnej kolumny lub według wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7c8a1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7c8a1-106">In this section</span></span>

[<span data-ttu-id="7c8a1-107">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c8a1-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="7c8a1-108">Opisuje opcje sortowania danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="7c8a1-109">Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c8a1-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="7c8a1-110">Opisuje, jak umożliwić użytkownikom sortowanie według kolumn, które nie są domyślnie sortowane.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="7c8a1-111">Instrukcje: dostosowywanie sortowania w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c8a1-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="7c8a1-112">Opisuje sposób programistycznego sortowania danych i dostosowywania sortowania przy użyciu zdarzenia <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> lub przez implementację interfejsu <xref:System.Collections.IComparer>.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="7c8a1-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7c8a1-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="7c8a1-114">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="7c8a1-115">Zawiera dokumentację referencyjną dla metody <xref:System.Windows.Forms.DataGridView.Sort%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="7c8a1-116">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="7c8a1-117">Zawiera dokumentację referencyjną dla wyliczenia <xref:System.Windows.Forms.DataGridViewColumnSortMode>.</span><span class="sxs-lookup"><span data-stu-id="7c8a1-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c8a1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c8a1-118">See also</span></span>

- [<span data-ttu-id="7c8a1-119">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7c8a1-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="7c8a1-120">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c8a1-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
