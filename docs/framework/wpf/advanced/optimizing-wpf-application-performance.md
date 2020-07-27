---
title: Optymalizowanie wydajności aplikacji
description: Użyj tych zasobów, aby zwiększyć wydajność aplikacji Windows Presentation Foundation, takich jak planowanie wydajności i korzystanie z zalet sprzętu.
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166323"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="20b9c-103">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="20b9c-104">Ta sekcja jest przeznaczona jako Dokumentacja dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperów aplikacji, którzy poszukują sposobów ulepszania wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20b9c-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="20b9c-105">Jeśli jesteś deweloperem, który jest nowy dla środowiska Microsoft .NET Framework i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , najpierw zapoznaj się z obiema platformami.</span><span class="sxs-lookup"><span data-stu-id="20b9c-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="20b9c-106">W tej sekcji założono, że działa wiedza i jest przeznaczony dla programistów, którzy już znają wystarczającą do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20b9c-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20b9c-107">Dane dotyczące wydajności podane w tej sekcji są oparte na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach uruchamianych na komputerze 2,8 GHz z 512 pamięcią RAM i kartą grafiki ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="20b9c-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20b9c-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="20b9c-108">In This Section</span></span>  
 [<span data-ttu-id="20b9c-109">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="20b9c-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="20b9c-110">Wykorzystanie możliwości sprzętu</span><span class="sxs-lookup"><span data-stu-id="20b9c-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="20b9c-111">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="20b9c-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="20b9c-112">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="20b9c-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="20b9c-113">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="20b9c-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="20b9c-114">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="20b9c-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="20b9c-115">Tekst</span><span class="sxs-lookup"><span data-stu-id="20b9c-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="20b9c-116">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="20b9c-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="20b9c-117">Formanty</span><span class="sxs-lookup"><span data-stu-id="20b9c-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="20b9c-118">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="20b9c-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="20b9c-119">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="20b9c-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="20b9c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20b9c-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="20b9c-121">Poziomy zmiany grafiki</span><span class="sxs-lookup"><span data-stu-id="20b9c-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="20b9c-122">Przegląd Renderowanie grafiki WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="20b9c-123">Układ</span><span class="sxs-lookup"><span data-stu-id="20b9c-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="20b9c-124">Drzewa w WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="20b9c-125">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="20b9c-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="20b9c-126">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="20b9c-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="20b9c-127">Przegląd Właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="20b9c-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="20b9c-128">Przegląd Obiekty Freezable</span><span class="sxs-lookup"><span data-stu-id="20b9c-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="20b9c-129">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="20b9c-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="20b9c-130">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="20b9c-131">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="20b9c-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="20b9c-132">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="20b9c-133">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="20b9c-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="20b9c-134">Przegląd Nawigacja</span><span class="sxs-lookup"><span data-stu-id="20b9c-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="20b9c-135">Porady i triki animacyjne</span><span class="sxs-lookup"><span data-stu-id="20b9c-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="20b9c-136">Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="20b9c-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
