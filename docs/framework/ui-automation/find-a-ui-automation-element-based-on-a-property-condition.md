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
ms.openlocfilehash: 536a71532f02782f9e84bb2bd086af212a77c0da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043667"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="869cb-102">Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości</span><span class="sxs-lookup"><span data-stu-id="869cb-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="869cb-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="869cb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="869cb-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="869cb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="869cb-105">Ten temat zawiera przykładowy kod pokazujący sposób lokalizowania elementu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie na podstawie określonej właściwości lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="869cb-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="869cb-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="869cb-106">Example</span></span>  
 <span data-ttu-id="869cb-107">W poniższym przykładzie określono zestaw warunków właściwości, które identyfikują określony element (lub elementy) zainteresowania w <xref:System.Windows.Automation.AutomationElement> drzewie.</span><span class="sxs-lookup"><span data-stu-id="869cb-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="869cb-108">Wyszukiwanie wszystkich pasujących elementów jest następnie wykonywane przy użyciu <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metody, która obejmuje <xref:System.Windows.Automation.AndCondition> serię operacji logicznych, aby ograniczyć liczbę pasujących elementów.</span><span class="sxs-lookup"><span data-stu-id="869cb-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="869cb-109">Podczas wyszukiwania z programu <xref:System.Windows.Automation.AutomationElement.RootElement%2A>należy próbować uzyskać tylko bezpośrednie elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="869cb-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="869cb-110">Wyszukiwanie elementów podrzędnych może się powtarzać przez setki lub nawet tysiące elementów, prawdopodobnie w wyniku przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="869cb-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="869cb-111">Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie od okna aplikacji lub kontenera na niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="869cb-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="869cb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="869cb-112">See also</span></span>

- <span data-ttu-id="869cb-113">[Przykład elementu menu InvokePattern i ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="869cb-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="869cb-114">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="869cb-114">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="869cb-115">Używanie właściwości AutomationID</span><span class="sxs-lookup"><span data-stu-id="869cb-115">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
