---
title: 'Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 7a567aa60e226803435b9b2b7b806097e9b47f76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230346"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="21a13-102">Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="21a13-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="21a13-103"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="21a13-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="21a13-104"><xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje standardowe model powiązanie danych formularzy Windows, więc tworzy powiązanie <xref:System.Data.DataView> i wielu innych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="21a13-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="21a13-105">W większości sytuacji, jednak użytkownik zostanie z nim powiązane <xref:System.Windows.Forms.BindingSource> składnik, który będzie zarządzać szczegółowe informacje o interakcji ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="21a13-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="21a13-106">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [— informacje o formancie DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="21a13-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="21a13-107">Aby nawiązać formantu DataGridView elementu DataView</span><span class="sxs-lookup"><span data-stu-id="21a13-107">To connect a DataGridView control to a DataView</span></span>  
  
1.  <span data-ttu-id="21a13-108">Implementuje metodę do obsługi Szczegóły pobierania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="21a13-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="21a13-109">Poniższy kod implementuje przykład `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter> składnika i używa ich do wypełnienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="21a13-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="21a13-110">Pamiętaj ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="21a13-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="21a13-111">Dostęp do serwera, należy za pomocą przykładowej bazie AdventureWorks programu SQL Server zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="21a13-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  <span data-ttu-id="21a13-112">W <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń z formularza, należy powiązać <xref:System.Windows.Forms.DataGridView> kontrolę <xref:System.Windows.Forms.BindingSource> składnika i wywołania `GetData` metodę, aby pobrać dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="21a13-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="21a13-113"><xref:System.Data.DataView> Jest tworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie dotyczące kontaktu <xref:System.Data.DataTable> , a następnie jest powiązany z <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="21a13-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="21a13-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21a13-114">See also</span></span>

- [<span data-ttu-id="21a13-115">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="21a13-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
