---
title: Jak utworzyć dodatek, który zwraca interfejs użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174592"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="07142-102">Jak utworzyć dodatek, który zwraca interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="07142-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="07142-103">W tym przykładzie pokazano, jak utworzyć dodatek, który zwraca Windows Presentation Foundation (WPF) do hosta WPF autonomicznej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07142-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="07142-104">Dodatek zwraca interfejs użytkownika, który jest formantem użytkownika WPF.</span><span class="sxs-lookup"><span data-stu-id="07142-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="07142-105">Zawartość formantu użytkownika jest pojedynczym przyciskiem, który po kliknięciu wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="07142-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="07142-106">Aplikacja autonomiczna WPF obsługuje dodatek i wyświetla formant użytkownika (zwracany przez dodatek) jako zawartość głównego okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07142-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="07142-107">**Wymagania wstępne**</span><span class="sxs-lookup"><span data-stu-id="07142-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="07142-108">W tym przykładzie wyróżniono rozszerzenia WPF do modelu dodatku .NET Framework, który włącza ten scenariusz i zakłada, że:</span><span class="sxs-lookup"><span data-stu-id="07142-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="07142-109">Znajomość modelu dodatku .NET Framework, w tym potoku, dodatku i rozwoju hosta.</span><span class="sxs-lookup"><span data-stu-id="07142-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="07142-110">Jeśli nie znasz tych pojęć, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="07142-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="07142-111">Aby zapoznać się z samouczkiem przedstawiającym implementację potoku, dodatku i aplikacji hosta, zobacz [Przewodnik: Tworzenie aplikacji rozszerzalnej](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="07142-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="07142-112">Znajomość rozszerzeń WPF do modelu dodatku .NET Framework, który można znaleźć tutaj: [Przegląd dodatków WPF](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07142-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07142-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="07142-113">Example</span></span>  
 <span data-ttu-id="07142-114">Aby utworzyć dodatek, który zwraca interfejs użytkownika WPF wymaga określonego kodu dla każdego segmentu potoku, dodatku i aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="07142-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="07142-115">Wdrażanie segmentu rurociągu kontraktowego</span><span class="sxs-lookup"><span data-stu-id="07142-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="07142-116">Metoda musi być zdefiniowana przez kontrakt dla zwrócenia interfejsu użytkownika, a <xref:System.AddIn.Contract.INativeHandleContract>jego wartość zwracana musi być typu .</span><span class="sxs-lookup"><span data-stu-id="07142-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="07142-117">Jest to wykazane `GetAddInUI` przez `IWPFAddInContract` metodę umowy w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07142-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="07142-118">Implementowanie segmentu potoku widoku dodatku</span><span class="sxs-lookup"><span data-stu-id="07142-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="07142-119">Ponieważ dodatek implementuje interfejsów użytkownika, które udostępnia jako <xref:System.Windows.FrameworkElement>podklasy , metoda w widoku `IWPFAddInView.GetAddInUI` dodatku, która <xref:System.Windows.FrameworkElement>koreluje z musi zwracać wartość typu .</span><span class="sxs-lookup"><span data-stu-id="07142-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="07142-120">Poniższy kod przedstawia dodatek w widoku umowy, zaimplementowane jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="07142-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="07142-121">Implementowanie segmentu potoku adaptera dodatku</span><span class="sxs-lookup"><span data-stu-id="07142-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="07142-122">Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (zgodnie z podglądem dodatku).</span><span class="sxs-lookup"><span data-stu-id="07142-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="07142-123">W związku <xref:System.Windows.FrameworkElement> z tym musi <xref:System.AddIn.Contract.INativeHandleContract> być przekształcony w przed przekroczeniem granicy izolacji.</span><span class="sxs-lookup"><span data-stu-id="07142-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="07142-124">Ta praca jest wykonywana przez kartę dodatku <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>przez wywołanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07142-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="07142-125">Implementowanie segmentu potoku widoku hosta</span><span class="sxs-lookup"><span data-stu-id="07142-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="07142-126">Ponieważ aplikacja hosta <xref:System.Windows.FrameworkElement>wyświetli , metoda w widoku hosta, który koreluje musi `IWPFAddInHostView.GetAddInUI` zwrócić wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="07142-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="07142-127">Poniższy kod przedstawia widok hosta umowy, zaimplementowany jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="07142-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="07142-128">Implementowanie segmentu potoku karty po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="07142-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="07142-129">Metoda kontraktu zwraca <xref:System.AddIn.Contract.INativeHandleContract>, ale aplikacja hosta <xref:System.Windows.FrameworkElement> oczekuje (zgodnie z określonymi przez widok hosta).</span><span class="sxs-lookup"><span data-stu-id="07142-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="07142-130">W związku <xref:System.AddIn.Contract.INativeHandleContract> z tym musi <xref:System.Windows.FrameworkElement> być przekształcony na po przekroczeniu granicy izolacji.</span><span class="sxs-lookup"><span data-stu-id="07142-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="07142-131">Ta praca jest wykonywana przez kartę <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>po stronie hosta przez wywołanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07142-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="07142-132">Implementowanie dodatku</span><span class="sxs-lookup"><span data-stu-id="07142-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="07142-133">Po utworzeniu karty dodatku i widoku dodatku dodatek (`WPFAddIn1.AddIn`) musi `IWPFAddInView.GetAddInUI` zaimplementować metodę zwracania <xref:System.Windows.FrameworkElement> obiektu (a <xref:System.Windows.Controls.UserControl> w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="07142-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="07142-134">Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI`, jest pokazana przez poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="07142-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="07142-135">Implementacja `IWPFAddInView.GetAddInUI` przez dodatek po prostu musi zwrócić nowe `AddInUI`wystąpienie , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07142-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="07142-136">Implementowanie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="07142-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="07142-137">Po utworzeniu karty po stronie hosta i widoku hosta aplikacja hosta może użyć modelu dodatku .NET Framework, aby `IWPFAddInHostView.GetAddInUI` otworzyć potok, uzyskać widok hosta dodatku i wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="07142-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="07142-138">Te kroki są pokazane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07142-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="07142-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07142-139">See also</span></span>

- <span data-ttu-id="07142-140">[Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="07142-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="07142-141">Dodatki WPF — omówienie</span><span class="sxs-lookup"><span data-stu-id="07142-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
