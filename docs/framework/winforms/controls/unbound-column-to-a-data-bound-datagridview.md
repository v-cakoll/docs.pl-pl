---
title: Dodawanie niepowiązanej kolumny do kontrolki DataGridView powiązanej z danymi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747063"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="f0317-102">Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f0317-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f0317-103">Dane wyświetlane w formancie <xref:System.Windows.Forms.DataGridView> zwykle pochodzą ze źródła danych pewnego rodzaju, ale może być konieczne wyświetlenie kolumny danych, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f0317-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="f0317-104">Ten rodzaj kolumny nosi nazwę kolumny niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="f0317-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="f0317-105">Kolumny niepowiązane mogą przyjmować wiele form.</span><span class="sxs-lookup"><span data-stu-id="f0317-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="f0317-106">Często są one używane do zapewnienia dostępu do szczegółów wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="f0317-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="f0317-107">Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanej kolumny **szczegółów** , aby wyświetlić tabelę podrzędną powiązaną z określonym wierszem w tabeli nadrzędnej podczas implementowania scenariusza wzorzec/szczegóły.</span><span class="sxs-lookup"><span data-stu-id="f0317-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="f0317-108">Aby reagować na kliknięcia przycisku, zaimplementuj procedurę obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>, która wyświetla formularz zawierający tabelę podrzędną.</span><span class="sxs-lookup"><span data-stu-id="f0317-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="f0317-109">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0317-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f0317-110">Zobacz również [instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f0317-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0317-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0317-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0317-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f0317-112">Compiling the Code</span></span>  
 <span data-ttu-id="f0317-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f0317-113">This example requires:</span></span>  
  
- <span data-ttu-id="f0317-114">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f0317-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f0317-115">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0317-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0317-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0317-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="f0317-117">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0317-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f0317-118">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0317-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
