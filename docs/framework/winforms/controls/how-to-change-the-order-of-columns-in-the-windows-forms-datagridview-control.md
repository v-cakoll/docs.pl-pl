---
title: 'Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: f3b1ddd583f76ab135d13108f8c62775ab894c83
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204503"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0fccb-102">Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fccb-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0fccb-103">Kiedy używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, w kolumnach czasami schematu źródła danych nie są wyświetlane w kolejności, aby je wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="0fccb-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="0fccb-104">Można zmienić kolejność wyświetlanych kolumn, używając <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumn> klasy.</span><span class="sxs-lookup"><span data-stu-id="0fccb-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="0fccb-105">Poniższy przykładowy kod powoduje przeniesienie niektórych kolumn generowane automatycznie podczas tworzenia wiązania do tabeli Klienci w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0fccb-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="0fccb-106">Aby uzyskać więcej informacji o tym, jak powiązać <xref:System.Windows.Forms.DataGridView> sterowania do tabeli bazy danych, zobacz [porady: powiązywanie danych z kontrolką DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0fccb-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="0fccb-107">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0fccb-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="0fccb-108">Zobacz też [porady: Zmienianie kolejności kolumn w Windows Forms DataGridView kontroli przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0fccb-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fccb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fccb-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fccb-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0fccb-110">Compiling the Code</span></span>  
 <span data-ttu-id="0fccb-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0fccb-111">This example requires:</span></span>  
  
-   <span data-ttu-id="0fccb-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView` , jest powiązana z tabelą z nazwami wskazanej kolumny, takie jak `Customers` tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0fccb-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="0fccb-113">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="0fccb-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fccb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fccb-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0fccb-115">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fccb-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0fccb-116">Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fccb-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
