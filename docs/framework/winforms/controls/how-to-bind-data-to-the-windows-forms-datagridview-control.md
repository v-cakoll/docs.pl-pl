---
title: 'Instrukcje: powiązywanie danych z Windows Forms formant DataGridView'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: bdba8af04cd9473b17d1a28f07ead7cd5bf43698
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139092"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="2ff21-102">Instrukcje: powiązywanie danych z Windows Forms formant DataGridView</span><span class="sxs-lookup"><span data-stu-id="2ff21-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="2ff21-103">Formant <xref:System.Windows.Forms.DataGridView> obsługuje model powiązań danych w warstwie Standardowa Windows Forms, dzięki czemu można powiązać z różnymi źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="2ff21-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="2ff21-104">Zwykle wiąże się z <xref:System.Windows.Forms.BindingSource>, która zarządza interakcją ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="2ff21-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="2ff21-105"><xref:System.Windows.Forms.BindingSource> może być dowolnym Windows Forms źródłem danych, co zapewnia dużą elastyczność podczas wybierania lub modyfikowania lokalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="2ff21-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="2ff21-106">Aby uzyskać więcej informacji na temat źródeł danych obsługiwanych przez formant <xref:System.Windows.Forms.DataGridView>, zobacz [formant DataGridView — Omówienie](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2ff21-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="2ff21-107">Program Visual Studio ma rozbudowaną obsługę powiązań danych z formantem DataGridView.</span><span class="sxs-lookup"><span data-stu-id="2ff21-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="2ff21-108">Aby uzyskać więcej informacji, zobacz [jak: powiązywanie danych z kontrolką DataGridView Windows Forms przy użyciu narzędzia Projektant](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="2ff21-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="2ff21-109">Aby połączyć formant DataGridView z danymi:</span><span class="sxs-lookup"><span data-stu-id="2ff21-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="2ff21-110">Zaimplementuj metodę, aby obsłużyć Szczegóły pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="2ff21-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="2ff21-111">Poniższy przykład kodu implementuje metodę `GetData`, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter>, i używa jej do wypełnienia <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="2ff21-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2ff21-112">Następnie wiąże <xref:System.Data.DataTable> z <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="2ff21-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="2ff21-113">W <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń, powiąż formant <xref:System.Windows.Forms.DataGridView> z <xref:System.Windows.Forms.BindingSource>i Wywołaj metodę `GetData`, aby pobrać dane.</span><span class="sxs-lookup"><span data-stu-id="2ff21-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="2ff21-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ff21-114">Example</span></span>

<span data-ttu-id="2ff21-115">Ten kompletny przykład kodu pobiera dane z bazy danych, aby wypełnić formant DataGridView w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ff21-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="2ff21-116">Formularz zawiera również przyciski do ponownego ładowania danych i przesyłania zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2ff21-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="2ff21-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2ff21-117">This example requires:</span></span> 

- <span data-ttu-id="2ff21-118">Dostęp do przykładowej bazy danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2ff21-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="2ff21-119">Aby uzyskać więcej informacji na temat instalowania przykładowej bazy danych Northwind, zobacz [Pobieranie przykładowych baz danych dla przykładów kodu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="2ff21-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="2ff21-120">Odwołania do zestawów system, system. Windows. Forms, system. Data i system. XML.</span><span class="sxs-lookup"><span data-stu-id="2ff21-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="2ff21-121">Aby skompilować i uruchomić ten przykład, wklej kod do pliku kodu *Form1* w nowym projekcie Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ff21-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="2ff21-122">Aby uzyskać informacje na temat kompilowania z poziomu wiersza polecenia C# lub Visual Basic, zobacz wiersza polecenia [kompilowanego za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilowanie z poziomu wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="2ff21-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="2ff21-123">Wypełnij zmienną `connectionString` w przykładzie wartościami dla przykładowego połączenia bazy danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2ff21-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="2ff21-124">Uwierzytelnianie systemu Windows, nazywane również zabezpieczeniami zintegrowanymi, jest bezpieczniejszym sposobem łączenia się z bazą danych niż przechowywanie hasła w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="2ff21-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="2ff21-125">Aby uzyskać więcej informacji o zabezpieczeniach połączeń, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="2ff21-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2ff21-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ff21-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2ff21-127">Wyświetlanie danych w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ff21-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ff21-128">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="2ff21-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
