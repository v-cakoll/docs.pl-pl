---
title: Pobierz właściwości elementu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968969"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="eecd1-102">Pobierz właściwości elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="eecd1-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="eecd1-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eecd1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="eecd1-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="eecd1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="eecd1-105">W tym temacie pokazano, jak pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="eecd1-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="eecd1-106">Pobierz bieżącą wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="eecd1-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="eecd1-107">Uzyskaj Właściwość <xref:System.Windows.Automation.AutomationElement> , której chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="eecd1-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="eecd1-108">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>lub <xref:System.Windows.Automation.AutomationElement.Current%2A> Pobierz strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="eecd1-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="eecd1-109">Pobierz buforowaną wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="eecd1-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="eecd1-110">Uzyskaj Właściwość <xref:System.Windows.Automation.AutomationElement> , której chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="eecd1-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="eecd1-111">Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="eecd1-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="eecd1-112">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>lub <xref:System.Windows.Automation.AutomationElement.Cached%2A> Pobierz strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="eecd1-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eecd1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="eecd1-113">Example</span></span>  
 <span data-ttu-id="eecd1-114">W poniższym przykładzie pokazano różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="eecd1-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="eecd1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eecd1-115">See also</span></span>

- [<span data-ttu-id="eecd1-116">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="eecd1-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="eecd1-117">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="eecd1-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="eecd1-118">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="eecd1-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
