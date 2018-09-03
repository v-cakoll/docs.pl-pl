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
ms.openlocfilehash: 292a1c0a57c992e847dd72a24508482cb6783121
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43471916"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="9bc4a-102">Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9bc4a-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="9bc4a-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9bc4a-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9bc4a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9bc4a-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="9bc4a-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="9bc4a-107"><xref:System.Windows.Automation.MultipleViewPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które zapewniają i można przełączać się między wiele reprezentacji ten sam zestaw kontrolek informacji lub podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="9bc4a-108">Kontrolki udostępniające wiele widoków przykłady widok listy (które można wyświetlić jego zawartość jako miniatury, Kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (koła, wiersz, pasek, wartość komórki przy użyciu formuły) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentów (normalny, układu strony sieci Web Drukuj układu, układu do czytania, kontur), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendarza (rok, miesiąc, tydzień, dzień), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skórki.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="9bc4a-109">Obsługiwane widoki są określane przez dewelopera kontrolek i są specyficzne dla każdego formantu.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9bc4a-110">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="9bc4a-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9bc4a-111">Jeśli implementacja wzorca kontrolki widoku wielu, należy zwrócić uwagę następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="9bc4a-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="9bc4a-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> również powinny być zrealizowane w kontenerze, który zarządza bieżący widok, jeśli jest inny niż formant, który zawiera bieżący widok.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="9bc4a-113">Na przykład Eksploratora Windows zawiera kontrolkę listy do bieżącej zawartości folderu, kiedy widoku dla kontrolki jest zarządzana z poziomu aplikacji w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="9bc4a-114">Formant, który jest w stanie sortowania jego zawartość nie jest uważany za obsługuje wiele widoków.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="9bc4a-115">Kolekcja widoków muszą być identyczne w wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="9bc4a-116">Wyświetlanie nazw musi być odpowiednia do stosowania w zamiany tekstu na mowę, Braille'a i inne aplikacje czytelny dla człowieka.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="9bc4a-117">Wymagane elementy IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="9bc4a-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="9bc4a-118">Poniższe właściwości i metod są wymagane do wykonania IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="9bc4a-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9bc4a-119">Required members</span></span>|<span data-ttu-id="9bc4a-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="9bc4a-120">Member type</span></span>|<span data-ttu-id="9bc4a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bc4a-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="9bc4a-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9bc4a-122">Property</span></span>|<span data-ttu-id="9bc4a-123">Brak</span><span class="sxs-lookup"><span data-stu-id="9bc4a-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="9bc4a-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="9bc4a-124">Method</span></span>|<span data-ttu-id="9bc4a-125">Brak</span><span class="sxs-lookup"><span data-stu-id="9bc4a-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="9bc4a-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="9bc4a-126">Method</span></span>|<span data-ttu-id="9bc4a-127">Brak</span><span class="sxs-lookup"><span data-stu-id="9bc4a-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="9bc4a-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="9bc4a-128">Method</span></span>|<span data-ttu-id="9bc4a-129">Brak</span><span class="sxs-lookup"><span data-stu-id="9bc4a-129">None</span></span>|  
  
 <span data-ttu-id="9bc4a-130">Brak zdarzeń skojarzonych z tym — wzorzec kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9bc4a-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9bc4a-131">Exceptions</span></span>  
 <span data-ttu-id="9bc4a-132">Dostawca musi zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="9bc4a-133">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="9bc4a-133">Exception type</span></span>|<span data-ttu-id="9bc4a-134">Warunek</span><span class="sxs-lookup"><span data-stu-id="9bc4a-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="9bc4a-135">Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest elementem członkowskim kolekcji obsługiwane widoki.</span><span class="sxs-lookup"><span data-stu-id="9bc4a-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bc4a-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bc4a-136">See Also</span></span>  
 [<span data-ttu-id="9bc4a-137">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="9bc4a-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="9bc4a-138">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9bc4a-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="9bc4a-139">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="9bc4a-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="9bc4a-140">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9bc4a-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="9bc4a-141">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9bc4a-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
