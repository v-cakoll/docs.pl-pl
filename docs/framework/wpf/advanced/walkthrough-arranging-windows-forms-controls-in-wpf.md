---
title: 'Przewodnik: rozmieszczanie formantów Windows Forms w WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179432"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="208e9-102">Przewodnik: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="208e9-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="208e9-103">W tym instruktażu pokazano, jak za pomocą funkcji układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmieścić kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w aplikacji hybrydowej.</span><span class="sxs-lookup"><span data-stu-id="208e9-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="208e9-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="208e9-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="208e9-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="208e9-105">Creating the project.</span></span>
- <span data-ttu-id="208e9-106">Używanie domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-106">Using default layout settings.</span></span>
- <span data-ttu-id="208e9-107">Ustalanie wielkości do zawartości.</span><span class="sxs-lookup"><span data-stu-id="208e9-107">Sizing to content.</span></span>
- <span data-ttu-id="208e9-108">Używanie pozycjonowania bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="208e9-108">Using absolute positioning.</span></span>
- <span data-ttu-id="208e9-109">Określanie rozmiaru jawnie.</span><span class="sxs-lookup"><span data-stu-id="208e9-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="208e9-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-110">Setting layout properties.</span></span>
- <span data-ttu-id="208e9-111">Zrozumienie ograniczeń porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="208e9-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="208e9-112">Dokowania.</span><span class="sxs-lookup"><span data-stu-id="208e9-112">Docking.</span></span>
- <span data-ttu-id="208e9-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="208e9-113">Setting visibility.</span></span>
- <span data-ttu-id="208e9-114">Hostowanie formantu, który nie rozciąga się.</span><span class="sxs-lookup"><span data-stu-id="208e9-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="208e9-115">Ponowne.</span><span class="sxs-lookup"><span data-stu-id="208e9-115">Scaling.</span></span>
- <span data-ttu-id="208e9-116">Wirując.</span><span class="sxs-lookup"><span data-stu-id="208e9-116">Rotating.</span></span>
- <span data-ttu-id="208e9-117">Ustawianie uzupełniania i marginesów.</span><span class="sxs-lookup"><span data-stu-id="208e9-117">Setting padding and margins.</span></span>
- <span data-ttu-id="208e9-118">Korzystanie z kontenerów układów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="208e9-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="208e9-119">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [organizowanie Windows Forms formantów w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="208e9-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="208e9-120">Po zakończeniu będziesz mieć świadomość funkcji układu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w @no__t aplikacji opartych na -1.</span><span class="sxs-lookup"><span data-stu-id="208e9-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="208e9-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="208e9-121">Prerequisites</span></span>

<span data-ttu-id="208e9-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="208e9-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="208e9-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="208e9-123">Creating the Project</span></span>

<span data-ttu-id="208e9-124">Aby utworzyć i skonfigurować projekt, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="208e9-125">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="208e9-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="208e9-126">W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="208e9-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="208e9-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="208e9-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="208e9-128">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="208e9-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="208e9-129">System. Drawing</span><span class="sxs-lookup"><span data-stu-id="208e9-129">System.Drawing</span></span>

3. <span data-ttu-id="208e9-130">Kliknij dwukrotnie plik *MainWindow. XAML* , aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="208e9-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="208e9-131">W elemencie <xref:System.Windows.Window> Dodaj następujące mapowanie przestrzeni nazw [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="208e9-132">W elemencie <xref:System.Windows.Controls.Grid> ustaw właściwość <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na `true` i zdefiniuj pięć wierszy i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="208e9-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="208e9-133">Używanie domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="208e9-133">Using Default Layout Settings</span></span>

<span data-ttu-id="208e9-134">Domyślnie element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje układ dla kontrolki hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="208e9-135">Aby użyć domyślnych ustawień układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="208e9-136">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="208e9-137">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-138">Kontrolka [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> pojawia się w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="208e9-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="208e9-139">Rozmiar hostowanej kontrolki jest ustalany na podstawie jej zawartości, a element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ma rozmiar, aby pomieścić obsługiwaną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="208e9-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="208e9-140">Ustalanie wielkości do zawartości</span><span class="sxs-lookup"><span data-stu-id="208e9-140">Sizing to Content</span></span>

<span data-ttu-id="208e9-141">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zapewnia, że rozmiar hostowanej kontrolki jest ustalany w celu poprawnego wyświetlania jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="208e9-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="208e9-142">Aby zmienić rozmiar na zawartość, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="208e9-143">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="208e9-144">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-145">Dwa nowe kontrolki przycisków mają rozmiar, aby wyświetlić dłuższy ciąg tekstowy i większy rozmiar czcionki, a elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zmieniane w celu uwzględnienia formantów hostowanych.</span><span class="sxs-lookup"><span data-stu-id="208e9-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="208e9-146">Używanie pozycjonowania bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="208e9-146">Using Absolute Positioning</span></span>

