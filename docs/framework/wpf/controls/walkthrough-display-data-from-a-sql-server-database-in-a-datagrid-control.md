---
title: 'Wskazówki: Wyświetlanie danych z serwera bazy danych SQL w formancie DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: e3db65c91e53ee0ed7b5e520bbc4989cd7404816
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075505"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="2a2e4-102">Przewodnik: Wyświetlanie danych z bazy danych programu SQL Server w formancie DataGrid</span><span class="sxs-lookup"><span data-stu-id="2a2e4-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="2a2e4-103">W tym przewodniku możesz pobierać dane z bazy danych programu SQL Server i wyświetlić te dane w <xref:System.Windows.Controls.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="2a2e4-104">ADO.NET Entity Framework umożliwia tworzenie klas jednostek, które reprezentują dane, a następnie napisz zapytanie, które pobiera określone dane z klasą jednostki za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a2e4-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2a2e4-105">Prerequisites</span></span>

<span data-ttu-id="2a2e4-106">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="2a2e4-106">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="2a2e4-107">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-107">Visual Studio.</span></span>

-   <span data-ttu-id="2a2e4-108">Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który zawiera przykładową bazę danych AdventureWorks podłączone do niego.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="2a2e4-109">Możesz pobrać bazy danych AdventureWorks z [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="2a2e4-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="2a2e4-110">Tworzenie klas jednostek</span><span class="sxs-lookup"><span data-stu-id="2a2e4-110">Create entity classes</span></span>

1.  <span data-ttu-id="2a2e4-111">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub C# i nadaj mu nazwę `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2.  <span data-ttu-id="2a2e4-112">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie wybierz pozycję **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="2a2e4-113">Zostanie wyświetlone okno dialogowe Dodaj nowy element.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-113">The Add New Item dialog box appears.</span></span>

3.  <span data-ttu-id="2a2e4-114">W okienku zainstalowane szablony zaznacz **danych** i na liście szablonów wybierz **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Szablon elementu modelu Entity Data Model ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4.  <span data-ttu-id="2a2e4-116">Nadaj plikowi nazwę `AdventureWorksModel.edmx` a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="2a2e4-117">Zostanie wyświetlony Kreator modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-117">The Entity Data Model Wizard appears.</span></span>

5.  <span data-ttu-id="2a2e4-118">Na ekranie Wybierz zawartość modelu wybierz **projektancie platformy EF z bazy danych** a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6.  <span data-ttu-id="2a2e4-119">Na ekranie Wybierz połączenie danych zapewnia połączenie z bazą danych AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="2a2e4-120">Aby uzyskać więcej informacji, zobacz [wybierz Your Data połączenie — okno dialogowe](https://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="2a2e4-120">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>

    <span data-ttu-id="2a2e4-121">Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i **zapisywanie ustawień połączenia w pliku App.Config jako jednostki** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7.  <span data-ttu-id="2a2e4-122">Na ekranie Wybierz obiekty bazy danych, rozwiń węzeł tabele, a następnie wybierz **produktu** i **ProductCategory** tabel.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="2a2e4-123">Można wygenerować klas jednostek dla wszystkich tabel. Jednak w tym przykładzie możesz tylko pobierać dane z tych dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="2a2e4-124">![Wybierz z tabel Product i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="2a2e4-124">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="2a2e4-125">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-125">Click **Finish**.</span></span>

     <span data-ttu-id="2a2e4-126">W Projektancie jednostki wyświetlania obiektów Product i ProductCategory.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="2a2e4-127">![Modele jednostki Product i ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="2a2e4-127">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="2a2e4-128">Pobieranie i prezentowanie danych</span><span class="sxs-lookup"><span data-stu-id="2a2e4-128">Retrieve and present the data</span></span>

1.  <span data-ttu-id="2a2e4-129">Otwórz plik MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-129">Open the MainWindow.xaml file.</span></span>

2.  <span data-ttu-id="2a2e4-130">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Window> do 450.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3.  <span data-ttu-id="2a2e4-131">W edytorze XAML, Dodaj następujący kod <xref:System.Windows.Controls.DataGrid> tag między `<Grid>` i `</Grid>` tagi do dodania <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="2a2e4-132">![Okno z DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="2a2e4-132">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4.  <span data-ttu-id="2a2e4-133">Wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-133">Select the <xref:System.Windows.Window>.</span></span>

5.  <span data-ttu-id="2a2e4-134">Za pomocą okna właściwości lub Edytor XAML, Utwórz program obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="2a2e4-135">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego programu obsługi zdarzeń](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="2a2e4-135">For more information, see [How to: Create a Simple Event Handler](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>

     <span data-ttu-id="2a2e4-136">Poniżej przedstawiono XAML dla pliku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a2e4-137">Jeśli używasz języka Visual Basic w pierwszym wierszu pliku MainWindow.xaml, Zastąp `x:Class="DataGridSQLExample.MainWindow"` z `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6.  <span data-ttu-id="2a2e4-138">Otwórz plik związany z kodem (pliku MainWindow.xaml.vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7.  <span data-ttu-id="2a2e4-139">Dodaj następujący kod, aby pobrać tylko określone wartości z połączonych tabel i ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.DataGrid> do wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8.  <span data-ttu-id="2a2e4-140">Uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-140">Run the example.</span></span>

     <span data-ttu-id="2a2e4-141">Powinien zostać wyświetlony <xref:System.Windows.Controls.DataGrid> wyświetlającą dane.</span><span class="sxs-lookup"><span data-stu-id="2a2e4-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="2a2e4-142">![DataGrid — przy użyciu danych z bazy danych SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="2a2e4-142">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="2a2e4-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a2e4-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="2a2e4-144">Jak I: rozpocząć korzystanie z programu Entity Framework w aplikacjach WPF?</span><span class="sxs-lookup"><span data-stu-id="2a2e4-144">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)