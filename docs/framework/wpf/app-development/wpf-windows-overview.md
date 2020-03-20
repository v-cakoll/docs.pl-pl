---
title: Omówienie systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145543"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="34f40-102">Przegląd Okna WPF</span><span class="sxs-lookup"><span data-stu-id="34f40-102">WPF Windows Overview</span></span>
<span data-ttu-id="34f40-103">Użytkownicy wchodzą w interakcje z autonomicznymi aplikacjami Programu Windows Presentation Foundation (WPF) za pośrednictwem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="34f40-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="34f40-104">Głównym celem okna jest hostowanie zawartości, która wizualizuje dane i umożliwia użytkownikom interakcję z danymi.</span><span class="sxs-lookup"><span data-stu-id="34f40-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="34f40-105">Autonomiczne aplikacje WPF zapewniają własne <xref:System.Windows.Window> okna przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="34f40-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="34f40-106">W tym <xref:System.Windows.Window> temacie przedstawiono przed pokryciem podstaw tworzenia okien i zarządzania nimi w aplikacjach autonomicznych.</span><span class="sxs-lookup"><span data-stu-id="34f40-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-107">Aplikacje WPF hostowane przez przeglądarkę, w tym aplikacje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przeglądarki XAML (XBAPs) i luźne strony, nie udostępniają własnych okien.</span><span class="sxs-lookup"><span data-stu-id="34f40-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="34f40-108">Zamiast tego są one hostowane w oknach dostarczonych przez program Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="34f40-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="34f40-109">Zobacz [Przegląd aplikacji przeglądarki WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34f40-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="34f40-110">Klasa Window</span><span class="sxs-lookup"><span data-stu-id="34f40-110">The Window Class</span></span>  
 <span data-ttu-id="34f40-111">Poniższy rysunek ilustruje części składowe okna:</span><span class="sxs-lookup"><span data-stu-id="34f40-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Zrzut ekranu przedstawiający elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="34f40-113">Okno jest podzielone na dwa obszary: obszar niebędący klientem i obszar klienta.</span><span class="sxs-lookup"><span data-stu-id="34f40-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="34f40-114">*Obszar niebędący klientem* okna jest implementowany przez WPF I zawiera części okna, które są wspólne dla większości okien, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="34f40-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="34f40-115">Obramowanie.</span><span class="sxs-lookup"><span data-stu-id="34f40-115">A border.</span></span>  
  
- <span data-ttu-id="34f40-116">Pasek tytułu.</span><span class="sxs-lookup"><span data-stu-id="34f40-116">A title bar.</span></span>  
  
- <span data-ttu-id="34f40-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="34f40-117">An icon.</span></span>  
  
- <span data-ttu-id="34f40-118">Minimalizuj, maksymalizuj i przywracaj przyciski.</span><span class="sxs-lookup"><span data-stu-id="34f40-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="34f40-119">Przycisk Zamknij.</span><span class="sxs-lookup"><span data-stu-id="34f40-119">A Close button.</span></span>  
  
- <span data-ttu-id="34f40-120">Menu System z elementami menu, które umożliwiają użytkownikom minimalizowanie, maksymalizację, przywracanie, przenoszenie, przenoszenie rozmiaru i zamykanie okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="34f40-121">*Obszar klienta* okna jest obszarem w obszarze nienależącym do okna i jest używany przez deweloperów do dodawania zawartości specyficznej dla aplikacji, takich jak paski menu, paski narzędzi i formanty.</span><span class="sxs-lookup"><span data-stu-id="34f40-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="34f40-122">W WPF WPF okno jest hermetyzowany przez <xref:System.Windows.Window> klasę, która służy do wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="34f40-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="34f40-123">Wyświetl okno.</span><span class="sxs-lookup"><span data-stu-id="34f40-123">Display a window.</span></span>  
  
