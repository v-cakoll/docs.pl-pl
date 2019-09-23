---
title: 'Instrukcje: Utwórz dodatek, który zwraca interfejs użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182671"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="10d3f-102">Instrukcje: Utwórz dodatek, który zwraca interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="10d3f-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="10d3f-103">Ten przykład pokazuje, jak utworzyć dodatek, który zwraca Windows Presentation Foundation (WPF) do aplikacji autonomicznej WPF hosta.</span><span class="sxs-lookup"><span data-stu-id="10d3f-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="10d3f-104">Dodatek zwraca interfejs użytkownika, który jest formantem użytkownika WPF.</span><span class="sxs-lookup"><span data-stu-id="10d3f-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="10d3f-105">Zawartość kontrolki użytkownika to pojedynczy przycisk, który po kliknięciu wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="10d3f-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="10d3f-106">Aplikacja autonomiczna WPF obsługuje dodatek i wyświetla kontrolkę użytkownika (zwracaną przez dodatek) jako zawartość głównego okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10d3f-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="10d3f-107">\*\*Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="10d3f-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="10d3f-108">W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który umożliwia ten scenariusz, i przyjmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="10d3f-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="10d3f-109">Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i opracowywania hosta.</span><span class="sxs-lookup"><span data-stu-id="10d3f-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="10d3f-110">Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="10d3f-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="10d3f-111">Aby zapoznać się z samouczkiem, który ilustruje implementację potoku, dodatek i aplikację hosta, zobacz [Przewodnik: Tworzenie aplikacji](../../add-ins/walkthrough-create-extensible-app.md)rozszerzalnej.</span><span class="sxs-lookup"><span data-stu-id="10d3f-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
- <span data-ttu-id="10d3f-112">Znajomość rozszerzeń WPF do modelu dodatku .NET Framework, który można znaleźć tutaj: [Omówienie dodatków WPF](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="10d3f-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d3f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="10d3f-113">Example</span></span>  
 <span data-ttu-id="10d3f-114">Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF, wymaga określonego kodu dla każdego segmentu potoku, dodatku i aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="10d3f-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="10d3f-115">Implementowanie segmentu potoku kontraktu</span><span class="sxs-lookup"><span data-stu-id="10d3f-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="10d3f-116">Metoda musi być zdefiniowana przez umowę zwracającą interfejs użytkownika, a jej zwracana wartość musi być typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="10d3f-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="10d3f-117">Jest to zademonstrowane przez `GetAddInUI` metodę `IWPFAddInContract` kontraktu w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="10d3f-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="10d3f-118">Implementowanie segmentu potoku widoku dodatku</span><span class="sxs-lookup"><span data-stu-id="10d3f-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="10d3f-119">[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] Ponieważ dodatek implementuje interfejs <xref:System.Windows.FrameworkElement>, zapewnia jako podklasy, metoda w widoku dodatku, który jest skorelowany do `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="10d3f-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="10d3f-120">Poniższy kod przedstawia widok dodatku kontraktu wdrożony jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="10d3f-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="10d3f-121">Implementowanie segmentu potoku karty dodatku</span><span class="sxs-lookup"><span data-stu-id="10d3f-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="10d3f-122">Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek <xref:System.Windows.FrameworkElement> zwraca (zgodnie z opisem w widoku dodatku).</span><span class="sxs-lookup"><span data-stu-id="10d3f-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="10d3f-123">W związku z tym <xref:System.Windows.FrameworkElement> , należy przekonwertować <xref:System.AddIn.Contract.INativeHandleContract> na wartość przed przekroczeniem granicy izolacji.</span><span class="sxs-lookup"><span data-stu-id="10d3f-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="10d3f-124">Ta operacja jest wykonywana przez adapter dodatku, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="10d3f-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="10d3f-125">Implementowanie segmentu potoku widoku hosta</span><span class="sxs-lookup"><span data-stu-id="10d3f-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="10d3f-126">Ponieważ aplikacja hosta będzie wyświetlać <xref:System.Windows.FrameworkElement>, metoda w widoku hosta, która jest skorelowana z `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="10d3f-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="10d3f-127">Poniższy kod przedstawia widok hosta kontraktu wdrożony jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="10d3f-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="10d3f-128">Implementowanie segmentu potoku karty po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="10d3f-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="10d3f-129">Metoda Contract zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale aplikacja hosta oczekuje <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta).</span><span class="sxs-lookup"><span data-stu-id="10d3f-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="10d3f-130">W <xref:System.AddIn.Contract.INativeHandleContract> związku z tym, należy przekonwertować na wartość <xref:System.Windows.FrameworkElement> po przekroczeniu granicy izolacji.</span><span class="sxs-lookup"><span data-stu-id="10d3f-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="10d3f-131">Ta operacja jest wykonywana przez adapter po stronie hosta przez wywołanie <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="10d3f-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="10d3f-132">Implementowanie dodatku</span><span class="sxs-lookup"><span data-stu-id="10d3f-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="10d3f-133">Po utworzeniu`WPFAddIn1.AddIn`wbudowanej karty sieciowej i dodatku dodatek () musi `IWPFAddInView.GetAddInUI` zaimplementować metodę, aby <xref:System.Windows.Controls.UserControl> zwrócić <xref:System.Windows.FrameworkElement> obiekt (w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="10d3f-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="10d3f-134">Implementacja elementu <xref:System.Windows.Controls.UserControl>, `AddInUI`jest pokazana przez następujący kod.</span><span class="sxs-lookup"><span data-stu-id="10d3f-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="10d3f-135">Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe `AddInUI`wystąpienie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="10d3f-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="10d3f-136">Implementowanie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="10d3f-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="10d3f-137">Po utworzeniu karty i widoku hosta po stronie hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby otworzyć potok, uzyskać widok hosta dodatku i wywołać `IWPFAddInHostView.GetAddInUI` metodę.</span><span class="sxs-lookup"><span data-stu-id="10d3f-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="10d3f-138">Te kroki przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="10d3f-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="10d3f-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10d3f-139">See also</span></span>

- <span data-ttu-id="10d3f-140">[Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="10d3f-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="10d3f-141">Dodatki WPF — omówienie</span><span class="sxs-lookup"><span data-stu-id="10d3f-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
