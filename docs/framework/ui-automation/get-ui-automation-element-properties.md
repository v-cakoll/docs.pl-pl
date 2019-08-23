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
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968969"
---
# <a name="get-ui-automation-element-properties"></a>Pobierz właściwości elementu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie pokazano, jak pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.  
  
### <a name="get-a-current-property-value"></a>Pobierz bieżącą wartość właściwości  
  
1. Uzyskaj Właściwość <xref:System.Windows.Automation.AutomationElement> , której chcesz pobrać.  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>lub <xref:System.Windows.Automation.AutomationElement.Current%2A> Pobierz strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.  
  
### <a name="get-a-cached-property-value"></a>Pobierz buforowaną wartość właściwości  
  
1. Uzyskaj Właściwość <xref:System.Windows.Automation.AutomationElement> , której chcesz pobrać. Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest>.  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>lub <xref:System.Windows.Automation.AutomationElement.Cached%2A> Pobierz strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Buforowanie w klientach automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
