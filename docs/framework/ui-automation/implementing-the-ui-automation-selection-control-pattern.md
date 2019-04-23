---
title: Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 6b5e0e4e0a14410c23833db6cc90d23e7959ad22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087727"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ISelectionProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.SelectionPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które działają jak kontenery dla kolekcji można wybierać podrzędnych elementów. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki wyboru, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Określa, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider> zezwalają na jedną lub wiele podrzędnych elementów do wybrania. Na przykład pola listy, widokiem listy a widokiem drzewa obsługuje wiele zaznaczeń pola kombi, suwaka i Grupa przycisków radiowych wsparcie pojedynczego wyboru.  
  
-   Formanty, które ma minimalne, maksymalne i ciągłego zakresu, takich jak **woluminu** kontrolki suwaka, powinny implementować <xref:System.Windows.Automation.Provider.IRangeValueProvider> zamiast <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Formanty pojedynczego wyboru, które zarządzają formantów podrzędnych, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, takich jak **rozdzielczość ekranu** suwak w **właściwości wyświetlania** okno dialogowe lub **kolorów Selektor** kontrolki wyboru z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (przedstawionym poniżej), należy zaimplementować <xref:System.Windows.Automation.Provider.ISelectionProvider>; ich elementy podrzędne należy zaimplementować obu <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Selektor kolorów z żółtym wyróżnione. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykładowe mapowanie parametrów próbników kolorów  
  
-   Menu nie obsługują <xref:System.Windows.Automation.SelectionPattern>. Jeśli pracujesz z elementów menu, które zawierają zarówno grafiki i tekstu (takich jak **okienko podglądu** elementy w **widoku** menu [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) i trzeba przekazać stanu, należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Wymagane elementy ISelectionProvider  
 Następujące właściwości, metody i zdarzenia są wymagane dla <xref:System.Windows.Automation.Provider.ISelectionProvider> interfejsu.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Powinien obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zdarzenie|Wywoływane, gdy wybór w kontenerze zmienił się znacząco i wymaga wysłania więcej Dodawanie i usuwanie wydarzeń niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> pozwala na stałe.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> i <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> właściwości mogą być dynamiczne. Na przykład początkowy stan formantu może nie mieć żadnych elementów, zaznaczona domyślnie, co oznacza, że <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> jest `false`. Jednak po wybraniu elementu kontrolka musi zawsze mieć co najmniej jeden wybrany element. Podobnie w rzadkich przypadkach, kontrolki mogą zezwalać na wiele elementów do wybrania podczas inicjowania, ale następnie zezwala na tylko jednej opcji ma zostać wykonane.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączona.|  
|<xref:System.InvalidOperationException>|Jeśli kontrolka jest ukryty.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki SelectionItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
