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
ms.openlocfilehash: f55862722c6062c5353fc3b1ab8569d4759ac342
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157290"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Pobierz obsługiwane wzorce kontrolek automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak pobrać obiekty wzorca kontrolki z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów.  
  
### <a name="obtain-all-control-patterns"></a>Uzyskaj wszystkie wzorce kontrolki  
  
1.  Pobierz <xref:System.Windows.Automation.AutomationElement> wzorce którego kontrolek, możesz są zainteresowani.  
  
2.  Wywołaj <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> można pobrać wszystkie wzorce kontrolki z elementem.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się, że klient nie używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Może mieć znaczny wpływ na wydajność, ponieważ ta metoda wywołuje <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> wewnętrznie dla każdego istniejącego wzorca kontrolki. Jeśli to możliwe, należy wywołać klienta <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> klucza wzorców zainteresowania.  
  
### <a name="obtain-a-specific-control-pattern"></a>Uzyskaj wzorca określonego formantu  
  
1.  Pobierz <xref:System.Windows.Automation.AutomationElement> wzorce którego kontrolek, możesz są zainteresowani.  
  
2.  Wywołaj <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lub <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zapytania dla określonego wzorca. Te metody są podobne, ale jeśli wzorzec nie zostanie znaleziony, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> zgłasza wyjątek, i <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> zwraca `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera <xref:System.Windows.Automation.AutomationElement> dla elementu listy i uzyskuje <xref:System.Windows.Automation.SelectionItemPattern> z tego elementu.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
