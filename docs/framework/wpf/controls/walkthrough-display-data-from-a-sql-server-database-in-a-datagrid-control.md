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
ms.openlocfilehash: fc8b35c89e76a415529d76db687bc96767384e11
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452126"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="07cb7-102">Przewodnik: wyświetlanie danych z SQL Serverj bazy danych w kontrolce DataGrid</span><span class="sxs-lookup"><span data-stu-id="07cb7-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="07cb7-103">W tym instruktażu pobierasz dane z bazy danych SQL Server i wyświetlają te dane w kontrolce <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="07cb7-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="07cb7-104">Za pomocą Entity Framework ADO.NET można tworzyć klasy jednostek, które reprezentują dane, i używać LINQ do zapisywania zapytania pobierającego określone dane z klasy jednostki.</span><span class="sxs-lookup"><span data-stu-id="07cb7-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07cb7-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="07cb7-105">Prerequisites</span></span>

<span data-ttu-id="07cb7-106">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="07cb7-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="07cb7-107">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07cb7-107">Visual Studio.</span></span>

- <span data-ttu-id="07cb7-108">Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express z dołączoną przykładową bazą danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="07cb7-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="07cb7-109">Bazę danych AdventureWorks można pobrać z witryny [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="07cb7-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="07cb7-110">Tworzenie klas jednostek</span><span class="sxs-lookup"><span data-stu-id="07cb7-110">Create entity classes</span></span>

1. <span data-ttu-id="07cb7-111">Utwórz nowy projekt aplikacji WPF w Visual Basic lub C#, a następnie nadaj mu nazwę `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="07cb7-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="07cb7-112">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="07cb7-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="07cb7-113">Pojawi się okno dialogowe Dodaj nowy element.</span><span class="sxs-lookup"><span data-stu-id="07cb7-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="07cb7-114">W okienku zainstalowane szablony wybierz pozycję **dane** , a następnie na liście szablony wybierz pozycję **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="07cb7-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Szablon elementu Entity Data Model ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="07cb7-116">Nazwij plik `AdventureWorksModel.edmx` a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="07cb7-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="07cb7-117">Zostanie wyświetlony Kreator modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="07cb7-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="07cb7-118">Na ekranie Wybierz zawartość modelu wybierz pozycję **Dr Designer z bazy danych** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="07cb7-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="07cb7-119">Na ekranie wybierz połączenie danych podaj połączenie z bazą danych AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="07cb7-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="07cb7-120">Aby uzyskać więcej informacji, zobacz [okno dialogowe Wybieranie połączenia danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="07cb7-120">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="07cb7-121">Upewnij się, że nazwa jest `AdventureWorksLT2008Entities` i że zaznaczono pole wyboru **Zapisz ustawienia połączenia jednostki w pliku App. config jako** zaznaczone, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="07cb7-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="07cb7-122">Na ekranie Wybierz obiekty bazy danych rozwiń węzeł tabele, a następnie wybierz tabele **produkt** i **ProductCategory** .</span><span class="sxs-lookup"><span data-stu-id="07cb7-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="07cb7-123">Można generować klasy jednostek dla wszystkich tabel; Jednak w tym przykładzie pobierasz tylko dane z tych dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="07cb7-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="07cb7-124">![Wybierz produkt i ProductCategory z tabel](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="07cb7-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="07cb7-125">Kliknij przycisk **Finish** (Zakończ).</span><span class="sxs-lookup"><span data-stu-id="07cb7-125">Click **Finish**.</span></span>

     <span data-ttu-id="07cb7-126">Jednostki Product i ProductCategory są wyświetlane w Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="07cb7-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="07cb7-127">![Modele jednostek produktu i ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="07cb7-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="07cb7-128">Pobieranie i prezentowanie danych</span><span class="sxs-lookup"><span data-stu-id="07cb7-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="07cb7-129">Otwórz plik MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="07cb7-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="07cb7-130">Ustaw właściwość <xref:System.Windows.FrameworkElement.Width%2A> na <xref:System.Windows.Window> na 450.</span><span class="sxs-lookup"><span data-stu-id="07cb7-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="07cb7-131">W edytorze XAML Dodaj następujący tag <xref:System.Windows.Controls.DataGrid> między tagami `<Grid>` i `</Grid>`, aby dodać <xref:System.Windows.Controls.DataGrid> o nazwie `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="07cb7-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="07cb7-132">![Okno z elementem DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="07cb7-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="07cb7-133">Wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="07cb7-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="07cb7-134">Za pomocą okno Właściwości lub edytora XAML Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Window> o nazwie `Window_Loaded` dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="07cb7-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="07cb7-135">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="07cb7-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="07cb7-136">Poniżej przedstawiono kod XAML dla MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="07cb7-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="07cb7-137">Jeśli używasz Visual Basic, w pierwszym wierszu MainWindow. XAML Zastąp `x:Class="DataGridSQLExample.MainWindow"` elementem `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="07cb7-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="07cb7-138">Otwórz plik związany z kodem (MainWindow. XAML. vb lub MainWindow.xaml.cs) dla <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="07cb7-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="07cb7-139">Dodaj następujący kod, aby pobrać tylko określone wartości z sprzężonych tabel i ustawić właściwość <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> na wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="07cb7-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="07cb7-140">Uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="07cb7-140">Run the example.</span></span>

     <span data-ttu-id="07cb7-141">Powinna zostać wyświetlona <xref:System.Windows.Controls.DataGrid>, która wyświetla dane.</span><span class="sxs-lookup"><span data-stu-id="07cb7-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="07cb7-142">![DataGrid z danymi z bazy danych SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="07cb7-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="07cb7-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07cb7-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
