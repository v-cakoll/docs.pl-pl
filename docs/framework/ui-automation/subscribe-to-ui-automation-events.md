---
title: Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: a5effd1d7a3cfaba5e068087b3008903e58b6739
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432991"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="3ef6a-102">Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3ef6a-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="3ef6a-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3ef6a-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3ef6a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3ef6a-105">W tym temacie pokazano, jak subskrybować zdarzenia wywoływane przez dostawców automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ef6a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ef6a-106">Example</span></span>  
 <span data-ttu-id="3ef6a-107">Poniższy przykładowy kod rejestruje procedurę obsługi zdarzeń dla zdarzenia, które jest zgłaszane, gdy wywoływana jest kontrolka, taka jak przycisk, i usuwa ją po zamknięciu formularza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="3ef6a-108">Zdarzenie jest identyfikowane przez <xref:System.Windows.Automation.AutomationEvent> przekazaną jako parametr do <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="3ef6a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ef6a-109">Example</span></span>  
 <span data-ttu-id="3ef6a-110">Poniższy przykład pokazuje, jak używać [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do subskrybowania zdarzenia, które jest zgłaszane w przypadku zmiany fokusu.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="3ef6a-111">Procedura obsługi zdarzeń jest wyrejestrowana w metodzie, która może być wywoływana przy zamykaniu aplikacji lub gdy powiadomienie o zdarzeniach interfejsu użytkownika nie jest już wymagane.</span><span class="sxs-lookup"><span data-stu-id="3ef6a-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="3ef6a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ef6a-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="3ef6a-113">Przegląd zdarzeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3ef6a-113">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
