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
# <a name="get-ui-automation-element-properties"></a>Pobierz właściwości elementu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie pokazano, jak pobrać właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.  
  
### <a name="get-a-current-property-value"></a>Pobierz bieżącą wartość właściwości  
  
1. Uzyskaj właściwość, której chcesz <xref:System.Windows.Automation.AutomationElement> pobrać.  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> lub Pobierz <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.  
  
### <a name="get-a-cached-property-value"></a>Pobierz buforowaną wartość właściwości  
  
1. Uzyskaj właściwość, której chcesz <xref:System.Windows.Automation.AutomationElement> pobrać. Właściwość musi być określona w <xref:System.Windows.Automation.CacheRequest> .  
  
2. Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> lub Pobierz <xref:System.Windows.Automation.AutomationElement.Cached%2A> strukturę właściwości i Pobierz wartość z jednego z jej elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano różne sposoby pobierania bieżących właściwości <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Buforowanie w klientach automatyzacji interfejsu użytkownika](caching-in-ui-automation-clients.md)
