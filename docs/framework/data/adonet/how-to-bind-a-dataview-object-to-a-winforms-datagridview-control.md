---
title: 'Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795002"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="1df88-102">Instrukcje: Wiązanie obiektu widoku danych z kontrolką DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1df88-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1df88-103"><xref:System.Windows.Forms.DataGridView> Formant zapewnia zaawansowany i elastyczny sposób wyświetlania danych w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="1df88-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="1df88-104">Formant obsługuje model powiązań danych w warstwie Standardowa Windows Forms, więc zostanie powiązany z <xref:System.Data.DataView> wieloma innymi źródłami danych i z nich. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="1df88-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="1df88-105">W większości sytuacji należy jednak powiązać ze <xref:System.Windows.Forms.BindingSource> składnikiem, który będzie zarządzać szczegółami współpracy ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="1df88-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="1df88-106">Aby uzyskać więcej informacji na <xref:System.Windows.Forms.DataGridView> temat kontrolki, zobacz [formant DataGridView — Omówienie](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1df88-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="1df88-107">Aby połączyć formant DataGridView z obiektem DataView</span><span class="sxs-lookup"><span data-stu-id="1df88-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="1df88-108">Zaimplementuj metodę, aby obsłużyć Szczegóły pobierania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1df88-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="1df88-109">Poniższy przykład kodu implementuje `GetData` metodę <xref:System.Data.SqlClient.SqlDataAdapter> inicjującą składnik i <xref:System.Data.DataSet>używa jej do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="1df88-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1df88-110">Pamiętaj, aby ustawić `connectionString` zmienną na wartość odpowiednią dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1df88-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="1df88-111">Będziesz potrzebować dostępu do serwera z zainstalowaną przykładową bazą danych SQL Server AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1df88-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="1df88-112">W procedurze obsługi <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> `GetData` zdarzeń formularza Powiąż formant ze składnikiem i Wywołaj metodę, aby pobrać dane z bazy danych. <xref:System.Windows.Forms.Form.Load></span><span class="sxs-lookup"><span data-stu-id="1df88-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="1df88-113">Program jest tworzony na podstawie zapytania LINQ to DataSet w ramach kontaktu <xref:System.Data.DataTable> , a następnie <xref:System.Windows.Forms.BindingSource> jest powiązany ze składnikiem. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="1df88-113">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="1df88-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1df88-114">See also</span></span>

- [<span data-ttu-id="1df88-115">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1df88-115">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
