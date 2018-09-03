---
title: 'Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 39c637fe30ed852f7d6e9fa7a1dbbfa72af9e4b4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466072"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="07e47-102">Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="07e47-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="07e47-103">Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pochodzić z określonego rodzaju źródła danych, ale możesz chcieć wyświetlić kolumny danych, która nie pochodzi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="07e47-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="07e47-104">Tego rodzaju kolumny jest nazywany niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="07e47-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="07e47-105">Niepowiązanych kolumn może mieć wiele form.</span><span class="sxs-lookup"><span data-stu-id="07e47-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="07e47-106">Służą one często, aby zapewnić dostęp do szczegółów wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="07e47-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="07e47-107">Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanych kolumn z **szczegóły** przycisków, aby wyświetlić tabeli podrzędnej związane z określonego wiersza w tabeli nadrzędnej, gdy implementować scenariusza wzorzec/szczegół.</span><span class="sxs-lookup"><span data-stu-id="07e47-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="07e47-108">Aby reagować na kliknięcia przycisku, zaimplementować <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> program obsługi zdarzeń, który wyświetla formularz zawierający tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="07e47-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="07e47-109">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07e47-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="07e47-110">Zobacz też [porady: Dodawanie i usuwanie kolumn w Windows Forms DataGridView kontroli przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="07e47-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e47-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="07e47-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07e47-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="07e47-112">Compiling the Code</span></span>  
 <span data-ttu-id="07e47-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="07e47-113">This example requires:</span></span>  
  
-   <span data-ttu-id="07e47-114">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="07e47-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="07e47-115">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="07e47-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e47-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07e47-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="07e47-117">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07e47-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="07e47-118">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07e47-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
