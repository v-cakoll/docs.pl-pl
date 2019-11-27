---
title: Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 193049aed6da3375b687e465678dca4dc90e6b39
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448812"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym omówieniu przedstawiono wzorce kontroli dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje o tym, jak klient automatyzacji interfejsu użytkownika może używać wzorców kontroli w celu uzyskania dostępu do informacji o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Wzorce kontrolek umożliwiają kategoryzowanie i Uwidacznianie funkcjonalności formantu niezależnie od typu formantu lub wyglądu kontrolki. Klienci automatyzacji interfejsu użytkownika mogą przeanalizować <xref:System.Windows.Automation.AutomationElement>, aby określić, które wzorce kontroli są obsługiwane, i zapewnić zachowanie kontrolki.  
  
 Aby uzyskać pełną listę wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Pobieranie wzorców kontrolek  
 Klienci pobierają wzorzec kontroli z <xref:System.Windows.Automation.AutomationElement>, wywołując <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienci mogą używać metody <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> lub pojedynczej właściwości `IsPatternAvailable` (na przykład <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>), aby określić, czy wzorzec lub Grupa wzorców są obsługiwane na <xref:System.Windows.Automation.AutomationElement>. Jednak bardziej wydajną próbą jest uzyskanie wzorca kontroli i testu dla odwołania `null` niż w celu sprawdzenia obsługiwanych właściwości i pobrania wzorca kontrolki, ponieważ powoduje to zmniejszenie liczby wywołań między procesami.  
  
 Poniższy przykład ilustruje, jak uzyskać <xref:System.Windows.Automation.TextPattern> wzorzec formantu z <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Pobieranie właściwości dla wzorców formantów  
 Klienci mogą pobierać wartości właściwości w wzorcach kontroli przez wywołanie <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> i rzutowanie obiektu zwróconego na odpowiedni typ. Aby uzyskać więcej informacji na temat właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
 Poza metodami `GetPropertyValue` wartości właściwości można pobrać za pomocą metod dostępu środowiska uruchomieniowego języka wspólnego (CLR), aby uzyskać dostęp do właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Kontrolki ze wzorcami zmiennych  
 Niektóre typy formantów obsługują różne wzorce w zależności od ich stanu lub sposobu, w jaki formant jest używany. Przykłady formantów, które mogą mieć wzorce zmiennych, to widoki listy (miniatury, kafelki, ikony, lista, szczegóły), wykresy programu Microsoft Excel (kołowy, liniowy, słupkowy, wartość komórki z formułą), obszar dokumentu programu Microsoft Word (normalny, układ sieci Web, konspekt, układ wydruku, drukowanie Wersja zapoznawcza) i karnacje programu Microsoft Windows Media Player.  
  
 Kontrolki implementujące niestandardowe typy kontrolek mogą mieć dowolny zestaw wzorców kontroli, które są potrzebne do reprezentowania ich funkcjonalności.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns.md)
- [Wzorzec tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](invoke-a-control-using-ui-automation.md)
- [Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Przykład wstawiania TextPattern tekstu](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przykład wyszukiwania i wybierania TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Przykład InvokePattern, ExpandCollapsePattern i TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
