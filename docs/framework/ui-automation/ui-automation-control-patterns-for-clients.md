---
title: Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
description: Zapoznaj się z omówieniem wzorców kontroli dla klientów automatyzacji interfejsu użytkownika. Użyj wzorców kontroli, aby uzyskać dostęp do informacji o interfejsie użytkownika.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: f2def328228a30ace6d0edc0661d6e79f237d6f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163876"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym omówieniu przedstawiono wzorce kontroli dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje dotyczące sposobu, w jaki klient automatyzacji interfejsu użytkownika może używać wzorców kontroli w celu uzyskania dostępu do informacji na temat [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
 Wzorce kontrolek umożliwiają kategoryzowanie i Uwidacznianie funkcjonalności formantu niezależnie od typu formantu lub wyglądu kontrolki. Klienci automatyzacji interfejsu użytkownika mogą przeanalizować, <xref:System.Windows.Automation.AutomationElement> Aby określić, które wzorce kontroli są obsługiwane, i zapewnić zachowanie formantu.  
  
 Aby uzyskać pełną listę wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Pobieranie wzorców kontrolek  
 Klienci pobierają wzorzec kontroli z elementu <xref:System.Windows.Automation.AutomationElement> przez wywołanie albo <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType> .  
  
 Klienci mogą używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metody lub pojedynczej `IsPatternAvailable` właściwości (na przykład) w <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty> celu określenia, czy wzorzec lub Grupa wzorców są obsługiwane w <xref:System.Windows.Automation.AutomationElement> . Jednak bardziej wydajną próbą jest uzyskanie wzorca kontroli i testu dla `null` odwołania niż sprawdzenie obsługiwanych właściwości i pobranie wzorca kontrolki, ponieważ powoduje to zmniejszenie liczby wywołań między procesami.  
  
 Poniższy przykład ilustruje, jak uzyskać <xref:System.Windows.Automation.TextPattern> wzorzec formantu z <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Pobieranie właściwości dla wzorców formantów  
 Klienci mogą pobrać wartości właściwości w wzorcach kontroli przez wywołanie albo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> i rzutowanie obiektu zwróconego do odpowiedniego typu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
 Poza `GetPropertyValue` metodami wartości właściwości można pobierać za pomocą metod dostępu środowiska uruchomieniowego języka wspólnego (CLR), aby uzyskać dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Kontrolki ze wzorcami zmiennych  
 Niektóre typy formantów obsługują różne wzorce w zależności od ich stanu lub sposobu, w jaki formant jest używany. Przykłady formantów, które mogą mieć wzorce zmiennych, to widoki listy (miniatury, kafelki, ikony, lista, szczegóły), wykresy programu Microsoft Excel (wykres kołowy, linia, pasek, wartość komórki z formułą), obszar dokumentu programu Microsoft Word (normalny, układ sieci Web, konspekt, układ wydruku, Podgląd wydruku) i karnacje programu Microsoft Windows Media Player.  
  
 Kontrolki implementujące niestandardowe typy kontrolek mogą mieć dowolny zestaw wzorców kontroli, które są potrzebne do reprezentowania ich funkcjonalności.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns.md)
- [Wzorzec tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](invoke-a-control-using-ui-automation.md)
- [Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Przykład wstawiania TextPattern tekstu](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przykład wyszukiwania i wybierania TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Przykład InvokePattern, ExpandCollapsePattern i TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
