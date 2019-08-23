---
title: Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: aef1d31499f65834fa1268147e45f82294fe560a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935688"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.ISelectionItemProvider>dotyczące wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 Wzorzec kontrolki służy do obsługi kontrolek, które działają jako osoby indywidualnej, do wyboru elementów podrzędnych formantów kontenera, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider>. <xref:System.Windows.Automation.SelectionItemPattern> Aby zapoznać się z przykładami formantów implementujących wzorzec kontrolki SelectionItem dla, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki elementu zaznaczania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki pojedynczego wyboru, które zarządzają kontrolkami <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>podrzędnymi, które implementują, takie jak suwak **rozdzielczości ekranu** w oknie dialogowym **właściwości wyświetlania** , powinny implementować <xref:System.Windows.Automation.Provider.ISelectionProvider> i ich elementy podrzędne powinny implementować oba <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> i .<xref:System.Windows.Automation.Provider.ISelectionItemProvider>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Wymagane elementy członkowskie dla ISelectionItemProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.ISelectionItemProvider>są wymagane następujące właściwości, metody i zdarzenia.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zdarzenie|Uruchamiany, gdy zaznaczenie w kontenerze znacząco uległo zmianie i wymaga wysyłania <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> więcej <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> i zdarzeń niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> na stałe.|  
  
- <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>Jeśli wynik a <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, a lub <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jest pojedynczym zaznaczonym elementem, <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> powinien zostać podniesiony; w przeciwnym razie Wyślij <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> zgodnie z potrzebami.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Gdy podejmowana jest jakakolwiek z następujących prób:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana dla kontenera pojedynczego wyboru, gdzie <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` i element jest już zaznaczony.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana w kontenerze wielokrotnego wyboru, <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> gdzie  =  `true` jest zaznaczony tylko jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>jest wywoływana dla kontenera pojedynczego wyboru, gdzie <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` i inny element jest już zaznaczony.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki wyboru automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Przykład dostawcy fragmentu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
