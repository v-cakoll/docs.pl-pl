---
title: "Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="6291c-102">Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="6291c-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="6291c-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6291c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6291c-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6291c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6291c-105">W tym temacie pokazano, jak można pobrać obiektów — wzorzec formantu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów.</span><span class="sxs-lookup"><span data-stu-id="6291c-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="6291c-106">Uzyskaj wszystkie wzorce formantu</span><span class="sxs-lookup"><span data-stu-id="6291c-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="6291c-107">Pobierz <xref:System.Windows.Automation.AutomationElement> którego kontrolę wzorce można są zainteresowani.</span><span class="sxs-lookup"><span data-stu-id="6291c-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="6291c-108">Wywołanie <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> można pobrać wszystkich wzorców formantu z elementu.</span><span class="sxs-lookup"><span data-stu-id="6291c-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6291c-109">Zdecydowanie zaleca się, że klient nie używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="6291c-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="6291c-110">Wydajność może być poważny wpływ jak ta metoda wywołuje <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> wewnętrznie dla każdego istniejącego wzorca formantu.</span><span class="sxs-lookup"><span data-stu-id="6291c-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="6291c-111">Jeśli to możliwe, należy wywołać klienta <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> klucza wzorców zainteresowań.</span><span class="sxs-lookup"><span data-stu-id="6291c-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="6291c-112">Uzyskaj wzorzec określonego formantu</span><span class="sxs-lookup"><span data-stu-id="6291c-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="6291c-113">Pobierz <xref:System.Windows.Automation.AutomationElement> którego kontrolę wzorce można są zainteresowani.</span><span class="sxs-lookup"><span data-stu-id="6291c-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="6291c-114">Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zapytania dla określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="6291c-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="6291c-115">Te metody są podobne, ale jeśli wzorzec nie zostanie znaleziony, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> zgłasza wyjątek, i <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="6291c-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6291c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="6291c-116">Example</span></span>  
 <span data-ttu-id="6291c-117">Poniższy przykład pobiera <xref:System.Windows.Automation.AutomationElement> dla elementu listy i uzyskuje <xref:System.Windows.Automation.SelectionItemPattern> od tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6291c-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="6291c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6291c-118">See Also</span></span>  
 [<span data-ttu-id="6291c-119">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="6291c-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
