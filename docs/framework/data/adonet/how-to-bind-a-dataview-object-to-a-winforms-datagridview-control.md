---
title: "Porady: powiązanie obiektu DataView do formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 599d91c9a19d68f26e4dbad285886b3c2e096b94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="33e47-102">Porady: powiązanie obiektu DataView do formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="33e47-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="33e47-103"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="33e47-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="33e47-104"><xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje standardowy model powiązanie danych formularzy systemu Windows, więc będzie powiązać <xref:System.Data.DataView> i różnych innych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="33e47-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="33e47-105">W większości sytuacji należy jednak użytkownik zostanie z nim powiązane <xref:System.Windows.Forms.BindingSource> składnik, który będzie zarządzać szczegółowe informacje o interakcji ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="33e47-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="33e47-106">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [informacje o formancie DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="33e47-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="33e47-107">Aby nawiązać połączenie DataView formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="33e47-107">To connect a DataGridView control to a DataView</span></span>  
  
1.  <span data-ttu-id="33e47-108">Implementuje metody obsługi szczegóły pobieranie danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="33e47-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="33e47-109">Poniższy kod przykładowy implementuje `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter> składnika i używa go do wypełnienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="33e47-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="33e47-110">Należy ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="33e47-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="33e47-111">Konieczne będzie dostęp do serwera z bazą danych przykładowych AdventureWorks programu SQL Server, które zostały zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="33e47-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  <span data-ttu-id="33e47-112">W <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń formularza, powiązać <xref:System.Windows.Forms.DataGridView> formant <xref:System.Windows.Forms.BindingSource> składnika i wywołania `GetData` metody do pobierania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="33e47-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="33e47-113"><xref:System.Data.DataView> Jest tworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie dotyczące kontaktu <xref:System.Data.DataTable> , a następnie jest powiązany z <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="33e47-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="33e47-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33e47-114">See Also</span></span>  
 [<span data-ttu-id="33e47-115">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="33e47-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
