---
title: 'Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a0b77a7356b09a5cc95ec165a62c45852f542b8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187430"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e8ac0-102">Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e8ac0-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e8ac0-103">Gdy użytkownicy wyświetlają dane wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontrolki, czasami muszą odwoływać się do pojedynczej kolumny lub zestaw kolumn, często.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="e8ac0-104">Na przykład wyświetlając tabelę informacje o kliencie, który zawiera wiele kolumn, jest przydatne do wyświetlania nazwy klientów przez cały czas podczas włączania innych kolumn w celu przewiń poza regionem widoczne.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="e8ac0-105">Aby uzyskać takie zachowanie, można zablokować kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="e8ac0-106">Po zablokowaniu kolumny, również są zablokowane wszystkie kolumny po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej).</span><span class="sxs-lookup"><span data-stu-id="e8ac0-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="e8ac0-107">Zamrożone kolumny pozostaną w miejscu, a wszystkie pozostałe kolumny można przewijać.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8ac0-108">Jeśli zmiany układu kolumn jest włączona, Zablokowane kolumny są traktowane jako różne od kolumny grupy.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="e8ac0-109">Użytkownicy mogą zmienić położenie kolumn w każdej grupie, ale kolumna nie może przenieść z jednej grupy do drugiego.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="e8ac0-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Właściwość kolumny określa, czy kolumna jest zawsze widoczny w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="e8ac0-111">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="e8ac0-112">Zobacz też [jak: Blokowanie kolumn w Windows Forms formantu DataGridView za pomocą projektanta](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e8ac0-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="e8ac0-113">Aby programowo Zablokuj kolumnę</span><span class="sxs-lookup"><span data-stu-id="e8ac0-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="e8ac0-114">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8ac0-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e8ac0-115">Compiling the Code</span></span>  
 <span data-ttu-id="e8ac0-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e8ac0-116">This example requires:</span></span>  
  
-   <span data-ttu-id="e8ac0-117">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="e8ac0-118">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="e8ac0-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ac0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8ac0-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="e8ac0-120">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8ac0-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="e8ac0-121">Instrukcje: Włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8ac0-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
