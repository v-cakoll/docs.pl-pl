---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3736d1e8b23b8e05882a3fe016be0ac1a18ef51d
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698958"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="a2282-102">Implementacja wzorca kontrolki RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2282-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="a2282-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a2282-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a2282-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a2282-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a2282-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IRangeValueProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2282-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="a2282-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a2282-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a2282-107"><xref:System.Windows.Automation.RangeValuePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które mogą być ustawione na wartość w zakresie.</span><span class="sxs-lookup"><span data-stu-id="a2282-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="a2282-108">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a2282-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a2282-109">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="a2282-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a2282-110">Jeśli implementacja wzorca kontrolki wartości zakresu, należy zwrócić uwagę następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="a2282-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="a2282-111">Formanty umożliwiają przekalibrowanie ich obsługiwanych właściwości, w zależności od preferencji użytkownika lub ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="a2282-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="a2282-112">Na przykład jest formantem termometru ustawioną wyświetlający temperaturę w stopniach Celsjusza lub w Fahrenheita.</span><span class="sxs-lookup"><span data-stu-id="a2282-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="a2282-113">Formanty, które mają wartości zakresu niejednoznaczny, takich jak paski postępu lub suwaki, powinien mieć tych wartości znormalizowane.</span><span class="sxs-lookup"><span data-stu-id="a2282-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="a2282-114">![Pasek postępu. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="a2282-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="a2282-115">Przykład pasek postępu, gdy wartość jest typu Integer i właściwości minimalne i maksymalne wartości są znormalizowane zgodnie z 0-100, odpowiednio</span><span class="sxs-lookup"><span data-stu-id="a2282-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="a2282-116">Wymagane elementy IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="a2282-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="a2282-117">Wymagany</span><span class="sxs-lookup"><span data-stu-id="a2282-117">Required member</span></span>|<span data-ttu-id="a2282-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="a2282-118">Member type</span></span>|<span data-ttu-id="a2282-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2282-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="a2282-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-120">Property</span></span>|<span data-ttu-id="a2282-121">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="a2282-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-122">Property</span></span>|<span data-ttu-id="a2282-123">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="a2282-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-124">Property</span></span>|<span data-ttu-id="a2282-125">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="a2282-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-126">Property</span></span>|<span data-ttu-id="a2282-127">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="a2282-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-128">Property</span></span>|<span data-ttu-id="a2282-129">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="a2282-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a2282-130">Property</span></span>|<span data-ttu-id="a2282-131">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="a2282-132">Metody</span><span class="sxs-lookup"><span data-stu-id="a2282-132">Methods</span></span>|<span data-ttu-id="a2282-133">Brak</span><span class="sxs-lookup"><span data-stu-id="a2282-133">None</span></span>|  
  
 <span data-ttu-id="a2282-134">Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2282-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="a2282-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="a2282-135">Exceptions</span></span>  
 <span data-ttu-id="a2282-136">Dostawcy należy zgłaszać następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="a2282-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a2282-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="a2282-137">Exception type</span></span>|<span data-ttu-id="a2282-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="a2282-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="a2282-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> jest wywoływana z wartością, która jest większa niż <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniej niż <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="a2282-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2282-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2282-140">See Also</span></span>  
 [<span data-ttu-id="a2282-141">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="a2282-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="a2282-142">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2282-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="a2282-143">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="a2282-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="a2282-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2282-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="a2282-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a2282-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
