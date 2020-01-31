---
title: 'Wskazówki: powiązanie z danymi w aplikacjach hybrydowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 1bb38436049e338ab6033ae3b6370732a457d520
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794226"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="34b41-102">Wskazówki: powiązanie z danymi w aplikacjach hybrydowych</span><span class="sxs-lookup"><span data-stu-id="34b41-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>

<span data-ttu-id="34b41-103">Powiązanie źródła danych z kontrolką jest niezbędne do zapewnienia użytkownikom dostępu do danych źródłowych, niezależnie od tego, czy używasz Windows Forms, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34b41-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using Windows Forms or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="34b41-104">W tym instruktażu pokazano, jak można używać powiązań danych w aplikacjach hybrydowych, które zawierają zarówno Windows Forms, jak i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34b41-104">This walkthrough shows how you can use data binding in hybrid applications that include both Windows Forms and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>

<span data-ttu-id="34b41-105">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="34b41-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="34b41-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="34b41-106">Creating the project.</span></span>

- <span data-ttu-id="34b41-107">Definiowanie szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-107">Defining the data template.</span></span>

- <span data-ttu-id="34b41-108">Określanie układu formularza.</span><span class="sxs-lookup"><span data-stu-id="34b41-108">Specifying the form layout.</span></span>

- <span data-ttu-id="34b41-109">Określanie powiązań danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-109">Specifying data bindings.</span></span>

- <span data-ttu-id="34b41-110">Wyświetlanie danych przy użyciu funkcji międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="34b41-110">Displaying data by using interoperation.</span></span>

- <span data-ttu-id="34b41-111">Dodawanie źródła danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="34b41-111">Adding the data source to the project.</span></span>

- <span data-ttu-id="34b41-112">Powiązanie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-112">Binding to the data source.</span></span>

