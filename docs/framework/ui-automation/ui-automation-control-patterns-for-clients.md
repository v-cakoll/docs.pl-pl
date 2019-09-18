---
title: Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 320833bf147fa16889cd188c7c729cd4dc028843
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042524"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym omówieniu przedstawiono wzorce kontroli dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje dotyczące sposobu, w jaki klient automatyzacji interfejsu użytkownika może używać wzorców kontroli w celu uzyskania [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]dostępu do informacji na temat.  
  
 Wzorce kontrolek umożliwiają kategoryzowanie i Uwidacznianie funkcjonalności formantu niezależnie od typu formantu lub wyglądu kontrolki. Klienci automatyzacji interfejsu użytkownika mogą przeanalizować <xref:System.Windows.Automation.AutomationElement> , aby określić, które wzorce kontroli są obsługiwane, i zapewnić zachowanie formantu.  
  
 Aby uzyskać pełną listę wzorców kontrolek, zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Pobieranie wzorców kontrolek  
 Klienci pobierają wzorzec kontroli z elementu <xref:System.Windows.Automation.AutomationElement> przez wywołanie albo <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienci mogą używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metody lub <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>pojedynczej `IsPatternAvailable` właściwości (na przykład) w celu określenia, czy wzorzec <xref:System.Windows.Automation.AutomationElement>lub Grupa wzorców są obsługiwane w. Jednak bardziej wydajną próbą jest uzyskanie wzorca kontroli i testu dla `null` odwołania niż sprawdzenie obsługiwanych właściwości i pobranie wzorca kontrolki, ponieważ powoduje to zmniejszenie liczby wywołań między procesami.  
  
 Poniższy przykład ilustruje, jak uzyskać <xref:System.Windows.Automation.TextPattern> wzorzec formantu <xref:System.Windows.Automation.AutomationElement>z.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Pobieranie właściwości dla wzorców formantów  
 Klienci mogą pobrać wartości właściwości w wzorcach kontroli przez wywołanie albo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> i rzutowanie obiektu zwróconego do odpowiedniego typu. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na temat właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
 Poza `GetPropertyValue` metodami wartości właściwości można pobierać za pomocą metod dostępu środowiska uruchomieniowego języka wspólnego (CLR), aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uzyskać dostęp do właściwości wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Kontrolki ze wzorcami zmiennych  
 Niektóre typy formantów obsługują różne wzorce w zależności od ich stanu lub sposobu, w jaki formant jest używany. Przykłady formantów, które mogą mieć wzorce zmiennych, to widoki listy (miniatury, kafelki, ikony, lista, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] szczegóły), wykresy (wykres kołowy, linia, słupek, wartość komórki [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]z formułą), obszar dokumentu (normalny, układ sieci Web, konspekt, układ wydruku, drukowanie Wersja zapoznawcza [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] ) i karnacje.  
  
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
