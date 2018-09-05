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
ms.openlocfilehash: 98b108be518a9fef03ee299d43ed591cf736f68f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564277"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="03e3e-102">Wskazówki: rozmieszczanie formantów Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="03e3e-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="03e3e-103">W tym instruktażu dowiesz się, jak używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji układu, aby zorganizować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek w aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="03e3e-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="03e3e-104">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="03e3e-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="03e3e-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="03e3e-106">Przy użyciu domyślnych ustawień układu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="03e3e-107">Ustalanie rozmiaru zawartości.</span><span class="sxs-lookup"><span data-stu-id="03e3e-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="03e3e-108">Za pomocą pozycjonowanie absolutne.</span><span class="sxs-lookup"><span data-stu-id="03e3e-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="03e3e-109">Jawne określenie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="03e3e-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="03e3e-110">Ustawianie właściwości układu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="03e3e-111">Opis ograniczeń porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="03e3e-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="03e3e-112">Dokowania.</span><span class="sxs-lookup"><span data-stu-id="03e3e-112">Docking.</span></span>  
  
-   <span data-ttu-id="03e3e-113">Ustawienie widoczności.</span><span class="sxs-lookup"><span data-stu-id="03e3e-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="03e3e-114">Hosting formant, który nie Stretch Database.</span><span class="sxs-lookup"><span data-stu-id="03e3e-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="03e3e-115">Skalowanie.</span><span class="sxs-lookup"><span data-stu-id="03e3e-115">Scaling.</span></span>  
  
-   <span data-ttu-id="03e3e-116">Obracanie.</span><span class="sxs-lookup"><span data-stu-id="03e3e-116">Rotating.</span></span>  
  
