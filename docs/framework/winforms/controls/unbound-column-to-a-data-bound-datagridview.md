---
title: "Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cd6a1494a98d912469f7e45c7751a0a9741ff17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="0e4e5-102">Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0e4e5-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0e4e5-103">Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pobierane z określonego rodzaju źródła danych, ale należy wyświetlić kolumny danych, które nie pochodzą ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="0e4e5-104">Tego rodzaju kolumny jest nazywany niepowiązanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="0e4e5-105">Niepowiązanych kolumn może mieć wiele form.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="0e4e5-106">Często są one używane do zapewniania dostępu do szczegółów wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="0e4e5-107">Poniższy przykładowy kod przedstawia sposób tworzenia niepowiązanych kolumn z **szczegóły** przyciski, aby wyświetlić tabeli podrzędnej dotyczące określonego wiersza w tabeli nadrzędnej podczas implementowania scenariusza wzorzec/szczegół.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="0e4e5-108">Aby odpowiadanie na kliknięcia przycisku, zaimplementuj <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obsługi zdarzeń, który wyświetla formularz zawierający tabelą podrzędną.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="0e4e5-109">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="0e4e5-110">Zobacz też [porady: Dodawanie i usuwanie kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0e4e5-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e4e5-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e4e5-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e4e5-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0e4e5-112">Compiling the Code</span></span>  
 <span data-ttu-id="0e4e5-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0e4e5-113">This example requires:</span></span>  
  
-   <span data-ttu-id="0e4e5-114">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="0e4e5-115">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="0e4e5-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e4e5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e4e5-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="0e4e5-117">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0e4e5-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0e4e5-118">Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0e4e5-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
