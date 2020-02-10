---
title: Rozmieszczanie formantów Windows Forms w WPF
titleSuffix: ''
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 5cf48b347be2d0ca6a9b55f3e19affb8b471aa2b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095102"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="14004-102">Wskazówki: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="14004-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="14004-103">W tym instruktażu pokazano, jak za pomocą funkcji układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmieścić kontrolki Windows Forms w aplikacji hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="14004-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange Windows Forms controls in a hybrid application.</span></span>

<span data-ttu-id="14004-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="14004-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="14004-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="14004-105">Creating the project.</span></span>
- <span data-ttu-id="14004-106">Używanie domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="14004-106">Using default layout settings.</span></span>
- <span data-ttu-id="14004-107">Ustalanie wielkości do zawartości.</span><span class="sxs-lookup"><span data-stu-id="14004-107">Sizing to content.</span></span>
- <span data-ttu-id="14004-108">Używanie pozycjonowania bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="14004-108">Using absolute positioning.</span></span>
- <span data-ttu-id="14004-109">Określanie rozmiaru jawnie.</span><span class="sxs-lookup"><span data-stu-id="14004-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="14004-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="14004-110">Setting layout properties.</span></span>
- <span data-ttu-id="14004-111">Zrozumienie ograniczeń porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="14004-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="14004-112">Dokowania.</span><span class="sxs-lookup"><span data-stu-id="14004-112">Docking.</span></span>
- <span data-ttu-id="14004-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="14004-113">Setting visibility.</span></span>
- <span data-ttu-id="14004-114">Hostowanie formantu, który nie rozciąga się.</span><span class="sxs-lookup"><span data-stu-id="14004-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="14004-115">Ponowne.</span><span class="sxs-lookup"><span data-stu-id="14004-115">Scaling.</span></span>
- <span data-ttu-id="14004-116">Wirując.</span><span class="sxs-lookup"><span data-stu-id="14004-116">Rotating.</span></span>
- <span data-ttu-id="14004-117">Ustawianie uzupełniania i marginesów.</span><span class="sxs-lookup"><span data-stu-id="14004-117">Setting padding and margins.</span></span>
- <span data-ttu-id="14004-118">Korzystanie z kontenerów układów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="14004-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="14004-119">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [organizowanie Windows Forms formantów w przykładzie WPF](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WpfLayoutHostingWfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="14004-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WpfLayoutHostingWfWithXaml).</span></span>

<span data-ttu-id="14004-120">Po zakończeniu uzyskasz informacje o funkcjach układu Windows Forms w aplikacjach opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14004-120">When you are finished, you will have an understanding of Windows Forms layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14004-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="14004-121">Prerequisites</span></span>

<span data-ttu-id="14004-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14004-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="14004-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="14004-123">Creating the Project</span></span>

<span data-ttu-id="14004-124">Aby utworzyć i skonfigurować projekt, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="14004-125">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="14004-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="14004-126">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="14004-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="14004-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="14004-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="14004-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="14004-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="14004-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="14004-129">System.Drawing</span></span>

3. <span data-ttu-id="14004-130">Kliknij dwukrotnie plik *MainWindow. XAML* , aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="14004-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="14004-131">W <xref:System.Windows.Window> elementu Dodaj następujące mapowanie przestrzeni nazw Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14004-131">In the <xref:System.Windows.Window> element, add the following Windows Forms namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="14004-132">W elemencie <xref:System.Windows.Controls.Grid> ustaw właściwość <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na `true` i zdefiniuj pięć wierszy i trzech kolumn.</span><span class="sxs-lookup"><span data-stu-id="14004-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="14004-133">Używanie domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="14004-133">Using Default Layout Settings</span></span>

<span data-ttu-id="14004-134">Domyślnie element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje układ kontrolki hostowanej Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14004-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted Windows Forms control.</span></span>

<span data-ttu-id="14004-135">Aby użyć domyślnych ustawień układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="14004-136">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="14004-137">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-138">W <xref:System.Windows.Controls.Canvas>zostanie wyświetlona kontrolka <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14004-138">The Windows Forms <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="14004-139">Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości, a element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ma rozmiar, aby pomieścić obsługiwaną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="14004-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="14004-140">Ustalanie wielkości do zawartości</span><span class="sxs-lookup"><span data-stu-id="14004-140">Sizing to Content</span></span>

