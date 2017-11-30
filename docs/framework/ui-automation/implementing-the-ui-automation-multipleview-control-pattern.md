---
title: "Implementacja wzorca formantu MultipleView dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 899f260dfef1d1e28a5a3605de772cdb7d358b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="c78b3-102">Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c78b3-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="c78b3-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c78b3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c78b3-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="c78b3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c78b3-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c78b3-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="c78b3-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c78b3-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c78b3-107"><xref:System.Windows.Automation.MultipleViewPattern> — Wzorzec formantu jest używana do obsługi formantów, które zapewniają i można przełączać się między wiele reprezentacje ten sam zestaw informacji formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c78b3-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="c78b3-108">Kontrolki udostępniające wiele widoków przykłady widok listy (które można wyświetlić jego zawartość jako miniatury, Kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (kołowego, wiersz, pasek, wartość komórki z formułą) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentów (normalny, układ sieci Web Drukowanie układu, układ do czytania, konspektu), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendarza (rok, miesiąc, tydzień, dzień), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] karnacji.</span><span class="sxs-lookup"><span data-stu-id="c78b3-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="c78b3-109">Obsługiwane widoki są określane przez dewelopera kontrolek i są specyficzne dla każdego formantu.</span><span class="sxs-lookup"><span data-stu-id="c78b3-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c78b3-110">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="c78b3-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c78b3-111">Gdy implementacja wzorca kontrolki widoku wielu, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="c78b3-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="c78b3-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>powinny zostać wdrożone również na kontenerze, który zarządza bieżący widok, jeśli różni się od formant, który umożliwia bieżącego widoku.</span><span class="sxs-lookup"><span data-stu-id="c78b3-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="c78b3-113">Na przykład Eksploratora Windows zawiera formant listy bieżącej zawartości folderu, gdy wyświetlanie formantu odbywa się z aplikacji Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="c78b3-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="c78b3-114">Formant, który może sortować jego zawartość nie jest uważana za obsługuje wiele widoków.</span><span class="sxs-lookup"><span data-stu-id="c78b3-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="c78b3-115">Kolekcja widoków muszą być identyczne w wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="c78b3-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="c78b3-116">Wyświetlanie nazw musi być odpowiednie do użycia w tekst na mowę, Braille'a i innych aplikacjach zrozumiałą dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c78b3-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="c78b3-117">Wymagane elementy IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="c78b3-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="c78b3-118">Poniższe właściwości i metody są wymagane do wykonania IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="c78b3-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="c78b3-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c78b3-119">Required members</span></span>|<span data-ttu-id="c78b3-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c78b3-120">Member type</span></span>|<span data-ttu-id="c78b3-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c78b3-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="c78b3-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c78b3-122">Property</span></span>|<span data-ttu-id="c78b3-123">Brak</span><span class="sxs-lookup"><span data-stu-id="c78b3-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="c78b3-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="c78b3-124">Method</span></span>|<span data-ttu-id="c78b3-125">Brak</span><span class="sxs-lookup"><span data-stu-id="c78b3-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="c78b3-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="c78b3-126">Method</span></span>|<span data-ttu-id="c78b3-127">Brak</span><span class="sxs-lookup"><span data-stu-id="c78b3-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="c78b3-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="c78b3-128">Method</span></span>|<span data-ttu-id="c78b3-129">Brak</span><span class="sxs-lookup"><span data-stu-id="c78b3-129">None</span></span>|  
  
 <span data-ttu-id="c78b3-130">Brak zdarzeń skojarzonych z tym — wzorzec formantu.</span><span class="sxs-lookup"><span data-stu-id="c78b3-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c78b3-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c78b3-131">Exceptions</span></span>  
 <span data-ttu-id="c78b3-132">Dostawca musi zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="c78b3-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="c78b3-133">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="c78b3-133">Exception type</span></span>|<span data-ttu-id="c78b3-134">Warunek</span><span class="sxs-lookup"><span data-stu-id="c78b3-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="c78b3-135">Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest członkiem kolekcji obsługiwane widoki.</span><span class="sxs-lookup"><span data-stu-id="c78b3-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c78b3-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c78b3-136">See Also</span></span>  
 [<span data-ttu-id="c78b3-137">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c78b3-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="c78b3-138">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c78b3-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="c78b3-139">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="c78b3-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="c78b3-140">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c78b3-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="c78b3-141">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c78b3-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
