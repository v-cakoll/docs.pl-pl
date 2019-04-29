---
title: Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: ff07f5264ccb3ec699e3676a2e9ba64443b2875f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610013"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które wizualnie rozwinąć w celu wyświetlenia większej ilości zawartości i zwinąć i ukryć zawartości. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki expandcollapse dla, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
- Agreguj kontrolek — utworzonych za pomocą obiektów podrzędnych, które będą dostarczać interfejs użytkownika przy użyciu funkcji Rozwiń/Zwiń — musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolować wzorzec ich elementów podrzędnych nie. Na przykład kontrolka pola kombi został utworzony za pomocą kombinacji pola listy, przycisk i kontrolkach edycji wzbogaconej, ale jest tylko pola kombi nadrzędny, musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Wyjątek stanowi formant menu, która będzie agregacją poszczególnych obiektów MenuItem. Może obsługiwać obiekty MenuItem <xref:System.Windows.Automation.ExpandCollapsePattern> — wzorzec kontrolki, ale nadrzędnego Menu kontroli nie. Podobne wyjątek ma zastosowanie do kontrolki drzewa i element drzewa.  
  
- Gdy <xref:System.Windows.Automation.ExpandCollapseState> kontrolki jest ustawiony na wartość <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, wszelkie <xref:System.Windows.Automation.ExpandCollapsePattern> funkcje są obecnie nieaktywne dla formantu i tylko informacje, które można uzyskać za pomocą tego wzorca kontrolki <xref:System.Windows.Automation.ExpandCollapseState>. Jeśli wszystkie jego obiekty podrzędne zostaną dodane, <xref:System.Windows.Automation.ExpandCollapseState> zmiany i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcja jest aktywowana.  
  
- <xref:System.Windows.Automation.ExpandCollapseState> odwołuje się do widoczność obiektów bezpośrednie podrzędne. nie odwołuje się do widoczność wszystkie obiekty zależne.  
  
- Rozwiń i Zwiń funkcje są specyficzne dla formantu. Poniżej przedstawiono przykłady to zachowanie.  
  
    - Osobiste Menu pakietu Office może być MenuItem-stanowy (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> i <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) gdzie kontrolka Określa stan do przyjęcia, kiedy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana.  
  
    - Wywoływanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem mogą być wyświetlane wszystkie obiekty podrzędne lub tylko bezpośrednie elementy podrzędne.  
  
    - Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> na kontrolce przechowuje informacje o stanie jego elementy potomne, zdarzenia zmiany widoczność powinny być przesyłane nie zdarzenia zmiany stanu, jeśli formant nadrzędny nie przechowuje stanu jego elementy podrzędne, jeśli zwinięte, formant może zniszczyć wszystkie elementy podrzędne, które nie są już widoczne i zgłoś zdarzenie niszczone; lub mogą ulec zmianie <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego obiektu podrzędnego i zgłoś zdarzenie zmiany widoczność.  
  
- Aby zagwarantować nawigacji, jest pożądane dla obiektu w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (ze stanem odpowiednich widoczności), niezależnie od jego elementów nadrzędnych <xref:System.Windows.Automation.ExpandCollapseState>. Jeśli elementy podrzędne są generowane na żądanie, mogą występować jedynie w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa po są wyświetlane najpierw czas lub tylko wtedy, gdy są one widoczne.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Wymagane elementy IExpandCollapseProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Zdarzenie|Ta kontrolka nie ma żadnych skojarzonych zdarzeń; Użyj ten delegat ogólny.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Albo <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana, gdy <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