<span data-ttu-id="208e9-147">Możesz użyć pozycjonowania bezwzględnego, aby umieścić element <xref:System.Windows.Forms.Integration.WindowsFormsHost> w dowolnym miejscu w interfejsie użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="208e9-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="208e9-148">Aby użyć pozycjonowania bezwzględnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="208e9-149">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="208e9-150">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-151">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej.</span><span class="sxs-lookup"><span data-stu-id="208e9-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="208e9-152">Określanie rozmiaru jawnie</span><span class="sxs-lookup"><span data-stu-id="208e9-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="208e9-153">Możesz określić rozmiar elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> przy użyciu właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="208e9-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="208e9-154">Aby określić rozmiar jawnie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="208e9-155">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="208e9-156">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-157">Dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawiono rozmiar 50 pikseli o szerokości do 70 pikseli, który jest mniejszy niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="208e9-158">Zawartość kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest odpowiednio zmieniana.</span><span class="sxs-lookup"><span data-stu-id="208e9-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="208e9-159">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="208e9-159">Setting Layout Properties</span></span>

<span data-ttu-id="208e9-160">Zawsze ustawiaj właściwości dotyczące układu w hostowanej kontroli przy użyciu właściwości elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="208e9-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="208e9-161">Ustawienie właściwości układu bezpośrednio w hostowanej kontrolce spowoduje zwrócenie nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="208e9-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="208e9-162">Ustawianie właściwości związanych z układem w formancie hostowanym w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="208e9-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="208e9-163">Aby wyświetlić efekty ustawiania właściwości kontrolki hostowanej, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="208e9-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="208e9-164">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="208e9-165">W **Eksplorator rozwiązań**kliknij dwukrotnie plik *MainWindow. XAML. vb* lub *MainWindow.XAML.cs* , aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="208e9-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="208e9-166">Skopiuj następujący kod do definicji klasy `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="208e9-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="208e9-167">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="208e9-168">Kliknij przycisk **kliknij mnie** .</span><span class="sxs-lookup"><span data-stu-id="208e9-168">Click the **Click me** button.</span></span> <span data-ttu-id="208e9-169">Obsługa zdarzeń `button1_Click` ustawia właściwości <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> w formancie hostowanym.</span><span class="sxs-lookup"><span data-stu-id="208e9-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="208e9-170">Powoduje to zmianę położenia hostowanej kontrolki w obrębie elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="208e9-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="208e9-171">Host utrzymuje ten sam obszar ekranu, ale hostowana kontrolka jest obcinana.</span><span class="sxs-lookup"><span data-stu-id="208e9-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="208e9-172">Zamiast tego, formant hostowany powinien zawsze wypełnić element <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="208e9-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="208e9-173">Informacje o ograniczeniach porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="208e9-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="208e9-174">Widoczne elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost> są zawsze rysowane na innych elementach WPF i nie mają wpływać na porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="208e9-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="208e9-175">Aby zobaczyć zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="208e9-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="208e9-176">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="208e9-177">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-178">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest malowany na elemencie Label.</span><span class="sxs-lookup"><span data-stu-id="208e9-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="208e9-179">Dokowania</span><span class="sxs-lookup"><span data-stu-id="208e9-179">Docking</span></span>

<span data-ttu-id="208e9-180">element <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje dokowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="208e9-181">Ustaw właściwość dołączoną <xref:System.Windows.Controls.DockPanel.Dock%2A>, aby zadokować formant hostowany w elemencie <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="208e9-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="208e9-182">Aby zadokować formant hostowany, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="208e9-183">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="208e9-184">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-185">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest zadokowany po prawej stronie elementu <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="208e9-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="208e9-186">Widoczność ustawień</span><span class="sxs-lookup"><span data-stu-id="208e9-186">Setting Visibility</span></span>

