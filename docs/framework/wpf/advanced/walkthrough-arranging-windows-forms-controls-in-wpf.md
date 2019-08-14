---
title: 'Przewodnik: rozmieszczanie kontrolek Windows Forms w WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972310"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="bf15c-102">Przewodnik: rozmieszczanie kontrolek Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="bf15c-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="bf15c-103">W tym instruktażu pokazano, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać funkcji układu do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozmieszczenia formantów w aplikacji hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="bf15c-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="bf15c-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="bf15c-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="bf15c-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-105">Creating the project.</span></span>

- <span data-ttu-id="bf15c-106">Używanie domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-106">Using default layout settings.</span></span>

- <span data-ttu-id="bf15c-107">Ustalanie wielkości do zawartości.</span><span class="sxs-lookup"><span data-stu-id="bf15c-107">Sizing to content.</span></span>

- <span data-ttu-id="bf15c-108">Używanie pozycjonowania bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="bf15c-108">Using absolute positioning.</span></span>

- <span data-ttu-id="bf15c-109">Określanie rozmiaru jawnie.</span><span class="sxs-lookup"><span data-stu-id="bf15c-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="bf15c-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-110">Setting layout properties.</span></span>

- <span data-ttu-id="bf15c-111">Zrozumienie ograniczeń porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="bf15c-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="bf15c-112">Dokowania.</span><span class="sxs-lookup"><span data-stu-id="bf15c-112">Docking.</span></span>

- <span data-ttu-id="bf15c-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="bf15c-113">Setting visibility.</span></span>

- <span data-ttu-id="bf15c-114">Hostowanie formantu, który nie rozciąga się.</span><span class="sxs-lookup"><span data-stu-id="bf15c-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="bf15c-115">Ponowne.</span><span class="sxs-lookup"><span data-stu-id="bf15c-115">Scaling.</span></span>

- <span data-ttu-id="bf15c-116">Wirując.</span><span class="sxs-lookup"><span data-stu-id="bf15c-116">Rotating.</span></span>

- <span data-ttu-id="bf15c-117">Ustawianie uzupełniania i marginesów.</span><span class="sxs-lookup"><span data-stu-id="bf15c-117">Setting padding and margins.</span></span>

- <span data-ttu-id="bf15c-118">Korzystanie z kontenerów układów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="bf15c-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="bf15c-119">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [organizowanie Windows Forms formantów w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="bf15c-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="bf15c-120">Po zakończeniu będziesz mieć świadomość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] funkcji układu opartych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="bf15c-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf15c-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bf15c-121">Prerequisites</span></span>

<span data-ttu-id="bf15c-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf15c-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="bf15c-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="bf15c-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="bf15c-124">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="bf15c-124">To create and set up the project</span></span>

1. <span data-ttu-id="bf15c-125">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="bf15c-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="bf15c-126">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="bf15c-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="bf15c-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="bf15c-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="bf15c-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="bf15c-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="bf15c-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="bf15c-129">System.Drawing</span></span>

3. <span data-ttu-id="bf15c-130">Kliknij dwukrotnie plik MainWindow. XAML, aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="bf15c-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="bf15c-131">W elemencie Dodaj następujące [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowanie przestrzeni nazw. <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="bf15c-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="bf15c-132">W elemencie ustaw właściwość na `true` i zdefiniuj pięć wierszy i trzy kolumny. <xref:System.Windows.Controls.Grid.ShowGridLines%2A> <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="bf15c-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="bf15c-133">Używanie domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="bf15c-133">Using Default Layout Settings</span></span>

<span data-ttu-id="bf15c-134">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element obsługuje układ kontrolki hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bf15c-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="bf15c-135">Aby użyć domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="bf15c-135">To use default layout settings</span></span>

1. <span data-ttu-id="bf15c-136">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="bf15c-137">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-138">Kontrolka zostanie wyświetlona w <xref:System.Windows.Controls.Canvas>. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bf15c-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bf15c-139">Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości <xref:System.Windows.Forms.Integration.WindowsFormsHost> , a rozmiar elementu jest dostosowany do obsługiwanej kontroli.</span><span class="sxs-lookup"><span data-stu-id="bf15c-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="bf15c-140">Ustalanie wielkości do zawartości</span><span class="sxs-lookup"><span data-stu-id="bf15c-140">Sizing to Content</span></span>

<span data-ttu-id="bf15c-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="bf15c-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="bf15c-142">Aby zmienić rozmiar na zawartość</span><span class="sxs-lookup"><span data-stu-id="bf15c-142">To size to content</span></span>