<span data-ttu-id="34b41-113">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [powiązanie danych w przykładowych aplikacjach hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="34b41-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>

<span data-ttu-id="34b41-114">Po zakończeniu będziesz mieć świadomość funkcji powiązań danych w aplikacjach hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="34b41-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34b41-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="34b41-115">Prerequisites</span></span>

<span data-ttu-id="34b41-116">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="34b41-116">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="34b41-117">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34b41-117">Visual Studio.</span></span>

- <span data-ttu-id="34b41-118">Dostęp do przykładowej bazy danych Northwind działającej na Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="34b41-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="34b41-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="34b41-119">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="34b41-120">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="34b41-120">To create and set up the project</span></span>

1. <span data-ttu-id="34b41-121">Utwórz projekt aplikacji WPF o nazwie `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="34b41-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>

2. <span data-ttu-id="34b41-122">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="34b41-122">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="34b41-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="34b41-123">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="34b41-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="34b41-124">System.Windows.Forms</span></span>

3. <span data-ttu-id="34b41-125">Otwórz MainWindow. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="34b41-125">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="34b41-126">W <xref:System.Windows.Window> elementu Dodaj następujące Windows Forms mapowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34b41-126">In the <xref:System.Windows.Window> element, add the following Windows Forms namespaces mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="34b41-127">Nadaj <xref:System.Windows.Controls.Grid> domyślnemu elementowi `mainGrid`, przypisując Właściwość <xref:System.Windows.FrameworkElement.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="34b41-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a><span data-ttu-id="34b41-128">Definiowanie szablonu danych</span><span class="sxs-lookup"><span data-stu-id="34b41-128">Defining the Data Template</span></span>

<span data-ttu-id="34b41-129">Główna lista klientów jest wyświetlana w kontrolce <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="34b41-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="34b41-130">Poniższy przykład kodu definiuje obiekt <xref:System.Windows.DataTemplate> o nazwie `ListItemsTemplate`, który kontroluje drzewo wizualne kontrolki <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="34b41-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="34b41-131">Ta <xref:System.Windows.DataTemplate> jest przypisana do właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> kontrolki <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="34b41-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>

### <a name="to-define-the-data-template"></a><span data-ttu-id="34b41-132">Aby zdefiniować szablon danych</span><span class="sxs-lookup"><span data-stu-id="34b41-132">To define the data template</span></span>

- <span data-ttu-id="34b41-133">Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34b41-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a><span data-ttu-id="34b41-134">Określanie układu formularza</span><span class="sxs-lookup"><span data-stu-id="34b41-134">Specifying the Form Layout</span></span>

<span data-ttu-id="34b41-135">Układ formularza jest definiowany przez siatkę z trzema wierszami i trzema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="34b41-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="34b41-136">w celu zidentyfikowania każdej kolumny w tabeli Customers są udostępniane <xref:System.Windows.Controls.Label> formanty.</span><span class="sxs-lookup"><span data-stu-id="34b41-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>

### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="34b41-137">Aby skonfigurować układ siatki</span><span class="sxs-lookup"><span data-stu-id="34b41-137">To set up the Grid layout</span></span>

- <span data-ttu-id="34b41-138">Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34b41-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="34b41-139">Aby skonfigurować kontrolki etykiet</span><span class="sxs-lookup"><span data-stu-id="34b41-139">To set up the Label controls</span></span>

- <span data-ttu-id="34b41-140">Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34b41-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a><span data-ttu-id="34b41-141">Określanie powiązań danych</span><span class="sxs-lookup"><span data-stu-id="34b41-141">Specifying Data Bindings</span></span>

<span data-ttu-id="34b41-142">Główna lista klientów jest wyświetlana w kontrolce <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="34b41-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="34b41-143">Dołączony `ListItemsTemplate` wiąże formant <xref:System.Windows.Controls.TextBlock> z bazą danych `ContactName`.</span><span class="sxs-lookup"><span data-stu-id="34b41-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>

<span data-ttu-id="34b41-144">Szczegóły każdego rekordu klienta są wyświetlane w kilku kontrolkach <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="34b41-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>

### <a name="to-specify-data-bindings"></a><span data-ttu-id="34b41-145">Aby określić powiązania danych</span><span class="sxs-lookup"><span data-stu-id="34b41-145">To specify data bindings</span></span>

- <span data-ttu-id="34b41-146">Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34b41-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     <span data-ttu-id="34b41-147">Klasa <xref:System.Windows.Data.Binding> wiąże kontrolki <xref:System.Windows.Controls.TextBox> z odpowiednimi polami w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="34b41-148">Wyświetlanie danych przy użyciu funkcji międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="34b41-148">Displaying Data by Using Interoperation</span></span>

<span data-ttu-id="34b41-149">Zamówienia odpowiadające wybranemu klientowi są wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="34b41-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="34b41-150">Formant `dataGridView1` jest powiązany ze źródłem danych w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="34b41-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="34b41-151">Formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest elementem nadrzędnym tej kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="34b41-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this Windows Forms control.</span></span>

### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="34b41-152">Aby wyświetlić dane w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="34b41-152">To display data in the DataGridView control</span></span>

- <span data-ttu-id="34b41-153">Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34b41-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="34b41-154">Dodawanie źródła danych do projektu</span><span class="sxs-lookup"><span data-stu-id="34b41-154">Adding the Data Source to the Project</span></span>

<span data-ttu-id="34b41-155">Za pomocą programu Visual Studio można łatwo dodać źródło danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="34b41-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="34b41-156">Ta procedura dodaje zestaw danych o jednoznacznie określonym typie do projektu.</span><span class="sxs-lookup"><span data-stu-id="34b41-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="34b41-157">Dodawane są również kilka innych klas pomocniczych, takich jak karty tabel dla każdej z wybranych tabel.</span><span class="sxs-lookup"><span data-stu-id="34b41-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="34b41-158">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="34b41-158">To add the data source</span></span>

1. <span data-ttu-id="34b41-159">Z menu **dane** wybierz pozycję **Dodaj nowe źródło danych**.</span><span class="sxs-lookup"><span data-stu-id="34b41-159">From the **Data** menu, select **Add New Data Source**.</span></span>

2. <span data-ttu-id="34b41-160">W **Kreatorze konfiguracji źródła danych**Utwórz połączenie z bazą danych Northwind przy użyciu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="34b41-161">Aby uzyskać więcej informacji, zobacz [jak: łączenie z danymi w bazie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="34b41-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>

3. <span data-ttu-id="34b41-162">Po wyświetleniu monitu w **Kreatorze konfiguracji źródła danych**Zapisz parametry połączenia jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="34b41-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>

4. <span data-ttu-id="34b41-163">Po wyświetleniu monitu o wybranie obiektów bazy danych wybierz tabele `Customers` i `Orders` i nadaj nazwę wygenerowanego zestawu danych `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="34b41-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>

## <a name="binding-to-the-data-source"></a><span data-ttu-id="34b41-164">Powiązanie ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="34b41-164">Binding to the Data Source</span></span>

<span data-ttu-id="34b41-165">Składnik <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> zapewnia jednolity interfejs dla źródła danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34b41-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="34b41-166">Powiązanie ze źródłem danych jest zaimplementowane w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="34b41-166">Binding to the data source is implemented in the code-behind file.</span></span>

### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="34b41-167">Aby powiązać ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="34b41-167">To bind to the data source</span></span>

1. <span data-ttu-id="34b41-168">Otwórz plik związany z kodem o nazwie MainWindow. XAML. vb lub MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="34b41-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="34b41-169">Skopiuj następujący kod do definicji klasy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="34b41-169">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="34b41-170">Ten kod deklaruje składnik <xref:System.Windows.Forms.BindingSource> i skojarzone klasy pomocnika, które łączą się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="34b41-171">Skopiuj poniższy kod do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="34b41-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="34b41-172">Ten kod tworzy i inicjuje składnik <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="34b41-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="34b41-173">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="34b41-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="34b41-174">W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="34b41-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="34b41-175">W okno Właściwości kliknij kartę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="34b41-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="34b41-176">Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="34b41-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="34b41-177">Skopiuj następujący kod do programu obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="34b41-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="34b41-178">Ten kod przypisuje składnik <xref:System.Windows.Forms.BindingSource> jako kontekst danych i wypełnia obiekty `Customers` i `Orders` kart.</span><span class="sxs-lookup"><span data-stu-id="34b41-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="34b41-179">Skopiuj następujący kod do definicji klasy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="34b41-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="34b41-180">Ta metoda obsługuje zdarzenie <xref:System.Windows.Data.CollectionView.CurrentChanged> i aktualizuje bieżący element powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="34b41-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. <span data-ttu-id="34b41-181">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="34b41-181">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="34b41-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34b41-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="34b41-183">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34b41-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="34b41-184">Przykład powiązania danych w aplikacjach hybrydowych</span><span class="sxs-lookup"><span data-stu-id="34b41-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)
- [<span data-ttu-id="34b41-185">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="34b41-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="34b41-186">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34b41-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
