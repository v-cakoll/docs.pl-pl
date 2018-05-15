---
title: Optymalizacja wydajności aplikacji WPF
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: faa06e4558401c1d0e9335fbc630c5371d1bc516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="11498-102">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="11498-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="11498-103">W tej sekcji służy jako punkt odniesienia dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperów, którzy szukasz sposobów, aby poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11498-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="11498-104">Jeśli jesteś deweloperem, który jest nowym składnikiem programu Microsoft .NET Framework i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], należy najpierw zapoznać się z obu platform.</span><span class="sxs-lookup"><span data-stu-id="11498-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="11498-105">W tej sekcji wymaga praktycznej wiedzy obu i jest przeznaczony dla programistów, którzy już wiesz, aby pobrać swoich aplikacji działa.</span><span class="sxs-lookup"><span data-stu-id="11498-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11498-106">Dane wydajności przekazane w tej sekcji są oparte na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji uruchomionych na 2,8 GHz PC z 512, pamięci RAM i ATI Radeon 9700 karty graficznej.</span><span class="sxs-lookup"><span data-stu-id="11498-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11498-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="11498-107">In This Section</span></span>  
 [<span data-ttu-id="11498-108">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="11498-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="11498-109">Wykorzystanie możliwości sprzętu</span><span class="sxs-lookup"><span data-stu-id="11498-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="11498-110">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="11498-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="11498-111">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="11498-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="11498-112">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="11498-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="11498-113">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="11498-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="11498-114">Tekst</span><span class="sxs-lookup"><span data-stu-id="11498-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="11498-115">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="11498-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="11498-116">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="11498-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="11498-117">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="11498-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="11498-118">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="11498-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="11498-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11498-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="11498-120">Warstwy renderowania grafiki</span><span class="sxs-lookup"><span data-stu-id="11498-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="11498-121">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="11498-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="11498-122">Układ</span><span class="sxs-lookup"><span data-stu-id="11498-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="11498-123">Drzewa w WPF</span><span class="sxs-lookup"><span data-stu-id="11498-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="11498-124">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="11498-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="11498-125">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="11498-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="11498-126">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="11498-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="11498-127">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="11498-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="11498-128">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="11498-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="11498-129">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="11498-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="11498-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="11498-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="11498-131">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="11498-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="11498-132">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="11498-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="11498-133">Nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="11498-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="11498-134">Animacja — porady i wskazówki</span><span class="sxs-lookup"><span data-stu-id="11498-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="11498-135">Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="11498-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
