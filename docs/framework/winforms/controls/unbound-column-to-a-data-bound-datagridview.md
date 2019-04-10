---
title: 'Instrukcje: dodawanie niepowiązanych kolumn do powiązanej z danymi kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 40308f7e8cc12dcff5b7d4393645f6a9007cc2b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215842"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="a95ee-102">Instrukcje: dodawanie niepowiązanych kolumn do powiązanej z danymi kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a95ee-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a95ee-103">Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pochodzić z określonego rodzaju źródła danych, ale możesz chcieć wyświetlić kolumny danych, która nie pochodzi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a95ee-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="a95ee-104">Tego rodzaju kolumny jest nazywany niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="a95ee-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="a95ee-105">Niepowiązanych kolumn może mieć wiele form.</span><span class="sxs-lookup"><span data-stu-id="a95ee-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="a95ee-106">Służą one często, aby zapewnić dostęp do szczegółów wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="a95ee-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="a95ee-107">Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanych kolumn z **szczegóły** przycisków, aby wyświetlić tabeli podrzędnej związane z określonego wiersza w tabeli nadrzędnej, gdy implementować scenariusza wzorzec/szczegół.</span><span class="sxs-lookup"><span data-stu-id="a95ee-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="a95ee-108">Aby reagować na kliknięcia przycisku, zaimplementować <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> program obsługi zdarzeń, który wyświetla formularz zawierający tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a95ee-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="a95ee-109">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a95ee-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="a95ee-110">Zobacz też [jak: Dodawanie i usuwanie kolumn w Windows Forms formantu DataGridView za pomocą projektanta](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a95ee-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a95ee-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a95ee-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a95ee-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a95ee-112">Compiling the Code</span></span>  
 <span data-ttu-id="a95ee-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a95ee-113">This example requires:</span></span>  
  
-   <span data-ttu-id="a95ee-114">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a95ee-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="a95ee-115">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="a95ee-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95ee-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a95ee-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a95ee-117">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a95ee-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a95ee-118">Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a95ee-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
