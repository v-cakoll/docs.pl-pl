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
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923723"
---
# <a name="invoke-a-control-using-ui-automation"></a>Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono sposób wykonywania następujących zadań:  
  
- Znajdź formant pasujący do określonych warunków właściwości, łącząc widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolki drzewa dla aplikacji docelowej.  
  
- <xref:System.Windows.Automation.AutomationElement> Utwórz dla każdej kontrolki.  
  
- Uzyskaj obiekt z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dowolnego<xref:System.Windows.Automation.InvokePattern> elementu, który obsługuje wzorzec kontrolki. <xref:System.Windows.Automation.InvokePattern>  
  
- Służy <xref:System.Windows.Automation.InvokePattern.Invoke%2A> do wywoływania formantu z programu obsługi zdarzeń klienta.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody <xref:System.Windows.Automation.AutomationElement> klasy do wygenerowania <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.InvokePattern.Invoke%2A> obiektu i wywołania kontrolki przy użyciu metody.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykład InvokePattern, ExpandCollapsePattern i TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
