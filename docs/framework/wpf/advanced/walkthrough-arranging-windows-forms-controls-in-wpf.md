---
title: 'Wskazówki: rozmieszczanie formantów Windows Forms w WPF'
ms.custom: ''
ms.date: 04/03/2018
ms.prod: .net-framework
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3129b4128444530b1277299f3f95ce49232421
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="b67d5-102">Wskazówki: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="b67d5-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="b67d5-103">Ten przewodnik przedstawia sposób użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje układ ułożyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="b67d5-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="b67d5-104">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="b67d5-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="b67d5-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="b67d5-106">Przy użyciu domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="b67d5-107">Ustawianie rozmiaru do zawartości.</span><span class="sxs-lookup"><span data-stu-id="b67d5-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="b67d5-108">Przy użyciu bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="b67d5-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="b67d5-109">Jawne określenie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b67d5-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="b67d5-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="b67d5-111">Opis ograniczeń porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="b67d5-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="b67d5-112">Dokowanie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-112">Docking.</span></span>  
  
-   <span data-ttu-id="b67d5-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="b67d5-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="b67d5-114">Hosting formant, który nie stretch.</span><span class="sxs-lookup"><span data-stu-id="b67d5-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="b67d5-115">Skalowanie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-115">Scaling.</span></span>  
  
-   <span data-ttu-id="b67d5-116">Obracanie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-116">Rotating.</span></span>  
  
