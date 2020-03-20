---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180063"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="bd42e-102">Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd42e-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="bd42e-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="bd42e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bd42e-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bd42e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bd42e-105">W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IToggleProvider>i konwencje dotyczące wdrażania, w tym informacje o metodach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="bd42e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="bd42e-106">Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="bd42e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="bd42e-107">Wzorzec <xref:System.Windows.Automation.TogglePattern> formantu służy do obsługi formantów, które mogą przełączać się między zestawem stanów i utrzymywać stan po ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="bd42e-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="bd42e-108">Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="bd42e-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="bd42e-109">Wytyczne i konwencje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="bd42e-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="bd42e-110">Podczas implementowania wzorca sterowania przełącz, należy zwrócić uwagę na następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="bd42e-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="bd42e-111">Formanty, które nie zachowują stanu po aktywacji, takie jak przyciski, przyciski paska narzędzi i hiperłącza, muszą zaimplementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="bd42e-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="bd42e-112">Formant musi przechodzić przez <xref:System.Windows.Automation.ToggleState> jego <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> w następującej kolejności: , a jeśli jest obsługiwany, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="bd42e-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="bd42e-113"><xref:System.Windows.Automation.TogglePattern>nie zapewnia SetState(newState) metoda ze względu na problemy związane z bezpośrednim ustawieniem <xref:System.Windows.Automation.ToggleState> trójstanowego CheckBox bez przechodzenia na rowerze przez jego odpowiedniej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bd42e-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="bd42e-114">Sterowanie RadioButton nie <xref:System.Windows.Automation.Provider.IToggleProvider>implementuje , ponieważ nie jest w stanie jeździć na rowerze przez jego prawidłowe stany.</span><span class="sxs-lookup"><span data-stu-id="bd42e-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="bd42e-115">Wymagana liczba członków dla iToggleProvider</span><span class="sxs-lookup"><span data-stu-id="bd42e-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="bd42e-116">Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IToggleProvider>do wdrożenia .</span><span class="sxs-lookup"><span data-stu-id="bd42e-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="bd42e-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="bd42e-117">Required member</span></span>|<span data-ttu-id="bd42e-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="bd42e-118">Member type</span></span>|<span data-ttu-id="bd42e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd42e-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="bd42e-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd42e-120">Method</span></span>|<span data-ttu-id="bd42e-121">Brak</span><span class="sxs-lookup"><span data-stu-id="bd42e-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="bd42e-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="bd42e-122">Property</span></span>|<span data-ttu-id="bd42e-123">Brak</span><span class="sxs-lookup"><span data-stu-id="bd42e-123">None</span></span>|  
  
 <span data-ttu-id="bd42e-124">Ten wzorzec formantu nie ma skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bd42e-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="bd42e-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="bd42e-125">Exceptions</span></span>  
 <span data-ttu-id="bd42e-126">Ten wzorzec formantu nie ma skojarzonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bd42e-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd42e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd42e-127">See also</span></span>

- [<span data-ttu-id="bd42e-128">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="bd42e-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bd42e-129">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd42e-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="bd42e-130">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="bd42e-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bd42e-131">Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd42e-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="bd42e-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd42e-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bd42e-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd42e-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
