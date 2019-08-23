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
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966660"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fefaf-102">Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fefaf-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fefaf-103">Gdy użytkownicy wyświetlają dane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms, czasami muszą odwoływać się do pojedynczej kolumny lub zestawu kolumn często.</span><span class="sxs-lookup"><span data-stu-id="fefaf-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="fefaf-104">Na przykład podczas wyświetlania tabeli informacji o kliencie zawierającej wiele kolumn warto wyświetlić nazwę klienta przez cały czas, jednocześnie włączając inne kolumny przewijane poza widocznym regionem.</span><span class="sxs-lookup"><span data-stu-id="fefaf-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="fefaf-105">Aby osiągnąć takie zachowanie, można zablokować kolumny w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="fefaf-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="fefaf-106">Po zablokowaniu kolumny wszystkie kolumny po lewej stronie (lub po prawej stronie w skrypcie języka od prawej do lewej) również są zamrożone.</span><span class="sxs-lookup"><span data-stu-id="fefaf-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="fefaf-107">Zablokowane kolumny pozostają na miejscu, gdy wszystkie inne kolumny można przewijać.</span><span class="sxs-lookup"><span data-stu-id="fefaf-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fefaf-108">W przypadku włączenia zmiany kolejności kolumn zablokowane kolumny są traktowane jako odrębne dla grupy z odblokowanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="fefaf-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="fefaf-109">Użytkownicy mogą zmieniać położenie kolumn w jednej grupie, ale nie mogą przenosić kolumn z jednej grupy do drugiej.</span><span class="sxs-lookup"><span data-stu-id="fefaf-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="fefaf-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Właściwość kolumny określa, czy kolumna jest zawsze widoczna w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="fefaf-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="fefaf-111">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fefaf-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="fefaf-112">Zapoznaj [się również z tematem: Zablokuj kolumny w kontrolce DataGridView Windows Forms przy](freeze-columns-in-the-datagrid-using-the-designer.md)użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="fefaf-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="fefaf-113">Aby programowo zablokować kolumnę</span><span class="sxs-lookup"><span data-stu-id="fefaf-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="fefaf-114">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="fefaf-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fefaf-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fefaf-115">Compiling the Code</span></span>  
 <span data-ttu-id="fefaf-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fefaf-116">This example requires:</span></span>  
  
- <span data-ttu-id="fefaf-117">Kontrolka o `dataGridView1` nazwie, która zawiera kolumnę o nazwie `AddToCartButton`. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="fefaf-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="fefaf-118">Odwołania do <xref:System?displayProperty=nameWithType> zestawów i <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fefaf-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefaf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fefaf-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="fefaf-120">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fefaf-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="fefaf-121">Instrukcje: Włączanie zmiany kolejności kolumn w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fefaf-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
