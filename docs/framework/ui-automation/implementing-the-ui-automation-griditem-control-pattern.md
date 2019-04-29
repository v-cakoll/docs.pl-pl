---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 932eb0af6afbe958695d5c084d2cb0c0bc188830
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609600"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="4001e-102">Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4001e-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="4001e-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4001e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4001e-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4001e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4001e-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, w tym informacji o właściwościach.</span><span class="sxs-lookup"><span data-stu-id="4001e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="4001e-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="4001e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="4001e-107"><xref:System.Windows.Automation.GridItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych poszczególnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="4001e-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="4001e-108">Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4001e-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4001e-109">Wytyczne dotyczące implementacji i konwencje</span><span class="sxs-lookup"><span data-stu-id="4001e-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="4001e-110">Podczas implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, należy pamiętać o następujących wytycznych i konwencje:</span><span class="sxs-lookup"><span data-stu-id="4001e-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="4001e-111">Współrzędne siatki zaczynają się od zera za pomocą lewa górna komórka o współrzędnych (0, 0).</span><span class="sxs-lookup"><span data-stu-id="4001e-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="4001e-112">Scalone komórki, będą zgłaszać ich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich podstawowej zakotwiczenia komórki zgodnie z definicją w dostawcy automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4001e-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="4001e-113">Zazwyczaj będzie najwyższego poziomu i skrajnie po lewej stronie wiersza lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="4001e-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="4001e-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> nie wymaga aktywnego manipulowania siatki, takie jak scalanie lub podział komórek.</span><span class="sxs-lookup"><span data-stu-id="4001e-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="4001e-115">Określa, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> można zwykle te typy można przemierzać (klientów automatyzacji interfejsu użytkownika może przechodzić do kontrolek sąsiadujące) przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="4001e-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="4001e-116">Wymagane elementy IGridItemProvider</span><span class="sxs-lookup"><span data-stu-id="4001e-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="4001e-117">Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="4001e-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="4001e-118">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4001e-118">Required members</span></span>|<span data-ttu-id="4001e-119">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="4001e-119">Member type</span></span>|<span data-ttu-id="4001e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4001e-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="4001e-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4001e-121">Property</span></span>|<span data-ttu-id="4001e-122">Brak</span><span class="sxs-lookup"><span data-stu-id="4001e-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="4001e-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4001e-123">Property</span></span>|<span data-ttu-id="4001e-124">Brak</span><span class="sxs-lookup"><span data-stu-id="4001e-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="4001e-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4001e-125">Property</span></span>|<span data-ttu-id="4001e-126">Brak</span><span class="sxs-lookup"><span data-stu-id="4001e-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="4001e-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4001e-127">Property</span></span>|<span data-ttu-id="4001e-128">Brak</span><span class="sxs-lookup"><span data-stu-id="4001e-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="4001e-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4001e-129">Property</span></span>|<span data-ttu-id="4001e-130">Brak</span><span class="sxs-lookup"><span data-stu-id="4001e-130">None</span></span>|  
  
 <span data-ttu-id="4001e-131">Ten wzorzec kontroli nie ma skojarzonych z nim metod lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4001e-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="4001e-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="4001e-132">Exceptions</span></span>  
 <span data-ttu-id="4001e-133">Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4001e-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4001e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4001e-134">See also</span></span>

- [<span data-ttu-id="4001e-135">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="4001e-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4001e-136">Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4001e-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="4001e-137">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="4001e-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4001e-138">Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4001e-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="4001e-139">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4001e-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="4001e-140">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4001e-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
