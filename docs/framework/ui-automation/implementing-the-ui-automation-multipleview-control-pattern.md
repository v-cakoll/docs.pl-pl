---
title: Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: edef213c0f4d43a15b7c6842ef6c62e95544da66
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039496"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="594d0-102">Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="594d0-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="594d0-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="594d0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="594d0-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="594d0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="594d0-105">W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="594d0-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="594d0-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="594d0-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="594d0-107"><xref:System.Windows.Automation.MultipleViewPattern> wzorzec kontroli służy do obsługi kontrolek, które zapewniają i mogą przełączać się między wieloma reprezentacjami tego samego zestawu informacji lub formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="594d0-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="594d0-108">Przykłady formantów, które mogą przedstawić wiele widoków, obejmują widok listy (który może wyświetlać jego zawartość jako miniatury, kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresy (kołowy, liniowy, słupkowy, wartość komórki z formułą), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumenty (normalne, układ sieci Web, układ wydruku, układ do czytania, konspekt), Microsoft Outlook Calendar (Year, month, Week, Day) i Microsoft Windows Media Player Skins.</span><span class="sxs-lookup"><span data-stu-id="594d0-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="594d0-109">Obsługiwane widoki są określane przez dewelopera kontroli i są specyficzne dla każdej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="594d0-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="594d0-110">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="594d0-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="594d0-111">Podczas implementowania wzorca kontroli wielu widoków należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="594d0-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="594d0-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> należy również zaimplementować w kontenerze, który zarządza bieżącym widokiem, jeśli różni się od kontrolki, która udostępnia bieżący widok.</span><span class="sxs-lookup"><span data-stu-id="594d0-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="594d0-113">Na przykład Eksplorator Windows zawiera kontrolkę listy dla zawartości bieżącego folderu, podczas gdy widok dla kontrolki jest zarządzany przez aplikację Eksplorator Windows.</span><span class="sxs-lookup"><span data-stu-id="594d0-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="594d0-114">Kontrolka, która może sortować zawartość, nie jest uważana za obsługę wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="594d0-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="594d0-115">Kolekcja widoków musi być taka sama w różnych wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="594d0-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="594d0-116">Nazwy widoków muszą być odpowiednie do użycia w zamiana tekstu na mowę, w języku Braille'a i w innych aplikacjach do czytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="594d0-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="594d0-117">Wymagane elementy członkowskie dla IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="594d0-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="594d0-118">Do zaimplementowania IMultipleViewProvider są wymagane następujące właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="594d0-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="594d0-119">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="594d0-119">Required members</span></span>|<span data-ttu-id="594d0-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="594d0-120">Member type</span></span>|<span data-ttu-id="594d0-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="594d0-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="594d0-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="594d0-122">Property</span></span>|<span data-ttu-id="594d0-123">Brak</span><span class="sxs-lookup"><span data-stu-id="594d0-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="594d0-124">Metoda</span><span class="sxs-lookup"><span data-stu-id="594d0-124">Method</span></span>|<span data-ttu-id="594d0-125">Brak</span><span class="sxs-lookup"><span data-stu-id="594d0-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="594d0-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="594d0-126">Method</span></span>|<span data-ttu-id="594d0-127">Brak</span><span class="sxs-lookup"><span data-stu-id="594d0-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="594d0-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="594d0-128">Method</span></span>|<span data-ttu-id="594d0-129">Brak</span><span class="sxs-lookup"><span data-stu-id="594d0-129">None</span></span>|  
  
 <span data-ttu-id="594d0-130">Z tym wzorcem kontroli nie są skojarzone żadne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="594d0-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="594d0-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="594d0-131">Exceptions</span></span>  
 <span data-ttu-id="594d0-132">Dostawca musi zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="594d0-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="594d0-133">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="594d0-133">Exception type</span></span>|<span data-ttu-id="594d0-134">Warunek</span><span class="sxs-lookup"><span data-stu-id="594d0-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="594d0-135">Gdy <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest elementem członkowskim kolekcji obsługiwane widoki.</span><span class="sxs-lookup"><span data-stu-id="594d0-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="594d0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="594d0-136">See also</span></span>

- [<span data-ttu-id="594d0-137">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="594d0-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="594d0-138">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="594d0-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="594d0-139">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="594d0-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="594d0-140">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="594d0-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="594d0-141">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="594d0-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
