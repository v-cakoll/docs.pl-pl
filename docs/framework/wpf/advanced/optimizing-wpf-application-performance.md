---
title: Optymalizacja wydajności aplikacji WPF
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: c1dd2587fb3642fb930fb7d5d6855a6e48c2ad2b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356393"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="e50cd-102">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="e50cd-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="e50cd-103">Ta sekcja jest przeznaczona jako odniesienie do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperów, którzy szukają sposobów poprawy wydajność ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e50cd-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="e50cd-104">Jeśli jesteś deweloperem, który jest nowym składnikiem programu Microsoft .NET Framework i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], należy najpierw zapoznać się z obu platform.</span><span class="sxs-lookup"><span data-stu-id="e50cd-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="e50cd-105">W tej sekcji zakłada praktyczną wiedzę na temat obu tych elementów i jest przeznaczony dla programistów, którzy już wiedzieć wystarczająco dużo, aby rozpocząć aplikacjach pracę.</span><span class="sxs-lookup"><span data-stu-id="e50cd-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e50cd-106">Dane wydajności przekazane w tej sekcji są oparte na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] działających na 2,8 GHz PC z 512 ilość pamięci RAM i 9700 Radeon ATI karty graficznej.</span><span class="sxs-lookup"><span data-stu-id="e50cd-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e50cd-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e50cd-107">In This Section</span></span>  
 [<span data-ttu-id="e50cd-108">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="e50cd-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="e50cd-109">Wykorzystanie możliwości sprzętu</span><span class="sxs-lookup"><span data-stu-id="e50cd-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="e50cd-110">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="e50cd-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="e50cd-111">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="e50cd-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="e50cd-112">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="e50cd-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="e50cd-113">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="e50cd-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="e50cd-114">Tekst</span><span class="sxs-lookup"><span data-stu-id="e50cd-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="e50cd-115">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="e50cd-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="e50cd-116">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="e50cd-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="e50cd-117">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="e50cd-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="e50cd-118">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="e50cd-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="e50cd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e50cd-119">See also</span></span>
- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="e50cd-120">Warstwy renderowania grafiki</span><span class="sxs-lookup"><span data-stu-id="e50cd-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="e50cd-121">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="e50cd-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="e50cd-122">Układ</span><span class="sxs-lookup"><span data-stu-id="e50cd-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="e50cd-123">Drzewa w WPF</span><span class="sxs-lookup"><span data-stu-id="e50cd-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="e50cd-124">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="e50cd-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="e50cd-125">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="e50cd-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="e50cd-126">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="e50cd-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="e50cd-127">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="e50cd-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="e50cd-128">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="e50cd-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="e50cd-129">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="e50cd-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="e50cd-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="e50cd-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="e50cd-131">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="e50cd-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="e50cd-132">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="e50cd-132">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="e50cd-133">Nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="e50cd-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="e50cd-134">Animacja — porady i wskazówki</span><span class="sxs-lookup"><span data-stu-id="e50cd-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="e50cd-135">Przewodnik: Buforowanie danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="e50cd-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
