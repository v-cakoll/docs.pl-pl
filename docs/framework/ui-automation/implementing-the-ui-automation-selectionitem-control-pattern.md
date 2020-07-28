---
title: Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
description: Zapoznaj się z instrukcjami i konwencjami, aby zaimplementować wzorzec kontrolki SelectionItem dla w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu ISelectionItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 441417aa370563a9ce8b513be6ca4507b21e1e4a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163541"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.ISelectionItemProvider> , w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 <xref:System.Windows.Automation.SelectionItemPattern>Wzorzec kontrolki służy do obsługi kontrolek, które działają jako osoby indywidualnej, do wyboru elementów podrzędnych formantów kontenera, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider> . Aby zapoznać się z przykładami formantów implementujących wzorzec kontrolki SelectionItem dla, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki elementu zaznaczania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki pojedynczego wyboru, które zarządzają kontrolkami podrzędnymi, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> , takie jak suwak **rozdzielczości ekranu** w oknie dialogowym **właściwości wyświetlania** , powinny implementować i <xref:System.Windows.Automation.Provider.ISelectionProvider> ich elementy podrzędne powinny implementować zarówno <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> , jak i <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>Wymagane elementy członkowskie dla ISelectionItemProvider  
 Do zaimplementowania są wymagane następujące właściwości, metody i zdarzenia <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wydarzenie|Uruchamiany, gdy zaznaczenie w kontenerze znacząco uległo zmianie i wymaga wysyłania więcej <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> i <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> zdarzeń niż na <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> stałe.|  
  
- Jeśli wynik a, a <xref:System.Windows.Automation.SelectionItemPattern.Select%2A> <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A> lub <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jest pojedynczym zaznaczonym elementem, <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> powinien zostać podniesiony; w przeciwnym razie Wyślij <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> zgodnie z potrzebami.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Gdy podejmowana jest jakakolwiek z następujących prób:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana dla kontenera pojedynczego wyboru <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` , gdzie i element jest już zaznaczony.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana w kontenerze wielokrotnego wyboru <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` , gdzie jest zaznaczony tylko jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>jest wywoływana dla kontenera pojedynczego wyboru <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` , gdzie i inny element jest już zaznaczony.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika](implementing-the-ui-automation-selection-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład dostawcy fragmentu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