- <span data-ttu-id="34f40-124">Skonfiguruj rozmiar, położenie i wygląd okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="34f40-125">Hostuj zawartość specyficzną dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="34f40-126">Zarządzanie okresem istnienia okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="34f40-127">Implementowanie okna</span><span class="sxs-lookup"><span data-stu-id="34f40-127">Implementing a Window</span></span>  
 <span data-ttu-id="34f40-128">Implementacja okna typowe obejmuje zarówno wygląd i zachowanie, gdzie *wygląd* definiuje, jak okno wygląda dla użytkowników i *zachowanie* definiuje sposób, w jaki okno działa, jak użytkownicy wchodzą z nim interakcji.</span><span class="sxs-lookup"><span data-stu-id="34f40-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="34f40-129">W WPF WPF, można zaimplementować wygląd [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i zachowanie okna przy użyciu kodu lub znaczników.</span><span class="sxs-lookup"><span data-stu-id="34f40-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="34f40-130">Ogólnie rzecz biorąc jednak wygląd okna jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementowany przy użyciu znaczników, a jego zachowanie jest implementowane przy użyciu kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="34f40-131">Aby włączyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do współpracy plik znaczników i plik związany z kodem, wymagane są następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="34f40-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="34f40-132">W znacznikach `Window` element musi `x:Class` zawierać atrybut.</span><span class="sxs-lookup"><span data-stu-id="34f40-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="34f40-133">Po utworzeniu aplikacji, istnienie `x:Class` w pliku znaczników powoduje, że aparat kompilacji `partial` firmy Microsoft (MSBuild) do utworzenia klasy, która pochodzi od <xref:System.Windows.Window> i ma nazwę, która jest określona przez `x:Class` atrybut.</span><span class="sxs-lookup"><span data-stu-id="34f40-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="34f40-134">Wymaga to dodania deklaracji obszaru nazw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XML `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` dla schematu ( ).</span><span class="sxs-lookup"><span data-stu-id="34f40-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="34f40-135">Wygenerowana `partial` klasa implementuje `InitializeComponent` metodę, która jest wywoływana do rejestrowania zdarzeń i ustawiania właściwości, które są implementowane w znacznikach.</span><span class="sxs-lookup"><span data-stu-id="34f40-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="34f40-136">W kodzie po zakoduje `partial` się klasa musi być klasą o tej samej nazwie, która jest określona przez `x:Class` atrybut w znacznikach i musi pochodzić od <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="34f40-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="34f40-137">Dzięki temu plik związany z kodem `partial` ma być skojarzony z klasą, która jest generowana dla pliku znaczników podczas tworzenia aplikacji (zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="34f40-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="34f40-138">W przypadku kodu <xref:System.Windows.Window> po zakodowaniu klasa musi `InitializeComponent` implementować konstruktora, który wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="34f40-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="34f40-139">`InitializeComponent`jest implementowana przez klasę wygenerowaną `partial` pliku znaczników, aby zarejestrować zdarzenia i ustawić właściwości, które są zdefiniowane w znacznikach.</span><span class="sxs-lookup"><span data-stu-id="34f40-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-140">Po dodaniu <xref:System.Windows.Window> nowego do projektu przy użyciu <xref:System.Windows.Window> programu Visual Studio, jest zaimplementowana przy użyciu znaczników i związanych z kodem i zawiera konfigurację niezbędną do utworzenia skojarzenia między znaczników i plików związanych z kodem, jak opisano poniżej.</span><span class="sxs-lookup"><span data-stu-id="34f40-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="34f40-141">Z tej konfiguracji w miejscu, można skupić się [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na definiowaniu wygląd okna w znacznikach i implementacji jego zachowanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="34f40-142">Poniższy przykład pokazuje okno z przyciskiem, zaimplementowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznikach <xref:System.Windows.Controls.Primitives.ButtonBase.Click> i program obsługi zdarzeń dla zdarzenia przycisku, zaimplementowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="34f40-143">Konfigurowanie definicji okna dla usługi MSBuild</span><span class="sxs-lookup"><span data-stu-id="34f40-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="34f40-144">Sposób implementowania okna określa, jak jest skonfigurowany dla MSBuild.</span><span class="sxs-lookup"><span data-stu-id="34f40-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="34f40-145">Dla okna, które jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdefiniowane przy użyciu znaczników i związanych z kodem:</span><span class="sxs-lookup"><span data-stu-id="34f40-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="34f40-146">Pliki znaczników XAML są skonfigurowane `Page` jako elementy MSBuild.</span><span class="sxs-lookup"><span data-stu-id="34f40-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="34f40-147">Pliki związane z kodem są skonfigurowane jako elementy MSBuild. `Compile`</span><span class="sxs-lookup"><span data-stu-id="34f40-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="34f40-148">Jest to pokazane w następującym pliku projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="34f40-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="34f40-149">Aby uzyskać informacje na temat tworzenia aplikacji WPF, zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="34f40-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="34f40-150">Okres istnienia okna</span><span class="sxs-lookup"><span data-stu-id="34f40-150">Window Lifetime</span></span>  
 <span data-ttu-id="34f40-151">Podobnie jak w przypadku każdej klasy, okno ma okres istnienia, który rozpoczyna się, gdy jest po raz pierwszy wystąpienia, po czym jest otwierany, aktywowany i dezaktywowany, a ostatecznie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="34f40-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="34f40-152">Otwieranie okna</span><span class="sxs-lookup"><span data-stu-id="34f40-152">Opening a Window</span></span>  
 <span data-ttu-id="34f40-153">Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, co zostanie zademonstrowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="34f40-154">W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone podczas uruchamiania aplikacji, <xref:System.Windows.Application.Startup> która występuje, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="34f40-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="34f40-155">Po wystąpieniu okna odwołanie do niego jest automatycznie dodawane do listy okien <xref:System.Windows.Application> zarządzanych <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>przez obiekt (patrz ).</span><span class="sxs-lookup"><span data-stu-id="34f40-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="34f40-156">Ponadto pierwsze okno, które ma zostać utworzone, jest <xref:System.Windows.Application> domyślnie ustawione jako <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>główne okno aplikacji (patrz ).</span><span class="sxs-lookup"><span data-stu-id="34f40-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="34f40-157">Okno jest ostatecznie otwierane <xref:System.Windows.Window.Show%2A> przez wywołanie metody; wynik jest pokazany na poniższym rysunku.</span><span class="sxs-lookup"><span data-stu-id="34f40-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Okno otwarte przez wywołanie Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="34f40-159">Okno, które jest <xref:System.Windows.Window.Show%2A> otwierane przez wywołanie jest niemodne okno, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-160"><xref:System.Windows.Window.ShowDialog%2A>jest wywoływana do otwierania okien, takich jak okna dialogowe modnie.</span><span class="sxs-lookup"><span data-stu-id="34f40-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="34f40-161">Zobacz [omówienie okien dialogowych, aby](dialog-boxes-overview.md) uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="34f40-162">Po <xref:System.Windows.Window.Show%2A> wywołaniu okno wykonuje pracę inicjowania, zanim zostanie wyświetlone do ustanowienia infrastruktury, która umożliwia odbieranie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34f40-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="34f40-163">Po zainicjowaniu okna <xref:System.Windows.Window.SourceInitialized> zdarzenie jest wywoływane i wyświetlane jest okno.</span><span class="sxs-lookup"><span data-stu-id="34f40-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="34f40-164">Jako skrót <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, które jest otwierane automatycznie po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="34f40-165">Po uruchomieniu aplikacji okno określone przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwierane bez trybu; wewnętrznie okno jest otwierane przez <xref:System.Windows.Window.Show%2A> wywołanie jego metody.</span><span class="sxs-lookup"><span data-stu-id="34f40-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="34f40-166">Własność okna</span><span class="sxs-lookup"><span data-stu-id="34f40-166">Window Ownership</span></span>  
 <span data-ttu-id="34f40-167">Okno, które jest otwierane przy użyciu <xref:System.Windows.Window.Show%2A> metody nie ma niejawnej relacji z oknem, które go utworzyło; użytkownicy mogą wchodzić w interakcje z każdym z okien niezależnie od drugiego, co oznacza, że w każdym oknie można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="34f40-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="34f40-168">Zakryj drugi (chyba że <xref:System.Windows.Window.Topmost%2A> jedno z `true`okien ma ustawioną właściwość).</span><span class="sxs-lookup"><span data-stu-id="34f40-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="34f40-169">Być zminimalizowane, zmaksymalizowane i przywrócone bez wpływu na inne.</span><span class="sxs-lookup"><span data-stu-id="34f40-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="34f40-170">Niektóre okna wymagają relacji z oknem, które je otwiera.</span><span class="sxs-lookup"><span data-stu-id="34f40-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="34f40-171">Na przykład aplikacja ide (Integrated Development Environment) może otworzyć okna właściwości i okna narzędzi, których typowym zachowaniem jest pokrycie okna, które je tworzy.</span><span class="sxs-lookup"><span data-stu-id="34f40-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="34f40-172">Ponadto takie okna powinny zawsze zamykać, minimalizować, maksymalizować i przywracać w porozumieniu z utworzonym ich oknem.</span><span class="sxs-lookup"><span data-stu-id="34f40-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="34f40-173">Taki związek można ustanowić, tworząc jedno okno *własne* drugie i <xref:System.Windows.Window.Owner%2A> uzyskuje się poprzez ustawienie właściwości *okna należącego* do właściciela z odniesieniem do *okna właściciela*.</span><span class="sxs-lookup"><span data-stu-id="34f40-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="34f40-174">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="34f40-175">Po ustanowieniu własności:</span><span class="sxs-lookup"><span data-stu-id="34f40-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="34f40-176">Okno należące do właściciela może odwoływać się <xref:System.Windows.Window.Owner%2A> do okna właściciela, sprawdzając wartość jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="34f40-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="34f40-177">Okno właściciela może odnajdować wszystkie okna, <xref:System.Windows.Window.OwnedWindows%2A> które posiada, sprawdzając wartość jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="34f40-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="34f40-178">Zapobieganie aktywacji okna</span><span class="sxs-lookup"><span data-stu-id="34f40-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="34f40-179">Istnieją scenariusze, w których okna nie powinny być aktywowane, gdy są wyświetlane, takie jak okna konwersacji aplikacji w stylu komunikatora internetowego lub okna powiadomień aplikacji poczty e-mail.</span><span class="sxs-lookup"><span data-stu-id="34f40-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="34f40-180">Jeśli aplikacja ma okno, które nie powinny być aktywowane, <xref:System.Windows.Window.ShowActivated%2A> gdy `false` jest <xref:System.Windows.Window.Show%2A> wyświetlany, można ustawić jego właściwości przed wywołaniem metody po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="34f40-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="34f40-181">W konsekwencji:</span><span class="sxs-lookup"><span data-stu-id="34f40-181">As a consequence:</span></span>  
  
- <span data-ttu-id="34f40-182">Okno nie jest aktywowane.</span><span class="sxs-lookup"><span data-stu-id="34f40-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="34f40-183"><xref:System.Windows.Window.Activated> Zdarzenie okna nie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="34f40-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="34f40-184">Aktualnie aktywowane okno pozostaje aktywowane.</span><span class="sxs-lookup"><span data-stu-id="34f40-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="34f40-185">Okno zostanie aktywowane, jednak, jak tylko użytkownik aktywuje go, klikając albo klienta lub obszaru nie-klienta.</span><span class="sxs-lookup"><span data-stu-id="34f40-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="34f40-186">W takim przypadku:</span><span class="sxs-lookup"><span data-stu-id="34f40-186">In this case:</span></span>  
  
- <span data-ttu-id="34f40-187">Okno jest aktywne.</span><span class="sxs-lookup"><span data-stu-id="34f40-187">The window is activated.</span></span>  
  
- <span data-ttu-id="34f40-188"><xref:System.Windows.Window.Activated> Zdarzenie okna jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="34f40-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="34f40-189">Wcześniej aktywowane okno zostanie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="34f40-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="34f40-190">Okna <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> zdarzenia są następnie wywoływane zgodnie z oczekiwaniami w odpowiedzi na akcje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34f40-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="34f40-191">Aktywacja okna</span><span class="sxs-lookup"><span data-stu-id="34f40-191">Window Activation</span></span>  
 <span data-ttu-id="34f40-192">Po pierwszym otwarciu okna staje się ono aktywnym <xref:System.Windows.Window.ShowActivated%2A> oknem (chyba że jest wyświetlane z ustawionym na `false`).</span><span class="sxs-lookup"><span data-stu-id="34f40-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="34f40-193">*Aktywne okno* jest oknem, które aktualnie przechwytuje dane wejściowe użytkownika, takie jak naciśnięcia klawiszy i kliknięcia myszą.</span><span class="sxs-lookup"><span data-stu-id="34f40-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="34f40-194">Gdy okno staje się aktywne, <xref:System.Windows.Window.Activated> wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="34f40-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-195">Po pierwszym otwarciu okna <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> i zdarzenia są <xref:System.Windows.Window.Activated> wywoływane tylko po wywoływaniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="34f40-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="34f40-196">Mając to na uwadze, okno można <xref:System.Windows.Window.ContentRendered> skutecznie uznać za otwarte, gdy jest podnoszone.</span><span class="sxs-lookup"><span data-stu-id="34f40-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="34f40-197">Gdy okno stanie się aktywne, użytkownik może aktywować inne okno w tej samej aplikacji lub aktywować inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="34f40-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="34f40-198">W takim przypadku aktualnie aktywne okno zostanie dezaktywowane i wywołuje <xref:System.Windows.Window.Deactivated> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="34f40-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="34f40-199">Podobnie, gdy użytkownik wybierze aktualnie dezaktywowane okno, <xref:System.Windows.Window.Activated> okno staje się aktywne ponownie i jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="34f40-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="34f40-200">Jednym z typowych powodów do obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest włączenie i wyłączenie funkcji, które można uruchomić tylko wtedy, gdy okno jest aktywne.</span><span class="sxs-lookup"><span data-stu-id="34f40-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="34f40-201">Na przykład niektóre systemy Windows wyświetlają interaktywną zawartość, która wymaga stałego wprowadzania danych przez użytkownika lub uwagi, w tym gier i odtwarzaczy wideo.</span><span class="sxs-lookup"><span data-stu-id="34f40-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="34f40-202">Poniższy przykład jest uproszczony odtwarzacz wideo, <xref:System.Windows.Window.Activated> który <xref:System.Windows.Window.Deactivated> pokazuje, jak obsługiwać i zaimplementować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="34f40-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="34f40-203">Inne typy aplikacji mogą nadal uruchamiać kod w tle, gdy okno jest dezaktywowane.</span><span class="sxs-lookup"><span data-stu-id="34f40-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="34f40-204">Na przykład klient poczty może kontynuować sondowanie serwera poczty, gdy użytkownik korzysta z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="34f40-205">Aplikacje takie jak te często zapewniają różne lub dodatkowe zachowanie, gdy okno główne jest dezaktywowane.</span><span class="sxs-lookup"><span data-stu-id="34f40-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="34f40-206">W odniesieniu do programu pocztowego może to oznaczać zarówno dodanie nowego elementu poczty do skrzynki odbiorczej, jak i dodanie ikony powiadomień do zasobnika systemowego.</span><span class="sxs-lookup"><span data-stu-id="34f40-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="34f40-207">Ikona powiadomień musi być wyświetlana tylko wtedy, gdy okno poczty nie <xref:System.Windows.Window.IsActive%2A> jest aktywne, co można określić, sprawdzając właściwość.</span><span class="sxs-lookup"><span data-stu-id="34f40-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="34f40-208">Jeśli zadanie w tle zostanie ukończone, okno może chcieć <xref:System.Windows.Window.Activate%2A> powiadomić użytkownika pilniej, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="34f40-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="34f40-209">Jeśli użytkownik wchodzi w interakcję z <xref:System.Windows.Window.Activate%2A> inną aplikacją aktywowany, gdy jest wywoływana, przycisk paska zadań okna miga.</span><span class="sxs-lookup"><span data-stu-id="34f40-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="34f40-210">Jeśli użytkownik wchodzi w interakcję z <xref:System.Windows.Window.Activate%2A> bieżącą aplikacją, wywołanie spowoduje wyświetlenie okna na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="34f40-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-211">Można obsługiwać aktywacji zakresu <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> aplikacji przy użyciu i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="34f40-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="34f40-212">Zamykanie okna</span><span class="sxs-lookup"><span data-stu-id="34f40-212">Closing a Window</span></span>  
 <span data-ttu-id="34f40-213">Życie okna zaczyna się kończyć, gdy użytkownik go zamknie.</span><span class="sxs-lookup"><span data-stu-id="34f40-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="34f40-214">Okno można zamknąć przy użyciu elementów w obszarze nienakładowym, w tym następujących:</span><span class="sxs-lookup"><span data-stu-id="34f40-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="34f40-215">Pozycja **Zamknij** menu **System.**</span><span class="sxs-lookup"><span data-stu-id="34f40-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="34f40-216">Naciśnięcie klawisza ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="34f40-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="34f40-217">Naciśnięcie przycisku **Zamknij.**</span><span class="sxs-lookup"><span data-stu-id="34f40-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="34f40-218">Można podać dodatkowe mechanizmy do obszaru klienta, aby zamknąć okno, z których bardziej powszechne są następujące:</span><span class="sxs-lookup"><span data-stu-id="34f40-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="34f40-219">Element **Zakończ** w menu **Plik,** zazwyczaj dla okien aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="34f40-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="34f40-220">A **Zamknij** element w **menu Plik,** zazwyczaj w oknie aplikacji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="34f40-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="34f40-221">Przycisk **Anuluj,** zazwyczaj w oknie dialogowym modalnego.</span><span class="sxs-lookup"><span data-stu-id="34f40-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="34f40-222">Przycisk **Zamknij,** zazwyczaj w niemodytnym oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="34f40-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="34f40-223">Aby zamknąć okno w odpowiedzi na jeden z tych <xref:System.Windows.Window.Close%2A> mechanizmów niestandardowych, należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="34f40-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="34f40-224">Poniższy przykład implementuje możliwość zamknięcia okna, wybierając **Exit** w **menu Plik.**</span><span class="sxs-lookup"><span data-stu-id="34f40-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="34f40-225">Po zamknięciu okna wywołuje dwa <xref:System.Windows.Window.Closing> zdarzenia: <xref:System.Windows.Window.Closed>i .</span><span class="sxs-lookup"><span data-stu-id="34f40-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="34f40-226"><xref:System.Windows.Window.Closing>jest podniesiona przed zamknięciem okna i zapewnia mechanizm, za pomocą którego można zapobiec zamknięciu okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="34f40-227">Częstym powodem, aby zapobiec zamknięciu okna jest, jeśli zawartość okna zawiera zmodyfikowane dane.</span><span class="sxs-lookup"><span data-stu-id="34f40-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="34f40-228">W tej sytuacji <xref:System.Windows.Window.Closing> zdarzenie może być obsługiwane w celu ustalenia, czy dane są zabrudzone, a jeśli tak, aby zapytać użytkownika, czy kontynuować zamykanie okna bez zapisywania danych lub anulować zamknięcie okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="34f40-229">W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="34f40-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="34f40-230">Program <xref:System.Windows.Window.Closing> obsługi zdarzeń <xref:System.ComponentModel.CancelEventArgs>jest przekazywany `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> a , `true` który implementuje właściwość, która jest ustawiona, aby zapobiec zamknięciu okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="34f40-231">Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwany lub jest obsługiwany, ale nie został anulowany, okno zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="34f40-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="34f40-232">Tuż przed zamknięciem okna, <xref:System.Windows.Window.Closed> jest podniesiony.</span><span class="sxs-lookup"><span data-stu-id="34f40-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="34f40-233">W tym momencie nie można zapobiec zamknięciu okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-234">Aplikację można skonfigurować tak, aby zamykała się automatycznie po zamknięciu głównego okna aplikacji (patrz) <xref:System.Windows.Application.MainWindow%2A>lub zamknięciu ostatniego okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="34f40-235">Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="34f40-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="34f40-236">Podczas gdy okno może być jawnie zamknięte za pomocą mechanizmów podanych w obszarach innych niż klient i klient, okno może być również niejawnie zamknięte w wyniku zachowania w innych częściach aplikacji lub systemu Windows, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="34f40-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="34f40-237">Użytkownik wylogowuje się lub wyłącza system Windows.</span><span class="sxs-lookup"><span data-stu-id="34f40-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="34f40-238">Właściciel okna zamyka (patrz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="34f40-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="34f40-239">Główne okno aplikacji jest <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>zamknięte i jest .</span><span class="sxs-lookup"><span data-stu-id="34f40-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="34f40-240"><xref:System.Windows.Application.Shutdown%2A>nazywa się.</span><span class="sxs-lookup"><span data-stu-id="34f40-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-241">Nie można ponownie otworzyć okna po jego zamknięciu.</span><span class="sxs-lookup"><span data-stu-id="34f40-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="34f40-242">Zdarzenia okresu istnienia okna</span><span class="sxs-lookup"><span data-stu-id="34f40-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="34f40-243">Na poniższej ilustracji przedstawiono sekwencję głównych zdarzeń w okresie istnienia okna:</span><span class="sxs-lookup"><span data-stu-id="34f40-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram, który pokazuje zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="34f40-245">Na poniższej ilustracji przedstawiono sekwencję głównych zdarzeń w okresie<xref:System.Windows.Window.ShowActivated%2A> istnienia okna, które jest wyświetlane bez aktywacji ( jest ustawiona na `false` przed wyświetleniem okna):</span><span class="sxs-lookup"><span data-stu-id="34f40-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram, który pokazuje zdarzenia w okresie istnienia okna bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="34f40-247">Lokalizacja okna</span><span class="sxs-lookup"><span data-stu-id="34f40-247">Window Location</span></span>  
 <span data-ttu-id="34f40-248">Gdy okno jest otwarte, ma lokalizację w wymiarach x i y względem pulpitu.</span><span class="sxs-lookup"><span data-stu-id="34f40-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="34f40-249">Lokalizację tę można określić, <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> sprawdzając odpowiednio właściwości i.</span><span class="sxs-lookup"><span data-stu-id="34f40-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="34f40-250">Można ustawić te właściwości, aby zmienić lokalizację okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="34f40-251">Można również określić początkową <xref:System.Windows.Window> lokalizację, kiedy pojawia <xref:System.Windows.Window.WindowStartupLocation%2A> się po raz <xref:System.Windows.WindowStartupLocation> pierwszy, ustawiając właściwość z jedną z następujących wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="34f40-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="34f40-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="34f40-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="34f40-253">Jeśli lokalizacja uruchamiania <xref:System.Windows.WindowStartupLocation.Manual>jest określona <xref:System.Windows.Window.Top%2A> jako , a <xref:System.Windows.Window> <xref:System.Windows.Window.Left%2A> właściwości i właściwości nie zostały ustawione, poprosi system Windows o wyświetlenie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="34f40-254">Najwyższa część systemu Windows i z-order</span><span class="sxs-lookup"><span data-stu-id="34f40-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="34f40-255">Oprócz lokalizacji x i y, okno ma również lokalizację w wymiarze z, która określa jego pionową pozycję względem innych okien.</span><span class="sxs-lookup"><span data-stu-id="34f40-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="34f40-256">Jest to znane jako okno z-order i istnieją dwa typy: normalny z-order i najwyższej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="34f40-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="34f40-257">Lokalizacja okna w *normalnej kolejności z* zależy od tego, czy jest ono aktualnie aktywne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="34f40-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="34f40-258">Domyślnie okno znajduje się w normalnej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="34f40-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="34f40-259">Lokalizacja okna w *najwyższej kolejności z* zależy również od tego, czy jest ono aktualnie aktywne, czy nie.</span><span class="sxs-lookup"><span data-stu-id="34f40-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="34f40-260">Ponadto okna w najwyższej kolejności z zawsze znajdują się nad oknami w normalnej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="34f40-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="34f40-261">Okno znajduje się w najwyższej kolejności z, ustawiając jego <xref:System.Windows.Window.Topmost%2A> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="34f40-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="34f40-262">W ramach każdego zamówienia z aktualnie aktywne okno pojawia się nad wszystkimi innymi oknami w tej samej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="34f40-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="34f40-263">Rozmiar okna</span><span class="sxs-lookup"><span data-stu-id="34f40-263">Window Size</span></span>  
 <span data-ttu-id="34f40-264">Oprócz lokalizacji pulpitu, okno ma rozmiar, który jest określany przez kilka właściwości, <xref:System.Windows.Window.SizeToContent%2A>w tym różne właściwości szerokości i wysokości i .</span><span class="sxs-lookup"><span data-stu-id="34f40-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="34f40-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.MaxWidth%2A> są używane do zarządzania zakresem szerokości, które okno może mieć w okresie jego istnienia i są skonfigurowane w sposób pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="34f40-266">Wysokość okna jest <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Height%2A>zarządzana <xref:System.Windows.FrameworkElement.MaxHeight%2A>przez program , i , i są skonfigurowane w sposób pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34f40-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="34f40-267">Ponieważ różne wartości szerokości i wartości wysokości określają zakres, możliwe jest, aby szerokość i wysokość okna o zmiennym rozmiarze były dostępne w dowolnym miejscu w określonym zakresie dla odpowiedniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="34f40-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="34f40-268">Aby wykryć jego aktualną szerokość i wysokość, należy sprawdzić <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="34f40-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="34f40-269">Jeśli chcesz, aby szerokość i wysokość okna miały rozmiar, który pasuje do rozmiaru zawartości okna, <xref:System.Windows.Window.SizeToContent%2A> możesz użyć właściwości, która ma następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="34f40-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="34f40-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="34f40-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="34f40-271">Brak efektu (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="34f40-271">No effect (default).</span></span>  
  
- <span data-ttu-id="34f40-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="34f40-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="34f40-273">Dopasuj do szerokości zawartości, która <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> ma taki sam efekt jak ustawienie zarówno do szerokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="34f40-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="34f40-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="34f40-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="34f40-275">Dopasuj do wysokości zawartości, która <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> ma taki sam efekt jak ustawienie zarówno na wysokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="34f40-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="34f40-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="34f40-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="34f40-277">Dopasuj do szerokości i wysokości zawartości, <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> która ma taki sam efekt <xref:System.Windows.FrameworkElement.MinWidth%2A> jak <xref:System.Windows.FrameworkElement.MaxWidth%2A> ustawienie zarówno na wysokości zawartości, jak i ustawienie zarówno szerokości, jak i szerokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="34f40-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="34f40-278">W poniższym przykładzie przedstawiono okno, które automatycznie rozmiary, aby dopasować jego zawartość, zarówno w pionie, jak i w poziomie, po raz pierwszy pokazano.</span><span class="sxs-lookup"><span data-stu-id="34f40-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="34f40-279">W poniższym przykładzie <xref:System.Windows.Window.SizeToContent%2A> pokazano, jak ustawić właściwość w kodzie, aby określić, jak okno jest resizes, aby dopasować jego zawartość .</span><span class="sxs-lookup"><span data-stu-id="34f40-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="34f40-280">Kolejność pierwszeństwa dla właściwości zmiany rozmiaru</span><span class="sxs-lookup"><span data-stu-id="34f40-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="34f40-281">Zasadniczo różne rozmiary właściwości okna łączą się w celu zdefiniowania zakresu szerokości i wysokości dla okna o zmiennym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="34f40-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="34f40-282">Aby upewnić się, <xref:System.Windows.Window> że prawidłowy zakres jest utrzymywany, ocenia wartości właściwości rozmiaru przy użyciu następujących zamówień pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="34f40-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="34f40-283">**Dla właściwości wysokości:**</span><span class="sxs-lookup"><span data-stu-id="34f40-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="34f40-284">**W przypadku właściwości szerokości:**</span><span class="sxs-lookup"><span data-stu-id="34f40-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="34f40-285">Kolejność pierwszeństwa można również określić rozmiar okna, gdy jest zmaksymalizowane, <xref:System.Windows.Window.WindowState%2A> który jest zarządzany z właściwością.</span><span class="sxs-lookup"><span data-stu-id="34f40-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="34f40-286">Stan okna</span><span class="sxs-lookup"><span data-stu-id="34f40-286">Window State</span></span>  
 <span data-ttu-id="34f40-287">W okresie istnienia okna o zmiennym rozmiarze może mieć trzy stany: normalny, zminimalizowany i zmaksymalizowany.</span><span class="sxs-lookup"><span data-stu-id="34f40-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="34f40-288">Okno o stanie *normalnym* jest domyślnym stanem okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="34f40-289">Okno z tym stanem umożliwia użytkownikowi przenoszenie i zmienianie jego rozmiaru za pomocą uchwytu o rozmiarze lub obramowania, jeśli można go zmienić rozmiar.</span><span class="sxs-lookup"><span data-stu-id="34f40-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="34f40-290">Okno z *zminimalizowanym* stanem zwija się <xref:System.Windows.Window.ShowInTaskbar%2A> do przycisku paska zadań, jeśli jest ustawione na `true`; w przeciwnym razie zwija się do najmniejszego możliwego rozmiaru i przenosi się do lewego dolnego rogu pulpitu.</span><span class="sxs-lookup"><span data-stu-id="34f40-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="34f40-291">Żaden typ zminimalizowanego okna nie może być przesunięty za pomocą obramowania lub uchwytu o rozmiarze, chociaż zminimalizowane okno, które nie jest wyświetlane na pasku zadań, można przeciągać wokół pulpitu.</span><span class="sxs-lookup"><span data-stu-id="34f40-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="34f40-292">Okno o *stanie zmaksymalizowanym* rozszerza się do maksymalnego rozmiaru, który może <xref:System.Windows.FrameworkElement.MaxWidth%2A>być, który będzie tylko tak duży, jak jego , <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.Window.SizeToContent%2A> właściwości dyktować.</span><span class="sxs-lookup"><span data-stu-id="34f40-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="34f40-293">Podobnie jak zminimalizowane okno, zmaksymalizowanego okna nie można zmienić rozmiaru za pomocą uchwytu zmienić rozmiar lub przeciągając obramowanie.</span><span class="sxs-lookup"><span data-stu-id="34f40-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f40-294">Wartości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.Height%2A> właściwości okna zawsze reprezentują wartości dla stanu normalnego, nawet wtedy, gdy okno jest obecnie zmaksymalizowane lub zminimalizowane.</span><span class="sxs-lookup"><span data-stu-id="34f40-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="34f40-295">Stan okna można skonfigurować, ustawiając <xref:System.Windows.Window.WindowState%2A> jego właściwość, która <xref:System.Windows.WindowState> może mieć jedną z następujących wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="34f40-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="34f40-296"><xref:System.Windows.WindowState.Normal>(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="34f40-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="34f40-297">W poniższym przykładzie pokazano, jak utworzyć okno, które jest wyświetlane jako zmaksymalizowane po otwarciu.</span><span class="sxs-lookup"><span data-stu-id="34f40-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="34f40-298">Ogólnie rzecz biorąc <xref:System.Windows.Window.WindowState%2A> należy ustawić, aby skonfigurować stan początkowy okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="34f40-299">Po wyświetleniu okna o zmiennym rozmiarze użytkownicy mogą nacisnąć przyciski minimalizowanie, maksymalizacja i przywracanie na pasku tytułu okna, aby zmienić stan okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="34f40-300">Wygląd okna</span><span class="sxs-lookup"><span data-stu-id="34f40-300">Window Appearance</span></span>  
 <span data-ttu-id="34f40-301">Wygląd obszaru klienta okna można zmienić, dodając do niego zawartość specyficzną dla okien, taką jak przyciski, etykiety i pola tekstowe.</span><span class="sxs-lookup"><span data-stu-id="34f40-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="34f40-302">Aby skonfigurować obszar nie-klient, <xref:System.Windows.Window> zawiera kilka <xref:System.Windows.Window.Icon%2A> właściwości, które obejmują, <xref:System.Windows.Window.Title%2A> aby ustawić ikonę okna i ustawić jego tytuł.</span><span class="sxs-lookup"><span data-stu-id="34f40-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="34f40-303">Można również zmienić wygląd i zachowanie obramowania obszaru nienaksingowego, konfigurując tryb zmiany rozmiaru okna, styl okna i to, czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.</span><span class="sxs-lookup"><span data-stu-id="34f40-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="34f40-304">Tryb ponownego rozmiaru</span><span class="sxs-lookup"><span data-stu-id="34f40-304">Resize Mode</span></span>  
 <span data-ttu-id="34f40-305">W zależności <xref:System.Windows.Window.WindowStyle%2A> od właściwości można kontrolować, jak (i czy) użytkownicy mogą zmienić rozmiar okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="34f40-306">Wybór stylu okna wpływa na to, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowanie za pomocą myszy, czy przyciski **Minimalizuj**, **Maksymalizuj**i **Zmienić rozmiar** są wyświetlane w obszarze nienawidalnym, a jeśli są wyświetlane, czy są włączone.</span><span class="sxs-lookup"><span data-stu-id="34f40-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="34f40-307">Można skonfigurować sposób ponownego rozmiaru okna, <xref:System.Windows.Window.ResizeMode%2A> ustawiając jego właściwość, <xref:System.Windows.ResizeMode> która może być jedną z następujących wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="34f40-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="34f40-308"><xref:System.Windows.ResizeMode.CanResize>(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="34f40-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="34f40-309">Podobnie <xref:System.Windows.Window.WindowStyle%2A>jak w przypadku trybu zmiany rozmiaru okna jest mało prawdopodobne, aby zmienić w okresie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jego istnienia, co oznacza, że najprawdopodobniej ustawić go z znaczników.</span><span class="sxs-lookup"><span data-stu-id="34f40-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="34f40-310">Należy zauważyć, że można wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone przez sprawdzenie <xref:System.Windows.Window.WindowState%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="34f40-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="34f40-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="34f40-311">Window Style</span></span>  
 <span data-ttu-id="34f40-312">Obramowanie, które jest widoczne z obszaru nie-klienta okna jest odpowiedni dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="34f40-313">Istnieją jednak okoliczności, w których potrzebne są różne rodzaje granic lub w ogóle nie są potrzebne granice, w zależności od rodzaju okna.</span><span class="sxs-lookup"><span data-stu-id="34f40-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="34f40-314">Aby kontrolować typ obramowania okna, <xref:System.Windows.Window.WindowStyle%2A> należy ustawić jego właściwość <xref:System.Windows.WindowStyle> z jedną z następujących wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="34f40-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="34f40-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>(domyślnie)</span><span class="sxs-lookup"><span data-stu-id="34f40-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="34f40-316">Efekt tych stylów okien są zilustrowane na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="34f40-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustracja stylów obramowania okien.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="34f40-318">Można ustawić <xref:System.Windows.Window.WindowStyle%2A> za [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocą znaczników lub kodu; ponieważ jest mało prawdopodobne, aby zmienić w okresie istnienia okna, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] najprawdopodobniej skonfigurujesz go przy użyciu znaczników.</span><span class="sxs-lookup"><span data-stu-id="34f40-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="34f40-319">Styl okna niekularnego</span><span class="sxs-lookup"><span data-stu-id="34f40-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="34f40-320">Istnieją również sytuacje, w <xref:System.Windows.Window.WindowStyle%2A> których style obramowania, które pozwala mieć nie są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="34f40-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="34f40-321">Na przykład można utworzyć aplikację z niesektorycznym obramowaniem, na przykład używa microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="34f40-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="34f40-322">Rozważmy na przykład okno dymka pokazane na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="34f40-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno dymne z napisem Przeciągnij mnie.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="34f40-324">Ten typ okna można utworzyć, <xref:System.Windows.Window.WindowStyle%2A> ustawiając właściwość na <xref:System.Windows.WindowStyle.None> <xref:System.Windows.Window> , i używając specjalnej obsługi, która ma przezroczystość.</span><span class="sxs-lookup"><span data-stu-id="34f40-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="34f40-325">Ta kombinacja wartości nakazuje okno do renderowania całkowicie przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="34f40-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="34f40-326">W tym stanie nie można używać ozdób obszaru nienakładowego okna (menu Zamknij, Minimalizuj, Maksymalizuj i Przywróć i przywróć) itd.In this state the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span><span class="sxs-lookup"><span data-stu-id="34f40-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="34f40-327">W związku z tym, trzeba podać własne.</span><span class="sxs-lookup"><span data-stu-id="34f40-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="34f40-328">Obecność paska zadań</span><span class="sxs-lookup"><span data-stu-id="34f40-328">Task Bar Presence</span></span>  

<span data-ttu-id="34f40-329">Domyślny wygląd okna zawiera przycisk paska zadań, taki jak pokazany na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="34f40-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Zrzut ekranu przedstawiający okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="34f40-331">Niektóre typy okien nie mają przycisku paska zadań, na przykład okien komunikatów i okien dialogowych (zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="34f40-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="34f40-332">Można kontrolować, czy przycisk paska zadań dla <xref:System.Windows.Window.ShowInTaskbar%2A> okna`true` jest wyświetlany, ustawiając właściwość (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="34f40-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="34f40-333">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="34f40-333">Security Considerations</span></span>  
 <span data-ttu-id="34f40-334"><xref:System.Windows.Window>wymaga `UnmanagedCode` uzyskania uprawnień zabezpieczających do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34f40-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="34f40-335">W przypadku aplikacji zainstalowanych i uruchomionych z komputera lokalnego mieszczą się w zestawie uprawnień przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34f40-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="34f40-336">Jednak nie mieści się to w zestawie uprawnień przyznanych aplikacjom uruchamianym z Internetu lub lokalnej strefy intranetu przy użyciu ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="34f40-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="34f40-337">W związku z tym użytkownicy otrzymają ostrzeżenie zabezpieczeń ClickOnce i będzie musiał podnieść zestaw uprawnień dla aplikacji do pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="34f40-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="34f40-338">Ponadto xbaps nie może domyślnie wyświetlać okien ani okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="34f40-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="34f40-339">Aby zapoznać się z omówieniem zagadnień dotyczących bezpieczeństwa aplikacji autonomicznych, zobacz [Strategia zabezpieczeń WPF — Zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="34f40-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="34f40-340">Inne typy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="34f40-340">Other Types of Windows</span></span>  
 <span data-ttu-id="34f40-341"><xref:System.Windows.Navigation.NavigationWindow>to okno przeznaczone do obsługi zawartości żeglownej.</span><span class="sxs-lookup"><span data-stu-id="34f40-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="34f40-342">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="34f40-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="34f40-343">Okna dialogowe są okna, które są często używane do zbierania informacji od użytkownika, aby zakończyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="34f40-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="34f40-344">Na przykład, gdy użytkownik chce otworzyć plik, okno dialogowe **Otwórz plik** jest zwykle wyświetlane przez aplikację, aby uzyskać nazwę pliku od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34f40-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="34f40-345">Aby uzyskać więcej informacji, zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34f40-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f40-346">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34f40-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="34f40-347">Okna dialogowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="34f40-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="34f40-348">Kompilowanie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="34f40-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
