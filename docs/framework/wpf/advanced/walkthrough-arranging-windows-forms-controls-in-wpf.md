---
title: 'Wskazówki: rozmieszczanie formantów Windows Forms w WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 484895db539b288bf388ff6c2ce3c29db55080b1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197842"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="445b1-102">Wskazówki: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="445b1-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="445b1-103">W tym instruktażu pokazano, jak za pomocą funkcji układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmieścić kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w aplikacji hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="445b1-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="445b1-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="445b1-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="445b1-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="445b1-105">Creating the project.</span></span>
- <span data-ttu-id="445b1-106">Używanie domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-106">Using default layout settings.</span></span>
- <span data-ttu-id="445b1-107">Ustalanie wielkości do zawartości.</span><span class="sxs-lookup"><span data-stu-id="445b1-107">Sizing to content.</span></span>
- <span data-ttu-id="445b1-108">Używanie pozycjonowania bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="445b1-108">Using absolute positioning.</span></span>
- <span data-ttu-id="445b1-109">Określanie rozmiaru jawnie.</span><span class="sxs-lookup"><span data-stu-id="445b1-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="445b1-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-110">Setting layout properties.</span></span>
- <span data-ttu-id="445b1-111">Zrozumienie ograniczeń porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="445b1-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="445b1-112">Dokowania.</span><span class="sxs-lookup"><span data-stu-id="445b1-112">Docking.</span></span>
- <span data-ttu-id="445b1-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="445b1-113">Setting visibility.</span></span>
- <span data-ttu-id="445b1-114">Hostowanie formantu, który nie rozciąga się.</span><span class="sxs-lookup"><span data-stu-id="445b1-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="445b1-115">Ponowne.</span><span class="sxs-lookup"><span data-stu-id="445b1-115">Scaling.</span></span>
- <span data-ttu-id="445b1-116">Wirując.</span><span class="sxs-lookup"><span data-stu-id="445b1-116">Rotating.</span></span>
- <span data-ttu-id="445b1-117">Ustawianie uzupełniania i marginesów.</span><span class="sxs-lookup"><span data-stu-id="445b1-117">Setting padding and margins.</span></span>
- <span data-ttu-id="445b1-118">Korzystanie z kontenerów układów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="445b1-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="445b1-119">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [organizowanie Windows Forms formantów w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="445b1-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="445b1-120">Po zakończeniu uzyskasz informacje o funkcjach układu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w aplikacjach opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="445b1-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="445b1-121">Prerequisites</span></span>

<span data-ttu-id="445b1-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="445b1-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="445b1-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="445b1-123">Creating the Project</span></span>

<span data-ttu-id="445b1-124">Aby utworzyć i skonfigurować projekt, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="445b1-125">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="445b1-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="445b1-126">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="445b1-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="445b1-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="445b1-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="445b1-128">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="445b1-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="445b1-129">System. Drawing</span><span class="sxs-lookup"><span data-stu-id="445b1-129">System.Drawing</span></span>

3. <span data-ttu-id="445b1-130">Kliknij dwukrotnie plik *MainWindow. XAML* , aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="445b1-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="445b1-131">W <xref:System.Windows.Window> elementu Dodaj następujące mapowanie przestrzeni nazw [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="445b1-132">W elemencie <xref:System.Windows.Controls.Grid> ustaw właściwość <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na `true` i zdefiniuj pięć wierszy i trzech kolumn.</span><span class="sxs-lookup"><span data-stu-id="445b1-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="445b1-133">Używanie domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="445b1-133">Using Default Layout Settings</span></span>

<span data-ttu-id="445b1-134">Domyślnie element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje układ kontrolki hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="445b1-135">Aby użyć domyślnych ustawień układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="445b1-136">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="445b1-137">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-138">W <xref:System.Windows.Controls.Canvas>zostanie wyświetlona kontrolka <xref:System.Windows.Forms.Button?displayProperty=nameWithType> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="445b1-139">Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości, a element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ma rozmiar, aby pomieścić obsługiwaną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="445b1-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="445b1-140">Ustalanie wielkości do zawartości</span><span class="sxs-lookup"><span data-stu-id="445b1-140">Sizing to Content</span></span>

