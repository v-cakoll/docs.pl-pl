---
title: 'Instrukcje: Powiąż dane z formantu DataGridView formularzy Windows'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010933"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="d8505-102">Instrukcje: Powiąż dane z formantu DataGridView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="d8505-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="d8505-103"><xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje standardowy model powiązanie danych formularzy Windows, dzięki czemu można powiązać różnorodne źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="d8505-104">Zazwyczaj można powiązać <xref:System.Windows.Forms.BindingSource> który zarządza interakcji ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="d8505-105"><xref:System.Windows.Forms.BindingSource> Mogą być dowolnego źródła danych Windows Forms, co zapewnia dużą elastyczność podczas wybierania lub modyfikowania lokalizacji usługi danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="d8505-106">Aby uzyskać więcej informacji o źródłach danych <xref:System.Windows.Forms.DataGridView> kontrolować obsługuje, zobacz [— informacje o formancie DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d8505-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="d8505-107">Program Visual Studio została rozbudowana Obsługa powiązanie danych z kontrolką DataGridView.</span><span class="sxs-lookup"><span data-stu-id="d8505-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="d8505-108">Aby uzyskać więcej informacji, zobacz [jak: Powiąż dane z formantu DataGridView formularzy Windows za pomocą projektanta](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d8505-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="d8505-109">Do formantu DataGridView połączyć się z danymi:</span><span class="sxs-lookup"><span data-stu-id="d8505-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="d8505-110">Implementuje metodę do obsługi Szczegóły pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="d8505-111">Poniższy kod implementuje przykład `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter>i używa ich do wypełnienia <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d8505-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d8505-112">Następnie powiąże <xref:System.Data.DataTable> do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="d8505-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="d8505-113">W formularzu <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń, powiązania <xref:System.Windows.Forms.DataGridView> kontrolę <xref:System.Windows.Forms.BindingSource>i wywoływać `GetData` metody do pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="d8505-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8505-114">Example</span></span>

<span data-ttu-id="d8505-115">Ten przykład kompletny kod pobiera dane z bazy danych do wypełnienia formantu DataGridView w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="d8505-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="d8505-116">Formularz zawiera również przycisków, aby ponownie załadować danych i przesyłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="d8505-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d8505-117">This example requires:</span></span> 

- <span data-ttu-id="d8505-118">Dostęp do przykładowej bazy danych Northwind programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8505-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="d8505-119">Aby uzyskać więcej informacji na temat Instalowanie przykładowej bazy danych Northwind, zobacz [przykładowych baz danych należy uzyskać przykłady kodu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d8505-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="d8505-120">Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms, dane systemowe i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="d8505-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="d8505-121">Aby skompilować i uruchomić ten przykład, Wklej kod do *Form1* pliku z kodem w nowym projekcie Windows Form.</span><span class="sxs-lookup"><span data-stu-id="d8505-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="d8505-122">Aby uzyskać informacje dotyczące tworzenia aplikacji z C# lub wiersza polecenia programu Visual Basic, zobacz [za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilacji z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="d8505-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="d8505-123">Wypełnij `connectionString` zmiennej w przykładzie z wartościami połączenia programu SQL Server Northwind przykładowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d8505-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="d8505-124">Uwierzytelnianie Windows, nazywany również zabezpieczenia zintegrowane jest bardziej bezpieczny sposób łączenia z bazą danych niż przechowywanie hasła w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="d8505-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="d8505-125">Aby uzyskać więcej informacji na temat zabezpieczeń połączeń, zobacz [chronić informacje o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="d8505-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d8505-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8505-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="d8505-127">Wyświetlanie danych w formancie DataGridView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="d8505-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d8505-128">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="d8505-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