-   <span data-ttu-id="b67d5-117">Ustawienie dopełnienia i marginesów.</span><span class="sxs-lookup"><span data-stu-id="b67d5-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="b67d5-118">Używanie kontenerów układ dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="b67d5-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="b67d5-119">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [rozmieszczanie formantów formularzy systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="b67d5-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="b67d5-120">Po ukończeniu będzie mieć wiedzę o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] układu funkcje w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b67d5-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b67d5-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b67d5-121">Prerequisites</span></span>  
 <span data-ttu-id="b67d5-122">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="b67d5-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="b67d5-123">.</span><span class="sxs-lookup"><span data-stu-id="b67d5-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b67d5-124">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="b67d5-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="b67d5-125">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="b67d5-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="b67d5-126">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="b67d5-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="b67d5-127">W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="b67d5-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="b67d5-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="b67d5-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="b67d5-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="b67d5-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="b67d5-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="b67d5-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="b67d5-131">Kliknij dwukrotnie MainWindow.xaml, aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="b67d5-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="b67d5-132">W <xref:System.Windows.Window> elementu, Dodaj następujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b67d5-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="b67d5-133">W <xref:System.Windows.Controls.Grid> zestaw elementu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwości `true` i zdefiniuj pięć wierszy i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="b67d5-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="b67d5-134">Przy użyciu domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="b67d5-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="b67d5-135">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu obsługuje układ dla hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="b67d5-136">Aby użyć domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="b67d5-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="b67d5-137">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="b67d5-138">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Formant jest widoczny w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="b67d5-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="b67d5-140">Obsługiwanego formantu jest o rozmiarze na podstawie jego zawartości i <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest dopasowywany do uwzględnienia obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="b67d5-141">Ustawianie rozmiaru zawartości</span><span class="sxs-lookup"><span data-stu-id="b67d5-141">Sizing to Content</span></span>  
 <span data-ttu-id="b67d5-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element gwarantuje, że obsługiwanego formantu jest dopasowywany do wyświetlania jej zawartości poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="b67d5-143">Rozmiar do zawartości</span><span class="sxs-lookup"><span data-stu-id="b67d5-143">To size to content</span></span>  
  
1.  <span data-ttu-id="b67d5-144">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="b67d5-145">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-146">Dwa nowe formanty przycisku jest dopasowywany do wyświetlania dłuższy ciąg tekstu i większy rozmiar czcionki prawidłowo i <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy zmieniany jest rozmiar do uwzględnienia hostowanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b67d5-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="b67d5-147">Bezwzględny</span><span class="sxs-lookup"><span data-stu-id="b67d5-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="b67d5-148">Umożliwia bezwzględny umieścić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element w dowolnym miejscu w interfejsie użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="b67d5-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="b67d5-149">Aby użyć położenia bezwzględne</span><span class="sxs-lookup"><span data-stu-id="b67d5-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="b67d5-150">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="b67d5-151">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element znajduje się 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="b67d5-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="b67d5-153">Jawne określenie rozmiaru</span><span class="sxs-lookup"><span data-stu-id="b67d5-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="b67d5-154">Można określić rozmiaru <xref:System.Windows.Forms.Integration.WindowsFormsHost> przy użyciu elementu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b67d5-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="b67d5-155">Aby jawnie określić rozmiar</span><span class="sxs-lookup"><span data-stu-id="b67d5-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="b67d5-156">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="b67d5-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest ustawiony na wartość rozmiaru 50 pikseli szerokości 70 pikseli, które jest mniejsze niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="b67d5-159">Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest odpowiednio zmienić rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b67d5-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="b67d5-160">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="b67d5-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="b67d5-161">Zawsze ustawić właściwości związane z układem formantu hostowanej przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="b67d5-162">Ustawianie właściwości układu bezpośrednio w formancie hostowanej umożliwia uzyskanie niezamierzone wyników.</span><span class="sxs-lookup"><span data-stu-id="b67d5-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="b67d5-163">Ustawianie właściwości związane z układem formantu hostowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="b67d5-164">Aby zobaczyć efekty Ustawianie właściwości formantu hostowanej</span><span class="sxs-lookup"><span data-stu-id="b67d5-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="b67d5-165">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="b67d5-166">W Eksploratorze rozwiązań kliknij dwukrotnie MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b67d5-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="b67d5-167">VB lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="b67d5-168">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b67d5-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="b67d5-169">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="b67d5-170">Kliknij przycisk **kliknij mnie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b67d5-170">Click the **Click me** button.</span></span> <span data-ttu-id="b67d5-171">`button1_Click` Ustawia program obsługi zdarzeń <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> właściwości obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="b67d5-172">Powoduje to, że można zmienić ich pozycji w ciągu obsługiwany formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="b67d5-173">Host przechowuje ten sam obszar ekranu, ale obsługiwanego formantu zostanie obcięta.</span><span class="sxs-lookup"><span data-stu-id="b67d5-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="b67d5-174">Zamiast tego należy zawsze wypełnienie obsługiwanego formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="b67d5-175">Opis ograniczeń porządek osi z</span><span class="sxs-lookup"><span data-stu-id="b67d5-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="b67d5-176">Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy zawsze są rysowane na inne elementy WPF i znajdują się poza zasięgiem porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="b67d5-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="b67d5-177">Aby wyświetlić to zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b67d5-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="b67d5-178">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="b67d5-179">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Jest malowany element za pośrednictwem elementu label.</span><span class="sxs-lookup"><span data-stu-id="b67d5-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="b67d5-181">Dokowanie</span><span class="sxs-lookup"><span data-stu-id="b67d5-181">Docking</span></span>  
 <span data-ttu-id="b67d5-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowania.</span><span class="sxs-lookup"><span data-stu-id="b67d5-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="b67d5-183">Ustaw <xref:System.Windows.Controls.DockPanel.Dock%2A> dołączonych właściwości dock obsługiwanego formantu w <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="b67d5-184">Aby dock obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="b67d5-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="b67d5-185">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="b67d5-186">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest zadokowane po prawej stronie <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="b67d5-188">Ustawienie widoczności</span><span class="sxs-lookup"><span data-stu-id="b67d5-188">Setting Visibility</span></span>  
 <span data-ttu-id="b67d5-189">Możesz wprowadzić Twojej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli niewidoczne lub zwinąć przez ustawienie <xref:System.Windows.UIElement.Visibility%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="b67d5-190">Gdy formant jest niewidoczny, nie jest wyświetlana, ale przypada miejsca układu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="b67d5-191">Po zwinięciu formantu, nie jest wyświetlany, nie jest zajmują miejsce układu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="b67d5-192">Aby ustawić widoczność obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="b67d5-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="b67d5-193">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="b67d5-194">W MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b67d5-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="b67d5-195">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="b67d5-196">Kliknij przycisk **kliknij, aby ukryć** przycisk, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="b67d5-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="b67d5-197">Kliknij przycisk **kliknij, aby zwinąć** przycisk, aby ukryć <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z układu całkowicie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="b67d5-198">Gdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest zwinięte, otaczających elementów zostaną ponownie posortowane zajmują jej miejsce.</span><span class="sxs-lookup"><span data-stu-id="b67d5-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="b67d5-199">Hosting formant, który nie Stretch</span><span class="sxs-lookup"><span data-stu-id="b67d5-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="b67d5-200">Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty mają o stałym rozmiarze i rozciąganie nie w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="b67d5-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="b67d5-201">Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrola Wyświetla miesiąca w stałym miejsce.</span><span class="sxs-lookup"><span data-stu-id="b67d5-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="b67d5-202">Do hostowania formantu, który nie stretch</span><span class="sxs-lookup"><span data-stu-id="b67d5-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="b67d5-203">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="b67d5-204">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-205"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest wyśrodkowane wiersza siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="b67d5-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="b67d5-206">Jeśli okno jest wystarczająco duży, może zostać wyświetlony co najmniej dwa miesiące, wyświetlane przez hostowanej <xref:System.Windows.Forms.MonthCalendar> sterowania, ale te jest wyśrodkowywana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="b67d5-207">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparatu układu Wyśrodkowuje elementy, które nie może ustalać w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="b67d5-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="b67d5-208">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="b67d5-208">Scaling</span></span>  
 <span data-ttu-id="b67d5-209">W odróżnieniu od elementów WPF większości formanty formularzy systemu Windows nie są stale skalowalności.</span><span class="sxs-lookup"><span data-stu-id="b67d5-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="b67d5-210">Aby zapewnić niestandardowego skalowania, Zastąp <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b67d5-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="b67d5-211">Aby skalować obsługiwanego formantu przy użyciu domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="b67d5-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="b67d5-212">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="b67d5-213">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-214">Obsługiwanego formantu i jego otaczających elementów są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="b67d5-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="b67d5-215">Jednak nie jest skalowana czcionki obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="b67d5-216">Obracanie</span><span class="sxs-lookup"><span data-stu-id="b67d5-216">Rotating</span></span>  
 <span data-ttu-id="b67d5-217">W odróżnieniu od elementów WPF formanty formularzy systemu Windows nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="b67d5-218"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu nie Obróć z innymi elementami WPF podczas stosowania przekształcenia obrotu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="b67d5-219">Obracanie wartości innej niż 180 stopni zgłasza <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b67d5-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="b67d5-220">Aby zobaczyć efekt obrotu w aplikacji hybrydowych</span><span class="sxs-lookup"><span data-stu-id="b67d5-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="b67d5-221">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="b67d5-222">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-223">Obsługiwanego formantu nie jest obracany, ale jego otaczających elementów są obracane kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="b67d5-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="b67d5-224">Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.</span><span class="sxs-lookup"><span data-stu-id="b67d5-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="b67d5-225">Ustawienie dopełnienia i marginesów</span><span class="sxs-lookup"><span data-stu-id="b67d5-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="b67d5-226">Wypełnienie i marginesów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu są podobne do uzupełnienia i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b67d5-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="b67d5-227">Wystarczy ustawić <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="b67d5-228">Aby ustawić dopełnienia i marginesów hostowanej formantu</span><span class="sxs-lookup"><span data-stu-id="b67d5-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="b67d5-229">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="b67d5-230">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-231">Dopełnienie i margines ustawienia są stosowane do hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w taki sam sposób, które mają zostać zastosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b67d5-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="b67d5-232">Używanie kontenerów układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="b67d5-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="b67d5-233"> udostępnia dwa kontenery układ dynamiczny, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="b67d5-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="b67d5-234">Można również użyć tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układów.</span><span class="sxs-lookup"><span data-stu-id="b67d5-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="b67d5-235">Aby użyć kontenera układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="b67d5-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="b67d5-236">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="b67d5-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="b67d5-237">MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b67d5-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="b67d5-238">Dodaj wywołanie do `InitializeFlowLayoutPanel` metody w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="b67d5-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="b67d5-239">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b67d5-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="b67d5-240"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element wypełnia <xref:System.Windows.Controls.DockPanel>, i <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza jej kontrolkach podrzędnych w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="b67d5-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67d5-241">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b67d5-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b67d5-242">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="b67d5-242">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="b67d5-243">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="b67d5-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="b67d5-244">Rozmieszczanie okien formantów formularzy w przykładowym WPF</span><span class="sxs-lookup"><span data-stu-id="b67d5-244">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="b67d5-245">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="b67d5-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="b67d5-246">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b67d5-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