<span data-ttu-id="445b1-141">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="445b1-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="445b1-142">Aby zmienić rozmiar na zawartość, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="445b1-143">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="445b1-144">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-145">Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zmieniane w celu uwzględnienia formantów hostowanych.</span><span class="sxs-lookup"><span data-stu-id="445b1-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="445b1-146">Używanie pozycjonowania bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="445b1-146">Using Absolute Positioning</span></span>

<span data-ttu-id="445b1-147">Możesz użyć pozycjonowania bezwzględnego, aby umieścić element <xref:System.Windows.Forms.Integration.WindowsFormsHost> w dowolnym miejscu w interfejsie użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="445b1-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="445b1-148">Aby użyć pozycjonowania bezwzględnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="445b1-149">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="445b1-150">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-151">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.</span><span class="sxs-lookup"><span data-stu-id="445b1-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="445b1-152">Określanie rozmiaru jawnie</span><span class="sxs-lookup"><span data-stu-id="445b1-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="445b1-153">Można określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu przy użyciu właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="445b1-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="445b1-154">Aby określić rozmiar jawnie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="445b1-155">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="445b1-156">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-157">Dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="445b1-158">Zawartość kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest zmieniana odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="445b1-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="445b1-159">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="445b1-159">Setting Layout Properties</span></span>

<span data-ttu-id="445b1-160">Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="445b1-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="445b1-161">Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="445b1-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="445b1-162">Ustawianie właściwości związanych z układem w formancie hostowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="445b1-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="445b1-163">Aby wyświetlić efekty ustawiania właściwości kontrolki hostowanej, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="445b1-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="445b1-164">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="445b1-165">W **Eksplorator rozwiązań**kliknij dwukrotnie plik *MainWindow. XAML. vb* lub *MainWindow.XAML.cs* , aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="445b1-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="445b1-166">Skopiuj następujący kod do definicji klasy `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="445b1-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="445b1-167">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="445b1-168">Kliknij przycisk **kliknij mnie** .</span><span class="sxs-lookup"><span data-stu-id="445b1-168">Click the **Click me** button.</span></span> <span data-ttu-id="445b1-169">Obsługa zdarzeń `button1_Click` ustawia właściwości <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> dla hostowanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="445b1-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="445b1-170">Powoduje to zmianę położenia hostowanej kontrolki w obrębie elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="445b1-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="445b1-171">Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana.</span><span class="sxs-lookup"><span data-stu-id="445b1-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="445b1-172">Zamiast tego, formant hostowany powinien zawsze wypełnić element <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="445b1-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="445b1-173">Informacje o ograniczeniach porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="445b1-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="445b1-174">Widoczne elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="445b1-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="445b1-175">Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="445b1-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="445b1-176">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="445b1-177">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-178">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest malowany na elemencie Label.</span><span class="sxs-lookup"><span data-stu-id="445b1-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="445b1-179">Dokowania</span><span class="sxs-lookup"><span data-stu-id="445b1-179">Docking</span></span>

<span data-ttu-id="445b1-180">element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje dokowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="445b1-181">Ustaw przyłączoną Właściwość <xref:System.Windows.Controls.DockPanel.Dock%2A>, aby zadokować formant hostowany w <xref:System.Windows.Controls.DockPanel> elemencie.</span><span class="sxs-lookup"><span data-stu-id="445b1-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="445b1-182">Aby zadokować formant hostowany, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="445b1-183">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="445b1-184">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-185">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest zadokowany po prawej stronie elementu <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="445b1-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="445b1-186">Widoczność ustawień</span><span class="sxs-lookup"><span data-stu-id="445b1-186">Setting Visibility</span></span>

