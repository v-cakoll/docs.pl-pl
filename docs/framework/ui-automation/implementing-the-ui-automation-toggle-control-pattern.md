---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447076"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="c74a0-102">Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c74a0-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="c74a0-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c74a0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c74a0-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c74a0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c74a0-105">W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IToggleProvider>, w tym informacje o metodach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="c74a0-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="c74a0-106">Linki do dodatkowych odwołań znajdują się na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="c74a0-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c74a0-107"><xref:System.Windows.Automation.TogglePattern> wzorzec kontroli służy do obsługi kontrolek, które mogą przechodzić przez zestaw stanów i zachować stan po ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="c74a0-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="c74a0-108">Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c74a0-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c74a0-109">Wytyczne i konwencje dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="c74a0-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c74a0-110">Podczas implementowania wzorca kontrolki Przełącz należy zwrócić uwagę na następujące wytyczne i konwencje:</span><span class="sxs-lookup"><span data-stu-id="c74a0-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="c74a0-111">Kontrolki, które nie utrzymują stanu po aktywowaniu, takie jak przyciski, przyciski paska narzędzi i hiperlinki, muszą implementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c74a0-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="c74a0-112">Kontrolka musi przechodzić przez <xref:System.Windows.Automation.ToggleState> w następującej kolejności: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> i, jeśli jest obsługiwana, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="c74a0-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="c74a0-113"><xref:System.Windows.Automation.TogglePattern> nie zapewnia metody setstate (newState) z powodu problemów otaczających bezpośrednie ustawienie pola wyboru Tri-State bez przechodzenia przez odpowiedni <xref:System.Windows.Automation.ToggleState> sekwencję.</span><span class="sxs-lookup"><span data-stu-id="c74a0-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="c74a0-114">Kontrolka RadioButton nie implementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest w stanie cyklicznie przechodzić przez prawidłowe Stany.</span><span class="sxs-lookup"><span data-stu-id="c74a0-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="c74a0-115">Wymagane elementy członkowskie dla IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="c74a0-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="c74a0-116">Do zaimplementowania <xref:System.Windows.Automation.Provider.IToggleProvider>są wymagane następujące właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="c74a0-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="c74a0-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="c74a0-117">Required member</span></span>|<span data-ttu-id="c74a0-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c74a0-118">Member type</span></span>|<span data-ttu-id="c74a0-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c74a0-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="c74a0-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="c74a0-120">Method</span></span>|<span data-ttu-id="c74a0-121">Brak</span><span class="sxs-lookup"><span data-stu-id="c74a0-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="c74a0-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c74a0-122">Property</span></span>|<span data-ttu-id="c74a0-123">Brak</span><span class="sxs-lookup"><span data-stu-id="c74a0-123">None</span></span>|  
  
 <span data-ttu-id="c74a0-124">Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c74a0-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c74a0-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c74a0-125">Exceptions</span></span>  
 <span data-ttu-id="c74a0-126">Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c74a0-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74a0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c74a0-127">See also</span></span>

- [<span data-ttu-id="c74a0-128">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="c74a0-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c74a0-129">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c74a0-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c74a0-130">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="c74a0-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c74a0-131">Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c74a0-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="c74a0-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c74a0-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="c74a0-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="c74a0-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
