---
title: Sortowanie danych w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4027f3ae604f2a3ff4996855fa6dd34d4de8ea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="35523-102">Sortowanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35523-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="35523-103">Domyślnie użytkownicy będą mogli sortować dane w `DataGridView` kontroli przez kliknięcie nagłówka kolumny pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="35523-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="35523-104">Można zmodyfikować `SortMode` właściwości określonych kolumn, aby umożliwić użytkownikom sortowanie według innych typów kolumn, gdy warto to zrobić.</span><span class="sxs-lookup"><span data-stu-id="35523-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="35523-105">Można również sortować dane programowo według dowolnej kolumny lub wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="35523-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35523-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="35523-106">In This Section</span></span>  
 [<span data-ttu-id="35523-107">Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35523-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="35523-108">Opisuje opcje sortowania danych w formancie.</span><span class="sxs-lookup"><span data-stu-id="35523-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="35523-109">Porady: Ustawianie trybów sortowania kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35523-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="35523-110">Opisuje sposób użytkownicy mogli sortować według kolumn, które nie są domyślnie sortowania.</span><span class="sxs-lookup"><span data-stu-id="35523-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="35523-111">Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35523-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="35523-112">Opisuje programowane sortowanie danych oraz dostosowywanie sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> zdarzenia lub implementując <xref:System.Collections.IComparer> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="35523-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35523-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="35523-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="35523-114">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="35523-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="35523-115">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="35523-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="35523-116">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="35523-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="35523-117">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridViewColumnSortMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="35523-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35523-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35523-118">See Also</span></span>  
 [<span data-ttu-id="35523-119">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="35523-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="35523-120">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35523-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
