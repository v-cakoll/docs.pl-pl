---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: db468a72f4ee39a5c58e0c5620dc38c0cae14c75
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201091"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="911bc-102">Implementacja wzorca kontrolki przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="911bc-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="911bc-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="911bc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="911bc-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="911bc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="911bc-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IToggleProvider>, wraz z informacjami dotyczącymi metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="911bc-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="911bc-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="911bc-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="911bc-107"><xref:System.Windows.Automation.TogglePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które mogą przechodzić przez zestaw stanów i obsługa po ustawieniu stanu.</span><span class="sxs-lookup"><span data-stu-id="911bc-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="911bc-108">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="911bc-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="911bc-109">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="911bc-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="911bc-110">Jeśli implementacja wzorca kontrolki przełącznika, należy zwrócić uwagę następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="911bc-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="911bc-111">Formanty, które nie zachowują stan, gdy aktywowany, takie jak przyciski, przyciski paska narzędzi i hiperłączy, musi implementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="911bc-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="911bc-112">Kontrolki musi przechodzić przez jego <xref:System.Windows.Automation.ToggleState> w następującej kolejności: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> i, jeśli jest obsługiwany, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="911bc-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="911bc-113"><xref:System.Windows.Automation.TogglePattern> udostępnia metody SetState(newState) z powodu problemów z otaczającego bezpośrednie ustawienie pola wyboru trzy-stanowy bez okrągło jego odpowiedniego <xref:System.Windows.Automation.ToggleState> sekwencji.</span><span class="sxs-lookup"><span data-stu-id="911bc-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="911bc-114">RadioButton — formant nie implementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest zdolny okrągło jego stany prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="911bc-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="911bc-115">Wymagane elementy IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="911bc-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="911bc-116">Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="911bc-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="911bc-117">Wymagany</span><span class="sxs-lookup"><span data-stu-id="911bc-117">Required member</span></span>|<span data-ttu-id="911bc-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="911bc-118">Member type</span></span>|<span data-ttu-id="911bc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="911bc-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="911bc-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="911bc-120">Method</span></span>|<span data-ttu-id="911bc-121">Brak</span><span class="sxs-lookup"><span data-stu-id="911bc-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="911bc-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="911bc-122">Property</span></span>|<span data-ttu-id="911bc-123">Brak</span><span class="sxs-lookup"><span data-stu-id="911bc-123">None</span></span>|  
  
 <span data-ttu-id="911bc-124">Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="911bc-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="911bc-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="911bc-125">Exceptions</span></span>  
 <span data-ttu-id="911bc-126">Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="911bc-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911bc-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="911bc-127">See Also</span></span>  
 [<span data-ttu-id="911bc-128">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="911bc-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="911bc-129">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="911bc-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="911bc-130">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="911bc-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="911bc-131">Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="911bc-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="911bc-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="911bc-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="911bc-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="911bc-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
