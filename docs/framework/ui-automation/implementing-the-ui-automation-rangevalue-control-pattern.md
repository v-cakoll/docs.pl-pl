---
title: "Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9ae70f1dfc4c0a8d97d2fbcfd23822450727e59e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="cc3e8-102">Implementacja wzorca kontrolki RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc3e8-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="cc3e8-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc3e8-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cc3e8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cc3e8-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IRangeValueProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="cc3e8-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="cc3e8-107"><xref:System.Windows.Automation.RangeValuePattern> — Wzorzec formantu jest używana do obsługi formantów, które można ustawić na wartość w zakresie.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="cc3e8-108">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cc3e8-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cc3e8-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="cc3e8-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cc3e8-110">Gdy implementacja wzorca formantu wartości zakresu, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="cc3e8-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="cc3e8-111">Formanty umożliwiają przekalibrowanie ich obsługiwanych właściwości ustalane na podstawie preferencji użytkownika lub ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="cc3e8-112">Na przykład jest formantem termometru, który można ustawić, aby wyświetlić temperatura w f lub c.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="cc3e8-113">Formanty, które ma niejednoznaczne zakres wartości, takich jak paski postępu lub suwaki, powinien mieć tych wartości z znormalizowanych.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="cc3e8-114">![Pasek postępu. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="cc3e8-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="cc3e8-115">Przykład pasek postępu, gdzie jest wartość typu Integer i właściwości minimalne i maksymalne wartości są odpowiednio znormalizowane do 0 do 100,</span><span class="sxs-lookup"><span data-stu-id="cc3e8-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="cc3e8-116">Wymagane elementy IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="cc3e8-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="cc3e8-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="cc3e8-117">Required member</span></span>|<span data-ttu-id="cc3e8-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="cc3e8-118">Member type</span></span>|<span data-ttu-id="cc3e8-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc3e8-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="cc3e8-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-120">Property</span></span>|<span data-ttu-id="cc3e8-121">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="cc3e8-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-122">Property</span></span>|<span data-ttu-id="cc3e8-123">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="cc3e8-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-124">Property</span></span>|<span data-ttu-id="cc3e8-125">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="cc3e8-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-126">Property</span></span>|<span data-ttu-id="cc3e8-127">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="cc3e8-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-128">Property</span></span>|<span data-ttu-id="cc3e8-129">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="cc3e8-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cc3e8-130">Property</span></span>|<span data-ttu-id="cc3e8-131">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="cc3e8-132">Metody</span><span class="sxs-lookup"><span data-stu-id="cc3e8-132">Methods</span></span>|<span data-ttu-id="cc3e8-133">Brak</span><span class="sxs-lookup"><span data-stu-id="cc3e8-133">None</span></span>|  
  
 <span data-ttu-id="cc3e8-134">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="cc3e8-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cc3e8-135">Exceptions</span></span>  
 <span data-ttu-id="cc3e8-136">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="cc3e8-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="cc3e8-137">Exception type</span></span>|<span data-ttu-id="cc3e8-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="cc3e8-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="cc3e8-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, która jest większa niż <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniej niż <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="cc3e8-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc3e8-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc3e8-140">See Also</span></span>  
 [<span data-ttu-id="cc3e8-141">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc3e8-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="cc3e8-142">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc3e8-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="cc3e8-143">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="cc3e8-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="cc3e8-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc3e8-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="cc3e8-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc3e8-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
