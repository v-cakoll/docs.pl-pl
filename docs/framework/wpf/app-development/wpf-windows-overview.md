---
title: Przegląd systemu Windows
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
ms.openlocfilehash: 17582192fabf85777bba250f6f53047a84f264b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742360"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="0cde3-102">Przegląd Okna WPF</span><span class="sxs-lookup"><span data-stu-id="0cde3-102">WPF Windows Overview</span></span>
<span data-ttu-id="0cde3-103">Użytkownicy pracują z autonomicznymi aplikacjami Windows Presentation Foundation (WPF) za pomocą systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0cde3-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="0cde3-104">Głównym celem okna jest hostowanie zawartości, która wizualizuje dane i umożliwia użytkownikom współdziałanie z danymi.</span><span class="sxs-lookup"><span data-stu-id="0cde3-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="0cde3-105">Autonomiczne aplikacje WPF zapewniają własne okna przy użyciu klasy <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="0cde3-106">Ten temat zawiera wprowadzenie <xref:System.Windows.Window> przed rozpoczęciem omawiania podstaw tworzenia i zarządzania oknami w aplikacjach autonomicznych.</span><span class="sxs-lookup"><span data-stu-id="0cde3-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-107">Hostowane w przeglądarce aplikacje WPF, w tym aplikacje przeglądarki XAML (XBAP) i luźno [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, nie zapewniają własnych okien.</span><span class="sxs-lookup"><span data-stu-id="0cde3-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="0cde3-108">Zamiast tego są one hostowane w systemie Windows udostępnianym przez program Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0cde3-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="0cde3-109">Zobacz [Omówienie aplikacji przeglądarki XAML w języku WPF](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0cde3-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="0cde3-110">Klasa okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-110">The Window Class</span></span>  
 <span data-ttu-id="0cde3-111">Na poniższej ilustracji przedstawiono części składowe okna:</span><span class="sxs-lookup"><span data-stu-id="0cde3-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Zrzut ekranu pokazujący elementy okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="0cde3-113">Okno jest podzielone na dwa obszary: obszar niebędący klientem i obszar klienta.</span><span class="sxs-lookup"><span data-stu-id="0cde3-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="0cde3-114">*Obszar niebędący klientem* okna jest implementowany przez WPF i zawiera części okna, które są wspólne dla większości systemu Windows, w tym:</span><span class="sxs-lookup"><span data-stu-id="0cde3-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="0cde3-115">Obramowanie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-115">A border.</span></span>  
  
- <span data-ttu-id="0cde3-116">Pasek tytułu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-116">A title bar.</span></span>  
  
- <span data-ttu-id="0cde3-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="0cde3-117">An icon.</span></span>  
  
- <span data-ttu-id="0cde3-118">Przyciski Minimalizuj, Maksymalizuj i Przywróć.</span><span class="sxs-lookup"><span data-stu-id="0cde3-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="0cde3-119">Przycisk Zamknij.</span><span class="sxs-lookup"><span data-stu-id="0cde3-119">A Close button.</span></span>  
  
- <span data-ttu-id="0cde3-120">Menu systemowe z elementami menu, które umożliwiają użytkownikom minimalizowanie, maksymalizowanie, przywracanie, przenoszenie, zmienianie rozmiaru i zamykanie okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="0cde3-121">*Obszar klienta* okna to obszar w obszarze nieklienckim okna, który jest używany przez deweloperów do dodawania zawartości specyficznej dla aplikacji, takiej jak paski menu, paski narzędzi i formanty.</span><span class="sxs-lookup"><span data-stu-id="0cde3-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="0cde3-122">W WPF, okno jest hermetyzowane przez klasę <xref:System.Windows.Window>, która służy do wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0cde3-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="0cde3-123">Wyświetl okno.</span><span class="sxs-lookup"><span data-stu-id="0cde3-123">Display a window.</span></span>  
  
- <span data-ttu-id="0cde3-124">Skonfiguruj rozmiar, położenie i wygląd okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="0cde3-125">Hostowanie zawartości specyficznej dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="0cde3-126">Zarządzanie okresem istnienia okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="0cde3-127">Implementowanie okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-127">Implementing a Window</span></span>  
 <span data-ttu-id="0cde3-128">Implementacja typowego okna składa się zarówno z wyglądu, jak i zachowania, w którym *wygląd* okna jest przeszukiwany użytkownikom i *zachowanie* definiuje sposób, w jaki okno działa jak użytkownicy.</span><span class="sxs-lookup"><span data-stu-id="0cde3-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="0cde3-129">W WPF można zaimplementować wygląd i zachowanie okna przy użyciu kodu lub [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="0cde3-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="0cde3-130">Ogólnie rzecz biorąc, wygląd okna jest implementowany przy użyciu znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a jego zachowanie jest implementowane za pomocą kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="0cde3-131">Aby umożliwić współdziałanie pliku znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i pliku związanego z kodem, wymagane są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0cde3-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="0cde3-132">W znaczniku element `Window` musi zawierać atrybut `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="0cde3-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="0cde3-133">Po skompilowaniu aplikacji istnienie `x:Class` w pliku znaczników powoduje, że program Microsoft Build Engine (MSBuild) tworzy klasę `partial`, która pochodzi od <xref:System.Windows.Window> i ma nazwę określoną przez atrybut `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="0cde3-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="0cde3-134">Wymaga to dodania deklaracji przestrzeni nazw XML dla schematu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).</span><span class="sxs-lookup"><span data-stu-id="0cde3-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="0cde3-135">Wygenerowana Klasa `partial` implementuje metodę `InitializeComponent`, która jest wywoływana, aby zarejestrować zdarzenia i ustawić właściwości zaimplementowane w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="0cde3-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="0cde3-136">W kodzie, Klasa musi być klasą `partial` o tej samej nazwie, która jest określona przez atrybut `x:Class` w znaczniku i musi pochodzić od <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="0cde3-137">Pozwala to skojarzyć plik związany z kodem z klasą `partial` generowaną dla pliku znaczników podczas kompilowania aplikacji (zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="0cde3-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="0cde3-138">W kodzie, Klasa <xref:System.Windows.Window> musi implementować konstruktora, który wywołuje metodę `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="0cde3-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="0cde3-139">`InitializeComponent` jest implementowana przez wygenerowaną klasę `partial` pliku znaczników w celu rejestrowania zdarzeń i ustawiania właściwości, które są zdefiniowane w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="0cde3-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-140">Po dodaniu nowego <xref:System.Windows.Window> do projektu przy użyciu programu Visual Studio, <xref:System.Windows.Window> jest implementowane przy użyciu znaczników i kodu, i zawiera konfigurację niezbędną do utworzenia skojarzenia między plikami znaczników i kodu, zgodnie z opisem w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="0cde3-141">W przypadku tej konfiguracji można skupić się na definiowaniu wyglądu okna w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika i implementacji jego zachowania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="0cde3-142">W poniższym przykładzie pokazano okno z przyciskiem, zaimplementowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup i program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku zaimplementowanego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="0cde3-143">Konfigurowanie definicji okna dla programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0cde3-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="0cde3-144">Sposób implementacji okna decyduje o sposobie jego konfiguracji dla programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0cde3-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="0cde3-145">Dla okna, które jest zdefiniowane przy użyciu zarówno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników, jak i kodu:</span><span class="sxs-lookup"><span data-stu-id="0cde3-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="0cde3-146">Pliki znaczników XAML są konfigurowane jako elementy `Page` programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0cde3-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="0cde3-147">Pliki związane z kodem są konfigurowane jako elementy `Compile` programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0cde3-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="0cde3-148">Jest to pokazane w następującym pliku projektu programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0cde3-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="0cde3-149">Aby uzyskać informacje na temat tworzenia aplikacji WPF, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="0cde3-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="0cde3-150">Okres istnienia okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-150">Window Lifetime</span></span>  
 <span data-ttu-id="0cde3-151">Podobnie jak w przypadku każdej klasy, okno ma okres istnienia rozpoczynający się po pierwszym utworzeniu wystąpienia, po którym jest otwierane, uaktywniane i dezaktywowane i ostatecznie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="0cde3-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="0cde3-152">Otwieranie okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-152">Opening a Window</span></span>  
 <span data-ttu-id="0cde3-153">Aby otworzyć okno, należy najpierw utworzyć jego wystąpienie, które jest zademonstrowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="0cde3-154">W tym przykładzie `MarkupAndCodeBehindWindow` jest tworzone podczas uruchamiania aplikacji, która występuje, gdy zdarzenie <xref:System.Windows.Application.Startup> zostanie zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="0cde3-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="0cde3-155">Po utworzeniu wystąpienia okna odwołanie do niego jest automatycznie dodawane do listy systemu Windows, która jest zarządzana przez obiekt <xref:System.Windows.Application> (zobacz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0cde3-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="0cde3-156">Ponadto pierwsze okno, które ma zostać utworzone, jest domyślnie ustawiane przez <xref:System.Windows.Application> jako główne okno aplikacji (zobacz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0cde3-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="0cde3-157">Okno jest ostatecznie otwarte przez wywołanie metody <xref:System.Windows.Window.Show%2A>; wyniki są pokazane na poniższym rysunku.</span><span class="sxs-lookup"><span data-stu-id="0cde3-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Okno otwarte przez wywołanie okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="0cde3-159">Okno otwierane przez wywołanie <xref:System.Windows.Window.Show%2A> jest oknem niemodalnym, co oznacza, że aplikacja działa w trybie, który umożliwia użytkownikom aktywowanie innych okien w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-160"><xref:System.Windows.Window.ShowDialog%2A> jest wywoływana, aby otwierać okna, takie jak okna dialogowe modalnie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="0cde3-161">Aby uzyskać więcej informacji, zobacz [Omówienie okien](dialog-boxes-overview.md) dialogowych.</span><span class="sxs-lookup"><span data-stu-id="0cde3-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="0cde3-162">Gdy <xref:System.Windows.Window.Show%2A> jest wywoływana, okno wykonuje działanie inicjalizacji przed wyświetleniem infrastruktury, która pozwala na odbieranie danych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0cde3-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="0cde3-163">Po zainicjowaniu okna zdarzenie <xref:System.Windows.Window.SourceInitialized> jest wywoływane i wyświetlane jest okno.</span><span class="sxs-lookup"><span data-stu-id="0cde3-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="0cde3-164">Jako skrót <xref:System.Windows.Application.StartupUri%2A> można ustawić, aby określić pierwsze okno, które jest otwierane automatycznie podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="0cde3-165">Po uruchomieniu aplikacji okno określone przez wartość <xref:System.Windows.Application.StartupUri%2A> jest otwierane niemodalnie; wewnętrznie okno jest otwierane przez wywołanie jego metody <xref:System.Windows.Window.Show%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="0cde3-166">Własność okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-166">Window Ownership</span></span>  
 <span data-ttu-id="0cde3-167">Okno otwierane za pomocą metody <xref:System.Windows.Window.Show%2A> nie ma niejawnej relacji z oknem, które je utworzyło; Użytkownicy mogą korzystać z dowolnego okna niezależnie od siebie, co oznacza, że oba okna mogą wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0cde3-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="0cde3-168">Należy pokryć drugą (chyba że jeden z okien ma właściwość <xref:System.Windows.Window.Topmost%2A> ustawioną na `true`).</span><span class="sxs-lookup"><span data-stu-id="0cde3-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="0cde3-169">Być zminimalizowane, zmaksymalizowane i przywrócone bez wpływu na pozostałe.</span><span class="sxs-lookup"><span data-stu-id="0cde3-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="0cde3-170">Niektóre okna wymagają relacji z oknem, które je otwiera.</span><span class="sxs-lookup"><span data-stu-id="0cde3-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="0cde3-171">Na przykład aplikacja zintegrowanego środowiska programistycznego (IDE) może otworzyć okno właściwości i okna narzędzi, których typowe zachowanie dotyczy tworzonego okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="0cde3-172">Ponadto takie okna powinny zawsze zamykać, minimalizować, maksymalizować i przywracać w połączeniu z oknem, które je utworzyło.</span><span class="sxs-lookup"><span data-stu-id="0cde3-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="0cde3-173">Tę relację można ustalić przez utworzenie jednego *okna innego i jest ono realizowane* przez ustawienie właściwości <xref:System.Windows.Window.Owner%2A> *należącego do okna* z odwołaniem do *okna właściciela*.</span><span class="sxs-lookup"><span data-stu-id="0cde3-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="0cde3-174">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="0cde3-175">Po ustanowieniu własności:</span><span class="sxs-lookup"><span data-stu-id="0cde3-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="0cde3-176">Posiadane okno może odwoływać się do swojego okna właściciela, sprawdzając wartość jego właściwości <xref:System.Windows.Window.Owner%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="0cde3-177">Okno właściciela może odnaleźć wszystkie okna, do których należy, sprawdzając wartość właściwości <xref:System.Windows.Window.OwnedWindows%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="0cde3-178">Zapobieganie aktywacji okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="0cde3-179">Istnieją scenariusze, w których nie należy aktywować systemu Windows, na przykład w oknach konwersacji w aplikacji w stylu programu Messenger lub oknach powiadomień aplikacji poczty e-mail.</span><span class="sxs-lookup"><span data-stu-id="0cde3-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="0cde3-180">Jeśli aplikacja zawiera okno, które nie powinno być aktywowane, gdy jest wyświetlany, można ustawić jego właściwość <xref:System.Windows.Window.ShowActivated%2A> na `false` przed wywołaniem <xref:System.Windows.Window.Show%2A> metody po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="0cde3-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="0cde3-181">W związku z tym:</span><span class="sxs-lookup"><span data-stu-id="0cde3-181">As a consequence:</span></span>  
  
- <span data-ttu-id="0cde3-182">Okno nie zostało aktywowane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="0cde3-183">Zdarzenie <xref:System.Windows.Window.Activated> okna nie zostało zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="0cde3-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="0cde3-184">Uaktywnione okno zostanie uaktywnione.</span><span class="sxs-lookup"><span data-stu-id="0cde3-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="0cde3-185">Okno zostanie aktywowane, jednak natychmiast po jego aktywowaniu przez kliknięcie w obszarze klienta lub nieklienckiego.</span><span class="sxs-lookup"><span data-stu-id="0cde3-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="0cde3-186">W takim przypadku:</span><span class="sxs-lookup"><span data-stu-id="0cde3-186">In this case:</span></span>  
  
- <span data-ttu-id="0cde3-187">Okno zostało aktywowane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-187">The window is activated.</span></span>  
  
- <span data-ttu-id="0cde3-188">Zdarzenie <xref:System.Windows.Window.Activated> okna zostało zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="0cde3-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="0cde3-189">Poprzednio aktywowane okno zostało zdezaktywowane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="0cde3-190">Zdarzenia <xref:System.Windows.Window.Deactivated> i <xref:System.Windows.Window.Activated> okna są następnie podnoszone zgodnie z oczekiwaniami w odpowiedzi na akcje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0cde3-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="0cde3-191">Aktywacja okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-191">Window Activation</span></span>  
 <span data-ttu-id="0cde3-192">Gdy okno jest otwierane po raz pierwszy, przechodzi do aktywnego okna (chyba że jest wyświetlane z <xref:System.Windows.Window.ShowActivated%2A> ustawionym na `false`).</span><span class="sxs-lookup"><span data-stu-id="0cde3-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="0cde3-193">*Aktywne okno* to okno, które aktualnie przechwytywa dane wprowadzane przez użytkownika, takie jak naciśnięcia klawiszy i kliknięć myszą.</span><span class="sxs-lookup"><span data-stu-id="0cde3-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="0cde3-194">Gdy okno zostanie uaktywnione, wywołuje zdarzenie <xref:System.Windows.Window.Activated>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-195">Po pierwszym otwarciu okna zdarzenia <xref:System.Windows.FrameworkElement.Loaded> i <xref:System.Windows.Window.ContentRendered> są wywoływane dopiero po podniesieniu zdarzenia <xref:System.Windows.Window.Activated>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="0cde3-196">Z tego względu okno może być efektywnie uważane za otwarte, gdy zostanie zgłoszone <xref:System.Windows.Window.ContentRendered>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="0cde3-197">Gdy okno zostanie uaktywnione, użytkownik może aktywować inne okno w tej samej aplikacji lub aktywować inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="0cde3-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="0cde3-198">W takim przypadku aktywne okno zostanie zdezaktywowane i wygeneruje zdarzenie <xref:System.Windows.Window.Deactivated>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="0cde3-199">Podobnie, gdy użytkownik wybierze aktualnie dezaktywowane okno, okno zostanie ponownie aktywowane i zostanie zgłoszone <xref:System.Windows.Window.Activated>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="0cde3-200">Jednym z typowych przyczyn obsługi <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated> jest włączenie i wyłączenie funkcji, która może być uruchamiana tylko wtedy, gdy okno jest aktywne.</span><span class="sxs-lookup"><span data-stu-id="0cde3-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="0cde3-201">Na przykład niektóre okna wyświetlają zawartość interaktywną, która wymaga stałego wprowadzania danych przez użytkownika lub uwagi, w tym gier i odtwarzaczy wideo.</span><span class="sxs-lookup"><span data-stu-id="0cde3-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="0cde3-202">Poniższy przykład to uproszczony odtwarzacz wideo, który pokazuje, jak obsłużyć <xref:System.Windows.Window.Activated> i <xref:System.Windows.Window.Deactivated>, aby zaimplementować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="0cde3-203">Inne typy aplikacji mogą nadal uruchamiać kod w tle, gdy okno zostanie zdezaktywowane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="0cde3-204">Na przykład klient poczty e-mail może kontynuować sondowanie serwera poczty, gdy użytkownik korzysta z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="0cde3-205">Aplikacje takie jak często zapewniają różne lub dodatkowe zachowanie podczas dezaktywacji okna głównego.</span><span class="sxs-lookup"><span data-stu-id="0cde3-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="0cde3-206">W odniesieniu do programu poczty może to oznaczać zarówno dodanie nowego elementu poczty do skrzynki odbiorczej, jak i dodanie ikony powiadomienia do paska zadań.</span><span class="sxs-lookup"><span data-stu-id="0cde3-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="0cde3-207">Ikona powiadomienia musi być wyświetlana tylko wtedy, gdy okno poczty nie jest aktywne, które można określić, sprawdzając Właściwość <xref:System.Windows.Window.IsActive%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="0cde3-208">Jeśli zadanie w tle zakończy pracę, okno może chcieć pilnie powiadomić użytkownika przez wywołanie metody <xref:System.Windows.Window.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="0cde3-209">Jeśli użytkownik korzysta z innej aplikacji aktywowanej po wywołaniu <xref:System.Windows.Window.Activate%2A>, zostanie uaktywniony przycisk paska zadań okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="0cde3-210">Jeśli użytkownik korzysta z bieżącej aplikacji, wywołanie <xref:System.Windows.Window.Activate%2A> spowoduje przełączenie okna do pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-211">Aktywację zakresu aplikacji można obsługiwać przy użyciu zdarzeń <xref:System.Windows.Application.Activated?displayProperty=nameWithType> i <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="0cde3-212">Zamykanie okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-212">Closing a Window</span></span>  
 <span data-ttu-id="0cde3-213">Okres istnienia okna przechodzi do końca, gdy użytkownik go zamknie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="0cde3-214">Okno może być zamknięte przy użyciu elementów w obszarze nieklienckim, w tym:</span><span class="sxs-lookup"><span data-stu-id="0cde3-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="0cde3-215">Element **zamknięcia** menu **systemowego** .</span><span class="sxs-lookup"><span data-stu-id="0cde3-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="0cde3-216">Naciśnij klawisze ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="0cde3-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="0cde3-217">Naciśnij przycisk **Zamknij** .</span><span class="sxs-lookup"><span data-stu-id="0cde3-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="0cde3-218">Do obszaru klienckiego można zapewnić dodatkowe mechanizmy zamykania okna, tym częściej są następujące:</span><span class="sxs-lookup"><span data-stu-id="0cde3-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="0cde3-219">Element **wyjścia** w menu **plik** , zazwyczaj dla głównych okien aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="0cde3-220">**Zamknij** element w menu **plik** , zazwyczaj w oknie aplikacji dodatkowej.</span><span class="sxs-lookup"><span data-stu-id="0cde3-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="0cde3-221">Przycisk **Anuluj** , zazwyczaj na modalnym oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="0cde3-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="0cde3-222">Przycisk **Zamknij** , zazwyczaj w niemodalnym oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="0cde3-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="0cde3-223">Aby zamknąć okno w odpowiedzi na jeden z tych niestandardowych mechanizmów, należy wywołać metodę <xref:System.Windows.Window.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="0cde3-224">W poniższym przykładzie jest implementowana możliwość zamykania okna przez wybranie polecenia **Wyjdź** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="0cde3-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="0cde3-225">Gdy okno zostanie zamknięte, wywołuje dwa zdarzenia: <xref:System.Windows.Window.Closing> i <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="0cde3-226"><xref:System.Windows.Window.Closing> jest wywoływane przed zamknięciem okna i udostępnia mechanizm, za pomocą którego można zablokować zamknięcie okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="0cde3-227">Jednym z najczęstszych powodów, aby uniknąć zamykania okna, jest to, że zawartość okna zawiera zmodyfikowane dane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="0cde3-228">W takiej sytuacji można obsłużyć zdarzenie <xref:System.Windows.Window.Closing>, aby określić, czy dane są zanieczyszczone, a jeśli tak, to w celu poproszenia użytkownika o kontynuowanie zamykania okna bez zapisywania danych lub anulowania zamknięcia okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="0cde3-229">W poniższym przykładzie przedstawiono kluczowe aspekty obsługi <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="0cde3-230">Procedura obsługi zdarzeń <xref:System.Windows.Window.Closing> została przeniesiona <xref:System.ComponentModel.CancelEventArgs>, która implementuje Właściwość `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ustawioną na `true`, aby zapobiec zamykaniu okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="0cde3-231">Jeśli <xref:System.Windows.Window.Closing> nie jest obsługiwana lub jest obsługiwana, ale nie została anulowana, okno zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="0cde3-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="0cde3-232">Tuż przed faktycznym zamknięciem okna zostanie zgłoszone <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="0cde3-233">W tym momencie nie można uniemożliwić zamykania okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-234">Aplikację można skonfigurować tak, aby była automatycznie zamykana podczas zamykania okna aplikacji głównej (zobacz <xref:System.Windows.Application.MainWindow%2A>) lub ostatniego zamknięcia okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="0cde3-235">Aby uzyskać szczegółowe informacje, zobacz <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="0cde3-236">Okno może być jawnie zamykane za pomocą mechanizmów dostępnych w obszarach nieklienta i klienta, a okno może być również niejawnie zamknięte w wyniku zachowania w innych częściach aplikacji lub systemu Windows, w tym:</span><span class="sxs-lookup"><span data-stu-id="0cde3-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="0cde3-237">Użytkownik wylogowuje się lub zamknie system Windows.</span><span class="sxs-lookup"><span data-stu-id="0cde3-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="0cde3-238">Zamknięcie właściciela okna (zobacz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="0cde3-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="0cde3-239">Okno aplikacji głównej jest zamknięte, a <xref:System.Windows.Application.ShutdownMode%2A> jest <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="0cde3-240"><xref:System.Windows.Application.Shutdown%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0cde3-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-241">Nie można otworzyć ponownie okna po jego zamknięciu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="0cde3-242">Zdarzenia okresu istnienia okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="0cde3-243">Na poniższej ilustracji przedstawiono sekwencję zdarzeń głównych w okresie istnienia okna:</span><span class="sxs-lookup"><span data-stu-id="0cde3-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="0cde3-245">Poniższa ilustracja przedstawia sekwencję zdarzeń głównych w okresie istnienia okna, które jest wyświetlane bez aktywacji (<xref:System.Windows.Window.ShowActivated%2A> jest ustawiona na `false` przed wyświetleniem okna):</span><span class="sxs-lookup"><span data-stu-id="0cde3-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram przedstawiający zdarzenia w okresie istnienia bez aktywacji.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="0cde3-247">Lokalizacja okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-247">Window Location</span></span>  
 <span data-ttu-id="0cde3-248">Gdy okno jest otwarte, ma miejsce w wymiarach x i y względem pulpitu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="0cde3-249">Tę lokalizację można określić, sprawdzając odpowiednio <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="0cde3-250">Można ustawić te właściwości, aby zmienić lokalizację okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="0cde3-251">Możesz również określić początkową lokalizację <xref:System.Windows.Window>, gdy po raz pierwszy pojawia się, ustawiając właściwość <xref:System.Windows.Window.WindowStartupLocation%2A> z jedną z następujących <xref:System.Windows.WindowStartupLocation> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="0cde3-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="0cde3-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="0cde3-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="0cde3-253">Jeśli lokalizacja początkowa jest określona jako <xref:System.Windows.WindowStartupLocation.Manual>, a właściwości <xref:System.Windows.Window.Left%2A> i <xref:System.Windows.Window.Top%2A> nie zostały ustawione, <xref:System.Windows.Window> zostanie poproszony o podanie systemu Windows o lokalizację, w której ma się pojawić.</span><span class="sxs-lookup"><span data-stu-id="0cde3-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="0cde3-254">System Windows i porządek Z góry</span><span class="sxs-lookup"><span data-stu-id="0cde3-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="0cde3-255">Poza lokalizacją x i y okno zawiera również lokalizację w wymiarze z, która określa położenie w pionie w odniesieniu do innych okien.</span><span class="sxs-lookup"><span data-stu-id="0cde3-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="0cde3-256">Jest to znane jako porządek osi z okna, a istnieją dwa typy: normalna kolejność z i kolejność z góry.</span><span class="sxs-lookup"><span data-stu-id="0cde3-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="0cde3-257">Lokalizacja okna w *normalnej kolejności z* jest określana na podstawie tego, czy jest ona obecnie aktywna, czy nie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="0cde3-258">Domyślnie okno znajduje się w normalnej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0cde3-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="0cde3-259">Lokalizacja okna w *górnym porządku osi z* jest również określana na podstawie tego, czy jest ona obecnie aktywna, czy nie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="0cde3-260">Co więcej, okna w najwyższej kolejności z są zawsze zlokalizowane powyżej systemu Windows w normalnej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0cde3-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="0cde3-261">Okno znajduje się w najwyższym porządku osi z, ustawiając właściwość <xref:System.Windows.Window.Topmost%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="0cde3-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="0cde3-262">W każdym porządku osi z aktywne okno jest wyświetlane nad wszystkimi innymi oknami w tej samej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0cde3-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="0cde3-263">Rozmiar okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-263">Window Size</span></span>  
 <span data-ttu-id="0cde3-264">Poza lokalizacją pulpitu okno ma rozmiar, który jest określany przez kilka właściwości, w tym różne właściwości width i height oraz <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="0cde3-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.MaxWidth%2A> są używane do zarządzania zakresem szerokości, które okno może mieć w okresie istnienia, i są skonfigurowane tak, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="0cde3-266">Wysokość okna jest zarządzana przez <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>i <xref:System.Windows.FrameworkElement.MaxHeight%2A>i są skonfigurowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="0cde3-267">Ponieważ różne wartości szerokości i wysokości określają zakres, możliwe jest, aby szerokość i wysokość okna o zmiennym rozmiarze znajdować się w dowolnym miejscu w określonym zakresie dla odpowiedniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="0cde3-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="0cde3-268">Aby wykryć bieżącą szerokość i wysokość, należy odpowiednio zbadać <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="0cde3-269">Jeśli chcesz, aby szerokość i wysokość okna miały rozmiar, który pasuje do rozmiaru zawartości okna, możesz użyć właściwości <xref:System.Windows.Window.SizeToContent%2A>, która ma następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="0cde3-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="0cde3-270"><xref:System.Windows.SizeToContent.Manual>.,</span><span class="sxs-lookup"><span data-stu-id="0cde3-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="0cde3-271">Brak efektu (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="0cde3-271">No effect (default).</span></span>  
  
- <span data-ttu-id="0cde3-272"><xref:System.Windows.SizeToContent.Width>.,</span><span class="sxs-lookup"><span data-stu-id="0cde3-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="0cde3-273">Dopasuj do szerokości zawartości, która ma taki sam efekt jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinWidth%2A>, jak i <xref:System.Windows.FrameworkElement.MaxWidth%2A> do szerokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="0cde3-274"><xref:System.Windows.SizeToContent.Height>.,</span><span class="sxs-lookup"><span data-stu-id="0cde3-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="0cde3-275">Dopasuj do wysokości zawartości, która ma taki sam efekt jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A>, jak i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="0cde3-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.,</span><span class="sxs-lookup"><span data-stu-id="0cde3-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="0cde3-277">Dopasuj do szerokości i wysokości zawartości, która ma taki sam skutek jak ustawienie zarówno <xref:System.Windows.FrameworkElement.MinHeight%2A>, jak i <xref:System.Windows.FrameworkElement.MaxHeight%2A> do wysokości zawartości, i Ustawianie zarówno <xref:System.Windows.FrameworkElement.MinWidth%2A>, jak i <xref:System.Windows.FrameworkElement.MaxWidth%2A> do szerokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="0cde3-278">W poniższym przykładzie pokazano okno, które automatycznie dopasowuje rozmiar do jego zawartości, zarówno w pionie, jak i w poziomie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="0cde3-279">Poniższy przykład pokazuje, jak ustawić właściwość <xref:System.Windows.Window.SizeToContent%2A> w kodzie, aby określić, jak zmienia się rozmiar okna w celu dopasowania do jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="0cde3-280">Kolejność pierwszeństwa we właściwościach ustalania wielkości</span><span class="sxs-lookup"><span data-stu-id="0cde3-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="0cde3-281">Zasadniczo różne rozmiary okna łączą się, aby zdefiniować zakres szerokości i wysokości okna o zmiennym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="0cde3-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="0cde3-282">Aby zapewnić zachowanie prawidłowego zakresu, <xref:System.Windows.Window> oblicza wartości właściwości rozmiaru przy użyciu następujących kolejności pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="0cde3-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="0cde3-283">**Dla właściwości wysokości:**</span><span class="sxs-lookup"><span data-stu-id="0cde3-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="0cde3-284">**Dla właściwości width:**</span><span class="sxs-lookup"><span data-stu-id="0cde3-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="0cde3-285">Kolejność pierwszeństwa może również określać rozmiar okna, gdy jest zmaksymalizowane, które jest zarządzane za pomocą właściwości <xref:System.Windows.Window.WindowState%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="0cde3-286">Stan okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-286">Window State</span></span>  
 <span data-ttu-id="0cde3-287">W okresie istnienia okna o zmiennym rozmiarze może istnieć trzy stany: normalny, zminimalizowany i zmaksymalizowany.</span><span class="sxs-lookup"><span data-stu-id="0cde3-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="0cde3-288">Okno z *normalnym* stanem jest domyślnym stanem okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="0cde3-289">Okno z tym stanem umożliwia użytkownikowi przeniesienie i zmianę jego rozmiaru przy użyciu uchwytu zmiany rozmiaru lub obramowania, jeśli zostanie on zmieniony.</span><span class="sxs-lookup"><span data-stu-id="0cde3-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="0cde3-290">Okno ze *zminimalizowanym* stanem jest zwijane do jego przycisku paska zadań, jeśli <xref:System.Windows.Window.ShowInTaskbar%2A> jest ustawiony na `true`; w przeciwnym razie zwija do najmniejszego możliwego rozmiaru, który może być i odszukany w lewym dolnym rogu pulpitu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="0cde3-291">Nie można zmienić rozmiaru okna zminimalizowanego za pomocą obramowania ani uchwytu zmiany rozmiaru, chociaż zminimalizowane okno, które nie jest wyświetlane na pasku zadań, może być przeciągane wokół pulpitu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="0cde3-292">Okno z *zmaksymalizowanym* stanem rozwija się do maksymalnego rozmiaru, który może być, co będzie tak duże, jak <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.Window.SizeToContent%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="0cde3-293">Jak okno zminimalizowane, nie można zmienić rozmiaru zmaksymalizowanego okna przy użyciu uchwytu zmiany rozmiaru lub przeciągając obramowanie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cde3-294">Wartości właściwości <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.Height%2A> okna zawsze reprezentują wartości dla normalnego stanu, nawet gdy okno jest obecnie zmaksymalizowane lub zminimalizowane.</span><span class="sxs-lookup"><span data-stu-id="0cde3-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="0cde3-295">Stan okna można skonfigurować przez ustawienie jego właściwości <xref:System.Windows.Window.WindowState%2A>, która może mieć jedną z następujących <xref:System.Windows.WindowState> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="0cde3-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="0cde3-296"><xref:System.Windows.WindowState.Normal> (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="0cde3-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="0cde3-297">Poniższy przykład pokazuje, jak utworzyć okno, które jest wyświetlane jako zmaksymalizowane, gdy zostanie otwarte.</span><span class="sxs-lookup"><span data-stu-id="0cde3-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="0cde3-298">Ogólnie rzecz biorąc, należy ustawić <xref:System.Windows.Window.WindowState%2A>, aby skonfigurować stan początkowy okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="0cde3-299">Po pobraniu okna o zmiennym rozmiarze użytkownicy mogą nacisnąć przyciski Minimalizuj, Maksymalizuj i Przywróć na pasku tytułu okna, aby zmienić stan okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="0cde3-300">Wygląd okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-300">Window Appearance</span></span>  
 <span data-ttu-id="0cde3-301">Aby zmienić wygląd obszaru klienta okna, można dodać do niego zawartość specyficzną dla okna, taką jak przyciski, etykiety i pola tekstowe.</span><span class="sxs-lookup"><span data-stu-id="0cde3-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="0cde3-302">Aby skonfigurować obszar niebędący klientem, <xref:System.Windows.Window> zawiera kilka właściwości, które obejmują <xref:System.Windows.Window.Icon%2A> do ustawiania ikony okna i <xref:System.Windows.Window.Title%2A> w celu ustawienia jej tytułu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="0cde3-303">Możesz również zmienić wygląd i zachowanie obramowania obszaru nieklienckiego, konfigurując tryb zmiany rozmiaru okna, styl okna i czy jest on wyświetlany jako przycisk na pasku zadań pulpitu.</span><span class="sxs-lookup"><span data-stu-id="0cde3-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="0cde3-304">Tryb zmiany rozmiaru</span><span class="sxs-lookup"><span data-stu-id="0cde3-304">Resize Mode</span></span>  
 <span data-ttu-id="0cde3-305">W zależności od właściwości <xref:System.Windows.Window.WindowStyle%2A> można kontrolować sposób, w jaki użytkownicy mogą zmieniać rozmiar okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="0cde3-306">Wybór stylu okna ma wpływ na to, czy użytkownik może zmienić rozmiar okna, przeciągając jego obramowanie przy użyciu myszy, czy przyciski **Minimalizuj**, **Maksymalizuj**i **Zmień rozmiar** pojawiają się w obszarze nieklienckim i, jeśli są wyświetlane, niezależnie od tego, czy są włączone.</span><span class="sxs-lookup"><span data-stu-id="0cde3-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="0cde3-307">Można skonfigurować sposób zmiany rozmiaru okna przez ustawienie jego właściwości <xref:System.Windows.Window.ResizeMode%2A>, która może być jedną z następujących <xref:System.Windows.ResizeMode> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="0cde3-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="0cde3-308"><xref:System.Windows.ResizeMode.CanResize> (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="0cde3-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="0cde3-309">Podobnie jak w przypadku <xref:System.Windows.Window.WindowStyle%2A>, tryb zmiany rozmiaru okna jest mało prawdopodobne, aby można go było zmienić w okresie istnienia, co oznacza, że najprawdopodobniej ustawisz go z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="0cde3-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="0cde3-310">Należy zauważyć, że można wykryć, czy okno jest zmaksymalizowane, zminimalizowane lub przywrócone, sprawdzając Właściwość <xref:System.Windows.Window.WindowState%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cde3-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="0cde3-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="0cde3-311">Window Style</span></span>  
 <span data-ttu-id="0cde3-312">Obramowanie, które jest widoczne z obszaru nieklienckiego okna, jest odpowiednie dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="0cde3-313">Istnieją jednak sytuacje, w których są zbędne różne typy obramowań lub nie są w ogóle stosowane żadne obramowania, w zależności od typu okna.</span><span class="sxs-lookup"><span data-stu-id="0cde3-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="0cde3-314">Aby sterować typem obramowania pobieranym przez okno, ustaw jej Właściwość <xref:System.Windows.Window.WindowStyle%2A> na jedną z następujących wartości wyliczenia <xref:System.Windows.WindowStyle>:</span><span class="sxs-lookup"><span data-stu-id="0cde3-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="0cde3-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="0cde3-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="0cde3-316">Efekt tych stylów okna przedstawiono na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="0cde3-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustracja stylów obramowania okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="0cde3-318">Można ustawić <xref:System.Windows.Window.WindowStyle%2A> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników lub kodu; ponieważ nie można jej zmienić w okresie istnienia okna, najprawdopodobniej skonfigurujesz go przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="0cde3-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="0cde3-319">Styl okna bez prostokąta</span><span class="sxs-lookup"><span data-stu-id="0cde3-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="0cde3-320">Istnieją również sytuacje, w których style obramowania, które <xref:System.Windows.Window.WindowStyle%2A> mogą być niewystarczające.</span><span class="sxs-lookup"><span data-stu-id="0cde3-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="0cde3-321">Na przykład możesz chcieć utworzyć aplikację z nieprostokątnym obramowaniem, np. Microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="0cde3-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="0cde3-322">Rozważmy na przykład okno dymek mowy pokazane na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="0cde3-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno bąbelka mowy z tekstem przeciągnij mnie.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="0cde3-324">Ten typ okna można utworzyć, ustawiając właściwość <xref:System.Windows.Window.WindowStyle%2A> na <xref:System.Windows.WindowStyle.None>i używając specjalnej pomocy technicznej, która <xref:System.Windows.Window> ma dla przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="0cde3-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="0cde3-325">Ta kombinacja wartości powoduje, że okno jest renderowane całkowicie przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="0cde3-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="0cde3-326">W tym stanie nie można używać modułów definiowania układu nieklienckiego (zamknięcie menu, minimalizowania, maksymalizowania i przywracania).</span><span class="sxs-lookup"><span data-stu-id="0cde3-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="0cde3-327">W związku z tym należy podać własny.</span><span class="sxs-lookup"><span data-stu-id="0cde3-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="0cde3-328">Obecność paska zadań</span><span class="sxs-lookup"><span data-stu-id="0cde3-328">Task Bar Presence</span></span>  

<span data-ttu-id="0cde3-329">Domyślny wygląd okna zawiera przycisk paska zadań, tak jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="0cde3-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Zrzut ekranu pokazujący okno z przyciskiem paska zadań.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="0cde3-331">Niektóre typy okien nie mają przycisku paska zadań, takiego jak okna dialogowe komunikatów i okien dialogowych (zobacz [okna dialogowe — Omówienie](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0cde3-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="0cde3-332">Można kontrolować, czy przycisk paska zadań dla okna jest pokazywany przez ustawienie właściwości <xref:System.Windows.Window.ShowInTaskbar%2A> (domyślnie`true`).</span><span class="sxs-lookup"><span data-stu-id="0cde3-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="0cde3-333">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0cde3-333">Security Considerations</span></span>  
 <span data-ttu-id="0cde3-334"><xref:System.Windows.Window> wymaga uprawnień zabezpieczeń `UnmanagedCode`, aby można było utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="0cde3-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="0cde3-335">W przypadku aplikacji zainstalowanych na komputerze lokalnym i uruchamianych z niej jest to zestaw uprawnień, które są przyznawane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="0cde3-336">Jednak jest to poza zestawem uprawnień przyznanym aplikacjom, które są uruchamiane z Internetu lub lokalnej strefy intranetowej przy użyciu technologii ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="0cde3-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="0cde3-337">W związku z tym użytkownicy otrzymają ostrzeżenie o zabezpieczeniach technologii ClickOnce i będą musieli podnieść poziom uprawnień dla aplikacji do pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="0cde3-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="0cde3-338">Ponadto aplikacje XBAP nie mogą domyślnie wyświetlać okien ani okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="0cde3-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="0cde3-339">Aby zapoznać się z zagadnieniami dotyczącymi zabezpieczeń aplikacji autonomicznych, zobacz [strategia zabezpieczeń WPF — zabezpieczenia platformy](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="0cde3-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="0cde3-340">Inne typy okien</span><span class="sxs-lookup"><span data-stu-id="0cde3-340">Other Types of Windows</span></span>  
 <span data-ttu-id="0cde3-341"><xref:System.Windows.Navigation.NavigationWindow> to okno, które jest przeznaczone do hostowania zawartości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="0cde3-342">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0cde3-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="0cde3-343">Okna dialogowe to okna, które są często używane do zbierania informacji od użytkownika w celu ukończenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="0cde3-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="0cde3-344">Na przykład, gdy użytkownik chce otworzyć plik, okno dialogowe **Otwórz plik** jest zwykle wyświetlane przez aplikację w celu uzyskania nazwy pliku od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0cde3-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="0cde3-345">Aby uzyskać więcej informacji, zobacz [okna dialogowe przegląd](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0cde3-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cde3-346">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cde3-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="0cde3-347">Okna dialogowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="0cde3-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="0cde3-348">Kompilowanie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="0cde3-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
