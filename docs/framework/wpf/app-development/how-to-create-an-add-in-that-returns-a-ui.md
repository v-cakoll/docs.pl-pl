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
ms.openlocfilehash: f882d62152d0116d5bff3bcd604f04c249443a94
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396672"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="6157e-102">Instrukcje: Utwórz dodatek, który zwraca interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="6157e-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="6157e-103">Ten przykład przedstawia sposób tworzenia dodatku, zwracające Windows Presentation Foundation (WPF) do hosta WPF autonomiczną aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6157e-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="6157e-104">Dodatek zwraca interfejs użytkownika, który jest formanty użytkownika WPF.</span><span class="sxs-lookup"><span data-stu-id="6157e-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="6157e-105">Zawartość kontrolki użytkownika nie ma jednego przycisku, po kliknięciu wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6157e-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="6157e-106">Oddzielną aplikację WPF obsługuje dodatku i wyświetla kontrolkę użytkownika (zwrócone przez dodatek) jako zawartość okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6157e-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="6157e-107">**Wymagania wstępne**</span><span class="sxs-lookup"><span data-stu-id="6157e-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="6157e-108">W tym przykładzie wyróżnia rozszerzenia WPF model dodatku .NET Framework, które umożliwiają w tym scenariuszu i przyjęto założenie, że:</span><span class="sxs-lookup"><span data-stu-id="6157e-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="6157e-109">Znajomość środowiska .NET Framework — w modelu, w tym potoku dodatku i rozwoju hosta.</span><span class="sxs-lookup"><span data-stu-id="6157e-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="6157e-110">Jeśli nie jesteś zaznajomiony z tych pojęć, zobacz [dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="6157e-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="6157e-111">Aby uzyskać samouczek, który przedstawia implementację potoku dodatku i aplikacji hosta, zobacz [instruktażu: Tworzenie aplikacji rozszerzalnej](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="6157e-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="6157e-112">Wiedzę na temat rozszerzeń WPF, .NET Framework — w modelu, który można znaleźć tutaj: [Przegląd dodatki WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6157e-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6157e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6157e-113">Example</span></span>  
 <span data-ttu-id="6157e-114">Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF wymaga określonego kodu dla każdy z segmentów potoku dodatku i aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="6157e-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="6157e-115">Implementowanie segmentów potoku kontraktu</span><span class="sxs-lookup"><span data-stu-id="6157e-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="6157e-116">Metoda musi być określona przez umowę do zwracania interfejsu użytkownika, a jego wartość zwracana musi być typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="6157e-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="6157e-117">Wskazuje na `GetAddInUI` metody `IWPFAddInContract` Umowę w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6157e-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="6157e-118">Implementowanie segmentów potoku dodatku widoku</span><span class="sxs-lookup"><span data-stu-id="6157e-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="6157e-119">Ponieważ dodatek implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zapewnia jako podklasy <xref:System.Windows.FrameworkElement>, metody, w widoku dodatku, odpowiadająca `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="6157e-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="6157e-120">Poniższy kod przedstawia widok dodatku kontrakt implementowany jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="6157e-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="6157e-121">Implementowanie segmentów potoku dodać strony karty</span><span class="sxs-lookup"><span data-stu-id="6157e-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="6157e-122">Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (jak określono w widoku dodatku).</span><span class="sxs-lookup"><span data-stu-id="6157e-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="6157e-123">W związku z tym <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.</span><span class="sxs-lookup"><span data-stu-id="6157e-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="6157e-124">Ta praca jest wykonywana przez siebie w Dodaj kartę przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6157e-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="6157e-125">Implementowanie segmentów potoku widok hosta</span><span class="sxs-lookup"><span data-stu-id="6157e-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="6157e-126">Ponieważ aplikacja hosta będzie wyświetlana <xref:System.Windows.FrameworkElement>, metody, w widoku hosta, które skorelowany `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="6157e-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="6157e-127">Poniższy kod przedstawia widok hosta umowy implementowany jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="6157e-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="6157e-128">Implementowanie segmentów potoku adaptery po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="6157e-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="6157e-129">Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale oczekuje, że aplikacja hosta <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta).</span><span class="sxs-lookup"><span data-stu-id="6157e-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="6157e-130">W związku z tym <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.</span><span class="sxs-lookup"><span data-stu-id="6157e-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="6157e-131">Ta praca jest wykonywana przez adapter po stronie hosta, wywołując <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6157e-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="6157e-132">Wdrażanie dodatku programu</span><span class="sxs-lookup"><span data-stu-id="6157e-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="6157e-133">Za pomocą karty add w side i widoku dodatku utworzeniu dodatku (`WPFAddIn1.AddIn`) musi implementować `IWPFAddInView.GetAddInUI` metodę, aby zwrócić <xref:System.Windows.FrameworkElement> obiektu ( <xref:System.Windows.Controls.UserControl> w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="6157e-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="6157e-134">Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI`, jest wyświetlany przez następujący kod.</span><span class="sxs-lookup"><span data-stu-id="6157e-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="6157e-135">Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe wystąpienie klasy `AddInUI`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6157e-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="6157e-136">Wdrażanie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="6157e-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="6157e-137">Adaptery po stronie hosta i widok hosta utworzony, aplikacji hosta umożliwia model dodatku .NET Framework Otwórz potok, uzyskać widok hosta dodatków i wywołania `IWPFAddInHostView.GetAddInUI` metody.</span><span class="sxs-lookup"><span data-stu-id="6157e-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="6157e-138">Te kroki są wyświetlane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6157e-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="6157e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6157e-139">See Also</span></span>  
 <span data-ttu-id="6157e-140">[Dodatki i rozszerzalność](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="6157e-140">[Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>  
 [<span data-ttu-id="6157e-141">Dodatki WPF — omówienie</span><span class="sxs-lookup"><span data-stu-id="6157e-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
