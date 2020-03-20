---
title: Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 02505224e4673592f1e169c40af1cfb098e5d9bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180099"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ISelectionItemProvider>i konwencje dotyczące implementacji, w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.SelectionItemPattern> formantu służy do obsługi formantów, które działają <xref:System.Windows.Automation.Provider.ISelectionProvider>jako indywidualne, wybieralne elementy podrzędne formantów kontenera, które implementują . Aby zapoznać się z przykładami formantów implementuujnych wzorca kontroli SelectionItem, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli elementu zaznaczenia należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Formanty pojedynczego wyboru, <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>które zarządzają formanty podrzędne, które implementują, takie jak <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> suwak <xref:System.Windows.Automation.Provider.ISelectionItemProvider> **Rozdzielczość ekranu** w oknie dialogowym Właściwości wyświetlania, powinny zostać zaimplementować, <xref:System.Windows.Automation.Provider.ISelectionProvider> a ich elementy podrzędne powinny zaimplementować zarówno elementy **podrzędne,** jak i .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>Wymagana liczba członków do iselectionItemProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.ISelectionItemProvider>są wymagane następujące właściwości, metody i zdarzenia.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wydarzenie|Wywoływane, gdy zaznaczenie w kontenerze uległo <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> znacznej <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> zmianie i wymaga wysyłania więcej <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> zdarzeń niż stałe zezwolenia.|  
  
- Jeżeli <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>wynik , an <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>lub <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> a jest pojedynczym <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> wybranym elementem, należy podnieść; w <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> przeciwnym razie wysłać w razie potrzeby.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|W przypadku podjęcia jakiejkolwiek z następujących czynności:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana w kontenerze <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` pojedynczego wyboru, w którym i element jest już zaznaczony.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>jest wywoływana w kontenerze <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` wielokrotnego wyboru, w którym i tylko jeden element jest zaznaczony.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>jest wywoływana w kontenerze <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` pojedynczego wyboru, w którym i inny element jest już zaznaczony.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki wyboru automatyzacji interfejsu użytkownika](implementing-the-ui-automation-selection-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
- [Przykład dostawcy fragmentu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
