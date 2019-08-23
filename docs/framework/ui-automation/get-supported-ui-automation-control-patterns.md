---
title: Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 8987526a572d3c9a239885407c19bd1ad3674f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968995"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono sposób pobierania obiektów wzorców kontroli z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów.  
  
### <a name="obtain-all-control-patterns"></a>Uzyskaj wszystkie wzorce kontroli  
  
1. Pobierz, <xref:System.Windows.Automation.AutomationElement> których wzorców kontroli interesują Cię.  
  
2. Wywołanie <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> w celu pobrania wszystkich wzorców kontrolek z elementu.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się, aby klient nie był używany <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Wydajność może być poważnie narażona na to, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> że ta metoda wywołuje wewnętrznie dla każdego istniejącego wzorca kontrolki. Jeśli to możliwe, klient powinien wywołać <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> kluczowe wzorce.  
  
### <a name="obtain-a-specific-control-pattern"></a>Uzyskiwanie określonego wzorca kontroli  
  
1. Pobierz, <xref:System.Windows.Automation.AutomationElement> których wzorców kontroli interesują Cię.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> Wywołaj <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> lub, aby wykonać zapytanie dotyczące określonego wzorca. Te metody są podobne, ale jeśli wzorzec nie zostanie znaleziony, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> zgłasza wyjątek i <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zwraca `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera <xref:System.Windows.Automation.AutomationElement> element listy i uzyskuje <xref:System.Windows.Automation.SelectionItemPattern> od tego elementu.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
