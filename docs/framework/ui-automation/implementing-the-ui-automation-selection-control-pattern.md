---
title: Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: f12ab6cc776daa4d6cca65d682cd299a0733a3a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935772"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.ISelectionProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.SelectionPattern> kontrolki służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych, które można wybrać. Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli zaznaczania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki implementujące <xref:System.Windows.Automation.Provider.ISelectionProvider> zezwolenie na wybranie jednego lub wielu elementów podrzędnych. Na przykład pole listy, widok listy i widok drzewa obsługują wiele zaznaczeń, natomiast Grupa przycisków kombi, suwak i przycisk radiowy obsługują pojedyncze zaznaczenie.  
  
- Kontrolki, które mają minimalny, maksymalny i ciągły zakres, takie jak kontrolka suwaka **woluminu** , <xref:System.Windows.Automation.Provider.IRangeValueProvider> powinny implementować zamiast. <xref:System.Windows.Automation.Provider.ISelectionProvider>  
  
- Kontrolki pojedynczego wyboru, które zarządzają kontrolkami <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>podrzędnymi, które implementują, takich jak suwak **rozdzielczość ekranu** w oknie dialogowym **właściwości wyświetlania** lub kontrolka [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] wyboru **selektora kolorów** z ( przedstawiony poniżej) powinien implementować <xref:System.Windows.Automation.Provider.ISelectionProvider>; ich elementy podrzędne powinny implementować zarówno <xref:System.Windows.Automation.Provider.ISelectionItemProvider> <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> , jak i.  
  
 ![Selektor kolorów z wyróżnioną żółtą opcją.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągu próbnika kolorów  
  
- Menu nie są obsługiwane <xref:System.Windows.Automation.SelectionPattern>. Jeśli pracujesz z elementami menu, które zawierają zarówno grafikę, jak i tekst (takie jak elementy **okienka podglądu** w menu **Widok** w programie Microsoft Outlook) i chcesz przekazać stan, należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Wymagane elementy członkowskie dla ISelectionProvider  
 Dla <xref:System.Windows.Automation.Provider.ISelectionProvider> interfejsu wymagane są następujące właściwości, metody i zdarzenia.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> użyciu <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>i.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> użyciu <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>i.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zdarzenie|Uruchamiany, gdy zaznaczenie w kontenerze znacząco uległo zmianie i wymaga wysyłania większej liczby zdarzeń dodawania i usuwania <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> niż na stałe.|  
  
 Właściwości <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> i<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> mogą być dynamiczne. Na przykład stan początkowy kontrolki może nie mieć żadnych elementów zaznaczonych domyślnie, co oznacza, że <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> jest. `false` Jednak po zaznaczeniu elementu kontrolka musi zawsze mieć wybrany co najmniej jeden element. Podobnie, w rzadkich przypadkach, formant może zezwolić na wybranie wielu elementów podczas inicjalizacji, ale w dalszym ciągu zezwala na tylko pojedyncze wybory.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|  
|<xref:System.InvalidOperationException>|Jeśli kontrolka jest ukryta.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki SelectionItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
