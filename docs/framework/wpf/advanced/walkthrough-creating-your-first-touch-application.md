---
title: "Wskazówki: tworzenie Twojej pierwszej aplikacji dotykowej"
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
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 502fb9ae0c488f5f3e438a3ae0a7087538183f1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="0bc4b-102">Wskazówki: tworzenie Twojej pierwszej aplikacji dotykowej</span><span class="sxs-lookup"><span data-stu-id="0bc4b-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="0bc4b-103">Umożliwia aplikacjom uwzględniał touch.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="0bc4b-104">Na przykład pozwala na interakcję z aplikacją za pomocą jednego lub więcej palców na urządzeniu dotykowe, takie jak ekran dotykowy tego przewodnika tworzy aplikację, która umożliwia użytkownikowi przenoszenie, zmienianie rozmiaru lub Obracanie pojedynczego obiektu przy użyciu touch.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0bc4b-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0bc4b-105">Prerequisites</span></span>  
 <span data-ttu-id="0bc4b-106">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="0bc4b-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="0bc4b-107">.,</span><span class="sxs-lookup"><span data-stu-id="0bc4b-107">.</span></span>  
  
-   <span data-ttu-id="0bc4b-108">Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="0bc4b-109">Urządzenie, które akceptuje dotykowym, takie jak ekran dotykowy, który obsługuje Touch z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="0bc4b-110">Ponadto powinien mieć podstawową wiedzę na temat sposobu tworzenia aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], szczególnie jak subskrybować i obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="0bc4b-111">Aby uzyskać więcej informacji, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="0bc4b-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="0bc4b-112">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0bc4b-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="0bc4b-113">Aby utworzyć aplikację</span><span class="sxs-lookup"><span data-stu-id="0bc4b-113">To create the application</span></span>  
  
1.  <span data-ttu-id="0bc4b-114">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="0bc4b-115">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="0bc4b-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="0bc4b-116">Zamień zawartość MainWindow.xaml następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="0bc4b-117">Ten kod znaczników tworzy prostą aplikację, która zawiera czerwony <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0bc4b-118"><xref:System.Windows.UIElement.IsManipulationEnabled%2A> Właściwość <xref:System.Windows.Shapes.Rectangle> ma wartość true, dzięki czemu będą otrzymywać zdarzeń manipulowanie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="0bc4b-119">Subskrybuje aplikacji <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, i <xref:System.Windows.UIElement.ManipulationInertiaStarting> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="0bc4b-120">Zdarzenia te zawierają logiki przenoszenia <xref:System.Windows.Shapes.Rectangle> gdy użytkownik modyfikuje go.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="0bc4b-121">Jeśli korzystasz z języka Visual Basic w pierwszym wierszu MainWindow.xaml, Zastąp `x:Class="BasicManipulation.MainWindow"` z `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="0bc4b-122">W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.UIElement.ManipulationStarting> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="0bc4b-123"><xref:System.Windows.UIElement.ManipulationStarting> Zdarzenie po [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykryje, że touch rozpoczyna danych wejściowych do manipulowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="0bc4b-124">Kod określa, czy pozycja operowanie powinny być względem <xref:System.Windows.Window> przez ustawienie <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="0bc4b-125">W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.Input.ManipulationDelta> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="0bc4b-126"><xref:System.Windows.Input.ManipulationDelta> Zdarzeń występuje po naciśnięciu wejściowy zmienia pozycję i może wystąpić wiele razy podczas manipulowania.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="0bc4b-127">Zdarzenie może również wystąpić po palcem jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="0bc4b-128">Na przykład, jeśli użytkownik przeciąga palcem ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzenie wielokrotnie jako przenosi palca.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="0bc4b-129">Gdy użytkownik wywołuje palca na ekranie <xref:System.Windows.Input.ManipulationDelta> zdarzeń będzie się powtarzał do symulowania bezwładności.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="0bc4b-130">Kod ma zastosowanie <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> do <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> przenieść go, gdy użytkownik przechodzi przez dotknięcie danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="0bc4b-131">Sprawdza również czy <xref:System.Windows.Shapes.Rectangle> znajduje się poza granicami <xref:System.Windows.Window> po wystąpieniu zdarzenia podczas bezwładności.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="0bc4b-132">Jeśli tak, aplikacja wywołuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metodę, aby zakończyć operowanie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="0bc4b-133">W `MainWindow` klasy, należy dodać następujące <xref:System.Windows.UIElement.ManipulationInertiaStarting> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="0bc4b-134"><xref:System.Windows.UIElement.ManipulationInertiaStarting> Zdarzenie wystąpi, gdy użytkownik wywołuje wszystkich palców na ekranie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="0bc4b-135">Kod ustawia prędkość początkowa i prędkości dla ruchu, rozszerzenia i obrotu prostokąta.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="0bc4b-136">Tworzenie i uruchamianie projektu.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="0bc4b-137">Powinny pojawić się czerwonego kwadratu są wyświetlane w oknie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="0bc4b-138">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0bc4b-138">Testing the Application</span></span>  
 <span data-ttu-id="0bc4b-139">Aby przetestować aplikację, wypróbuj następujące operacje.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="0bc4b-140">Należy pamiętać, że można wykonać więcej niż jedną z nich w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="0bc4b-141">Aby przenieść <xref:System.Windows.Shapes.Rectangle>, umieść palcem <xref:System.Windows.Shapes.Rectangle> i przesuń palcem po ekranie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="0bc4b-142">Aby zmienić rozmiar <xref:System.Windows.Shapes.Rectangle>, umieść dwoma palcami <xref:System.Windows.Shapes.Rectangle> i Przenieś palcami razem lub je od siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="0bc4b-143">Obracanie <xref:System.Windows.Shapes.Rectangle>, umieść dwoma palcami <xref:System.Windows.Shapes.Rectangle> i obracania palcami wokół siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="0bc4b-144">Aby spowodować bezwładności, szybko podnieść palcami na ekranie wykonywać operacje poprzedniej.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="0bc4b-145"><xref:System.Windows.Shapes.Rectangle> Będzie przenosić, Zmień rozmiar lub obracać przez kilka sekund, zanim przestanie.</span><span class="sxs-lookup"><span data-stu-id="0bc4b-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc4b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bc4b-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