<span data-ttu-id="14004-141">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="14004-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="14004-142">Aby zmienić rozmiar na zawartość, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="14004-143">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="14004-144">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-145">Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zmieniane w celu uwzględnienia formantów hostowanych.</span><span class="sxs-lookup"><span data-stu-id="14004-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="14004-146">Używanie pozycjonowania bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="14004-146">Using Absolute Positioning</span></span>

<span data-ttu-id="14004-147">Możesz użyć pozycjonowania bezwzględnego, aby umieścić element <xref:System.Windows.Forms.Integration.WindowsFormsHost> w dowolnym miejscu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14004-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="14004-148">Aby użyć pozycjonowania bezwzględnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="14004-149">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="14004-150">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-151">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest umieszczony 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.</span><span class="sxs-lookup"><span data-stu-id="14004-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="14004-152">Określanie rozmiaru jawnie</span><span class="sxs-lookup"><span data-stu-id="14004-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="14004-153">Można określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu przy użyciu właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="14004-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="14004-154">Aby określić rozmiar jawnie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="14004-155">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="14004-156">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-157">Dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="14004-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="14004-158">Zawartość kontrolki Windows Forms jest zmieniana odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="14004-158">The content of the Windows Forms control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="14004-159">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="14004-159">Setting Layout Properties</span></span>

<span data-ttu-id="14004-160">Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="14004-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="14004-161">Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="14004-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="14004-162">Ustawianie właściwości związanych z układem w formancie hostowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="14004-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="14004-163">Aby wyświetlić efekty ustawiania właściwości kontrolki hostowanej, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="14004-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="14004-164">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="14004-165">W **Eksplorator rozwiązań**kliknij dwukrotnie plik *MainWindow. XAML. vb* lub *MainWindow.XAML.cs* , aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="14004-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="14004-166">Skopiuj następujący kod do definicji klasy `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="14004-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="14004-167">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="14004-168">Kliknij przycisk **kliknij mnie** .</span><span class="sxs-lookup"><span data-stu-id="14004-168">Click the **Click me** button.</span></span> <span data-ttu-id="14004-169">Obsługa zdarzeń `button1_Click` ustawia właściwości <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> dla hostowanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="14004-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="14004-170">Powoduje to zmianę położenia hostowanej kontrolki w ramach elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="14004-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="14004-171">Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana.</span><span class="sxs-lookup"><span data-stu-id="14004-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="14004-172">Zamiast tego, formant hostowany powinien zawsze wypełnić element <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="14004-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="14004-173">Informacje o ograniczeniach porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="14004-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="14004-174">Widoczne elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="14004-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="14004-175">Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="14004-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="14004-176">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="14004-177">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-178">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest malowany na elemencie Label.</span><span class="sxs-lookup"><span data-stu-id="14004-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="14004-179">Dokowania</span><span class="sxs-lookup"><span data-stu-id="14004-179">Docking</span></span>

<span data-ttu-id="14004-180">element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje dokowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14004-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="14004-181">Ustaw przyłączoną Właściwość <xref:System.Windows.Controls.DockPanel.Dock%2A>, aby zadokować formant hostowany w <xref:System.Windows.Controls.DockPanel> elemencie.</span><span class="sxs-lookup"><span data-stu-id="14004-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="14004-182">Aby zadokować formant hostowany, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="14004-183">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="14004-184">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-185">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest zadokowany po prawej stronie elementu <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="14004-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="14004-186">Widoczność ustawień</span><span class="sxs-lookup"><span data-stu-id="14004-186">Setting Visibility</span></span>

