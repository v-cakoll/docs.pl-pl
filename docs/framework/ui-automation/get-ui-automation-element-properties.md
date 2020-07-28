---
title: Pobierz właściwości elementu automatyzacji interfejsu użytkownika
description: Zobacz instrukcje i przykład pokazujący, jak pobrać bieżące lub buforowane właściwości elementu automatyzacji interfejsu użytkownika.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164108"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="bbf87-103">Pobierz właściwości elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bbf87-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="bbf87-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bbf87-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bbf87-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bbf87-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bbf87-106">W tym temacie pokazano, jak pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="bbf87-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="bbf87-107">Pobierz bieżącą wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="bbf87-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="bbf87-108">Uzyskaj właściwość, której chcesz <xref:System.Windows.Automation.AutomationElement> pobrać.</span><span class="sxs-lookup"><span data-stu-id="bbf87-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="bbf87-109">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub Pobierz <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bbf87-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="bbf87-110">Pobierz buforowaną wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="bbf87-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="bbf87-111">Uzyskaj właściwość, której chcesz <xref:System.Windows.Automation.AutomationElement> pobrać.</span><span class="sxs-lookup"><span data-stu-id="bbf87-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="bbf87-112">Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bbf87-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="bbf87-113">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz <xref:System.Windows.Automation.AutomationElement.Cached%2A> strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bbf87-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf87-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbf87-114">Example</span></span>  
 <span data-ttu-id="bbf87-115">W poniższym przykładzie pokazano różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="bbf87-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="bbf87-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbf87-116">See also</span></span>

- [<span data-ttu-id="bbf87-117">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="bbf87-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="bbf87-118">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bbf87-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="bbf87-119">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bbf87-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
