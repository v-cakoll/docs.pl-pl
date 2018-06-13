---
title: Implementacja wzorca formantu MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 777f529b3b925a965b24cf1a4b38b9d3b9adae7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408382"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="ee7e6-102">Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ee7e6-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="ee7e6-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ee7e6-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ee7e6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ee7e6-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="ee7e6-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="ee7e6-107"><xref:System.Windows.Automation.MultipleViewPattern> — Wzorzec formantu jest używana do obsługi formantów, które zapewniają i można przełączać się między wiele reprezentacje ten sam zestaw informacji formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="ee7e6-108">Kontrolki udostępniające wiele widoków przykłady widok listy (które można wyświetlić jego zawartość jako miniatury, Kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (kołowego, wiersz, pasek, wartość komórki z formułą) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentów (normalny, układ sieci Web Drukowanie układu, układ do czytania, konspektu), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendarza (rok, miesiąc, tydzień, dzień), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] karnacji.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="ee7e6-109">Obsługiwane widoki są określane przez dewelopera kontrolek i są specyficzne dla każdego formantu.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ee7e6-110">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="ee7e6-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ee7e6-111">Gdy implementacja wzorca kontrolki widoku wielu, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="ee7e6-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="ee7e6-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> powinny zostać wdrożone również na kontenerze, który zarządza bieżący widok, jeśli różni się od formant, który umożliwia bieżącego widoku.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="ee7e6-113">Na przykład Eksploratora Windows zawiera formant listy bieżącej zawartości folderu, gdy wyświetlanie formantu odbywa się z aplikacji Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="ee7e6-114">Formant, który może sortować jego zawartość nie jest uważana za obsługuje wiele widoków.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="ee7e6-115">Kolekcja widoków muszą być identyczne w wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="ee7e6-116">Wyświetlanie nazw musi być odpowiednie do użycia w tekst na mowę, Braille'a i innych aplikacjach zrozumiałą dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="ee7e6-117">Wymagane elementy IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="ee7e6-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="ee7e6-118">Poniższe właściwości i metody są wymagane do wykonania IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="ee7e6-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ee7e6-119">Required members</span></span>|<span data-ttu-id="ee7e6-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ee7e6-120">Member type</span></span>|<span data-ttu-id="ee7e6-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee7e6-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="ee7e6-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ee7e6-122">Property</span></span>|<span data-ttu-id="ee7e6-123">Brak</span><span class="sxs-lookup"><span data-stu-id="ee7e6-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="ee7e6-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee7e6-124">Method</span></span>|<span data-ttu-id="ee7e6-125">Brak</span><span class="sxs-lookup"><span data-stu-id="ee7e6-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="ee7e6-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee7e6-126">Method</span></span>|<span data-ttu-id="ee7e6-127">Brak</span><span class="sxs-lookup"><span data-stu-id="ee7e6-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="ee7e6-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee7e6-128">Method</span></span>|<span data-ttu-id="ee7e6-129">Brak</span><span class="sxs-lookup"><span data-stu-id="ee7e6-129">None</span></span>|  
  
 <span data-ttu-id="ee7e6-130">Brak zdarzeń skojarzonych z tym — wzorzec formantu.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ee7e6-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ee7e6-131">Exceptions</span></span>  
 <span data-ttu-id="ee7e6-132">Dostawca musi zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ee7e6-133">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="ee7e6-133">Exception type</span></span>|<span data-ttu-id="ee7e6-134">Warunek</span><span class="sxs-lookup"><span data-stu-id="ee7e6-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="ee7e6-135">Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest członkiem kolekcji obsługiwane widoki.</span><span class="sxs-lookup"><span data-stu-id="ee7e6-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee7e6-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee7e6-136">See Also</span></span>  
 [<span data-ttu-id="ee7e6-137">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="ee7e6-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="ee7e6-138">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ee7e6-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="ee7e6-139">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="ee7e6-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="ee7e6-140">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ee7e6-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="ee7e6-141">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ee7e6-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