1. <span data-ttu-id="bf15c-143">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="bf15c-144">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-145">Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy są zmieniane w celu uwzględnienia formantów hostowanych.</span><span class="sxs-lookup"><span data-stu-id="bf15c-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="bf15c-146">Używanie pozycjonowania bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="bf15c-146">Using Absolute Positioning</span></span>

<span data-ttu-id="bf15c-147">Możesz użyć pozycjonowania bezwzględnego, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby umieścić element w dowolnym miejscu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf15c-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="bf15c-148">Aby użyć pozycjonowania bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="bf15c-148">To use absolute positioning</span></span>

1. <span data-ttu-id="bf15c-149">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="bf15c-150">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.</span><span class="sxs-lookup"><span data-stu-id="bf15c-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="bf15c-152">Określanie rozmiaru jawnie</span><span class="sxs-lookup"><span data-stu-id="bf15c-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="bf15c-153">Możesz określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.FrameworkElement.Width%2A> przy użyciu właściwości i <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="bf15c-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="bf15c-154">Aby określić rozmiar jawnie</span><span class="sxs-lookup"><span data-stu-id="bf15c-154">To specify size explicitly</span></span>

1. <span data-ttu-id="bf15c-155">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="bf15c-156">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-157">Dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="bf15c-158">Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu jest odpowiednio zmieniana.</span><span class="sxs-lookup"><span data-stu-id="bf15c-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="bf15c-159">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="bf15c-159">Setting Layout Properties</span></span>

<span data-ttu-id="bf15c-160">Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="bf15c-161">Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="bf15c-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="bf15c-162">Ustawianie właściwości związanych z układem w formancie hostowanym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w programie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="bf15c-163">Aby wyświetlić efekty ustawiania właściwości w formancie hostowanym</span><span class="sxs-lookup"><span data-stu-id="bf15c-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="bf15c-164">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="bf15c-165">W Eksplorator rozwiązań kliknij dwukrotnie pozycję MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="bf15c-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="bf15c-166">vb lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="bf15c-167">Skopiuj poniższy kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="bf15c-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="bf15c-168">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="bf15c-169">Kliknij przycisk **kliknij mnie** .</span><span class="sxs-lookup"><span data-stu-id="bf15c-169">Click the **Click me** button.</span></span> <span data-ttu-id="bf15c-170"><xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control.Left%2A> Program obsługi `button1_Click` zdarzeń ustawia właściwości i dla kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="bf15c-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="bf15c-171">Powoduje to zmianę położenia hostowanej kontrolki w obrębie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="bf15c-172">Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana.</span><span class="sxs-lookup"><span data-stu-id="bf15c-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="bf15c-173">Zamiast tego, formant hostowany powinien zawsze wypełnić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span><span class="sxs-lookup"><span data-stu-id="bf15c-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="bf15c-174">Informacje o ograniczeniach porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="bf15c-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="bf15c-175">Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="bf15c-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="bf15c-176">Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bf15c-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="bf15c-177">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="bf15c-178">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest malowany na elemencie Label.</span><span class="sxs-lookup"><span data-stu-id="bf15c-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="bf15c-180">Dokowania</span><span class="sxs-lookup"><span data-stu-id="bf15c-180">Docking</span></span>

<span data-ttu-id="bf15c-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>element obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowanie.</span><span class="sxs-lookup"><span data-stu-id="bf15c-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="bf15c-182">Ustaw załączoną właściwość, <xref:System.Windows.Controls.DockPanel.Dock%2A> aby zadokować formant hostowany <xref:System.Windows.Controls.DockPanel> w elemencie.</span><span class="sxs-lookup"><span data-stu-id="bf15c-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="bf15c-183">Aby zadokować formant hostowany</span><span class="sxs-lookup"><span data-stu-id="bf15c-183">To dock a hosted control</span></span>

1. <span data-ttu-id="bf15c-184">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="bf15c-185">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-186">Element jest zadokowany po prawej stronie <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="bf15c-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="bf15c-187">Widoczność ustawień</span><span class="sxs-lookup"><span data-stu-id="bf15c-187">Setting Visibility</span></span>

