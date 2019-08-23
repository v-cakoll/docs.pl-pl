---
title: Przenoszenie elementu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 43b1e005cdb499fae920a0999feaa56c5409f653
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964693"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="6e376-102">Przenoszenie elementu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="6e376-102">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="6e376-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6e376-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6e376-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e376-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6e376-105">W tym przykładzie pokazano, jak przenieść [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element do określonej lokalizacji ekranu.</span><span class="sxs-lookup"><span data-stu-id="6e376-105">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e376-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e376-106">Example</span></span>  
 <span data-ttu-id="6e376-107"><xref:System.Windows.Automation.WindowPattern> Poniższy przykład używa <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent> wzorcówformantów<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> i <xref:System.Windows.Automation.TransformPattern> do programistycznego przenoszenia aplikacji docelowejdolokalizacjidyskretnychekranuiśledzenia.[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e376-107">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="6e376-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e376-108">See also</span></span>

- [<span data-ttu-id="6e376-109">Przykład WindowPattern</span><span class="sxs-lookup"><span data-stu-id="6e376-109">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
