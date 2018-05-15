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
manager: markl
ms.openlocfilehash: eed3f6771526f7a026bd411b3f12c39b4bb64bf4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="1fb3c-102">Implementacja wzorca kontrolki przełącznika automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fb3c-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="1fb3c-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1fb3c-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1fb3c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1fb3c-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IToggleProvider>, wraz z informacjami dotyczącymi metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="1fb3c-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="1fb3c-107"><xref:System.Windows.Automation.TogglePattern> — Wzorzec formantu jest używana do obsługi formantów, które można zestawu stanów i obsługa stanie po ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="1fb3c-108">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1fb3c-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="1fb3c-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="1fb3c-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="1fb3c-110">Podczas implementowania Toggle — wzorzec formantu, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="1fb3c-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="1fb3c-111">Formanty, które nie obsługują stanu po uaktywnieniu, takie jak przyciski, przyciski paska narzędzi i hiperłącza, musi implementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="1fb3c-112">Formant musi przechodzić przez jego <xref:System.Windows.Automation.ToggleState> w następującej kolejności: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> i, jeśli jest to obsługiwane, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="1fb3c-113"><xref:System.Windows.Automation.TogglePattern> udostępnia metody SetState(newState) z powodu problemów z otaczającego bezpośrednie ustawienie elementu CheckBox trzy stanowy bez okrągło jej odpowiednie <xref:System.Windows.Automation.ToggleState> sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="1fb3c-114">RadioButton — formant nie implementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest zdolny okrągło jego nieprawidłowy stan.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="1fb3c-115">Wymagane elementy IToggleProvider</span><span class="sxs-lookup"><span data-stu-id="1fb3c-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="1fb3c-116">Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="1fb3c-117">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="1fb3c-117">Required member</span></span>|<span data-ttu-id="1fb3c-118">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="1fb3c-118">Member type</span></span>|<span data-ttu-id="1fb3c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fb3c-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="1fb3c-120">Metoda</span><span class="sxs-lookup"><span data-stu-id="1fb3c-120">Method</span></span>|<span data-ttu-id="1fb3c-121">Brak</span><span class="sxs-lookup"><span data-stu-id="1fb3c-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="1fb3c-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1fb3c-122">Property</span></span>|<span data-ttu-id="1fb3c-123">Brak</span><span class="sxs-lookup"><span data-stu-id="1fb3c-123">None</span></span>|  
  
 <span data-ttu-id="1fb3c-124">Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="1fb3c-125">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="1fb3c-125">Exceptions</span></span>  
 <span data-ttu-id="1fb3c-126">Ten wzorzec formantu ma bez wyjątków skojarzone.</span><span class="sxs-lookup"><span data-stu-id="1fb3c-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb3c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fb3c-127">See Also</span></span>  
 [<span data-ttu-id="1fb3c-128">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="1fb3c-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="1fb3c-129">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fb3c-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="1fb3c-130">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="1fb3c-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="1fb3c-131">Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fb3c-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="1fb3c-132">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fb3c-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="1fb3c-133">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fb3c-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
