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
ms.openlocfilehash: fa3e289f042af3e55e8fc56528c29d5701c33d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961149"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="e85f9-102">Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e85f9-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="e85f9-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e85f9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e85f9-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e85f9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e85f9-105">W tym temacie pokazano, jak subskrybować zdarzenia wywoływane przez dostawców automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e85f9-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e85f9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e85f9-106">Example</span></span>  
 <span data-ttu-id="e85f9-107">Poniższy przykładowy kod rejestruje procedurę obsługi zdarzeń dla zdarzenia, które jest zgłaszane, gdy wywoływana jest kontrolka, taka jak przycisk, i usuwa ją po zamknięciu formularza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e85f9-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="e85f9-108">Zdarzenie jest identyfikowane przez <xref:System.Windows.Automation.AutomationEvent> przekazaną jako parametr do. <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A></span><span class="sxs-lookup"><span data-stu-id="e85f9-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="e85f9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e85f9-109">Example</span></span>  
 <span data-ttu-id="e85f9-110">Poniższy przykład pokazuje, jak używać [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do subskrybowania zdarzenia, które jest zgłaszane w przypadku zmiany fokusu.</span><span class="sxs-lookup"><span data-stu-id="e85f9-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="e85f9-111">Procedura obsługi zdarzeń jest wyrejestrowana w metodzie, która może być wywoływana przy zamykaniu aplikacji lub gdy powiadomienie o zdarzeniach interfejsu użytkownika nie jest już wymagane.</span><span class="sxs-lookup"><span data-stu-id="e85f9-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="e85f9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e85f9-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="e85f9-113">Przegląd zdarzeń automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e85f9-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
