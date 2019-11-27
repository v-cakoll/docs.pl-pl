---
title: Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 754af531a20805c53785a37695dce97bb7967a53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447119"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ISelectionProvider>, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 <xref:System.Windows.Automation.SelectionPattern> wzorzec kontroli służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych, które można wybrać. Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli zaznaczania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki implementujące <xref:System.Windows.Automation.Provider.ISelectionProvider> umożliwiają wybranie jednego lub wielu elementów podrzędnych. Na przykład pole listy, widok listy i widok drzewa obsługują wiele zaznaczeń, natomiast Grupa przycisków kombi, suwak i przycisk radiowy obsługują pojedyncze zaznaczenie.  
  
- Kontrolki, które mają minimalny, maksymalny i ciągły zakres, takie jak kontrolka suwaka **głośności** , powinny implementować <xref:System.Windows.Automation.Provider.IRangeValueProvider> zamiast <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
- Kontrolki pojedynczego wyboru, które zarządzają kontrolkami podrzędnymi, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, takie jak suwak **rozdzielczość ekranu** w oknie dialogowym **właściwości wyświetlania** lub kontrolka wyboru **selektora kolorów** z programu Microsoft Word (przedstawiony poniżej), powinny implementować <xref:System.Windows.Automation.Provider.ISelectionProvider>; ich elementy podrzędne powinny implementować zarówno <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>, jak i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Selektor kolorów z wyróżnioną żółtą opcją.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągu próbnika kolorów  
  
- Menu nie obsługują <xref:System.Windows.Automation.SelectionPattern>. Jeśli pracujesz z elementami menu, które zawierają zarówno grafikę, jak i tekst (takie jak elementy **okienka podglądu** w menu **Widok** w programie Microsoft Outlook) i chcesz przekazać stan, należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Wymagane elementy członkowskie dla ISelectionProvider  
 Dla interfejsu <xref:System.Windows.Automation.Provider.ISelectionProvider> są wymagane następujące właściwości, metody i zdarzenia.  
  
|Wymagane elementy członkowskie|Type|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wydarzenie|Uruchamiany, gdy zaznaczenie w kontenerze znacząco uległo zmianie i wymaga wysyłania większej liczby zdarzeń dodawania i usuwania niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> stałej.|  
  
 Właściwości <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> i <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> mogą być dynamiczne. Na przykład stan początkowy kontrolki może nie mieć żadnych elementów zaznaczonych domyślnie, co oznacza, że <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> jest `false`. Jednak po zaznaczeniu elementu kontrolka musi zawsze mieć wybrany co najmniej jeden element. Podobnie, w rzadkich przypadkach, formant może zezwolić na wybranie wielu elementów podczas inicjalizacji, ale w dalszym ciągu zezwala na tylko pojedyncze wybory.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|  
|<xref:System.InvalidOperationException>|Jeśli kontrolka jest ukryta.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki SelectionItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