<span data-ttu-id="445b1-187">Formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] można uczynić niewidocznym lub zwijać, ustawiając właściwość <xref:System.Windows.UIElement.Visibility%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="445b1-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="445b1-188">Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="445b1-189">Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="445b1-190">Aby ustawić widoczność hostowanej kontrolki, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="445b1-191">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="445b1-192">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="445b1-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="445b1-193">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="445b1-194">Kliknij przycisk **kliknij, aby uczynić niewidocznym** , aby element <xref:System.Windows.Forms.Integration.WindowsFormsHost> był niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="445b1-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="445b1-195">Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie ukryć element <xref:System.Windows.Forms.Integration.WindowsFormsHost> z układu.</span><span class="sxs-lookup"><span data-stu-id="445b1-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="445b1-196">Gdy formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest zwinięty, elementy otaczające są zmieniane w celu zajmowanego miejsca.</span><span class="sxs-lookup"><span data-stu-id="445b1-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="445b1-197">Hostowanie formantu, który nie rozciąga się</span><span class="sxs-lookup"><span data-stu-id="445b1-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="445b1-198">Niektóre kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="445b1-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="445b1-199">Na przykład kontrolka <xref:System.Windows.Forms.MonthCalendar> wyświetla miesiąc w stałym obszarze.</span><span class="sxs-lookup"><span data-stu-id="445b1-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="445b1-200">Aby hostować formant, który nie rozciąga się, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="445b1-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="445b1-201">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="445b1-202">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-203">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="445b1-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="445b1-204">Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez obsługiwaną kontrolę <xref:System.Windows.Forms.MonthCalendar>, ale są one wyśrodkowane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="445b1-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="445b1-205">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu aparatu aparat centrów elementów, których nie można zmieniać, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="445b1-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="445b1-206">Ponowne</span><span class="sxs-lookup"><span data-stu-id="445b1-206">Scaling</span></span>

<span data-ttu-id="445b1-207">W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna.</span><span class="sxs-lookup"><span data-stu-id="445b1-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="445b1-208">Aby zapewnić niestandardowe skalowanie, Zastąp metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="445b1-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="445b1-209">Aby skalować formant hostowany przy użyciu zachowania domyślnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="445b1-210">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="445b1-211">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-212">Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="445b1-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="445b1-213">Jednak czcionka kontrolki hostowanej nie jest skalowana.</span><span class="sxs-lookup"><span data-stu-id="445b1-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="445b1-214">Wirując</span><span class="sxs-lookup"><span data-stu-id="445b1-214">Rotating</span></span>

<span data-ttu-id="445b1-215">W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="445b1-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="445b1-216">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu.</span><span class="sxs-lookup"><span data-stu-id="445b1-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="445b1-217">Każda wartość obrotu inna niż 180 stopni wywołuje zdarzenie <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="445b1-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="445b1-218">Aby zobaczyć efekt rotacji w aplikacji hybrydowej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="445b1-219">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="445b1-220">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-221">Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="445b1-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="445b1-222">Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.</span><span class="sxs-lookup"><span data-stu-id="445b1-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="445b1-223">Ustawianie uzupełniania i marginesów</span><span class="sxs-lookup"><span data-stu-id="445b1-223">Setting Padding and Margins</span></span>

<span data-ttu-id="445b1-224">Uzupełnienie i marginesy w układzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są podobne do uzupełniania i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="445b1-225">Po prostu ustaw właściwości <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="445b1-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="445b1-226">Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="445b1-227">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="445b1-228">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-229">Ustawienia uzupełniania i marginesu są stosowane do kontrolek hostowanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w taki sam sposób, w jaki byłyby stosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="445b1-230">Używanie kontenerów układów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="445b1-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="445b1-231">oferuje dwa kontenery układu dynamicznego, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="445b1-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="445b1-232">Możesz również używać tych kontenerów w układach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="445b1-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="445b1-233">Aby użyć dynamicznego kontenera układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="445b1-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="445b1-234">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="445b1-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="445b1-235">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="445b1-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="445b1-236">Dodaj wywołanie metody `InitializeFlowLayoutPanel` w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="445b1-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="445b1-237">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="445b1-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="445b1-238">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> wypełnia <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> układa jego kontrolki podrzędne w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="445b1-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="445b1-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="445b1-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="445b1-240">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="445b1-240">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="445b1-241">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="445b1-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="445b1-242">Rozmieszczanie formantów Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="445b1-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="445b1-243">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="445b1-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="445b1-244">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="445b1-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
