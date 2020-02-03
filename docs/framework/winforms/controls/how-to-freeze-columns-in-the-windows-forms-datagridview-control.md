---
title: Zablokuj kolumny w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6d1a98e5c4332078c6012cb7c9ed836108abd86c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736743"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d68e8-102">Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d68e8-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d68e8-103">Gdy użytkownicy będą wyświetlać dane wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms, czasami muszą odwoływać się do pojedynczej kolumny lub zestawu kolumn często.</span><span class="sxs-lookup"><span data-stu-id="d68e8-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="d68e8-104">Na przykład podczas wyświetlania tabeli informacji o kliencie zawierającej wiele kolumn warto wyświetlić nazwę klienta przez cały czas, jednocześnie włączając inne kolumny przewijane poza widocznym regionem.</span><span class="sxs-lookup"><span data-stu-id="d68e8-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="d68e8-105">Aby osiągnąć takie zachowanie, można zablokować kolumny w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="d68e8-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="d68e8-106">Po zablokowaniu kolumny wszystkie kolumny po lewej stronie (lub po prawej stronie w skrypcie języka od prawej do lewej) również są zamrożone.</span><span class="sxs-lookup"><span data-stu-id="d68e8-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="d68e8-107">Zablokowane kolumny pozostają na miejscu, gdy wszystkie inne kolumny można przewijać.</span><span class="sxs-lookup"><span data-stu-id="d68e8-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d68e8-108">W przypadku włączenia zmiany kolejności kolumn zablokowane kolumny są traktowane jako odrębne dla grupy z odblokowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="d68e8-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="d68e8-109">Użytkownicy mogą zmieniać położenie kolumn w jednej grupie, ale nie mogą przenosić kolumn z jednej grupy do drugiej.</span><span class="sxs-lookup"><span data-stu-id="d68e8-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="d68e8-110">Właściwość <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> kolumny określa, czy kolumna jest zawsze widoczna w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="d68e8-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="d68e8-111">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d68e8-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="d68e8-112">Zobacz również [instrukcje: zamrażanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d68e8-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="d68e8-113">Aby programowo zablokować kolumnę</span><span class="sxs-lookup"><span data-stu-id="d68e8-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="d68e8-114">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="d68e8-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d68e8-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d68e8-115">Compiling the Code</span></span>  
 <span data-ttu-id="d68e8-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d68e8-116">This example requires:</span></span>  
  
- <span data-ttu-id="d68e8-117">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`, która zawiera kolumnę o nazwie `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="d68e8-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="d68e8-118">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d68e8-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68e8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d68e8-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d68e8-120">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d68e8-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="d68e8-121">Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d68e8-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
