---
title: Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: eb77f26bbe3546a3f90804c3648f8547fb6abad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180093"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IValueProvider>i konwencje dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.ValuePattern> formantu jest używany do obsługi formantów, które mają wartość wewnętrzną nie obejmujące zakres i które mogą być reprezentowane jako ciąg. Ten ciąg można edytować, w zależności od formantu i jego ustawień. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca kontroli wartości należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Formanty <xref:System.Windows.Automation.ControlType.ListItem> <xref:System.Windows.Automation.ControlType.TreeItem> takie <xref:System.Windows.Automation.ValuePattern> jak i musi obsługiwać, jeśli wartość dowolnego z elementów jest edytowalny, niezależnie od bieżącego trybu edycji formantu. Formant nadrzędny <xref:System.Windows.Automation.ValuePattern> musi również obsługiwać, jeśli elementy podrzędne są edytowalne.  
  
 ![Edytowalny element listy.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Przykład edytowanego elementu listy  
  
- Edycja jednowierszowa steruje programowym dostępem <xref:System.Windows.Automation.Provider.IValueProvider>do ich zawartości poprzez wdrożenie . Jednak wielowierszowe kontrolki <xref:System.Windows.Automation.Provider.IValueProvider>edycji nie implementują ; zamiast tego zapewniają dostęp do swoich <xref:System.Windows.Automation.Provider.ITextProvider>treści poprzez wdrożenie .  
  
- Aby pobrać zawartość tekstową formantu edycji wielowierszowej, formant musi zaimplementować <xref:System.Windows.Automation.Provider.ITextProvider>. Jednak <xref:System.Windows.Automation.Provider.ITextProvider> nie obsługuje ustawiania wartości formantu.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>nie obsługuje pobierania informacji o formatowaniu lub wartości podciągów. Zaimplementuj <xref:System.Windows.Automation.Provider.ITextProvider> w tych scenariuszach.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>musi być zaimplementowana przez formanty, takie jak kontrolka wyboru **selektora kolorów** z programu Microsoft Word (ilustrowana poniżej), która obsługuje mapowanie ciągów między wartością koloru (na przykład "żółty") a równoważną wewnętrzną strukturą RGB.  
  
 ![Próbnik kolorów z żółtym podświetlenym.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągów próbkowania kolorów  
  
- Formant powinien <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> mieć `true` ustawiony <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> i `false` ustawiony na przed <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>zezwoleniem na wywołanie .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>Wymagane elementy członkowskie dla iValueProvider  
 Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IValueProvider>do wdrożenia .  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Brak|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Jeśli informacje specyficzne dla ustawień regionalnych są przekazywane do formantu w niepoprawnym formacie, takim jak nieprawidłowo sformatowana data.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Jeśli nowa wartość nie może być przekonwertowana z ciągu na format, który rozpoznawany jest przez formant.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Gdy podejmowana jest próba manipulowania formantem, który nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przykładowy wstawianie tekstu wzorzec wartości](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
