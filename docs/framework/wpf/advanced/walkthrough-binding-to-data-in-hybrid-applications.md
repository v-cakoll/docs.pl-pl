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
ms.openlocfilehash: 773708eab617e7f4cfdffad2e5019e66c60ebf37
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787067"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="a3a7f-102">Wskazówki: powiązanie z danymi w aplikacjach hybrydowych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="a3a7f-103">Powiązanie źródła danych z kontrolką ma zasadnicze znaczenie dla zapewniając użytkownikom dostęp do danych bazowych, czy używasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3a7f-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="a3a7f-104">W tym instruktażu przedstawiono sposób korzystania powiązanie danych w aplikacjach hybrydowych, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="a3a7f-105">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="a3a7f-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a3a7f-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="a3a7f-107">Definiowanie szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="a3a7f-108">Określanie układu formularza.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="a3a7f-109">Określanie powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="a3a7f-110">Wyświetlanie danych za pomocą międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="a3a7f-111">Dodawanie źródła danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="a3a7f-112">Powiązania ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="a3a7f-113">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [powiązanie danych w przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="a3a7f-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="a3a7f-114">Gdy skończysz, konieczne będzie zrozumienie funkcji wiązania danych w aplikacjach hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a3a7f-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a3a7f-115">Prerequisites</span></span>  
 <span data-ttu-id="a3a7f-116">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="a3a7f-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a3a7f-117">.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-117">.</span></span>  
  
-   <span data-ttu-id="a3a7f-118">Dostęp do przykładowej bazy danych Northwind uruchomiony program Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a3a7f-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="a3a7f-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="a3a7f-120">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="a3a7f-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="a3a7f-121">Utwórz projekt aplikacji WPF, o nazwie `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="a3a7f-122">W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="a3a7f-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="a3a7f-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="a3a7f-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a3a7f-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="a3a7f-125">Otwieranie pliku MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3a7f-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="a3a7f-126">W <xref:System.Windows.Window> elementu, Dodaj następujący kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="a3a7f-127">Nazwa domyślna <xref:System.Windows.Controls.Grid> elementu `mainGrid` , przypisując <xref:System.Windows.FrameworkElement.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="a3a7f-128">Definiowanie szablonu danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-128">Defining the Data Template</span></span>  
 <span data-ttu-id="a3a7f-129">Zostanie wyświetlona lista wzorca odbiorców, w <xref:System.Windows.Controls.ListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a3a7f-130">Poniższy przykład kodu przedstawia <xref:System.Windows.DataTemplate> obiektu o nazwie `ListItemsTemplate` sterującą drzewie wizualnym <xref:System.Windows.Controls.ListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a3a7f-131">To <xref:System.Windows.DataTemplate> jest przypisany do <xref:System.Windows.Controls.ListBox> kontrolki <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="a3a7f-132">Aby zdefiniować szablon danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-132">To define the data template</span></span>  
  
-   <span data-ttu-id="a3a7f-133">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="a3a7f-134">Określanie układu formularza</span><span class="sxs-lookup"><span data-stu-id="a3a7f-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="a3a7f-135">Układ formularza jest definiowany przez siatka zawierająca trzy wiersze i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="a3a7f-136"><xref:System.Windows.Controls.Label> Dzięki kontrolkom do identyfikowania każdej kolumny w tabeli Klienci.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="a3a7f-137">Aby zdefiniować układ siatki</span><span class="sxs-lookup"><span data-stu-id="a3a7f-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="a3a7f-138">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="a3a7f-139">Aby skonfigurować formantów etykiet</span><span class="sxs-lookup"><span data-stu-id="a3a7f-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="a3a7f-140">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="a3a7f-141">Określanie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="a3a7f-142">Zostanie wyświetlona lista wzorca odbiorców, w <xref:System.Windows.Controls.ListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a3a7f-143">Dołączony `ListItemsTemplate` wiąże <xref:System.Windows.Controls.TextBlock> kontrolę `ContactName` pola z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="a3a7f-144">Szczegóły poszczególnych rekordów klientów są wyświetlane w kilku <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="a3a7f-145">Aby określić powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="a3a7f-146">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="a3a7f-147"><xref:System.Windows.Data.Binding> Klasy powiązań <xref:System.Windows.Controls.TextBox> formanty do odpowiednich pól w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="a3a7f-148">Wyświetlanie danych za pomocą międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="a3a7f-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="a3a7f-149">Zamówienia odpowiadający wybranego klienta są wyświetlane w <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="a3a7f-150">`dataGridView1` Kontrolka jest powiązana ze źródłem danych w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="a3a7f-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant jest elementem nadrzędnym [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="a3a7f-152">Wyświetlanie danych w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="a3a7f-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="a3a7f-153">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="a3a7f-154">Dodawanie źródła danych do projektu</span><span class="sxs-lookup"><span data-stu-id="a3a7f-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="a3a7f-155">Za pomocą programu Visual Studio można łatwo dodać źródło danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="a3a7f-156">Ta procedura dodaje silnie typizowany zestaw danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="a3a7f-157">Dodano także kilka innych klas pomocy technicznej, takie jak adapterów tabel dla każdej wybranej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="a3a7f-158">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="a3a7f-159">Z **danych** menu, wybierz opcję **Dodaj nowe źródło danych**.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="a3a7f-160">W **Kreatora konfiguracji źródła danych**, Utwórz połączenie z bazą danych Northwind za pomocą zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="a3a7f-161">Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w bazie danych](https://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span><span class="sxs-lookup"><span data-stu-id="a3a7f-161">For more information, see [How to: Connect to Data in a Database](https://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="a3a7f-162">Po wyświetleniu monitu przez **Kreatora konfiguracji źródła danych**, Zapisz parametry połączenia jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="a3a7f-163">Po wyświetleniu monitu, aby wybrać obiekty bazy danych, wybierz `Customers` i `Orders` tabel i nazwę wygenerowanego zestawu danych `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="a3a7f-164">Powiązania ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="a3a7f-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Składnik zapewnia ujednolicony interfejs dla źródła danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="a3a7f-166">Powiązania ze źródłem danych jest zaimplementowana w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="a3a7f-167">Aby powiązać ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="a3a7f-168">Otwórz plik związany z kodem, który nosi nazwę pliku MainWindow.xaml.vb lub MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="a3a7f-169">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="a3a7f-170">Ten kod deklaruje <xref:System.Windows.Forms.BindingSource> składników i klas pomocniczych skojarzone, łączących się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="a3a7f-171">Skopiuj następujący kod do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="a3a7f-172">Ten kod tworzy i inicjuje <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="a3a7f-173">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="a3a7f-174">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="a3a7f-175">W oknie dialogowym właściwości kliknij **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="a3a7f-176">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="a3a7f-177">Skopiuj następujący kod do <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="a3a7f-178">Ten kod przypisuje <xref:System.Windows.Forms.BindingSource> składnika, ponieważ kontekst danych i wypełnienie `Customers` i `Orders` obiektów karty.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="a3a7f-179">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="a3a7f-180">Ta metoda obsługuje <xref:System.Windows.Data.CollectionView.CurrentChanged> zdarzeń i aktualizacji bieżący element powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="a3a7f-181">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="a3a7f-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a7f-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3a7f-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a3a7f-183">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a3a7f-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="a3a7f-184">Powiązywanie danych w przykładowej aplikacji hybrydowych</span><span class="sxs-lookup"><span data-stu-id="a3a7f-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="a3a7f-185">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="a3a7f-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="a3a7f-186">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3a7f-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
