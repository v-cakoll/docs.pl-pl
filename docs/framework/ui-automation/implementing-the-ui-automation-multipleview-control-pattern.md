---
title: Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 26e8ae7d0c560d8539b17e29d47545894cb4bb0f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545198"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="232d5-102">Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="232d5-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="232d5-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="232d5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="232d5-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="232d5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="232d5-105">W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IMultipleViewProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="232d5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="232d5-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="232d5-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="232d5-107">Wzorzec <xref:System.Windows.Automation.MultipleViewPattern> kontrolki służy do obsługi kontrolek, które zapewniają i mogą przełączać się między wieloma reprezentacjami tego samego zestawu informacji lub formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="232d5-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="232d5-108">Przykłady kontrolek, które mogą przedstawić wiele widoków, obejmują widok listy (który może wyświetlać jego zawartość jako miniatury, kafelki, ikony lub szczegóły [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] ), wykresy (wykres kołowy, liniowy, słupkowy, wartość [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] komórki z formułą), dokumenty (normalne, układ sieci Web, Układ wydruku, układ do czytania, konspekt), Kalendarz programu Microsoft Outlook (rok, miesiąc, tydzień, dzień) [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] i karnacje.</span><span class="sxs-lookup"><span data-stu-id="232d5-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="232d5-109">Obsługiwane widoki są określane przez dewelopera kontroli i są specyficzne dla każdej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="232d5-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="232d5-110">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="232d5-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="232d5-111">Podczas implementowania wzorca kontroli wielu widoków należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="232d5-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="232d5-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>należy również zaimplementować w kontenerze, który zarządza bieżącym widokiem, jeśli różni się od kontrolki, która udostępnia bieżący widok.</span><span class="sxs-lookup"><span data-stu-id="232d5-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="232d5-113">Na przykład Eksplorator Windows zawiera kontrolkę listy dla zawartości bieżącego folderu, podczas gdy widok dla kontrolki jest zarządzany przez aplikację Eksplorator Windows.</span><span class="sxs-lookup"><span data-stu-id="232d5-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="232d5-114">Kontrolka, która może sortować zawartość, nie jest uważana za obsługę wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="232d5-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="232d5-115">Kolekcja widoków musi być taka sama w różnych wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="232d5-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="232d5-116">Nazwy widoków muszą być odpowiednie do użycia w zamiana tekstu na mowę, w języku Braille'a i w innych aplikacjach do czytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="232d5-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="232d5-117">Wymagane elementy członkowskie dla IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="232d5-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="232d5-118">Do zaimplementowania IMultipleViewProvider są wymagane następujące właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="232d5-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="232d5-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="232d5-119">Required members</span></span>|<span data-ttu-id="232d5-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="232d5-120">Member type</span></span>|<span data-ttu-id="232d5-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="232d5-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="232d5-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="232d5-122">Property</span></span>|<span data-ttu-id="232d5-123">Brak</span><span class="sxs-lookup"><span data-stu-id="232d5-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="232d5-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="232d5-124">Method</span></span>|<span data-ttu-id="232d5-125">Brak</span><span class="sxs-lookup"><span data-stu-id="232d5-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="232d5-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="232d5-126">Method</span></span>|<span data-ttu-id="232d5-127">Brak</span><span class="sxs-lookup"><span data-stu-id="232d5-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="232d5-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="232d5-128">Method</span></span>|<span data-ttu-id="232d5-129">Brak</span><span class="sxs-lookup"><span data-stu-id="232d5-129">None</span></span>|  
  
 <span data-ttu-id="232d5-130">Z tym wzorcem kontroli nie są skojarzone żadne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="232d5-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="232d5-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="232d5-131">Exceptions</span></span>  
 <span data-ttu-id="232d5-132">Dostawca musi zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="232d5-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="232d5-133">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="232d5-133">Exception type</span></span>|<span data-ttu-id="232d5-134">Warunek</span><span class="sxs-lookup"><span data-stu-id="232d5-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="232d5-135"><xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> Gdy lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest elementem członkowskim kolekcji obsługiwane widoki.</span><span class="sxs-lookup"><span data-stu-id="232d5-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="232d5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="232d5-136">See also</span></span>

- [<span data-ttu-id="232d5-137">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="232d5-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="232d5-138">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="232d5-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="232d5-139">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="232d5-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="232d5-140">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="232d5-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="232d5-141">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="232d5-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
