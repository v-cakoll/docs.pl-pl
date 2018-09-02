---
title: Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 410fe76fe6e3ddba143622c1bc4d0270d906d854
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423152"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementacja wzorca kontrolki SelectionItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które działają jako osobę, można wybierać podrzędnych elementów kontrolki kontenera, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider>. Przykłady formantów, które implementują wzorca kontrolki SelectionItem dla, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki SelectionItem, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Formanty pojedynczego wyboru, które zarządzają formantów podrzędnych, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, takich jak **rozdzielczość ekranu** suwak w **właściwości wyświetlania** okno dialogowe, należy zaimplementować <xref:System.Windows.Automation.Provider.ISelectionProvider>i ich elementy podrzędne należy zaimplementować obu <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Wymagane elementy ISelectionItemProvider  
 Następujące właściwości, metody i zdarzenia są zobowiązani do realizacji <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zdarzenie|Wywoływane, gdy wybór w kontenerze zmienił się znacząco i wymaga wysłania więcej <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> i <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> zdarzeń, niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> pozwala na stałe.|  
  
-   Jeśli wynik <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, lub <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> jest jednego wybranego elementu <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> powinien być wywoływany; w przeciwnym razie Wyślij <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> odpowiednio.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Jeśli dowolny z następujących próba:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> jest wywoływana w kontenerze pojedynczego wyboru gdzie <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` i element jest już wybrany.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> jest wywoływana w kontenerze wielokrotnego wyboru gdzie <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` i wybrano tylko jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> jest wywoływana w kontenerze pojedynczego wyboru gdzie <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` i inny element jest już wybrany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca kontrolki wyboru automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Przykład dostawcy fragmentu](https://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
