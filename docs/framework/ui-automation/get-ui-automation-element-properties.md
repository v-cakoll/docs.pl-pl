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
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435499"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="00f8e-102">Pobierz właściwości elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="00f8e-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="00f8e-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="00f8e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="00f8e-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="00f8e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="00f8e-105">W tym temacie pokazano, jak pobrać właściwości elementu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00f8e-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="00f8e-106">Pobierz bieżącą wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="00f8e-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="00f8e-107">Uzyskaj <xref:System.Windows.Automation.AutomationElement> którego właściwość chcesz uzyskać.</span><span class="sxs-lookup"><span data-stu-id="00f8e-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="00f8e-108">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>lub Pobierz strukturę właściwości <xref:System.Windows.Automation.AutomationElement.Current%2A> i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="00f8e-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="00f8e-109">Pobierz buforowaną wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="00f8e-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="00f8e-110">Uzyskaj <xref:System.Windows.Automation.AutomationElement> którego właściwość chcesz uzyskać.</span><span class="sxs-lookup"><span data-stu-id="00f8e-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="00f8e-111">Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="00f8e-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="00f8e-112">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>lub Pobierz strukturę właściwości <xref:System.Windows.Automation.AutomationElement.Cached%2A> i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="00f8e-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00f8e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="00f8e-113">Example</span></span>  
 <span data-ttu-id="00f8e-114">W poniższym przykładzie przedstawiono różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="00f8e-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="00f8e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00f8e-115">See also</span></span>

- [<span data-ttu-id="00f8e-116">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="00f8e-116">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="00f8e-117">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="00f8e-117">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="00f8e-118">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="00f8e-118">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
