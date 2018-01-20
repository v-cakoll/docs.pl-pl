---
title: "Wskazówki: rozmieszczanie formantów Windows Forms w WPF"
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
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480d61f6ca2aa67e0de48030655a6368c70554f4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="8a0a0-102">Wskazówki: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="8a0a0-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="8a0a0-103">Ten przewodnik przedstawia sposób użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje układ ułożyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="8a0a0-104">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="8a0a0-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="8a0a0-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="8a0a0-106">Przy użyciu domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="8a0a0-107">Ustawianie rozmiaru do zawartości.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="8a0a0-108">Przy użyciu bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="8a0a0-109">Jawne określenie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="8a0a0-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="8a0a0-111">Opis ograniczeń porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="8a0a0-112">Dokowanie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-112">Docking.</span></span>  
  
-   <span data-ttu-id="8a0a0-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="8a0a0-114">Hosting formant, który nie stretch.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="8a0a0-115">Skalowanie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-115">Scaling.</span></span>  
  
-   <span data-ttu-id="8a0a0-116">Obracanie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-116">Rotating.</span></span>  
  
-   <span data-ttu-id="8a0a0-117">Ustawienie dopełnienia i marginesów.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="8a0a0-118">Używanie kontenerów układ dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="8a0a0-119">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [rozmieszczanie formantów formularzy systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="8a0a0-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="8a0a0-120">Po ukończeniu będzie mieć wiedzę o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] układu funkcje w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a0a0-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8a0a0-121">Prerequisites</span></span>  
 <span data-ttu-id="8a0a0-122">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="8a0a0-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="8a0a0-123">.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8a0a0-124">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="8a0a0-125">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="8a0a0-126">Utwórz projekt aplikacji WPF o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="8a0a0-127">W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="8a0a0-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="8a0a0-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="8a0a0-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="8a0a0-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="8a0a0-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="8a0a0-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="8a0a0-131">Kliknij dwukrotnie MainWindow.xaml, aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="8a0a0-132">W <xref:System.Windows.Window> elementu, Dodaj następujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="8a0a0-133">W <xref:System.Windows.Controls.Grid> zestaw elementu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwości `true` i zdefiniuj pięć wierszy i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="8a0a0-134">Przy użyciu domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="8a0a0-135">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu obsługuje układ dla hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="8a0a0-136">Aby użyć domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="8a0a0-137">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="8a0a0-138">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Formant jest widoczny w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="8a0a0-140">Obsługiwanego formantu jest o rozmiarze na podstawie jego zawartości i <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest dopasowywany do uwzględnienia obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="8a0a0-141">Ustawianie rozmiaru zawartości</span><span class="sxs-lookup"><span data-stu-id="8a0a0-141">Sizing to Content</span></span>  
 <span data-ttu-id="8a0a0-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element gwarantuje, że obsługiwanego formantu jest dopasowywany do wyświetlania jej zawartości poprawnie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="8a0a0-143">Rozmiar do zawartości</span><span class="sxs-lookup"><span data-stu-id="8a0a0-143">To size to content</span></span>  
  
1.  <span data-ttu-id="8a0a0-144">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="8a0a0-145">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-146">Dwa nowe formanty przycisku jest dopasowywany do wyświetlania dłuższy ciąg tekstu i większy rozmiar czcionki prawidłowo i <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy zmieniany jest rozmiar do uwzględnienia hostowanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="8a0a0-147">Bezwzględny</span><span class="sxs-lookup"><span data-stu-id="8a0a0-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="8a0a0-148">Umożliwia bezwzględny umieścić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element w dowolnym miejscu w interfejsie użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="8a0a0-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="8a0a0-149">Aby użyć położenia bezwzględne</span><span class="sxs-lookup"><span data-stu-id="8a0a0-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="8a0a0-150">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="8a0a0-151">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element znajduje się 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="8a0a0-153">Jawne określenie rozmiaru</span><span class="sxs-lookup"><span data-stu-id="8a0a0-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="8a0a0-154">Można określić rozmiaru <xref:System.Windows.Forms.Integration.WindowsFormsHost> przy użyciu elementu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="8a0a0-155">Aby jawnie określić rozmiar</span><span class="sxs-lookup"><span data-stu-id="8a0a0-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="8a0a0-156">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="8a0a0-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest ustawiony na wartość rozmiaru 50 pikseli szerokości 70 pikseli, które jest mniejsze niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="8a0a0-159">Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest odpowiednio zmienić rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="8a0a0-160">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="8a0a0-161">Zawsze ustawić właściwości związane z układem formantu hostowanej przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8a0a0-162">Ustawianie właściwości układu bezpośrednio w formancie hostowanej umożliwia uzyskanie niezamierzone wyników.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="8a0a0-163">Ustawianie właściwości związane z układem formantu hostowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="8a0a0-164">Aby zobaczyć efekty Ustawianie właściwości formantu hostowanej</span><span class="sxs-lookup"><span data-stu-id="8a0a0-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="8a0a0-165">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="8a0a0-166">W Eksploratorze rozwiązań kliknij dwukrotnie MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="8a0a0-167">VB lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="8a0a0-168">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="8a0a0-169">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="8a0a0-170">Kliknij przycisk **kliknij mnie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-170">Click the **Click me** button.</span></span> <span data-ttu-id="8a0a0-171">`button1_Click` Ustawia program obsługi zdarzeń <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> właściwości obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="8a0a0-172">Powoduje to, że można zmienić ich pozycji w ciągu obsługiwany formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8a0a0-173">Host przechowuje ten sam obszar ekranu, ale obsługiwanego formantu zostanie obcięta.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="8a0a0-174">Zamiast tego należy zawsze wypełnienie obsługiwanego formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="8a0a0-175">Opis ograniczeń porządek osi z</span><span class="sxs-lookup"><span data-stu-id="8a0a0-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="8a0a0-176">Domyślnie widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy są zawsze pobierane na drugim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów, są one dotknięta porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-176">By default, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="8a0a0-177">Aby włączyć porządku osi, ustaw <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> na wartość true i <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> właściwości <xref:System.Windows.Interop.CompositionMode.Full> lub <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-177">To enable z-ordering, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-default-z-order-behavior"></a><span data-ttu-id="8a0a0-178">Aby wyświetlić domyślne zachowanie porządku osi z</span><span class="sxs-lookup"><span data-stu-id="8a0a0-178">To see the default z-order behavior</span></span>  
  
1.  <span data-ttu-id="8a0a0-179">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-179">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  <span data-ttu-id="8a0a0-180">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-180">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Jest malowany element za pośrednictwem elementu label.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-181">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a><span data-ttu-id="8a0a0-182">Aby wyświetlić zachowanie porządku osi z, gdy IsRedirected ma wartość true</span><span class="sxs-lookup"><span data-stu-id="8a0a0-182">To see the z-order behavior when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="8a0a0-183">Zastąp następujące XAML w poprzednim przykładzie porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-183">Replace the previous z-order example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     <span data-ttu-id="8a0a0-184">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-184">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-185">Label element jest malowane przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-185">The label element is painted over the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="docking"></a><span data-ttu-id="8a0a0-186">Dokowanie</span><span class="sxs-lookup"><span data-stu-id="8a0a0-186">Docking</span></span>  
 <span data-ttu-id="8a0a0-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>Element obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowania.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="8a0a0-188">Ustaw <xref:System.Windows.Controls.DockPanel.Dock%2A> dołączonych właściwości dock obsługiwanego formantu w <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-188">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="8a0a0-189">Aby dock obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-189">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="8a0a0-190">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-190">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="8a0a0-191">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-191">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-192"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest zadokowane po prawej stronie <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-192">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="8a0a0-193">Ustawienie widoczności</span><span class="sxs-lookup"><span data-stu-id="8a0a0-193">Setting Visibility</span></span>  
 <span data-ttu-id="8a0a0-194">Możesz wprowadzić Twojej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli niewidoczne lub zwinąć przez ustawienie <xref:System.Windows.UIElement.Visibility%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-194">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="8a0a0-195">Gdy formant jest niewidoczny, nie jest wyświetlana, ale przypada miejsca układu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-195">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="8a0a0-196">Po zwinięciu formantu, nie jest wyświetlany, nie jest zajmują miejsce układu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-196">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="8a0a0-197">Aby ustawić widoczność obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-197">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="8a0a0-198">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-198">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="8a0a0-199">W MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-199">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="8a0a0-200">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-200">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="8a0a0-201">Kliknij przycisk **kliknij, aby ukryć** przycisk, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element jest niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-201">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="8a0a0-202">Kliknij przycisk **kliknij, aby zwinąć** przycisk, aby ukryć <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z układu całkowicie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-202">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="8a0a0-203">Gdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest zwinięte, otaczających elementów zostaną ponownie posortowane zajmują jej miejsce.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-203">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="8a0a0-204">Hosting formant, który nie Stretch</span><span class="sxs-lookup"><span data-stu-id="8a0a0-204">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="8a0a0-205">Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty mają o stałym rozmiarze i rozciąganie nie w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-205">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="8a0a0-206">Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrola Wyświetla miesiąca w stałym miejsce.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-206">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="8a0a0-207">Do hostowania formantu, który nie stretch</span><span class="sxs-lookup"><span data-stu-id="8a0a0-207">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="8a0a0-208">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-208">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="8a0a0-209">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-209">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-210"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest wyśrodkowane wiersza siatki, ale nie jest rozciągany w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-210">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="8a0a0-211">Jeśli okno jest wystarczająco duży, może zostać wyświetlony co najmniej dwa miesiące, wyświetlane przez hostowanej <xref:System.Windows.Forms.MonthCalendar> sterowania, ale te jest wyśrodkowywana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-211">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="8a0a0-212">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparatu układu Wyśrodkowuje elementy, które nie może ustalać w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-212">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="8a0a0-213">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="8a0a0-213">Scaling</span></span>  
 <span data-ttu-id="8a0a0-214">W odróżnieniu od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, większość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie są stale skalowalności.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-214">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, most [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls are not continuously scalable.</span></span> <span data-ttu-id="8a0a0-215">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element skaluje jego obsługiwanego formantu, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-215">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element scales its hosted control when possible.</span></span>  <span data-ttu-id="8a0a0-216">Aby włączyć skalowanie pełni funkcjonalnymi, ustaw <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> na wartość true i <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> właściwości <xref:System.Windows.Interop.CompositionMode.Full> lub <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-216">To enable full-fledged scaling, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="8a0a0-217">Aby skalować obsługiwanego formantu przy użyciu domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="8a0a0-217">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="8a0a0-218">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-218">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="8a0a0-219">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-219">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-220">Obsługiwanego formantu i jego otaczających elementów są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-220">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="8a0a0-221">Jednak nie jest skalowana czcionki obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-221">However, the hosted control's font is not scaled.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a><span data-ttu-id="8a0a0-222">Aby skalować obsługiwanego formantu przez ustawienie IsRedirected na wartość true</span><span class="sxs-lookup"><span data-stu-id="8a0a0-222">To scale a hosted control by setting IsRedirected to true</span></span>  
  
1.  <span data-ttu-id="8a0a0-223">Zastąp poprzedni przykład skalowania następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-223">Replace the previous scaling example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  <span data-ttu-id="8a0a0-224">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-224">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-225">Obsługiwanego formantu, jego otaczających elementów i czcionki obsługiwanego formantu są skalowane według współczynnika 0,5.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-225">The hosted control, its surrounding elements, and the hosted control's font are scaled by a factor of 0.5.</span></span>  
  
## <a name="rotating"></a><span data-ttu-id="8a0a0-226">Obracanie</span><span class="sxs-lookup"><span data-stu-id="8a0a0-226">Rotating</span></span>  
 <span data-ttu-id="8a0a0-227">W odróżnieniu od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-227">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls do not support rotation.</span></span> <span data-ttu-id="8a0a0-228">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu nie Obróć z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów podczas stosowania przekształcenia obrotu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-228">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements when a rotation transformation is applied.</span></span> <span data-ttu-id="8a0a0-229">Obracanie wartości innej niż 180 stopni zgłasza <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-229">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>  <span data-ttu-id="8a0a0-230">Aby włączyć, obracanie o dowolny kąt, ustaw <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> na wartość true i <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> właściwości <xref:System.Windows.Interop.CompositionMode.Full> lub <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-230">To enable rotating to any angle, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="8a0a0-231">Aby zobaczyć efekt obrotu w aplikacji hybrydowych</span><span class="sxs-lookup"><span data-stu-id="8a0a0-231">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="8a0a0-232">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-232">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="8a0a0-233">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-233">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-234">Obsługiwanego formantu nie jest obracany, ale jego otaczających elementów są obracane kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-234">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="8a0a0-235">Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-235">You may have to resize the window to see the elements.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a><span data-ttu-id="8a0a0-236">Aby zobaczyć efekt obrotu w aplikacji hybrydowych, gdy IsRedirected ma wartość true</span><span class="sxs-lookup"><span data-stu-id="8a0a0-236">To see the effect of rotation in a hybrid application when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="8a0a0-237">Zastąp następujące XAML w poprzednim przykładzie obrotu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-237">Replace the previous rotation example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  <span data-ttu-id="8a0a0-238">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-239">Obraca się obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-239">The hosted control is rotated.</span></span>  <span data-ttu-id="8a0a0-240">Należy pamiętać, że <xref:System.Windows.Media.RotateTransform.Angle%2A> właściwość można ustawić dowolną wartość.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-240">Note that the <xref:System.Windows.Media.RotateTransform.Angle%2A> property can be set to any value.</span></span> <span data-ttu-id="8a0a0-241">Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-241">You may have to resize the window to see the elements.</span></span>  
  
## <a name="setting-padding-and-margins"></a><span data-ttu-id="8a0a0-242">Ustawienie dopełnienia i marginesów</span><span class="sxs-lookup"><span data-stu-id="8a0a0-242">Setting Padding and Margins</span></span>  
 <span data-ttu-id="8a0a0-243">Wypełnienie i marginesów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu są podobne do uzupełnienia i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a0a0-243">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="8a0a0-244">Wystarczy ustawić <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-244">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="8a0a0-245">Aby ustawić dopełnienia i marginesów hostowanej formantu</span><span class="sxs-lookup"><span data-stu-id="8a0a0-245">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="8a0a0-246">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-246">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="8a0a0-247">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-247">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-248">Dopełnienie i margines ustawienia są stosowane do hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w taki sam sposób, które mają zostać zastosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a0a0-248">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="8a0a0-249">Używanie kontenerów układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="8a0a0-249">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="8a0a0-250">udostępnia dwa kontenery układ dynamiczny, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-250"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="8a0a0-251">Można również użyć tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układów.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-251">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="8a0a0-252">Aby użyć kontenera układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="8a0a0-252">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="8a0a0-253">Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-253">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="8a0a0-254">MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-254">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="8a0a0-255">Dodaj wywołanie do `InitializeFlowLayoutPanel` metody w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-255">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="8a0a0-256">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-256">Press F5 to build and run the application.</span></span> <span data-ttu-id="8a0a0-257"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element wypełnia <xref:System.Windows.Controls.DockPanel>, i <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza jej kontrolkach podrzędnych w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-257">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0a0-258">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a0a0-258">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8a0a0-259">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="8a0a0-259">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="8a0a0-260">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="8a0a0-260">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="8a0a0-261">Rozmieszczanie okien formantów formularzy w przykładowym WPF</span><span class="sxs-lookup"><span data-stu-id="8a0a0-261">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="8a0a0-262">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="8a0a0-262">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="8a0a0-263">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a0a0-263">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
