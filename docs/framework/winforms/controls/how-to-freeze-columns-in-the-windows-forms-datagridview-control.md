---
title: 'Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85930731daa223fda8353f295e631c33bda5144
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9d8c1-102">Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9d8c1-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9d8c1-103">Gdy użytkownicy wyświetlać dane wyświetlane w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli, czasami muszą odwoływać się do jednej kolumny lub zestaw kolumn często.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="9d8c1-104">Na przykład podczas wyświetlania informacji klienta, który zawiera wiele kolumn tabeli, jest przydatne do wyświetlenia nazwy klienta przez cały czas podczas włączania obsługi innych kolumn przewinięcia poza region widoczny.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="9d8c1-105">Aby osiągnąć ten problem, można zablokować kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="9d8c1-106">Po zablokowaniu kolumny zablokowanych również wszystkich kolumn po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej).</span><span class="sxs-lookup"><span data-stu-id="9d8c1-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="9d8c1-107">Zablokowane kolumny pozostają bez zmian, gdy mogą być przewijane w innych kolumn.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d8c1-108">Jeśli włączono zmiany układu kolumn zablokowane kolumny są traktowane jako grupę różne od kolumny.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="9d8c1-109">Użytkownicy można zmienić kolumny w każdej grupie, ale nie może przenieść kolumny z jednej grupy, do drugiego.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="9d8c1-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Właściwość kolumny określa, czy kolumna jest zawsze widocznych w siatce.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="9d8c1-111">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="9d8c1-112">Zobacz też [porady: blokowanie kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9d8c1-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="9d8c1-113">Aby zablokować kolumnę programowo</span><span class="sxs-lookup"><span data-stu-id="9d8c1-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="9d8c1-114">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d8c1-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9d8c1-115">Compiling the Code</span></span>  
 <span data-ttu-id="9d8c1-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9d8c1-116">This example requires:</span></span>  
  
-   <span data-ttu-id="9d8c1-117">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="9d8c1-118">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8c1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d8c1-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="9d8c1-120">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d8c1-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="9d8c1-121">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d8c1-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
