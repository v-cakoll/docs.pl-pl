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
ms.openlocfilehash: 93e0fba4288ba3231bfed45252bdaa78892d008c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610052"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="b9c4b-102">Pobierz właściwości elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9c4b-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="b9c4b-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b9c4b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b9c4b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b9c4b-105">W tym temacie pokazano, jak pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="b9c4b-106">Pobieranie bieżącej wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="b9c4b-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="b9c4b-107">Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz otrzymywać.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="b9c4b-108">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Current%2A> właściwości struktury i Pobierz wartości z jednej z jej członków.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="b9c4b-109">Wartość właściwości pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b9c4b-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="b9c4b-110">Uzyskaj <xref:System.Windows.Automation.AutomationElement> właściwości, których chcesz otrzymywać.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="b9c4b-111">Właściwość musi zostać określona w <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="b9c4b-112">Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, lub pobrać <xref:System.Windows.Automation.AutomationElement.Cached%2A> właściwości struktury i Pobierz wartości z jednej z jej członków.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c4b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9c4b-113">Example</span></span>  
 <span data-ttu-id="b9c4b-114">Poniższy przykład pokazuje różne sposoby, aby pobrać bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="b9c4b-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="b9c4b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9c4b-115">See also</span></span>

- [<span data-ttu-id="b9c4b-116">Właściwości automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="b9c4b-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="b9c4b-117">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9c4b-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="b9c4b-118">Buforowanie w klientach automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="b9c4b-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
