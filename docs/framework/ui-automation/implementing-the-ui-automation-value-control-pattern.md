---
title: Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami, aby zaimplementować wzorzec kontroli wartości w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu IValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: a15c0b50996e2c0dfdc937bc9565d5f9ba20c992
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168195"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IValueProvider> , w tym informacje dotyczące zdarzeń i właściwości. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 <xref:System.Windows.Automation.ValuePattern>Wzorzec kontrolki służy do obsługi kontrolek, które mają wewnętrzną wartość bez łączenia zakresu i które mogą być reprezentowane jako ciąg. Ten ciąg można edytować w zależności od kontrolki i jej ustawień. Przykłady formantów implementujących ten wzorzec można znaleźć w temacie [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli wartości należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki takie jak <xref:System.Windows.Automation.ControlType.ListItem> i <xref:System.Windows.Automation.ControlType.TreeItem> muszą obsługiwać <xref:System.Windows.Automation.ValuePattern> , jeśli wartość któregokolwiek z elementów jest edytowalna, niezależnie od bieżącego trybu edycji kontrolki. Formant nadrzędny musi również obsługiwać <xref:System.Windows.Automation.ValuePattern> , jeśli elementy podrzędne są edytowalne.  
  
 ![Edytowalny element listy.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Przykład edytowalnego elementu listy  
  
- Kontrolki edycji pojedynczej linii obsługują dostęp programistyczny do zawartości przez implementację <xref:System.Windows.Automation.Provider.IValueProvider> . Jednak wielowierszowe kontrolki edycji nie są implementowane <xref:System.Windows.Automation.Provider.IValueProvider> ; zamiast tego zapewniają dostęp do ich zawartości przez implementację <xref:System.Windows.Automation.Provider.ITextProvider> .  
  
- Aby można było pobrać zawartość tekstową wielowierszowej kontrolki edycji, formant musi być zaimplementowany <xref:System.Windows.Automation.Provider.ITextProvider> . Jednak program nie <xref:System.Windows.Automation.Provider.ITextProvider> obsługuje ustawiania wartości formantu.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>nie obsługuje pobierania informacji o formatowaniu ani wartości podciągów. Zaimplementuj <xref:System.Windows.Automation.Provider.ITextProvider> w tych scenariuszach.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>musi być zaimplementowany przez kontrolki, takie jak formant wyboru **selektora kolorów** z programu Microsoft Word (przedstawiony poniżej), który obsługuje mapowanie ciągów między wartością koloru (na przykład "żółta") i równoważną wewnętrzną strukturę RGB.  
  
 ![Selektor kolorów z wyróżnioną żółtą opcją.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągu próbnika kolorów  
  
- Kontrolka powinna mieć <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> ustawioną wartość `true` i <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> ustawioną `false` przed zezwoleniem na wywołanie <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>Wymagane elementy członkowskie dla IValueProvider  
 Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IValueProvider> .  
  
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

- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przykład wstawiania ValuePattern tekstu](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
