---
title: Optymalizowanie wydajności aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: cc6ea051401199a87965565c920068fd55cb05d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743947"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="bb6ef-102">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="bb6ef-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="bb6ef-103">Ta sekcja jest przeznaczona jako Dokumentacja dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperów aplikacji, którzy poszukują sposobów ulepszania wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb6ef-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="bb6ef-104">Jeśli jesteś deweloperem, który jest nowym elementem Microsoft .NET Framework i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najpierw zapoznaj się z obiema platformami.</span><span class="sxs-lookup"><span data-stu-id="bb6ef-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="bb6ef-105">W tej sekcji założono, że działa wiedza i jest przeznaczony dla programistów, którzy już znają wystarczającą do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb6ef-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb6ef-106">Dane dotyczące wydajności podane w tej sekcji bazują na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach uruchamianych na komputerze 2,8 GHz z 512 pamięcią RAM i kartą grafiki ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="bb6ef-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb6ef-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bb6ef-107">In This Section</span></span>  
 [<span data-ttu-id="bb6ef-108">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="bb6ef-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="bb6ef-109">Wykorzystanie możliwości sprzętu</span><span class="sxs-lookup"><span data-stu-id="bb6ef-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="bb6ef-110">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="bb6ef-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="bb6ef-111">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="bb6ef-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="bb6ef-112">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="bb6ef-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="bb6ef-113">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="bb6ef-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="bb6ef-114">Tekst</span><span class="sxs-lookup"><span data-stu-id="bb6ef-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="bb6ef-115">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="bb6ef-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="bb6ef-116">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="bb6ef-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="bb6ef-117">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="bb6ef-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="bb6ef-118">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="bb6ef-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb6ef-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb6ef-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="bb6ef-120">Warstwy renderowania grafiki</span><span class="sxs-lookup"><span data-stu-id="bb6ef-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="bb6ef-121">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="bb6ef-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="bb6ef-122">Układ</span><span class="sxs-lookup"><span data-stu-id="bb6ef-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="bb6ef-123">Drzewa w WPF</span><span class="sxs-lookup"><span data-stu-id="bb6ef-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="bb6ef-124">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="bb6ef-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="bb6ef-125">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="bb6ef-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="bb6ef-126">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="bb6ef-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="bb6ef-127">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="bb6ef-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="bb6ef-128">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="bb6ef-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="bb6ef-129">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="bb6ef-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="bb6ef-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="bb6ef-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="bb6ef-131">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="bb6ef-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="bb6ef-132">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="bb6ef-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="bb6ef-133">Nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="bb6ef-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="bb6ef-134">Animacja — porady i wskazówki</span><span class="sxs-lookup"><span data-stu-id="bb6ef-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="bb6ef-135">Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="bb6ef-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
