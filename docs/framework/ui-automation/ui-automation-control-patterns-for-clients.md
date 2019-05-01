---
title: Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1b0d374c9dc3e24302a8acfbc56cd9468f41def5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033101"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym omówieniu przedstawiono wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika. Zawiera informacje dotyczące sposobu automatyzacji interfejsu użytkownika klient może używać wzorców kontrolek na dostęp do informacji o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Wzorce kontrolki umożliwiają klasyfikowanie i ujawniać funkcjonalność formantu niezależnie od typu formantu lub wygląd formantu. Klienci automatyzacji interfejsu użytkownika można sprawdzić <xref:System.Windows.Automation.AutomationElement> ustalenie, które określają wzorce są obsługiwane i należy zapewnić zachowanie formantu.  
  
 Aby uzyskać pełną listę wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Pobieranie wzorców kontrolki  
 Klienci pobierają wzorca kontrolki z <xref:System.Windows.Automation.AutomationElement> , wywołując jedną <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Klienci mogą używać <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> metody lub osoba `IsPatternAvailable` właściwości (na przykład <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) do określenia, czy wzorzec lub grupy wzorców jest obsługiwana na <xref:System.Windows.Automation.AutomationElement>. Jednak jest bardziej wydajne, aby spróbować uzyskać wzorca kontrolki i testować aplikacje dla `null` odwołania, niż można sprawdzić obsługiwanych właściwości i pobrać wzorca kontrolki, ponieważ powoduje ona mniejszą liczbę wywołań między procesami.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Windows.Automation.TextPattern> — wzorzec kontrolki z <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Trwa pobieranie właściwości wzorce kontrolki  
 Klienci mogą pobierać wartości właściwości na wzorce kontrolki, wywołując jedną <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> lub <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> i rzutowania obiekt zwrócony do odpowiedniego typu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Oprócz `GetPropertyValue` metody, właściwości mogą być pobierane za pośrednictwem [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] metod dostępu w celu uzyskania dostępu do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości przy użyciu wzorca.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Formanty z wzory zmiennej  
 Niektóre typy formantów obsługuje różnych wzorców w zależności od ich stanu lub sposób, w którym formant jest używany. Przykłady formantów, które mogą mieć wzorów zmiennej są widoki list (miniatury, Kafelki, ikony, lista, szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (koło, wiersz paska wartość komórki przy użyciu formuły) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]firmy dokumentów obszaru (normalny, układu strony sieci Web konspektu, układ wydruku Print Wersja zapoznawcza), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skórki.  
  
 Implementowanie kontrolek niestandardowych typów formantów może mieć dowolny zbiór wzorców kontrolek, które są potrzebne do reprezentowania ich funkcje.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)
- [Wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Przykładowy tekst wstawienia TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextPattern wyszukiwania i wybór próbki](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Klasy InvokePattern klasy ExpandCollapsePattern oraz klasy TogglePattern próbki](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
