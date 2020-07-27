---
title: Odnalezienie elementu automatyzacji interfejsu użytkownika dla elementu listy
description: Zobacz przykład, który pokazuje, jak znaleźć element automatyzacji interfejsu użytkownika dla elementu listy, gdy jest znany indeks elementu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: ec6464bc0ec504fd34ed113c9bed1a54a7d4eaec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168403"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="7de54-103">Odnalezienie elementu automatyzacji interfejsu użytkownika dla elementu listy</span><span class="sxs-lookup"><span data-stu-id="7de54-103">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="7de54-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7de54-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7de54-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7de54-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7de54-106">W tym temacie pokazano, jak pobrać <xref:System.Windows.Automation.AutomationElement> element dla elementu na liście, gdy jest znany indeks elementu.</span><span class="sxs-lookup"><span data-stu-id="7de54-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de54-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7de54-107">Example</span></span>  
 <span data-ttu-id="7de54-108">Poniższy przykład przedstawia dwa sposoby pobierania określonego elementu z listy, jeden przy użyciu <xref:System.Windows.Automation.TreeWalker> i drugi przy użyciu <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="7de54-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="7de54-109">Pierwsza technika jest szybsza dla formantów Win32, ale druga jest szybsza dla formantów Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7de54-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="7de54-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7de54-110">See also</span></span>

- [<span data-ttu-id="7de54-111">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7de54-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
