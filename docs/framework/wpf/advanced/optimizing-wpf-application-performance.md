---
title: Optymalizacja wydajności aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 54d69e87ef2a9c5318e394422e3bcfcabcc76210
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646251"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="846dc-102">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="846dc-103">Ta sekcja jest przeznaczona [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jako punkt odniesienia dla deweloperów aplikacji, którzy szukają sposobów na poprawę wydajności swoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="846dc-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="846dc-104">Jeśli jesteś deweloperem, który jest nowy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie Microsoft .NET Framework i , należy najpierw zapoznać się z obu platform.</span><span class="sxs-lookup"><span data-stu-id="846dc-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="846dc-105">W tej sekcji przyjęto, że wiedza robocza obu tych obrażeń jest napisana dla programistów, którzy już wiedzą wystarczająco dużo, aby uruchomić swoje aplikacje.</span><span class="sxs-lookup"><span data-stu-id="846dc-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="846dc-106">Dane dotyczące wydajności podane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tej sekcji są oparte na aplikacjach działających na komputerze 2,8 GHz z 512 RAM i kartą graficzną ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="846dc-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="846dc-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="846dc-107">In This Section</span></span>  
 [<span data-ttu-id="846dc-108">Planowanie wydajności aplikacji</span><span class="sxs-lookup"><span data-stu-id="846dc-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="846dc-109">Wykorzystanie możliwości sprzętu</span><span class="sxs-lookup"><span data-stu-id="846dc-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="846dc-110">Układ i projekt</span><span class="sxs-lookup"><span data-stu-id="846dc-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="846dc-111">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="846dc-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="846dc-112">Zachowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="846dc-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="846dc-113">Zasoby aplikacji</span><span class="sxs-lookup"><span data-stu-id="846dc-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="846dc-114">Tekst</span><span class="sxs-lookup"><span data-stu-id="846dc-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="846dc-115">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="846dc-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="846dc-116">Formanty</span><span class="sxs-lookup"><span data-stu-id="846dc-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="846dc-117">Inne zalecenia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="846dc-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="846dc-118">Czas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="846dc-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="846dc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="846dc-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="846dc-120">Poziomy zmiany grafiki</span><span class="sxs-lookup"><span data-stu-id="846dc-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="846dc-121">Przegląd Renderowanie grafiki WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="846dc-122">Układ</span><span class="sxs-lookup"><span data-stu-id="846dc-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="846dc-123">Drzewa w WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="846dc-124">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="846dc-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="846dc-125">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="846dc-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="846dc-126">Przegląd Właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="846dc-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="846dc-127">Przegląd Obiekty Freezable</span><span class="sxs-lookup"><span data-stu-id="846dc-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="846dc-128">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="846dc-128">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="846dc-129">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="846dc-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="846dc-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="846dc-131">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="846dc-132">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="846dc-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="846dc-133">Przegląd Nawigacja</span><span class="sxs-lookup"><span data-stu-id="846dc-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="846dc-134">Porady i triki animacyjne</span><span class="sxs-lookup"><span data-stu-id="846dc-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="846dc-135">Przewodnik: przechowywanie w pamięci podręcznej danych aplikacji w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="846dc-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
