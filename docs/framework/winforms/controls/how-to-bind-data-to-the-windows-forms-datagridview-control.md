---
title: Powiązywanie danych z kontrolką DataGridView
ms.date: 02/08/2019
description: Dowiedz się, jak formant DataGridView obsługuje standardowy model powiązań danych Windows Forms, aby można było powiązać z różnymi źródłami danych.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904419"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="f3244-103">Instrukcje: powiązywanie danych z Windows Forms formant DataGridView</span><span class="sxs-lookup"><span data-stu-id="f3244-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="f3244-104"><xref:System.Windows.Forms.DataGridView>Formant obsługuje model powiązań danych w warstwie standardowa Windows Forms, więc można powiązać z wieloma źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="f3244-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="f3244-105">Zwykle wiąże się to z <xref:System.Windows.Forms.BindingSource> usługą, która zarządza interakcją ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="f3244-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="f3244-106"><xref:System.Windows.Forms.BindingSource>Może to być dowolne Windows Forms źródła danych, co zapewnia dużą elastyczność podczas wybierania lub modyfikowania lokalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="f3244-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="f3244-107">Aby uzyskać więcej informacji o źródłach danych <xref:System.Windows.Forms.DataGridView> obsługiwanych przez kontrolkę, zobacz [formant DataGridView — Omówienie](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f3244-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="f3244-108">Program Visual Studio ma rozbudowaną obsługę powiązań danych z formantem DataGridView.</span><span class="sxs-lookup"><span data-stu-id="f3244-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="f3244-109">Aby uzyskać więcej informacji, zobacz [jak: powiązywanie danych z kontrolką DataGridView Windows Forms przy użyciu narzędzia Projektant](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f3244-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="f3244-110">Aby połączyć formant DataGridView z danymi:</span><span class="sxs-lookup"><span data-stu-id="f3244-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="f3244-111">Zaimplementuj metodę, aby obsłużyć Szczegóły pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="f3244-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="f3244-112">Poniższy przykład kodu implementuje `GetData` metodę inicjującą a <xref:System.Data.SqlClient.SqlDataAdapter> i używa jej do wypełnienia <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="f3244-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="f3244-113">Następnie tworzy powiązanie z <xref:System.Data.DataTable> <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="f3244-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="f3244-114">W programie <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń formularza Powiąż formant z <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> i Wywołaj `GetData` metodę, aby pobrać dane.</span><span class="sxs-lookup"><span data-stu-id="f3244-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="f3244-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3244-115">Example</span></span>

<span data-ttu-id="f3244-116">Ten kompletny przykład kodu pobiera dane z bazy danych, aby wypełnić formant DataGridView w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f3244-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="f3244-117">Formularz zawiera również przyciski do ponownego ładowania danych i przesyłania zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f3244-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="f3244-118">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f3244-118">This example requires:</span></span>

- <span data-ttu-id="f3244-119">Dostęp do przykładowej bazy danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f3244-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="f3244-120">Aby uzyskać więcej informacji na temat instalowania przykładowej bazy danych Northwind, zobacz [Pobieranie przykładowych baz danych dla przykładów kodu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f3244-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="f3244-121">Odwołania do zestawów system, system. Windows. Forms, system. Data i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="f3244-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="f3244-122">Aby skompilować i uruchomić ten przykład, wklej kod do pliku kodu *Form1* w nowym projekcie Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3244-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="f3244-123">Aby uzyskać informacje na temat kompilowania z poziomu wiersza polecenia C# lub Visual Basic, zobacz wiersz [polecenia kompilacja z csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompiluj z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="f3244-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="f3244-124">Wypełnij `connectionString` zmienną w przykładzie wartościami dla przykładowego połączenia bazy danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f3244-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="f3244-125">Uwierzytelnianie systemu Windows, nazywane również zabezpieczeniami zintegrowanymi, jest bezpieczniejszym sposobem łączenia się z bazą danych niż przechowywanie hasła w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="f3244-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="f3244-126">Aby uzyskać więcej informacji o zabezpieczeniach połączeń, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="f3244-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3244-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3244-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="f3244-128">Wyświetlanie danych w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3244-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f3244-129">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="f3244-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
