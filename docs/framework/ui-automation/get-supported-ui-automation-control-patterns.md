---
title: Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435638"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="04524-102">Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="04524-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="04524-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="04524-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="04524-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="04524-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="04524-105">W tym temacie przedstawiono sposób pobierania obiektów wzorców kontroli z elementów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04524-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="04524-106">Uzyskaj wszystkie wzorce kontroli</span><span class="sxs-lookup"><span data-stu-id="04524-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="04524-107">Pobierz <xref:System.Windows.Automation.AutomationElement> którego interesuje Cię wzorce.</span><span class="sxs-lookup"><span data-stu-id="04524-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="04524-108">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>, aby uzyskać wszystkie wzorce kontrolek z elementu.</span><span class="sxs-lookup"><span data-stu-id="04524-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="04524-109">Zdecydowanie zaleca się, aby klient nie używał <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="04524-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="04524-110">Wydajność może być poważnie narażona na to, że ta metoda wywołuje <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> wewnętrznie dla każdego istniejącego wzorca kontrolki.</span><span class="sxs-lookup"><span data-stu-id="04524-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="04524-111">Jeśli to możliwe, klient powinien wywoływać <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> w celu uzyskania kluczowych wzorców zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="04524-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="04524-112">Uzyskiwanie określonego wzorca kontroli</span><span class="sxs-lookup"><span data-stu-id="04524-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="04524-113">Pobierz <xref:System.Windows.Automation.AutomationElement> którego interesuje Cię wzorce.</span><span class="sxs-lookup"><span data-stu-id="04524-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="04524-114">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>, aby wykonać zapytanie dotyczące określonego wzorca.</span><span class="sxs-lookup"><span data-stu-id="04524-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="04524-115">Te metody są podobne, ale jeśli wzorzec nie zostanie znaleziony, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> zgłasza wyjątek, a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="04524-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04524-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="04524-116">Example</span></span>  
 <span data-ttu-id="04524-117">Poniższy przykład pobiera <xref:System.Windows.Automation.AutomationElement> dla elementu listy i uzyskuje <xref:System.Windows.Automation.SelectionItemPattern> z tego elementu.</span><span class="sxs-lookup"><span data-stu-id="04524-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="04524-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04524-118">See also</span></span>

- [<span data-ttu-id="04524-119">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="04524-119">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
