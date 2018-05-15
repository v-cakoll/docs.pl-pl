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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73678433692f5532f712f0d2c7a3c5bf138a87b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="bd79d-102">Pobierz właściwości elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd79d-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="bd79d-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bd79d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bd79d-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bd79d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bd79d-105">W tym temacie pokazano, jak można pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="bd79d-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="bd79d-106">Pobierz bieżącą wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="bd79d-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="bd79d-107">Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz uzyskać.</span><span class="sxs-lookup"><span data-stu-id="bd79d-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="bd79d-108">Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturę właściwości i get wartość jednego z jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bd79d-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="bd79d-109">Pobieranie wartości właściwości pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="bd79d-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="bd79d-110">Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz uzyskać.</span><span class="sxs-lookup"><span data-stu-id="bd79d-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="bd79d-111">Właściwość muszą podano w <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="bd79d-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="bd79d-112">Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Cached%2A> strukturę właściwości i get wartość jednego z jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bd79d-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd79d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd79d-113">Example</span></span>  
 <span data-ttu-id="bd79d-114">W poniższym przykładzie przedstawiono różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="bd79d-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="bd79d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd79d-115">See Also</span></span>  
 [<span data-ttu-id="bd79d-116">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="bd79d-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="bd79d-117">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd79d-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="bd79d-118">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bd79d-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
