---
title: Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1ee0df5b133f08ec3cf6ba617c80c480e207ddf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179956"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym przeglądzie przedstawiono wzorce kontroli dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje o tym, jak klient automatyzacji interfejsu użytkownika [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]może używać wzorców sterowania, aby uzyskać dostęp do informacji o .  
  
 Wzorce kontroli umożliwiają kategoryzowanie i udostępnianie funkcji formantu niezależnie od typu formantu lub wyglądu formantu. Automatyzacja interfejsu użytkownika <xref:System.Windows.Automation.AutomationElement> klienci mogą zbadać, aby określić, które wzorce kontroli są obsługiwane i mieć pewność zachowania formantu.  
  
 Aby uzyskać pełną listę wzorców sterowania, zobacz [Omówienie wzorców sterowania automatyzacją](ui-automation-control-patterns-overview.md)interfejsu użytkownika .  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Uzyskiwanie wzorców kontroli  
 Klienci pobierają wzorzec <xref:System.Windows.Automation.AutomationElement> kontroli z <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> wywoływania albo lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienci mogą <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> użyć metody `IsPatternAvailable` lub indywidualnej <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>właściwości (na przykład ), aby określić, czy <xref:System.Windows.Automation.AutomationElement>wzorzec lub grupa wzorców jest obsługiwana w pliku . Jednak jest bardziej wydajne, aby spróbować uzyskać wzorzec kontroli i przetestować `null` dla odwołania niż sprawdzić obsługiwane właściwości i pobrać wzorzec kontroli, ponieważ powoduje to mniej wywołań między procesami.  
  
 W poniższym przykładzie pokazano, jak uzyskać wzorzec <xref:System.Windows.Automation.TextPattern> kontroli z . <xref:System.Windows.Automation.AutomationElement>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Pobieranie właściwości w wzorcach kontroli  
 Klienci mogą pobierać wartości właściwości na wzorce <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> kontroli, wywołując albo i <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> rzutowanie obiektu zwróconego do odpowiedniego typu. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
 Oprócz `GetPropertyValue` metod wartości właściwości można pobrać za pośrednictwem akcesorów środowiska wykonawczego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] języka wspólnego (CLR), aby uzyskać dostęp do właściwości wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Formanty ze zmiennymi wzorcami  
 Niektóre typy kontroli obsługują różne wzorce w zależności od ich stanu lub sposobu, w jaki formant jest używany. Przykładami formantów, które mogą mieć zmienne wzorce, są widoki listy (miniatury, kafelki, ikony, lista, szczegóły), wykresy programu Microsoft Excel (kołowe, liniowe, słupkowe, wartości komórki z formułą), obszar dokumentu programu Microsoft Word (normalny, Układ sieci Web, Konspekt, Układ wydruku, Drukowanie Wersja zapoznawcza) i skórki programu Microsoft Windows Media Player.  
  
 Formanty implementujące typy formantów niestandardowych może mieć dowolny zestaw wzorców kontroli, które są potrzebne do reprezentowania ich funkcji.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns.md)
- [Wzorzec tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](invoke-a-control-using-ui-automation.md)
- [Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)
- [Przykładowy wstawianie tekstu textPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przykład wyszukiwania i zaznaczenia textpattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvokePattern, ExpandCollapsePattern i Przełącz przykładowy](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
