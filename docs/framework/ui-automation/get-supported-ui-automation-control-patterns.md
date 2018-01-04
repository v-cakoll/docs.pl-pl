---
title: "Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 26cdf2dea8ec924d4345c1591be8fee1ed489c0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a>Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak można pobrać obiektów — wzorzec formantu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów.  
  
### <a name="obtain-all-control-patterns"></a>Uzyskaj wszystkie wzorce formantu  
  
1.  Pobierz <xref:System.Windows.Automation.AutomationElement> którego kontrolę wzorce można są zainteresowani.  
  
2.  Wywołanie <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> można pobrać wszystkich wzorców formantu z elementu.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się, że klient nie używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Wydajność może być poważny wpływ jak ta metoda wywołuje <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> wewnętrznie dla każdego istniejącego wzorca formantu. Jeśli to możliwe, należy wywołać klienta <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> klucza wzorców zainteresowań.  
  
### <a name="obtain-a-specific-control-pattern"></a>Uzyskaj wzorzec określonego formantu  
  
1.  Pobierz <xref:System.Windows.Automation.AutomationElement> którego kontrolę wzorce można są zainteresowani.  
  
2.  Wywołanie <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zapytania dla określonego wzorca. Te metody są podobne, ale jeśli wzorzec nie zostanie znaleziony, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> zgłasza wyjątek, i <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zwraca `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera <xref:System.Windows.Automation.AutomationElement> dla elementu listy i uzyskuje <xref:System.Windows.Automation.SelectionItemPattern> od tego elementu.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
