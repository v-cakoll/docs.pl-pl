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
# <a name="get-ui-automation-element-properties"></a>Pobierz właściwości elementu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie pokazano, jak pobrać właściwości elementu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="get-a-current-property-value"></a>Pobierz bieżącą wartość właściwości  
  
1. Uzyskaj <xref:System.Windows.Automation.AutomationElement> którego właściwość chcesz uzyskać.  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>lub Pobierz strukturę właściwości <xref:System.Windows.Automation.AutomationElement.Current%2A> i Pobierz wartość z jednego z jej elementów członkowskich.  
  
### <a name="get-a-cached-property-value"></a>Pobierz buforowaną wartość właściwości  
  
1. Uzyskaj <xref:System.Windows.Automation.AutomationElement> którego właściwość chcesz uzyskać. Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest>.  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>lub Pobierz strukturę właściwości <xref:System.Windows.Automation.AutomationElement.Cached%2A> i Pobierz wartość z jednego z jej elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md)
