---
title: Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 708393ced89e56536b92f73f603695f00fb5e76e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204901"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="e055c-102">Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości</span><span class="sxs-lookup"><span data-stu-id="e055c-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="e055c-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e055c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e055c-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e055c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e055c-105">Ten temat zawiera przykładowy kod, który pokazuje, jak można zlokalizować elementu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa na podstawie określoną właściwość lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="e055c-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e055c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e055c-106">Example</span></span>  
 <span data-ttu-id="e055c-107">W poniższym przykładzie zestaw warunków właściwości są określone, zidentyfikuj niektórych elementu (lub elementów) zainteresowania w <xref:System.Windows.Automation.AutomationElement> drzewa.</span><span class="sxs-lookup"><span data-stu-id="e055c-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="e055c-108">Następnie zostanie przeprowadzone wyszukiwanie dla wszystkich elementów zgodnych z <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metodę, która zawiera szereg <xref:System.Windows.Automation.AndCondition> operacji logicznych, aby ograniczyć liczbę zgodnych elementów.</span><span class="sxs-lookup"><span data-stu-id="e055c-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e055c-109">Podczas wyszukiwania z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, należy spróbować uzyskać tylko bezpośrednie elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e055c-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="e055c-110">Wyszukiwanie elementów podrzędnych może wykonać iterację setek lub nawet tysięcy elementów, które prawdopodobnie spowodowało przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="e055c-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="e055c-111">Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontenerów na niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="e055c-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="e055c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e055c-112">See Also</span></span>  
 [<span data-ttu-id="e055c-113">Klasy InvokePattern i przykładowych elementów Menu klasy ExpandCollapsePattern</span><span class="sxs-lookup"><span data-stu-id="e055c-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="e055c-114">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e055c-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="e055c-115">Używanie właściwości AutomationID</span><span class="sxs-lookup"><span data-stu-id="e055c-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
