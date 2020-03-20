---
title: Powiąż dane z formantem DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182275"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="207bf-102">Jak: Powiązać dane z formantem DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="207bf-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="207bf-103">Formant <xref:System.Windows.Forms.DataGridView> obsługuje standardowy model wiązania danych windows forms, dzięki czemu może wiązać się z różnymi źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="207bf-104">Zazwyczaj należy powiązać <xref:System.Windows.Forms.BindingSource> z, który zarządza interakcji ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="207bf-105">Może <xref:System.Windows.Forms.BindingSource> to być dowolne źródło danych Windows Forms, co zapewnia dużą elastyczność przy wyborze lub modyfikowaniu lokalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="207bf-106">Aby uzyskać więcej informacji <xref:System.Windows.Forms.DataGridView> na temat źródeł danych, które obsługuje formant, zobacz [omówienie kontroli DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="207bf-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="207bf-107">Visual Studio ma rozbudowaną obsługę powiązania danych z formantem DataGridView.</span><span class="sxs-lookup"><span data-stu-id="207bf-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="207bf-108">Aby uzyskać więcej informacji, zobacz [Jak: Powiązać dane z formantem DataGridView formularzy systemu Windows za pomocą projektanta](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="207bf-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="207bf-109">Aby połączyć formant DataGridView z danymi:</span><span class="sxs-lookup"><span data-stu-id="207bf-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="207bf-110">Zaimplementuj metodę obsługi szczegółów pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="207bf-111">Poniższy przykład kodu `GetData` implementuje metodę, <xref:System.Data.SqlClient.SqlDataAdapter>która inicjuje program , <xref:System.Data.DataTable>i używa jej do wypełniania pliku .</span><span class="sxs-lookup"><span data-stu-id="207bf-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="207bf-112">Następnie wiąże się <xref:System.Data.DataTable> z <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="207bf-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="207bf-113">W programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza <xref:System.Windows.Forms.DataGridView> powiąż formant z programem <xref:System.Windows.Forms.BindingSource>, i wywołaj `GetData` metodę pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="207bf-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="207bf-114">Example</span></span>

<span data-ttu-id="207bf-115">Ten przykład pełnego kodu pobiera dane z bazy danych w celu wypełnienia formantu DataGridView w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="207bf-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="207bf-116">Formularz zawiera również przyciski do ponownego ładowania danych i przesyłania zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="207bf-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="207bf-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="207bf-117">This example requires:</span></span>

- <span data-ttu-id="207bf-118">Dostęp do przykładowej bazy danych programu Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="207bf-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="207bf-119">Aby uzyskać więcej informacji na temat instalowania przykładowej bazy danych Northwind, zobacz [Pobieranie przykładowych baz danych dla ADO.NET przykładowych kodu](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="207bf-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="207bf-120">Odwołania do zestawów System, System.Windows.Forms, System.Data i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="207bf-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="207bf-121">Aby skompilować i uruchomić ten przykład, wklej kod do pliku kodu *Form1* w nowym projekcie Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="207bf-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="207bf-122">Aby uzyskać informacje o budowaniu z wiersza polecenia C# lub Visual Basic, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilacja z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="207bf-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="207bf-123">Wypełnij zmienną `connectionString` w przykładzie wartościami dla przykładowego połączenia bazy danych programu Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="207bf-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="207bf-124">Uwierzytelnianie systemu Windows, nazywane również zintegrowanymi zabezpieczeniami, jest bezpieczniejszym sposobem łączenia się z bazą danych niż przechowywanie hasła w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="207bf-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="207bf-125">Aby uzyskać więcej informacji na temat zabezpieczeń połączeń, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="207bf-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="207bf-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="207bf-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="207bf-127">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="207bf-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="207bf-128">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="207bf-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
