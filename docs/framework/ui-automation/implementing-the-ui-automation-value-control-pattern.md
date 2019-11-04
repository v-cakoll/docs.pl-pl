---
title: Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 75cf628b6faad1f8c52a70c77baa4ede21160510
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458136"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IValueProvider>, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 <xref:System.Windows.Automation.ValuePattern> wzorzec kontrolki służy do obsługi kontrolek, które mają wewnętrzną wartość bez łączenia zakresu i który może być reprezentowany jako ciąg. Ten ciąg można edytować w zależności od kontrolki i jej ustawień. Przykłady formantów implementujących ten wzorzec można znaleźć w temacie [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli wartości należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki, takie jak <xref:System.Windows.Automation.ControlType.ListItem> i <xref:System.Windows.Automation.ControlType.TreeItem>, muszą obsługiwać <xref:System.Windows.Automation.ValuePattern>, jeśli wartość któregokolwiek z elementów jest edytowalna, niezależnie od bieżącego trybu edycji kontrolki. Kontrolka nadrzędna musi również obsługiwać <xref:System.Windows.Automation.ValuePattern>, jeśli elementy podrzędne są edytowalne.  
  
 ![Edytowalny element listy.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Przykład edytowalnego elementu listy  
  
- Jednowierszowe kontrolki edycji obsługują dostęp programistyczny do ich zawartości przez implementację <xref:System.Windows.Automation.Provider.IValueProvider>. Jednak wielowierszowe kontrolki edycji nie implementują <xref:System.Windows.Automation.Provider.IValueProvider>; Zamiast tego zapewniają dostęp do zawartości przez implementację <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- Aby pobrać zawartość tekstową wielowierszowej kontrolki edycji, formant musi implementować <xref:System.Windows.Automation.Provider.ITextProvider>. Jednak <xref:System.Windows.Automation.Provider.ITextProvider> nie obsługuje ustawiania wartości formantu.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> nie obsługuje pobierania informacji o formatowaniu ani wartości podciągów. Zaimplementuj <xref:System.Windows.Automation.Provider.ITextProvider> w tych scenariuszach.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> muszą być implementowane przez kontrolki, takie jak kontrolka wyboru **selektora kolorów** z programu Microsoft Word (przedstawiony poniżej), która obsługuje mapowanie ciągów między wartością koloru (na przykład "żółta") i równoważną wewnętrzną strukturę RGB.  
  
 ![Selektor kolorów z wyróżnioną żółtą opcją.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągu próbnika kolorów  
  
- Kontrolka powinna mieć ustawiony <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> na `true` i <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> ustawione na `false` przed umożliwieniem wywołania <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Wymagane elementy członkowskie dla IValueProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.IValueProvider>są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Brak|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli informacje specyficzne dla ustawień regionalnych są przesyłane do formantu w nieprawidłowym formacie, na przykład w niewłaściwie sformatowanej dacie.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli nie można przekonwertować nowej wartości z ciągu na format rozpoznawany przez formant.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Gdy podejmowana jest próba manipulowania kontrolką, która nie jest włączona.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przykład wstawiania ValuePattern tekstu](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
