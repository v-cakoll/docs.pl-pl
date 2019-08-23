---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932123"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="31d8a-102">Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="31d8a-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="31d8a-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="31d8a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="31d8a-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="31d8a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="31d8a-105">W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IRangeValueProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="31d8a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="31d8a-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="31d8a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="31d8a-107">Wzorzec <xref:System.Windows.Automation.RangeValuePattern> kontrolki służy do obsługi kontrolek, które mogą być ustawione na wartość z zakresu.</span><span class="sxs-lookup"><span data-stu-id="31d8a-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="31d8a-108">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="31d8a-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="31d8a-109">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="31d8a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="31d8a-110">Podczas implementowania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="31d8a-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="31d8a-111">Kontrolki umożliwiają rekalibrację obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="31d8a-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="31d8a-112">Przykładem jest kontrolka termometru, którą można ustawić, aby wyświetlić temperaturę w stopniach Fahrenheita lub Celsjusza.</span><span class="sxs-lookup"><span data-stu-id="31d8a-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="31d8a-113">Kontrolki, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć normalne wartości.</span><span class="sxs-lookup"><span data-stu-id="31d8a-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="31d8a-114">![Pasek postępu.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="31d8a-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="31d8a-115">Przykład paska postępu, gdzie wartość jest typu Integer, a wartości właściwości minimum i maksimum są znormalizowane odpowiednio do 0 i 100.</span><span class="sxs-lookup"><span data-stu-id="31d8a-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="31d8a-116">Wymagane elementy członkowskie dla IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="31d8a-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="31d8a-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="31d8a-117">Required member</span></span>|<span data-ttu-id="31d8a-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="31d8a-118">Member type</span></span>|<span data-ttu-id="31d8a-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31d8a-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="31d8a-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-120">Property</span></span>|<span data-ttu-id="31d8a-121">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="31d8a-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-122">Property</span></span>|<span data-ttu-id="31d8a-123">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="31d8a-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-124">Property</span></span>|<span data-ttu-id="31d8a-125">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="31d8a-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-126">Property</span></span>|<span data-ttu-id="31d8a-127">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="31d8a-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-128">Property</span></span>|<span data-ttu-id="31d8a-129">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="31d8a-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31d8a-130">Property</span></span>|<span data-ttu-id="31d8a-131">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="31d8a-132">Metody</span><span class="sxs-lookup"><span data-stu-id="31d8a-132">Methods</span></span>|<span data-ttu-id="31d8a-133">Brak</span><span class="sxs-lookup"><span data-stu-id="31d8a-133">None</span></span>|  
  
 <span data-ttu-id="31d8a-134">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="31d8a-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="31d8a-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="31d8a-135">Exceptions</span></span>  
 <span data-ttu-id="31d8a-136">Dostawcy muszą zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="31d8a-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="31d8a-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="31d8a-137">Exception type</span></span>|<span data-ttu-id="31d8a-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="31d8a-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="31d8a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, która jest większa <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniejsza niż. <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty></span><span class="sxs-lookup"><span data-stu-id="31d8a-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31d8a-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31d8a-140">See also</span></span>

- [<span data-ttu-id="31d8a-141">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="31d8a-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="31d8a-142">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="31d8a-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="31d8a-143">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="31d8a-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="31d8a-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="31d8a-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="31d8a-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="31d8a-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
