---
title: "Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows"
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
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2107da50f3b8a569bc329dbb1ae1722141921e11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="59a10-102">Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="59a10-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="59a10-103">Jeśli używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, w kolumnach czasami schematu źródła danych nie są wyświetlane w kolejności, aby je wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="59a10-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="59a10-104">Można zmienić kolejność wyświetlanych kolumn za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumn> klasy.</span><span class="sxs-lookup"><span data-stu-id="59a10-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="59a10-105">Poniższy przykład kodu powoduje przeniesienie niektóre kolumny są generowane automatycznie podczas wiązania z tabeli Klienci w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="59a10-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="59a10-106">Aby uzyskać więcej informacji o sposobie wiązania <xref:System.Windows.Forms.DataGridView> sterowania do tabeli bazy danych, zobacz [porady: wiązania danych formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="59a10-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="59a10-107">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59a10-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="59a10-108">Zobacz też [porady: Zmienianie kolejności kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="59a10-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="59a10-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="59a10-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59a10-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="59a10-110">Compiling the Code</span></span>  
 <span data-ttu-id="59a10-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="59a10-111">This example requires:</span></span>  
  
-   <span data-ttu-id="59a10-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView` takich jak, który jest powiązany z tabelą z nazwami wskazanej kolumny `Customers` tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="59a10-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="59a10-113">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="59a10-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a10-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59a10-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="59a10-115">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="59a10-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="59a10-116">Porady: wiązanie danych formularzy systemu Windows formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="59a10-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
