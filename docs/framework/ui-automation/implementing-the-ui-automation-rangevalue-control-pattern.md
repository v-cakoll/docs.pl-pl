---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180178"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="17fc7-102">Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="17fc7-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="17fc7-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="17fc7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="17fc7-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="17fc7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="17fc7-105">W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IRangeValueProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="17fc7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="17fc7-106">Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="17fc7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="17fc7-107">Wzorzec <xref:System.Windows.Automation.RangeValuePattern> formantu służy do obsługi formantów, które można ustawić na wartość w zakresie.</span><span class="sxs-lookup"><span data-stu-id="17fc7-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="17fc7-108">Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="17fc7-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="17fc7-109">Wytyczne i konwencje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="17fc7-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="17fc7-110">Podczas wdrażania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="17fc7-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="17fc7-111">Formanty umożliwiają ponowną kalibrację ich obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17fc7-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="17fc7-112">Przykładem tego jest kontrola termometru, którą można ustawić, aby wyświetlić temperaturę w Fahrenheita lub Celsjusza.</span><span class="sxs-lookup"><span data-stu-id="17fc7-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="17fc7-113">Formanty, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć te wartości znormalizowane.</span><span class="sxs-lookup"><span data-stu-id="17fc7-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="17fc7-114">![Pasek postępu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="17fc7-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="17fc7-115">Przykład paska postępu, na którym wartość jest typu Liczba całkowita, a minimalne i maksymalne wartości właściwości są znormalizowane odpowiednio do 0 i 100</span><span class="sxs-lookup"><span data-stu-id="17fc7-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="17fc7-116">Wymagane elementy członkowskie dla IRangeValueProvider</span><span class="sxs-lookup"><span data-stu-id="17fc7-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="17fc7-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="17fc7-117">Required member</span></span>|<span data-ttu-id="17fc7-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="17fc7-118">Member type</span></span>|<span data-ttu-id="17fc7-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17fc7-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="17fc7-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-120">Property</span></span>|<span data-ttu-id="17fc7-121">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="17fc7-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-122">Property</span></span>|<span data-ttu-id="17fc7-123">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="17fc7-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-124">Property</span></span>|<span data-ttu-id="17fc7-125">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="17fc7-126">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-126">Property</span></span>|<span data-ttu-id="17fc7-127">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="17fc7-128">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-128">Property</span></span>|<span data-ttu-id="17fc7-129">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="17fc7-130">Właściwość</span><span class="sxs-lookup"><span data-stu-id="17fc7-130">Property</span></span>|<span data-ttu-id="17fc7-131">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="17fc7-132">Metody</span><span class="sxs-lookup"><span data-stu-id="17fc7-132">Methods</span></span>|<span data-ttu-id="17fc7-133">Brak</span><span class="sxs-lookup"><span data-stu-id="17fc7-133">None</span></span>|  
  
 <span data-ttu-id="17fc7-134">Ten wzorzec formantu nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17fc7-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="17fc7-135">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="17fc7-135">Exceptions</span></span>  
 <span data-ttu-id="17fc7-136">Dostawcy muszą zgłaszać następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="17fc7-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="17fc7-137">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="17fc7-137">Exception type</span></span>|<span data-ttu-id="17fc7-138">Warunek</span><span class="sxs-lookup"><span data-stu-id="17fc7-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="17fc7-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> która jest <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>większa lub mniejsza niż .</span><span class="sxs-lookup"><span data-stu-id="17fc7-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17fc7-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17fc7-140">See also</span></span>

- [<span data-ttu-id="17fc7-141">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="17fc7-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="17fc7-142">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="17fc7-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="17fc7-143">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="17fc7-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="17fc7-144">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="17fc7-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="17fc7-145">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="17fc7-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
