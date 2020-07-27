---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami dotyczącymi wdrażania wzorca kontroli RangeValue dla w automatyzacji interfejsu użytkownika. Zobacz wymagane elementy członkowskie dla interfejsu IRangeValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: ccb6aeb5f8451975d7e2e9649bbb82c0c3ae23d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164074"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="34bbc-104">Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="34bbc-104">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="34bbc-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34bbc-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="34bbc-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="34bbc-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="34bbc-107">W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IRangeValueProvider> , w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="34bbc-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="34bbc-108">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="34bbc-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="34bbc-109"><xref:System.Windows.Automation.RangeValuePattern>Wzorzec kontrolki służy do obsługi kontrolek, które mogą być ustawione na wartość z zakresu.</span><span class="sxs-lookup"><span data-stu-id="34bbc-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="34bbc-110">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="34bbc-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="34bbc-111">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="34bbc-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="34bbc-112">Podczas implementowania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="34bbc-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="34bbc-113">Kontrolki umożliwiają rekalibrację obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34bbc-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="34bbc-114">Przykładem jest kontrolka termometru, którą można ustawić, aby wyświetlić temperaturę w stopniach Fahrenheita lub Celsjusza.</span><span class="sxs-lookup"><span data-stu-id="34bbc-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="34bbc-115">Kontrolki, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć normalne wartości.</span><span class="sxs-lookup"><span data-stu-id="34bbc-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="34bbc-116">![Pasek postępu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="34bbc-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="34bbc-117">Przykład paska postępu, gdzie wartość jest typu Integer, a wartości właściwości minimum i maksimum są znormalizowane odpowiednio do 0 i 100.</span><span class="sxs-lookup"><span data-stu-id="34bbc-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="34bbc-118">Wymagane elementy członkowskie dla IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="34bbc-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="34bbc-119">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="34bbc-119">Required member</span></span>|<span data-ttu-id="34bbc-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="34bbc-120">Member type</span></span>|<span data-ttu-id="34bbc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34bbc-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="34bbc-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-122">Property</span></span>|<span data-ttu-id="34bbc-123">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="34bbc-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-124">Property</span></span>|<span data-ttu-id="34bbc-125">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="34bbc-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-126">Property</span></span>|<span data-ttu-id="34bbc-127">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="34bbc-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-128">Property</span></span>|<span data-ttu-id="34bbc-129">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="34bbc-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-130">Property</span></span>|<span data-ttu-id="34bbc-131">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="34bbc-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="34bbc-132">Property</span></span>|<span data-ttu-id="34bbc-133">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="34bbc-134">Metody</span><span class="sxs-lookup"><span data-stu-id="34bbc-134">Methods</span></span>|<span data-ttu-id="34bbc-135">Brak</span><span class="sxs-lookup"><span data-stu-id="34bbc-135">None</span></span>|  
  
 <span data-ttu-id="34bbc-136">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="34bbc-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="34bbc-137">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="34bbc-137">Exceptions</span></span>  
 <span data-ttu-id="34bbc-138">Dostawcy muszą zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="34bbc-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="34bbc-139">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="34bbc-139">Exception type</span></span>|<span data-ttu-id="34bbc-140">Warunek</span><span class="sxs-lookup"><span data-stu-id="34bbc-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="34bbc-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, która jest większa <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniejsza niż <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty> .</span><span class="sxs-lookup"><span data-stu-id="34bbc-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34bbc-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34bbc-142">See also</span></span>

- [<span data-ttu-id="34bbc-143">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="34bbc-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="34bbc-144">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="34bbc-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="34bbc-145">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="34bbc-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="34bbc-146">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="34bbc-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="34bbc-147">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="34bbc-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
