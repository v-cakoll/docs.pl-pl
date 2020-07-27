---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami, aby zaimplementować wzorzec kontrolki przełącznika w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu IToggleProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: f9ae850a560101582b5f1a461de19f260ef59798
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168030"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="7c7c8-104">Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c7c8-104">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="7c7c8-105">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7c7c8-106">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7c7c8-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7c7c8-107">W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IToggleProvider> , w tym informacje o metodach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="7c7c8-108">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="7c7c8-109"><xref:System.Windows.Automation.TogglePattern>Wzorzec kontrolki służy do obsługi kontrolek, które mogą przechodzić przez zestaw stanów i zachować stan po ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-109">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="7c7c8-110">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7c7c8-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7c7c8-111">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="7c7c8-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7c7c8-112">Podczas implementowania wzorca kontrolki Przełącz należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="7c7c8-112">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="7c7c8-113">Kontrolki, które nie utrzymują stanu po aktywowaniu, takie jak przyciski, przyciski paska narzędzi i hiperlinki, muszą być implementowane w <xref:System.Windows.Automation.Provider.IInvokeProvider> zamian.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-113">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="7c7c8-114">Kontrolka musi przechodzić <xref:System.Windows.Automation.ToggleState> w następujący sposób w następującej kolejności: <xref:System.Windows.Automation.ToggleState.On> , <xref:System.Windows.Automation.ToggleState.Off> i, jeśli jest obsługiwana, <xref:System.Windows.Automation.ToggleState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="7c7c8-114">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="7c7c8-115"><xref:System.Windows.Automation.TogglePattern>nie zapewnia metody setstate (newState) z powodu problemów otaczających bezpośrednie ustawienie pola wyboru Tri-State bez przechodzenia przez odpowiednią <xref:System.Windows.Automation.ToggleState> sekwencję.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-115"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="7c7c8-116">Kontrolka RadioButton nie jest zaimplementowana <xref:System.Windows.Automation.Provider.IToggleProvider> , ponieważ nie jest w stanie przechodzić przez prawidłowe Stany.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-116">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="7c7c8-117">Wymagane elementy członkowskie dla IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="7c7c8-117">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="7c7c8-118">Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IToggleProvider> .</span><span class="sxs-lookup"><span data-stu-id="7c7c8-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="7c7c8-119">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="7c7c8-119">Required member</span></span>|<span data-ttu-id="7c7c8-120">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="7c7c8-120">Member type</span></span>|<span data-ttu-id="7c7c8-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c7c8-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="7c7c8-122">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c8-122">Method</span></span>|<span data-ttu-id="7c7c8-123">Brak</span><span class="sxs-lookup"><span data-stu-id="7c7c8-123">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="7c7c8-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7c7c8-124">Property</span></span>|<span data-ttu-id="7c7c8-125">Brak</span><span class="sxs-lookup"><span data-stu-id="7c7c8-125">None</span></span>|  
  
 <span data-ttu-id="7c7c8-126">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-126">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="7c7c8-127">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="7c7c8-127">Exceptions</span></span>  
 <span data-ttu-id="7c7c8-128">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7c7c8-128">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7c8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c7c8-129">See also</span></span>

- [<span data-ttu-id="7c7c8-130">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="7c7c8-130">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7c7c8-131">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c7c8-131">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="7c7c8-132">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="7c7c8-132">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7c7c8-133">Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c7c8-133">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="7c7c8-134">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c7c8-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="7c7c8-135">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7c7c8-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
