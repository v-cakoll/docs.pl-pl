---
title: Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 3c04892fc0f1ec89b1b6555c60231ecf968a1345
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149425"
---
# <a name="invoke-a-control-using-ui-automation"></a>Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób wykonywania następujących zadań:  
  
-   Znajdź formant, który dopasowuje warunki określonej właściwości przy zalet widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa dla aplikacji docelowej.  
  
-   Utwórz <xref:System.Windows.Automation.AutomationElement> dla każdego formantu.  
  
-   Uzyskaj <xref:System.Windows.Automation.InvokePattern> obiektu za pomocą dowolnego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] znaleziony element, który obsługuje <xref:System.Windows.Automation.InvokePattern> — wzorzec kontrolki.  
  
-   Użyj <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywołania kontrolki z obsługi zdarzeń klienta.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do generowania <xref:System.Windows.Automation.InvokePattern> obiektu i wywoływanie kontrolki przy użyciu <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metody.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Zobacz także

- [Klasy InvokePattern klasy ExpandCollapsePattern oraz klasy TogglePattern próbki](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