<span data-ttu-id="bf15c-188">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Formant można ukryć lub zwinąć, <xref:System.Windows.UIElement.Visibility%2A> ustawiając właściwość dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="bf15c-189">Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="bf15c-190">Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="bf15c-191">Aby ustawić widoczność hostowanej kontrolki</span><span class="sxs-lookup"><span data-stu-id="bf15c-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="bf15c-192">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="bf15c-193">W MainWindow. XAML. vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="bf15c-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="bf15c-194">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="bf15c-195">Kliknij przycisk **kliknij, aby uczynić** niewidocznym, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby element był niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="bf15c-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="bf15c-196">Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie <xref:System.Windows.Forms.Integration.WindowsFormsHost> ukryć element z układu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="bf15c-197">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Gdy formant jest zwinięty, otaczające elementy są zmieniane w celu zajmowanego miejsca.</span><span class="sxs-lookup"><span data-stu-id="bf15c-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="bf15c-198">Hostowanie formantu, który nie rozciąga się</span><span class="sxs-lookup"><span data-stu-id="bf15c-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="bf15c-199">Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="bf15c-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="bf15c-200">Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrolka wyświetla miesiąc w stałym miejscu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="bf15c-201">Aby hostować formant, który nie rozciąga się</span><span class="sxs-lookup"><span data-stu-id="bf15c-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="bf15c-202">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="bf15c-203">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="bf15c-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="bf15c-205">Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez obsługiwaną <xref:System.Windows.Forms.MonthCalendar> kontrolę, ale są one wyśrodkowane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="bf15c-206">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Układ aparatu układu centruje elementy, które nie mogą być skalowane, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="bf15c-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="bf15c-207">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="bf15c-207">Scaling</span></span>

<span data-ttu-id="bf15c-208">W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna.</span><span class="sxs-lookup"><span data-stu-id="bf15c-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="bf15c-209">Aby zapewnić niestandardowe skalowanie, należy zastąpić <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="bf15c-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="bf15c-210">Aby skalować formant hostowany przy użyciu zachowania domyślnego</span><span class="sxs-lookup"><span data-stu-id="bf15c-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="bf15c-211">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="bf15c-212">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-213">Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="bf15c-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="bf15c-214">Jednak czcionka kontrolki hostowanej nie jest skalowana.</span><span class="sxs-lookup"><span data-stu-id="bf15c-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="bf15c-215">Wirując</span><span class="sxs-lookup"><span data-stu-id="bf15c-215">Rotating</span></span>

<span data-ttu-id="bf15c-216">W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="bf15c-217"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="bf15c-218">Każda wartość obrotu inna niż 180 stopni wywołuje <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bf15c-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="bf15c-219">Aby zobaczyć efekt rotacji w aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="bf15c-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="bf15c-220">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="bf15c-221">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-222">Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="bf15c-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="bf15c-223">Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.</span><span class="sxs-lookup"><span data-stu-id="bf15c-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="bf15c-224">Ustawianie uzupełniania i marginesów</span><span class="sxs-lookup"><span data-stu-id="bf15c-224">Setting Padding and Margins</span></span>

<span data-ttu-id="bf15c-225">Uzupełnienie i marginesy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w układzie są podobne do uzupełniania i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]marginesów w.</span><span class="sxs-lookup"><span data-stu-id="bf15c-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="bf15c-226">Po prostu ustaw <xref:System.Windows.Controls.Control.Padding%2A> właściwości <xref:System.Windows.FrameworkElement.Margin%2A> i dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="bf15c-227">Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej</span><span class="sxs-lookup"><span data-stu-id="bf15c-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="bf15c-228">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="bf15c-229">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-230">Ustawienia uzupełniania i marginesu są stosowane do formantów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostowanych w taki sam sposób, w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]jaki byłyby stosowane.</span><span class="sxs-lookup"><span data-stu-id="bf15c-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="bf15c-231">Używanie kontenerów układów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="bf15c-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="bf15c-232">Program <xref:System.Windows.Forms.FlowLayoutPanel> udostępnia dwa kontenery układu dynamicznego <xref:System.Windows.Forms.TableLayoutPanel>i.</span><span class="sxs-lookup"><span data-stu-id="bf15c-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="bf15c-233">Możesz również używać tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układach.</span><span class="sxs-lookup"><span data-stu-id="bf15c-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="bf15c-234">Aby użyć dynamicznego kontenera układu</span><span class="sxs-lookup"><span data-stu-id="bf15c-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="bf15c-235">Skopiuj poniższy kod XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="bf15c-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="bf15c-236">W MainWindow. XAML. vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="bf15c-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="bf15c-237">Dodaj wywołanie `InitializeFlowLayoutPanel` metody w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="bf15c-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="bf15c-238">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bf15c-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="bf15c-239"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>wypełnia i rozmieszcza<xref:System.Windows.Forms.FlowLayoutPanel> kontrolki podrzędne w domyślnym. <xref:System.Windows.Controls.DockPanel></span><span class="sxs-lookup"><span data-stu-id="bf15c-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf15c-240">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf15c-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="bf15c-241">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bf15c-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="bf15c-242">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="bf15c-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="bf15c-243">Rozmieszczanie formantów Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="bf15c-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="bf15c-244">Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="bf15c-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="bf15c-245">Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf15c-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