<span data-ttu-id="208e9-187">Można sprawić, aby kontrolka [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] była niewidoczna lub zwijana, ustawiając właściwość <xref:System.Windows.UIElement.Visibility%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="208e9-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="208e9-188">Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje przestrzeń układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="208e9-189">Gdy formant jest zwinięty, nie jest wyświetlany ani nie zajmuje obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="208e9-190">Aby ustawić widoczność hostowanej kontrolki, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="208e9-191">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="208e9-192">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="208e9-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="208e9-193">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="208e9-194">Kliknij przycisk **kliknij, aby uczynić niewidocznym** , aby element <xref:System.Windows.Forms.Integration.WindowsFormsHost> był niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="208e9-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="208e9-195">Kliknij przycisk **kliknij, aby zwinąć** , aby całkowicie ukryć element <xref:System.Windows.Forms.Integration.WindowsFormsHost> z układu.</span><span class="sxs-lookup"><span data-stu-id="208e9-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="208e9-196">Gdy formant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest zwinięty, elementy otaczające są zmieniane, aby zajmowały miejsce.</span><span class="sxs-lookup"><span data-stu-id="208e9-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="208e9-197">Hostowanie formantu, który nie rozciąga się</span><span class="sxs-lookup"><span data-stu-id="208e9-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="208e9-198">Niektóre kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają stały rozmiar i nie rozciągają się w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="208e9-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="208e9-199">Na przykład kontrolka <xref:System.Windows.Forms.MonthCalendar> wyświetla miesiąc w stałym obszarze.</span><span class="sxs-lookup"><span data-stu-id="208e9-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="208e9-200">Aby hostować formant, który nie rozciąga się, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="208e9-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="208e9-201">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="208e9-202">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-203">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest wyśrodkowany w wierszu siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="208e9-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="208e9-204">Jeśli okno jest wystarczająco duże, może pojawić się co najmniej dwa miesiące wyświetlane przez obsługiwaną kontrolę <xref:System.Windows.Forms.MonthCalendar>, ale są one wyśrodkowane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="208e9-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="208e9-205">Układ aparatu układu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie może mieć rozmiaru, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="208e9-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="208e9-206">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="208e9-206">Scaling</span></span>

<span data-ttu-id="208e9-207">W przeciwieństwie do elementów WPF większość formantów Windows Forms nie jest ciągle skalowalna.</span><span class="sxs-lookup"><span data-stu-id="208e9-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="208e9-208">Aby zapewnić niestandardowe skalowanie, Zastąp metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="208e9-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="208e9-209">Aby skalować formant hostowany przy użyciu zachowania domyślnego, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="208e9-210">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="208e9-211">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-212">Kontrolka hostowana i jej otaczające elementy są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="208e9-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="208e9-213">Jednak czcionka kontrolki hostowanej nie jest skalowana.</span><span class="sxs-lookup"><span data-stu-id="208e9-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="208e9-214">Wirując</span><span class="sxs-lookup"><span data-stu-id="208e9-214">Rotating</span></span>

<span data-ttu-id="208e9-215">W przeciwieństwie do elementów WPF, formanty Windows Forms nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="208e9-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="208e9-216">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie jest obracany z innymi elementami WPF w przypadku zastosowania transformacji obrotu.</span><span class="sxs-lookup"><span data-stu-id="208e9-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="208e9-217">Każda wartość obrotu inna niż 180 stopni wywołuje zdarzenie <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="208e9-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="208e9-218">Aby zobaczyć efekt rotacji w aplikacji hybrydowej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="208e9-219">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="208e9-220">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-221">Formant hostowany nie jest obrócony, ale jego elementy otaczające są obracane o kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="208e9-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="208e9-222">Może być konieczne zmianę rozmiaru okna, aby zobaczyć elementy.</span><span class="sxs-lookup"><span data-stu-id="208e9-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="208e9-223">Ustawianie uzupełniania i marginesów</span><span class="sxs-lookup"><span data-stu-id="208e9-223">Setting Padding and Margins</span></span>

<span data-ttu-id="208e9-224">Uzupełnienie i marginesy w układzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są podobne do uzupełniania i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="208e9-225">Po prostu ustaw właściwości <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="208e9-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="208e9-226">Aby ustawić uzupełnienie i marginesy dla kontrolki hostowanej, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="208e9-227">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="208e9-228">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-229">Ustawienia uzupełniania i marginesu są stosowane do formantów hostowanych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] w taki sam sposób, w jaki byłyby stosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="208e9-230">Używanie kontenerów układów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="208e9-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="208e9-231">oferuje dwa kontenery układu dynamicznego, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="208e9-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="208e9-232">Możesz również używać tych kontenerów w układach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="208e9-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="208e9-233">Aby użyć dynamicznego kontenera układu, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="208e9-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="208e9-234">Skopiuj następujący kod XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="208e9-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="208e9-235">W *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*Skopiuj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="208e9-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="208e9-236">Dodaj wywołanie metody `InitializeFlowLayoutPanel` w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="208e9-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="208e9-237">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="208e9-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="208e9-238">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> wypełnia <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza kontrolki podrzędne w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="208e9-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="208e9-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="208e9-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="208e9-240">Projektuj kod XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="208e9-240">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="208e9-241">Zagadnienia dotyczące układu elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="208e9-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="208e9-242">Rozmieszczanie formantów Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="208e9-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="208e9-243">Przewodnik: hosting złożonego formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="208e9-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="208e9-244">Przewodnik: hosting złożonego formantu WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="208e9-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
