---
title: Odnalezienie elementu automatyzacji interfejsu użytkownika dla elementu listy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 2474edf95bf598ba9284b5f6ac36a9e0af1317a1
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741758"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Odnalezienie elementu automatyzacji interfejsu użytkownika dla elementu listy
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie pokazano, jak pobrać <xref:System.Windows.Automation.AutomationElement> dla elementu na liście, gdy jest znany indeks elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa sposoby pobierania określonego elementu z listy, jeden przy użyciu <xref:System.Windows.Automation.TreeWalker> i innych przy użyciu <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 Pierwsza technika jest szybsza dla formantów Win32, ale druga jest szybsza dla formantów Windows Presentation Foundation (WPF).  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](obtaining-ui-automation-elements.md)
