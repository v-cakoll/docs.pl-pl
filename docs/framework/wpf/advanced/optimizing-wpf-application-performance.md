---
title: "Optymalizacja wydajności aplikacji WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9ea154bc7c7a20bcdd57e1f271a4010f50646de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="e12db-102">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="e12db-103">W tej sekcji służy jako punkt odniesienia dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperów, którzy szukasz sposobów, aby poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e12db-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="e12db-104">Jeśli jesteś deweloperem, który jest nowym składnikiem [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], należy najpierw zapoznać się z obu platform.</span><span class="sxs-lookup"><span data-stu-id="e12db-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="e12db-105">W tej sekcji wymaga praktycznej wiedzy obu i jest przeznaczony dla programistów, którzy już wiesz, aby pobrać swoich aplikacji działa.</span><span class="sxs-lookup"><span data-stu-id="e12db-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e12db-106">Dane wydajności przekazane w tej sekcji są oparte na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji uruchomionych na 2,8 GHz PC z 512, pamięci RAM i ATI Radeon 9700 karty graficznej.</span><span class="sxs-lookup"><span data-stu-id="e12db-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e12db-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e12db-107">In This Section</span></span>  
 [<span data-ttu-id="e12db-108">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="e12db-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="e12db-109">Dzięki funkcji sprzętu</span><span class="sxs-lookup"><span data-stu-id="e12db-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="e12db-110">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="e12db-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="e12db-111">Grafika 2W i utworzenia obrazu</span><span class="sxs-lookup"><span data-stu-id="e12db-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="e12db-112">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="e12db-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="e12db-113">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="e12db-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="e12db-114">Tekst</span><span class="sxs-lookup"><span data-stu-id="e12db-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="e12db-115">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="e12db-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="e12db-116">Formanty</span><span class="sxs-lookup"><span data-stu-id="e12db-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="e12db-117">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="e12db-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="e12db-118">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="e12db-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="e12db-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e12db-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="e12db-120">Warstw renderowania grafiki</span><span class="sxs-lookup"><span data-stu-id="e12db-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="e12db-121">Przegląd renderowania grafiki WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="e12db-122">Układ</span><span class="sxs-lookup"><span data-stu-id="e12db-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="e12db-123">Drzewa na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="e12db-124">Rysowanie obiekty — omówienie</span><span class="sxs-lookup"><span data-stu-id="e12db-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="e12db-125">Przy użyciu obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="e12db-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="e12db-126">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="e12db-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="e12db-127">Obiekty obiektu freezable — omówienie</span><span class="sxs-lookup"><span data-stu-id="e12db-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="e12db-128">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="e12db-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="e12db-129">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="e12db-130">Rysowanie sformatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="e12db-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="e12db-131">Typografia na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="e12db-132">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="e12db-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e12db-133">Omówienie nawigacji</span><span class="sxs-lookup"><span data-stu-id="e12db-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="e12db-134">Animacja porady i wskazówki</span><span class="sxs-lookup"><span data-stu-id="e12db-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="e12db-135">Wskazówki: Buforowania danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="e12db-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
