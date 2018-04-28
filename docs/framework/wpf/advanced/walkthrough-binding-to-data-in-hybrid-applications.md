---
title: 'Wskazówki: powiązanie z danymi w aplikacjach hybrydowych'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8afe4732363ec61d73db13e9b190381cbd8f29d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="5c8d6-102">Wskazówki: powiązanie z danymi w aplikacjach hybrydowych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="5c8d6-103">Powiązanie z formantem źródła danych jest istotne dla zapewnia użytkownikom dostęp do danych, czy używasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c8d6-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="5c8d6-104">W tym przewodniku przedstawiono używania wiązania z danymi w aplikacjach hybrydowych, które obejmują zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="5c8d6-105">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="5c8d6-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="5c8d6-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="5c8d6-107">Definiowanie szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="5c8d6-108">Określenie układu formularza.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="5c8d6-109">Określanie powiązań danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="5c8d6-110">Wyświetlanie danych przy użyciu współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="5c8d6-111">Dodawanie źródła danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="5c8d6-112">Powiązania ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="5c8d6-113">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [powiązania danych w przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="5c8d6-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](http://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="5c8d6-114">Po ukończeniu będzie mieć zrozumienia funkcji wiązania danych w aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c8d6-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5c8d6-115">Prerequisites</span></span>  
 <span data-ttu-id="5c8d6-116">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="5c8d6-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="5c8d6-117">.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-117">.</span></span>  
  
-   <span data-ttu-id="5c8d6-118">Dostęp do przykładowej bazy danych Northwind uruchomione przez program Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5c8d6-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="5c8d6-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="5c8d6-120">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="5c8d6-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="5c8d6-121">Utwórz projekt aplikacji WPF o nazwie `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="5c8d6-122">W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="5c8d6-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="5c8d6-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="5c8d6-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="5c8d6-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="5c8d6-125">Otwórz MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c8d6-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="5c8d6-126">W <xref:System.Windows.Window> elementu, Dodaj następujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="5c8d6-127">Nazwa domyślna <xref:System.Windows.Controls.Grid> elementu `mainGrid` przypisując <xref:System.Windows.FrameworkElement.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="5c8d6-128">Definiowanie szablonu danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-128">Defining the Data Template</span></span>  
 <span data-ttu-id="5c8d6-129">Listę wzorcową klientów jest wyświetlany w <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c8d6-130">Poniższy przykładowy kod definiuje <xref:System.Windows.DataTemplate> obiektu o nazwie `ListItemsTemplate` steruje drzewie wizualnym <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c8d6-131">To <xref:System.Windows.DataTemplate> jest przypisany do <xref:System.Windows.Controls.ListBox> formantu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="5c8d6-132">Aby zdefiniować szablon danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-132">To define the data template</span></span>  
  
-   <span data-ttu-id="5c8d6-133">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="5c8d6-134">Określenie układu formularza</span><span class="sxs-lookup"><span data-stu-id="5c8d6-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="5c8d6-135">Układu formularza jest zdefiniowana przez siatkę z trzy wiersze i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="5c8d6-136"><xref:System.Windows.Controls.Label> Formanty są dostarczane do identyfikowania każdej kolumny w tabeli Klienci.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="5c8d6-137">Aby skonfigurować układ siatki</span><span class="sxs-lookup"><span data-stu-id="5c8d6-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="5c8d6-138">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="5c8d6-139">Aby skonfigurować formantów etykiet</span><span class="sxs-lookup"><span data-stu-id="5c8d6-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="5c8d6-140">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="5c8d6-141">Określanie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="5c8d6-142">Listę wzorcową klientów jest wyświetlany w <xref:System.Windows.Controls.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c8d6-143">Dołączony `ListItemsTemplate` wiąże <xref:System.Windows.Controls.TextBlock> formant `ContactName` pole z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="5c8d6-144">Szczegóły każdego rekordu klienta są wyświetlane w kilku <xref:System.Windows.Controls.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="5c8d6-145">Aby określić powiązania danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="5c8d6-146">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="5c8d6-147"><xref:System.Windows.Data.Binding> Klasy wiązania <xref:System.Windows.Controls.TextBox> formanty do odpowiednich pól w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="5c8d6-148">Wyświetlanie danych przy użyciu współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5c8d6-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="5c8d6-149">Zamówienia odpowiadającego danego odbiorcy są wyświetlane w <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="5c8d6-150">`dataGridView1` Kontrolka jest powiązana ze źródłem danych w pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="5c8d6-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolka jest elementem nadrzędnym [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="5c8d6-152">Aby wyświetlić dane w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="5c8d6-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="5c8d6-153">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="5c8d6-154">Dodawanie źródła danych do projektu</span><span class="sxs-lookup"><span data-stu-id="5c8d6-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="5c8d6-155">Program Visual Studio można łatwo dodać źródła danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="5c8d6-156">Ta procedura dodaje silnie typizowanego zestaw danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="5c8d6-157">Dodano również kilka innych klas pomocy technicznej, takie jak karty tabeli dla wszystkich wybranych tabel.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="5c8d6-158">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="5c8d6-159">Z **danych** menu, wybierz opcję **Dodaj nowe źródło danych**.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="5c8d6-160">W **Kreator konfiguracji źródła danych**, Utwórz połączenie z bazą danych Northwind przy użyciu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="5c8d6-161">Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w bazie danych](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span><span class="sxs-lookup"><span data-stu-id="5c8d6-161">For more information, see [How to: Connect to Data in a Database](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="5c8d6-162">Po wyświetleniu monitu przez **Kreator konfiguracji źródła danych**, Zapisz parametry połączenia jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="5c8d6-163">Po wyświetleniu monitu, aby wybrać obiekty bazy danych, wybierz `Customers` i `Orders` tabel i nazwę wygenerowanego zestawu danych `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="5c8d6-164">Powiązania ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="5c8d6-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Stanowi ujednolicony interfejs dla źródła danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="5c8d6-166">Powiązania ze źródłem danych jest zaimplementowana w pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="5c8d6-167">Aby powiązać ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="5c8d6-168">Otwórz plik CodeBehind, który jest nazwane MainWindow.xaml.vb lub MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="5c8d6-169">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="5c8d6-170">Ten kod deklaruje <xref:System.Windows.Forms.BindingSource> składnika i klasy pomocnicze skojarzony, które połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="5c8d6-171">Skopiuj następujący kod do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="5c8d6-172">Ten kod tworzy i inicjuje <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="5c8d6-173">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="5c8d6-174">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="5c8d6-175">Kliknij w oknie właściwości **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="5c8d6-176">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="5c8d6-177">Skopiuj następujący kod do <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="5c8d6-178">Ten kod przypisuje <xref:System.Windows.Forms.BindingSource> składnika jako kontekst danych i wypełnienie `Customers` i `Orders` obiektów karty.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="5c8d6-179">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="5c8d6-180">Ta metoda obsługuje <xref:System.Windows.Data.CollectionView.CurrentChanged> zdarzeń i aktualizuje bieżącego elementu powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="5c8d6-181">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5c8d6-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8d6-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c8d6-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="5c8d6-183">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="5c8d6-183">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="5c8d6-184">Wiązanie danych w przykładowej aplikacji hybrydowych</span><span class="sxs-lookup"><span data-stu-id="5c8d6-184">Data Binding in Hybrid Applications Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="5c8d6-185">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="5c8d6-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="5c8d6-186">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c8d6-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
