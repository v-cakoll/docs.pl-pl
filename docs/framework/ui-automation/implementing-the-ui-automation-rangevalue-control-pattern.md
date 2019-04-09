---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: aeb14bddf98adf53a52c8897994bd0fb6fa498ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175802"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="3add7-102">Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3add7-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="3add7-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3add7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3add7-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="3add7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3add7-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IRangeValueProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="3add7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="3add7-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3add7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="3add7-107"><xref:System.Windows.Automation.RangeValuePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które mogą być ustawione na wartość w zakresie.</span><span class="sxs-lookup"><span data-stu-id="3add7-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="3add7-108">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3add7-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3add7-109">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="3add7-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="3add7-110">Jeśli implementacja wzorca kontrolki wartości zakresu, należy zwrócić uwagę następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="3add7-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="3add7-111">Formanty umożliwiają przekalibrowanie ich obsługiwanych właściwości, w zależności od preferencji użytkownika lub ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="3add7-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="3add7-112">Na przykład jest formantem termometru ustawioną wyświetlający temperaturę w stopniach Celsjusza lub w Fahrenheita.</span><span class="sxs-lookup"><span data-stu-id="3add7-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="3add7-113">Formanty, które mają wartości zakresu niejednoznaczny, takich jak paski postępu lub suwaki, powinien mieć tych wartości znormalizowane.</span><span class="sxs-lookup"><span data-stu-id="3add7-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="3add7-114">![Pasek postępu. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="3add7-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="3add7-115">Przykład pasek postępu, gdy wartość jest typu Integer i właściwości minimalne i maksymalne wartości są znormalizowane zgodnie z 0-100, odpowiednio</span><span class="sxs-lookup"><span data-stu-id="3add7-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="3add7-116">Wymagane elementy IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="3add7-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="3add7-117">Wymagany</span><span class="sxs-lookup"><span data-stu-id="3add7-117">Required member</span></span>|<span data-ttu-id="3add7-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3add7-118">Member type</span></span>|<span data-ttu-id="3add7-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3add7-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="3add7-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-120">Property</span></span>|<span data-ttu-id="3add7-121">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="3add7-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-122">Property</span></span>|<span data-ttu-id="3add7-123">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="3add7-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-124">Property</span></span>|<span data-ttu-id="3add7-125">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="3add7-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-126">Property</span></span>|<span data-ttu-id="3add7-127">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="3add7-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-128">Property</span></span>|<span data-ttu-id="3add7-129">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="3add7-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3add7-130">Property</span></span>|<span data-ttu-id="3add7-131">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="3add7-132">Metody</span><span class="sxs-lookup"><span data-stu-id="3add7-132">Methods</span></span>|<span data-ttu-id="3add7-133">Brak</span><span class="sxs-lookup"><span data-stu-id="3add7-133">None</span></span>|  
  
 <span data-ttu-id="3add7-134">Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3add7-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="3add7-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3add7-135">Exceptions</span></span>  
 <span data-ttu-id="3add7-136">Dostawcy należy zgłaszać następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3add7-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="3add7-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="3add7-137">Exception type</span></span>|<span data-ttu-id="3add7-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="3add7-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> <span data-ttu-id="3add7-139">jest wywoływana z wartością, która jest większa niż <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniej niż <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="3add7-139">is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3add7-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3add7-140">See also</span></span>

- [<span data-ttu-id="3add7-141">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="3add7-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3add7-142">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3add7-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3add7-143">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="3add7-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3add7-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3add7-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="3add7-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3add7-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
