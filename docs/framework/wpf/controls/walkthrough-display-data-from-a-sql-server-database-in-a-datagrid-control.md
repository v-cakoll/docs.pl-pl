---
title: "Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8ed596706c8d656842191262c25301db595ee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="3bdc3-102">Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid</span><span class="sxs-lookup"><span data-stu-id="3bdc3-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="3bdc3-103">W tym przewodniku, pobieranie danych z bazy danych programu SQL Server i wyświetlić dane w <xref:System.Windows.Controls.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="3bdc3-104">ADO.NET Entity Framework umożliwia tworzenie klasy jednostki, które reprezentują dane i użyć LINQ, aby zapisać kwerendę, która pobiera określone dane z klasy jednostka.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3bdc3-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3bdc3-105">Prerequisites</span></span>  
 <span data-ttu-id="3bdc3-106">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="3bdc3-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="3bdc3-107">.,</span><span class="sxs-lookup"><span data-stu-id="3bdc3-107">.</span></span>  
  
-   <span data-ttu-id="3bdc3-108">Dostęp do działającego wystąpienia programu SQL Server lub SQL Server Express zawierający przykładową bazę danych AdventureWorks do niego dołączony.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="3bdc3-109">Możesz pobrać z bazy danych AdventureWorks z [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="3bdc3-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="3bdc3-110">Do tworzenia klas jednostki</span><span class="sxs-lookup"><span data-stu-id="3bdc3-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="3bdc3-111">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub C# i nadaj mu nazwę `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="3bdc3-112">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż pozycję **Dodaj**, a następnie wybierz **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="3bdc3-113">Zostanie wyświetlone okno dialogowe Dodaj nowy element.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="3bdc3-114">Wybierz w okienku zainstalowane szablony **danych** i na liście szablonów wybierz **Tryb danych jednostki ADO.NET**l.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="3bdc3-115">![Wybierz modelu danych jednostki ADO.NET](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="3bdc3-116">Nadaj nazwę plikowi `AdventureWorksModel.edmx` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="3bdc3-117">Zostanie wyświetlony Kreator modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="3bdc3-118">Na ekranie Wybierz zawartość modelu wybierz **generowania z bazy danych** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="3bdc3-119">![Generuj należy wybierać opcji bazy danych](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="3bdc3-120">Na ekranie Wybierz połączenie danych Podaj połączenia z bazą danych AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="3bdc3-121">Aby uzyskać więcej informacji, zobacz [wybierz Twoje dane okno dialogowe połączenia](http://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="3bdc3-121">For more information, see [Choose Your Data Connection Dialog Box](http://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="3bdc3-122">![Podaj połączenia z bazą danych](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="3bdc3-123">Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i **Zapisz ustawienia połączenia w pliku App.Config jako jednostki** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="3bdc3-124">Na ekranie Wybierz obiekty bazy danych użytkownika, rozwiń węzeł tabele, a następnie wybierz **produktu** i **ProductCategory** tabel.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="3bdc3-125">Można wygenerować klas jednostek dla wszystkich tabel. Jednak w tym przykładzie można tylko pobieranie danych z tych dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="3bdc3-126">![Wybierz produkt i ProductCategory z tabel](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="3bdc3-127">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="3bdc3-128">Obiekty produktu i ProductCategory są wyświetlane w programie Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="3bdc3-129">![Modele jednostki produktu i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="3bdc3-130">Aby pobrać i przedstawiają dane</span><span class="sxs-lookup"><span data-stu-id="3bdc3-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="3bdc3-131">Otwórz plik MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="3bdc3-132">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Window> do 450.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="3bdc3-133">W edytorze XAML, Dodaj następujący <xref:System.Windows.Controls.DataGrid> tagu między `<Grid>` i `</Grid>` znaczniki, aby dodać <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="3bdc3-134">![Okno z elementu DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="3bdc3-135">Wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="3bdc3-136">Przy użyciu okna właściwości lub edytora XAML, utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="3bdc3-137">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego obsługi zdarzeń](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="3bdc3-137">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="3bdc3-138">Poniżej przedstawiono XAML MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3bdc3-139">Jeśli korzystasz z języka Visual Basic w pierwszym wierszu MainWindow.xaml, Zastąp `x:Class="DataGridSQLExample.MainWindow"` z `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="3bdc3-140">Otwórz plik CodeBehind (MainWindow.xaml.vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="3bdc3-141">Dodaj następujący kod, aby pobrać tylko określone wartości z połączonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="3bdc3-142">Można uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-142">Run the example.</span></span>  
  
     <span data-ttu-id="3bdc3-143">Powinny pojawić się <xref:System.Windows.Controls.DataGrid> wyświetlający dane.</span><span class="sxs-lookup"><span data-stu-id="3bdc3-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="3bdc3-144">![DataGrid z danymi z bazy danych SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="3bdc3-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3bdc3-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3bdc3-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdc3-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bdc3-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="3bdc3-147">Jak I: wprowadzenie do programu Entity Framework w aplikacjach WPF?</span><span class="sxs-lookup"><span data-stu-id="3bdc3-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](http://go.microsoft.com/fwlink/?LinkId=159868)
