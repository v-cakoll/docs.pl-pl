---
title: 'Instrukcje: Dodawanie niepowiązanych kolumn do formantu DataGridView formularzy Windows powiązane z danymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: d7f96aa8d11cee9427a9e51f8e79fc55adc79355
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712019"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="ace7c-102">Instrukcje: Dodawanie niepowiązanych kolumn do formantu DataGridView formularzy Windows powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="ace7c-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ace7c-103">Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pochodzić z określonego rodzaju źródła danych, ale możesz chcieć wyświetlić kolumny danych, która nie pochodzi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ace7c-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="ace7c-104">Tego rodzaju kolumny jest nazywany niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="ace7c-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="ace7c-105">Niepowiązanych kolumn może mieć wiele form.</span><span class="sxs-lookup"><span data-stu-id="ace7c-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="ace7c-106">Służą one często, aby zapewnić dostęp do szczegółów wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="ace7c-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="ace7c-107">Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanych kolumn z **szczegóły** przycisków, aby wyświetlić tabeli podrzędnej związane z określonego wiersza w tabeli nadrzędnej, gdy implementować scenariusza wzorzec/szczegół.</span><span class="sxs-lookup"><span data-stu-id="ace7c-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="ace7c-108">Aby reagować na kliknięcia przycisku, zaimplementować <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> program obsługi zdarzeń, który wyświetla formularz zawierający tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ace7c-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="ace7c-109">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ace7c-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="ace7c-110">Zobacz też [jak: Dodawanie i usuwanie kolumn w Windows Forms formantu DataGridView za pomocą projektanta](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="ace7c-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace7c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ace7c-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ace7c-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ace7c-112">Compiling the Code</span></span>  
 <span data-ttu-id="ace7c-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ace7c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="ace7c-114">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ace7c-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="ace7c-115">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="ace7c-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace7c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ace7c-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="ace7c-117">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace7c-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ace7c-118">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace7c-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
