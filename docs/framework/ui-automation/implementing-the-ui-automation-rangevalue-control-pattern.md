---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 57986fa28a7a1bb7f70409b332147ff5b9615ec0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043423"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="fb360-102">Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb360-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="fb360-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fb360-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fb360-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fb360-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fb360-105">W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IRangeValueProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="fb360-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="fb360-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="fb360-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="fb360-107">Wzorzec <xref:System.Windows.Automation.RangeValuePattern> kontrolki służy do obsługi kontrolek, które mogą być ustawione na wartość z zakresu.</span><span class="sxs-lookup"><span data-stu-id="fb360-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="fb360-108">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fb360-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fb360-109">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="fb360-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="fb360-110">Podczas implementowania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="fb360-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="fb360-111">Kontrolki umożliwiają rekalibrację obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fb360-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="fb360-112">Przykładem jest kontrolka termometru, którą można ustawić, aby wyświetlić temperaturę w stopniach Fahrenheita lub Celsjusza.</span><span class="sxs-lookup"><span data-stu-id="fb360-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="fb360-113">Kontrolki, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć normalne wartości.</span><span class="sxs-lookup"><span data-stu-id="fb360-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="fb360-114">![Pasek postępu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="fb360-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="fb360-115">Przykład paska postępu, gdzie wartość jest typu Integer, a wartości właściwości minimum i maksimum są znormalizowane odpowiednio do 0 i 100.</span><span class="sxs-lookup"><span data-stu-id="fb360-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="fb360-116">Wymagane elementy członkowskie dla IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="fb360-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="fb360-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="fb360-117">Required member</span></span>|<span data-ttu-id="fb360-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fb360-118">Member type</span></span>|<span data-ttu-id="fb360-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb360-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="fb360-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-120">Property</span></span>|<span data-ttu-id="fb360-121">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="fb360-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-122">Property</span></span>|<span data-ttu-id="fb360-123">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="fb360-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-124">Property</span></span>|<span data-ttu-id="fb360-125">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="fb360-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-126">Property</span></span>|<span data-ttu-id="fb360-127">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="fb360-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-128">Property</span></span>|<span data-ttu-id="fb360-129">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="fb360-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fb360-130">Property</span></span>|<span data-ttu-id="fb360-131">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="fb360-132">Metody</span><span class="sxs-lookup"><span data-stu-id="fb360-132">Methods</span></span>|<span data-ttu-id="fb360-133">Brak</span><span class="sxs-lookup"><span data-stu-id="fb360-133">None</span></span>|  
  
 <span data-ttu-id="fb360-134">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fb360-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fb360-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="fb360-135">Exceptions</span></span>  
 <span data-ttu-id="fb360-136">Dostawcy muszą zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="fb360-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="fb360-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="fb360-137">Exception type</span></span>|<span data-ttu-id="fb360-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="fb360-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="fb360-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, która jest większa <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniejsza niż. <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty></span><span class="sxs-lookup"><span data-stu-id="fb360-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb360-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb360-140">See also</span></span>

- [<span data-ttu-id="fb360-141">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="fb360-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="fb360-142">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb360-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="fb360-143">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="fb360-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="fb360-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb360-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="fb360-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fb360-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
