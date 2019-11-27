---
title: Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 53a5a739918e61d53b3102c2c85d4ef2b8425173
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447111"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> wzorzec kontrolki służy do obsługi kontrolek, które działają jako osoby indywidualnej, do wyboru elementów podrzędnych formantów kontenera, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider>. Aby zapoznać się z przykładami formantów implementujących wzorzec kontrolki SelectionItem dla, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki elementu zaznaczania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki pojedynczego wyboru, które zarządzają kontrolkami podrzędnymi, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, takie jak suwak **rozdzielczość ekranu** w oknie dialogowym **właściwości wyświetlania** , powinny implementować <xref:System.Windows.Automation.Provider.ISelectionProvider> i ich elementy podrzędne powinny implementować zarówno <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> jak i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Wymagane elementy członkowskie dla ISelectionItemProvider  
 Do implementowania <xref:System.Windows.Automation.Provider.ISelectionItemProvider>są wymagane następujące właściwości, metody i zdarzenia.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wydarzenie|Uruchamiany, gdy wybór w kontenerze znacząco uległ zmianie i wymaga wysyłania większej liczby <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> i zdarzeń <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> stałej.|  
  
- Jeśli wynik <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>lub <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jest pojedynczym zaznaczonym elementem, należy podwyższyć <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> w przeciwnym razie Wyślij <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> zgodnie z potrzebami.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Gdy podejmowana jest jakakolwiek z następujących prób:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> jest wywoływana w kontenerze z pojedynczym wyborem, gdzie <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` i element jest już zaznaczony.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> jest wywoływana dla kontenera wielokrotnego wyboru, gdzie <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` i wybrano tylko jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> jest wywoływana w kontenerze z pojedynczym wyborem, gdzie <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` i inny element jest już zaznaczony.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki wyboru automatyzacji interfejsu użytkownika](implementing-the-ui-automation-selection-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład dostawcy fragmentu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
