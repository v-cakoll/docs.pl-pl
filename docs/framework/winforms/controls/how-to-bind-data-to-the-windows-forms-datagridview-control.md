---
title: 'Porady: powiązanie danych z formantem DataGridView formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c3be381f67ae57e9fbd9dd526d4d3364c864903
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="a4c24-102">Porady: powiązanie danych z formantem DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4c24-102">How to: Bind Data to the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a4c24-103"><xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje standardowy model powiązanie danych formularzy systemu Windows, więc zostanie powiązany z różnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to a variety of data sources.</span></span> <span data-ttu-id="a4c24-104">W większości przypadków, jednak użytkownik zostanie z nim powiązane <xref:System.Windows.Forms.BindingSource> składników, które będą zarządzać szczegółowe informacje o interakcji ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-104">In most circumstances, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component which will manage the details of interacting with the data source.</span></span> <span data-ttu-id="a4c24-105"><xref:System.Windows.Forms.BindingSource> Składnika może reprezentować dowolnego źródła danych formularzy systemu Windows i zapewnia elastyczność podczas wybierania lub modyfikowania lokalizację danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-105">The <xref:System.Windows.Forms.BindingSource> component can represent any Windows Forms data source and gives you great flexibility when choosing or modifying the location of your data.</span></span> <span data-ttu-id="a4c24-106">Aby uzyskać więcej informacji o źródłach danych obsługiwane przez <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [informacje o formancie DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a4c24-106">For more information about the data sources supported by the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="a4c24-107">Brak kompleksową obsługę tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4c24-107">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="a4c24-108">Zobacz też [porady: powiązanie danych do systemu Windows Forms DataGridView formantu przy użyciu projektanta](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a4c24-108">Also see [How to: Bind Data to the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a4c24-109">Procedura</span><span class="sxs-lookup"><span data-stu-id="a4c24-109">Procedure</span></span>  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a><span data-ttu-id="a4c24-110">Aby nawiązać połączenie danych formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c24-110">To connect a DataGridView control to data</span></span>  
  
1.  <span data-ttu-id="a4c24-111">Implementuje metody obsługi szczegóły pobieranie danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-111">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="a4c24-112">Poniższy kod przykładowy implementuje `GetData` metodę, która inicjuje <xref:System.Data.SqlClient.SqlDataAdapter> składnika i używa go do wypełnienia <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a4c24-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a4c24-113"><xref:System.Data.DataTable> Następnie jest powiązany z <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="a4c24-113">The <xref:System.Data.DataTable> is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a4c24-114">Należy ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-114">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="a4c24-115">Konieczne będzie dostęp do serwera z bazy danych przykładowych Northwind SQL Server, które zostały zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="a4c24-115">You will need access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  <span data-ttu-id="a4c24-116">Do formularza <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń, bind <xref:System.Windows.Forms.DataGridView> formant <xref:System.Windows.Forms.BindingSource> składnika i wywołania `GetData` metody do pobierania danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-116">In your form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="a4c24-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4c24-117">Example</span></span>  
 <span data-ttu-id="a4c24-118">W poniższym przykładzie kompletny kod zawiera przyciski do ponownego ładowania danych z bazy danych i przesyłanie zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-118">The following complete code example provides buttons for reloading data from the database and submitting changes to the database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4c24-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a4c24-119">Compiling the Code</span></span>  
 <span data-ttu-id="a4c24-120">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a4c24-120">This example requires:</span></span>  
  
-   <span data-ttu-id="a4c24-121">Odwołania do zestawów systemu, System.Windows.Forms dane systemowe i zestawów System.XML.</span><span class="sxs-lookup"><span data-stu-id="a4c24-121">References to the System, System.Windows.Forms, System.Data, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="a4c24-122">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a4c24-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a4c24-123">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="a4c24-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="a4c24-124">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a4c24-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a4c24-125">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4c24-125">.NET Framework Security</span></span>  
 <span data-ttu-id="a4c24-126">Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4c24-126">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="a4c24-127">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a4c24-127">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="a4c24-128">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="a4c24-128">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c24-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c24-129">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="a4c24-130">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4c24-130">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="a4c24-131">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="a4c24-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