<span data-ttu-id="14004-187">Formant Windows Forms można uczynić niewidocznym lub zwijać, ustawiając właściwość <xref:System.Windows.UIElement.Visibility%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="14004-187">You can make your Windows Forms control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="14004-188">Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu.</span><span class="sxs-lookup"><span data-stu-id="14004-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="14004-189">Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="14004-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="14004-190">Aby ustawić widoczność hostowanej kontrolki, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="14004-191">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="14004-192">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="14004-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="14004-193">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="14004-194">Kliknij przycisk **kliknij, aby uczynić niewidocznym** , aby element <xref:System.Windows.Forms.Integration.WindowsFormsHost> był niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="14004-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="14004-195">Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie ukryć element <xref:System.Windows.Forms.Integration.WindowsFormsHost> z układu.</span><span class="sxs-lookup"><span data-stu-id="14004-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="14004-196">Gdy formant Windows Forms jest zwinięty, elementy otaczające są zmieniane w celu zajmowanego miejsca.</span><span class="sxs-lookup"><span data-stu-id="14004-196">When the Windows Forms control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="14004-197">Hostowanie formantu, który nie rozciąga się</span><span class="sxs-lookup"><span data-stu-id="14004-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="14004-198">Niektóre kontrolki Windows Forms mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="14004-198">Some Windows Forms controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="14004-199">Na przykład kontrolka <xref:System.Windows.Forms.MonthCalendar> wyświetla miesiąc w stałym miejscu.</span><span class="sxs-lookup"><span data-stu-id="14004-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="14004-200">Aby hostować formant, który nie rozciąga się, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="14004-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="14004-201">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="14004-202">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-203">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="14004-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="14004-204">Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez hostowaną kontrolkę <xref:System.Windows.Forms.MonthCalendar>, ale są one wyśrodkowane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="14004-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="14004-205">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu aparatu aparat centrów elementów, których nie można zmieniać, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="14004-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="14004-206">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="14004-206">Scaling</span></span>

<span data-ttu-id="14004-207">W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna.</span><span class="sxs-lookup"><span data-stu-id="14004-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="14004-208">Aby zapewnić niestandardowe skalowanie, Zastąp metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14004-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="14004-209">Aby skalować formant hostowany przy użyciu zachowania domyślnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="14004-210">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="14004-211">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-212">Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="14004-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="14004-213">Jednak czcionka kontrolki hostowanej nie jest skalowana.</span><span class="sxs-lookup"><span data-stu-id="14004-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="14004-214">Wirując</span><span class="sxs-lookup"><span data-stu-id="14004-214">Rotating</span></span>

<span data-ttu-id="14004-215">W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="14004-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="14004-216">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu.</span><span class="sxs-lookup"><span data-stu-id="14004-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="14004-217">Każda wartość obrotu inna niż 180 stopni wywołuje zdarzenie <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="14004-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="14004-218">Aby zobaczyć efekt rotacji w aplikacji hybrydowej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="14004-219">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="14004-220">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-221">Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="14004-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="14004-222">Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.</span><span class="sxs-lookup"><span data-stu-id="14004-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="14004-223">Ustawianie uzupełniania i marginesów</span><span class="sxs-lookup"><span data-stu-id="14004-223">Setting Padding and Margins</span></span>

<span data-ttu-id="14004-224">Uzupełnienie i marginesy w układzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są podobne do uzupełniania i marginesów w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14004-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in Windows Forms.</span></span> <span data-ttu-id="14004-225">Po prostu ustaw właściwości <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="14004-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="14004-226">Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="14004-227">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="14004-228">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-229">Ustawienia uzupełniania i marginesu są stosowane do kontrolek hostowanych Windows Forms w taki sam sposób, w jaki byłyby stosowane w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14004-229">The padding and margin settings are applied to the hosted Windows Forms controls in the same way they would be applied in Windows Forms.</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="14004-230">Używanie kontenerów układów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="14004-230">Using Dynamic Layout Containers</span></span>

<span data-ttu-id="14004-231">Windows Forms oferuje dwa kontenery układu dynamicznego, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="14004-231">Windows Forms provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="14004-232">Możesz również używać tych kontenerów w układach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14004-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="14004-233">Aby użyć dynamicznego kontenera układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="14004-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="14004-234">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="14004-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="14004-235">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="14004-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="14004-236">Dodaj wywołanie do metody `InitializeFlowLayoutPanel` w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="14004-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="14004-237">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="14004-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="14004-238">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> wypełnia <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> układa jego kontrolki podrzędne w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="14004-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="14004-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14004-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="14004-240">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14004-240">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="14004-241">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="14004-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="14004-242">Rozmieszczanie formantów Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="14004-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WpfLayoutHostingWfWithXaml)
- [<span data-ttu-id="14004-243">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="14004-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="14004-244">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14004-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