-   <span data-ttu-id="03e3e-117">Dopełnienie ustawienia zaznaczania i marginesów.</span><span class="sxs-lookup"><span data-stu-id="03e3e-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="03e3e-118">Używanie kontenerów układ dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="03e3e-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="03e3e-119">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [rozmieszczanie formantów formularzy Windows w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="03e3e-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="03e3e-120">Po zakończeniu będziesz mieć zrozumienia [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] układ funkcje w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03e3e-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="03e3e-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="03e3e-121">Prerequisites</span></span>  
 <span data-ttu-id="03e3e-122">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="03e3e-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="03e3e-123">.</span><span class="sxs-lookup"><span data-stu-id="03e3e-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="03e3e-124">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="03e3e-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="03e3e-125">Aby utworzyć i skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="03e3e-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="03e3e-126">Utwórz projekt aplikacji WPF, o nazwie `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="03e3e-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="03e3e-127">W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="03e3e-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="03e3e-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="03e3e-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="03e3e-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="03e3e-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="03e3e-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="03e3e-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="03e3e-131">Kliknij dwukrotnie opcję MainWindow.xaml, aby otworzyć go w widoku XAML.</span><span class="sxs-lookup"><span data-stu-id="03e3e-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="03e3e-132">W <xref:System.Windows.Window> elementu, Dodaj następujący kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="03e3e-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="03e3e-133">W <xref:System.Windows.Controls.Grid> Ustaw element <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość `true` i zdefiniowanie pięciu wierszy i trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="03e3e-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="03e3e-134">Przy użyciu domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="03e3e-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="03e3e-135">Domyślnie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element obsługuje układ hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.</span><span class="sxs-lookup"><span data-stu-id="03e3e-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="03e3e-136">Aby użyć domyślnych ustawień układu</span><span class="sxs-lookup"><span data-stu-id="03e3e-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="03e3e-137">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="03e3e-138">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Formant jest widoczny w <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="03e3e-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="03e3e-140">Hostowanej kontroli ma rozmiar na podstawie jego zawartości i <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ma rozmiar umożliwiających obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="03e3e-141">Ustalanie rozmiaru zawartości</span><span class="sxs-lookup"><span data-stu-id="03e3e-141">Sizing to Content</span></span>  
 <span data-ttu-id="03e3e-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element gwarantuje zmieniania rozmiaru do prawidłowego wyświetlenia jego zawartości hostowanej kontroli.</span><span class="sxs-lookup"><span data-stu-id="03e3e-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="03e3e-143">Rozmiar do zawartości</span><span class="sxs-lookup"><span data-stu-id="03e3e-143">To size to content</span></span>  
  
1.  <span data-ttu-id="03e3e-144">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="03e3e-145">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-146">Dwa nowe formanty przycisku mają rozmiar do wyświetlenia dłuższy ciąg tekstowy i większy rozmiar czcionki prawidłowo i <xref:System.Windows.Forms.Integration.WindowsFormsHost> zmieniany jest rozmiar elementów do uwzględnienia hostowanej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="03e3e-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="03e3e-147">Za pomocą pozycjonowanie absolutne</span><span class="sxs-lookup"><span data-stu-id="03e3e-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="03e3e-148">Pozycjonowanie absolutne można użyć do umieszczenia <xref:System.Windows.Forms.Integration.WindowsFormsHost> element w dowolnym miejscu w interfejsie użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="03e3e-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="03e3e-149">Aby użyć pozycjonowanie absolutne</span><span class="sxs-lookup"><span data-stu-id="03e3e-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="03e3e-150">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="03e3e-151">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest umieszczany 20 pikseli od górnej krawędzi komórki siatki i 20 pikseli od lewej strony.</span><span class="sxs-lookup"><span data-stu-id="03e3e-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="03e3e-153">Jawne określenie rozmiaru</span><span class="sxs-lookup"><span data-stu-id="03e3e-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="03e3e-154">Można określić rozmiar <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu za pomocą <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="03e3e-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="03e3e-155">Aby jawnie określić rozmiar</span><span class="sxs-lookup"><span data-stu-id="03e3e-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="03e3e-156">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="03e3e-157">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest ustawiony na wartość o rozmiarze 50 pikseli szerokości i 70 pikseli, który jest mniejszy niż domyślne ustawienia układu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="03e3e-159">Zawartość [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest nieco inaczej rozmieszczone odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="03e3e-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="03e3e-160">Ustawianie właściwości układu</span><span class="sxs-lookup"><span data-stu-id="03e3e-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="03e3e-161">Zawsze ustawić właściwości związane z układem formantu hostowanej przy użyciu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="03e3e-162">Ustawianie właściwości układu bezpośrednio w kontrolce hostowanej umożliwia uzyskanie niepożądanych wyników.</span><span class="sxs-lookup"><span data-stu-id="03e3e-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="03e3e-163">Ustawianie właściwości związane z układem sterowanie hostowanej w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="03e3e-164">Aby zobaczyć efekty Ustawianie właściwości formantu hostowanej</span><span class="sxs-lookup"><span data-stu-id="03e3e-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="03e3e-165">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="03e3e-166">W Eksploratorze rozwiązań kliknij dwukrotnie opcję MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="03e3e-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="03e3e-167">w języku VB lub MainWindow.xaml.cs, aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="03e3e-168">Skopiuj następujący kod do `MainWindow` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="03e3e-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="03e3e-169">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="03e3e-170">Kliknij przycisk **kliknij mnie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="03e3e-170">Click the **Click me** button.</span></span> <span data-ttu-id="03e3e-171">`button1_Click` Ustawia program obsługi zdarzeń <xref:System.Windows.Forms.Control.Top%2A> i <xref:System.Windows.Forms.Control.Left%2A> właściwości obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="03e3e-172">Powoduje to, że obsługiwany formant można zmieniać pozycji w ramach <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="03e3e-173">Host obsługuje ten sam obszar ekranu, ale obsługiwanego formantu zostanie obcięta.</span><span class="sxs-lookup"><span data-stu-id="03e3e-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="03e3e-174">Zamiast tego należy zawsze wypełnienie obsługiwanego formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="03e3e-175">Opis ograniczeń porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="03e3e-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="03e3e-176">Widoczne <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów są zawsze rysowane na podstawie innych elementów WPF i są dotknięte porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="03e3e-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="03e3e-177">Aby wyświetlić to zachowanie porządku osi z, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="03e3e-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="03e3e-178">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="03e3e-179">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Za pośrednictwem elementu label jest malowany element.</span><span class="sxs-lookup"><span data-stu-id="03e3e-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="03e3e-181">Dokowanie</span><span class="sxs-lookup"><span data-stu-id="03e3e-181">Docking</span></span>  
 <span data-ttu-id="03e3e-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> obsługuje element [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokowania.</span><span class="sxs-lookup"><span data-stu-id="03e3e-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="03e3e-183">Ustaw <xref:System.Windows.Controls.DockPanel.Dock%2A> dołączona właściwość, aby zadokować obsługiwanego formantu w <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="03e3e-184">Aby zadokować obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="03e3e-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="03e3e-185">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="03e3e-186">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element jest zadokowany na prawej krawędzi <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="03e3e-188">Ustawienie widoczności</span><span class="sxs-lookup"><span data-stu-id="03e3e-188">Setting Visibility</span></span>  
 <span data-ttu-id="03e3e-189">Możesz wprowadzić swoje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować niewidoczne lub zwijanie ustawienie <xref:System.Windows.UIElement.Visibility%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="03e3e-190">Gdy kontrolka jest niewidoczna, nie jest wyświetlana, ale zajmuje miejsce układu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="03e3e-191">Gdy formant jest zwinięte, nie jest wyświetlana, ani jest zajmują miejsce.</span><span class="sxs-lookup"><span data-stu-id="03e3e-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="03e3e-192">Aby ustawić widoczność obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="03e3e-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="03e3e-193">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="03e3e-194">W MainWindow.xaml.vb lub MainWindow.xaml.cs Skopiuj poniższy kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="03e3e-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="03e3e-195">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="03e3e-196">Kliknij przycisk **kliknij, aby ukryć** , aby wprowadzić <xref:System.Windows.Forms.Integration.WindowsFormsHost> element niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="03e3e-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="03e3e-197">Kliknij przycisk **kliknij, aby zwinąć** przycisk, aby ukryć <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu z układu całkowicie.</span><span class="sxs-lookup"><span data-stu-id="03e3e-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="03e3e-198">Gdy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli jest zwinięte, otaczających elementów są nieco inaczej rozmieszczone zajmować jego przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="03e3e-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="03e3e-199">Hosting formantu, który dopasowuje</span><span class="sxs-lookup"><span data-stu-id="03e3e-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="03e3e-200">Niektóre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki ma stały rozmiar i nie stretch w celu wypełnienia dostępnego miejsca w układzie.</span><span class="sxs-lookup"><span data-stu-id="03e3e-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="03e3e-201">Na przykład <xref:System.Windows.Forms.MonthCalendar> kontrolka Wyświetla miesiąc w stałym miejscu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="03e3e-202">Do hostowania formantu, który nie Stretch Database</span><span class="sxs-lookup"><span data-stu-id="03e3e-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="03e3e-203">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="03e3e-204">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-205"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu elastycznego jest wyśrodkowane wiersz siatki, ale nie jest rozciągana w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="03e3e-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="03e3e-206">Jeśli okno jest wystarczająco duży, może zostać wyświetlony co najmniej dwóch miesięcy, wyświetlane przez hostowanej <xref:System.Windows.Forms.MonthCalendar> kontroli, ale te jest wyśrodkowywana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="03e3e-207">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparatu układu centra elementy, które nie może mieć rozmiar w celu wypełnienia dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="03e3e-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="03e3e-208">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="03e3e-208">Scaling</span></span>  
 <span data-ttu-id="03e3e-209">W odróżnieniu od elementów WPF większości kontrolek Windows Forms nie są stale skalowalne.</span><span class="sxs-lookup"><span data-stu-id="03e3e-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="03e3e-210">Aby zapewnić Skalowanie niestandardowe, możesz zastąpić <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="03e3e-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="03e3e-211">Aby skalować obsługiwanego formantu przy użyciu domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="03e3e-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="03e3e-212">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="03e3e-213">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-214">Hostowanej formantem i jego otaczających elementów są skalowane przez współczynnik 0,5.</span><span class="sxs-lookup"><span data-stu-id="03e3e-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="03e3e-215">Czcionka obsługiwanego formantu nie jest skalowana.</span><span class="sxs-lookup"><span data-stu-id="03e3e-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="03e3e-216">Obracanie</span><span class="sxs-lookup"><span data-stu-id="03e3e-216">Rotating</span></span>  
 <span data-ttu-id="03e3e-217">W odróżnieniu od elementów WPF kontrolek formularzy Windows Forms nie obsługują obrotu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="03e3e-218"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu nie Obróć z innymi elementami WPF stosowania transformacji obrotu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="03e3e-219">Wartości obrotu innej niż 180 stopni zgłasza <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03e3e-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="03e3e-220">Aby zobaczyć efekt obrotu w aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="03e3e-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="03e3e-221">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="03e3e-222">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-223">Nie jest obracany hostowanej kontroli, ale jego otaczających elementów są obracane kąt 180 stopni.</span><span class="sxs-lookup"><span data-stu-id="03e3e-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="03e3e-224">Może być konieczne zmiany rozmiaru okna, aby wyświetlić elementy.</span><span class="sxs-lookup"><span data-stu-id="03e3e-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="03e3e-225">Dopełnienie ustawienia zaznaczania i marginesów</span><span class="sxs-lookup"><span data-stu-id="03e3e-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="03e3e-226">Wypełnienie i marginesów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu są podobne do wypełnienia zaznaczania i marginesów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03e3e-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="03e3e-227">Po prostu ustaw <xref:System.Windows.Controls.Control.Padding%2A> i <xref:System.Windows.FrameworkElement.Margin%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="03e3e-228">Aby ustawić dopełnienia i marginesów hostowanej formantu</span><span class="sxs-lookup"><span data-stu-id="03e3e-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="03e3e-229">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="03e3e-230">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-231">Wypełnienie i margines ustawienia są stosowane do obsługiwanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek w taki sam sposób, które mają zostać zastosowane w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03e3e-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="03e3e-232">Używanie kontenerów układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="03e3e-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="03e3e-233"> udostępnia dwa kontenery układ dynamiczny, <xref:System.Windows.Forms.FlowLayoutPanel> i <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="03e3e-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="03e3e-234">Możesz również użyć tych kontenerów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układów.</span><span class="sxs-lookup"><span data-stu-id="03e3e-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="03e3e-235">Aby użyć kontenera układ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="03e3e-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="03e3e-236">Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="03e3e-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="03e3e-237">W MainWindow.xaml.vb lub MainWindow.xaml.cs skopiuj następujący kod do definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="03e3e-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="03e3e-238">Dodaj wywołanie do `InitializeFlowLayoutPanel` metody w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="03e3e-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="03e3e-239">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="03e3e-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="03e3e-240"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Wstawia element <xref:System.Windows.Controls.DockPanel>, i <xref:System.Windows.Forms.FlowLayoutPanel> rozmieszcza jego formantów podrzędnych w domyślnym <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="03e3e-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e3e-241">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03e3e-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="03e3e-242">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03e3e-242">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="03e3e-243">Zagadnienia dotyczące układu dla elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="03e3e-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="03e3e-244">Windows rozmieszczanie formantów formularzy w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="03e3e-244">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="03e3e-245">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="03e3e-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="03e3e-246">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03e3e-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
