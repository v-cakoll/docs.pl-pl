---
title: Zmiana kolejności kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746545"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8a3b2-102">Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8a3b2-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8a3b2-103">Gdy używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, kolumny w schemacie źródła danych czasami nie są wyświetlane w kolejności, w jakiej chcesz je wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="8a3b2-104">Można zmienić kolejność wyświetlania kolumn za pomocą właściwości <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> klasy <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="8a3b2-105">Poniższy przykład kodu zmienia położenie niektórych kolumn generowanych automatycznie podczas tworzenia powiązania z tabelą Customers w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="8a3b2-106">Aby uzyskać więcej informacji o sposobie powiązania formantu <xref:System.Windows.Forms.DataGridView> z tabelą bazy danych, zobacz [How to: bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8a3b2-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="8a3b2-107">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8a3b2-108">Zapoznaj się również z tematem [: zmiana kolejności kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8a3b2-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a3b2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a3b2-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a3b2-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8a3b2-110">Compiling the Code</span></span>  
 <span data-ttu-id="8a3b2-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8a3b2-111">This example requires:</span></span>  
  
- <span data-ttu-id="8a3b2-112">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `customersDataGridView`, która jest powiązana z tabelą ze wskazanymi nazwami kolumn, takimi jak tabela `Customers` w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="8a3b2-113">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>i <xref:System.Xml?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a3b2-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3b2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a3b2-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8a3b2-115">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a3b2-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8a3b2-116">Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a3b2-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
