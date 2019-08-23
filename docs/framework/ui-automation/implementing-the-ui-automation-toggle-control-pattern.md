---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 2293dc77369ecf019bd1093808135eeefd99c115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932062"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="fd1a9-102">Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd1a9-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="fd1a9-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fd1a9-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fd1a9-105">W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IToggleProvider>dotyczące wdrażania, w tym informacje o metodach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="fd1a9-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="fd1a9-107">Wzorzec <xref:System.Windows.Automation.TogglePattern> kontrolki służy do obsługi kontrolek, które mogą przechodzić przez zestaw stanów i zachować stan po ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="fd1a9-108">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fd1a9-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fd1a9-109">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="fd1a9-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="fd1a9-110">Podczas implementowania wzorca kontrolki Przełącz należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="fd1a9-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="fd1a9-111">Kontrolki, które nie utrzymują stanu po aktywowaniu, takie jak przyciski, przyciski paska narzędzi i hiperlinki, <xref:System.Windows.Automation.Provider.IInvokeProvider> muszą być implementowane w zamian.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="fd1a9-112"><xref:System.Windows.Automation.ToggleState> Kontrolka musi przechodzić w następujący sposób w następującej kolejności <xref:System.Windows.Automation.ToggleState.On>: <xref:System.Windows.Automation.ToggleState.Off> , i, jeśli jest <xref:System.Windows.Automation.ToggleState.Indeterminate>obsługiwana,.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="fd1a9-113"><xref:System.Windows.Automation.TogglePattern>nie zapewnia metody setstate (NewState) z powodu problemów otaczających bezpośrednie ustawienie pola wyboru Tri-State bez przechodzenia przez odpowiednią <xref:System.Windows.Automation.ToggleState> sekwencję.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="fd1a9-114">Kontrolka RadioButton nie jest zaimplementowana <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest w stanie przechodzić przez prawidłowe Stany.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="fd1a9-115">Wymagane elementy członkowskie dla IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="fd1a9-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="fd1a9-116">Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="fd1a9-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="fd1a9-117">Required member</span></span>|<span data-ttu-id="fd1a9-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fd1a9-118">Member type</span></span>|<span data-ttu-id="fd1a9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd1a9-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="fd1a9-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd1a9-120">Method</span></span>|<span data-ttu-id="fd1a9-121">Brak</span><span class="sxs-lookup"><span data-stu-id="fd1a9-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="fd1a9-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fd1a9-122">Property</span></span>|<span data-ttu-id="fd1a9-123">Brak</span><span class="sxs-lookup"><span data-stu-id="fd1a9-123">None</span></span>|  
  
 <span data-ttu-id="fd1a9-124">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fd1a9-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="fd1a9-125">Exceptions</span></span>  
 <span data-ttu-id="fd1a9-126">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fd1a9-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1a9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd1a9-127">See also</span></span>

- [<span data-ttu-id="fd1a9-128">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd1a9-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="fd1a9-129">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd1a9-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="fd1a9-130">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="fd1a9-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="fd1a9-131">Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd1a9-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="fd1a9-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd1a9-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="fd1a9-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd1a9-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
