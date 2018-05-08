---
title: Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f593fb09e8c1056c28d351bfdf0218a0161fd9e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementacja wzorca kontrolki ExpandCollapse dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> — Wzorzec formantu jest używana do obsługi formantów, które wizualnie Rozwiń, aby wyświetlić więcej zawartości i zwijanie ukrycia zawartości. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Podczas implementowania ExpandCollapse — wzorzec kontrolki, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Formanty agregacji — skompilowanej za pomocą obiektów podrzędnych, co stanowi interfejsu użytkownika dla funkcji Rozwiń/Zwiń — musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolować wzorzec ich elementy podrzędne nie. Na przykład wbudowana w kombinację pola listy, przycisk i formantów edycji kontrolki pola kombi, ale jest tylko pola kombi nadrzędnego, który musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Wyjątkiem jest formant menu, która jest agregacją pojedyncze obiekty MenuItem. Obiekty MenuItem może obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> — wzorzec formantu, ale nadrzędnego Menu sterowania nie. Podobne wyjątek dotyczy formantów drzewa i element drzewa.  
  
-   Gdy <xref:System.Windows.Automation.ExpandCollapseState> formantu ma ustawioną wartość <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, wszelkie <xref:System.Windows.Automation.ExpandCollapsePattern> funkcje są obecnie nieaktywne formantu i jest tylko informacje można uzyskać za pomocą tego wzorca formantu <xref:System.Windows.Automation.ExpandCollapseState>. Jeśli później zostaną dodane wszystkie jego obiekty podrzędne, <xref:System.Windows.Automation.ExpandCollapseState> zmiany i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcji jest aktywny.  
  
-   <xref:System.Windows.Automation.ExpandCollapseState> odwołuje się do widoczność obiektów natychmiastowego podrzędnych. nie odwołuje się do widoczność wszystkie obiekty zależne.  
  
-   Rozwiń węzeł, a funkcja zwijania jest specyficzne dla formantu. Poniżej przedstawiono przykłady tego zachowania.  
  
    -   Menu osobiste Office może być MenuItem trzy stanowy (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> i <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) gdy formant określa stan przyjęcie, kiedy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana.  
  
    -   Wywoływanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem może wyświetlać wszystkie elementy podrzędne lub tylko bezpośrednie elementy podrzędne.  
  
    -   Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> w formancie przechowuje informacje o stanie jego elementy podrzędne zdarzenia zmiany widoczność mają być wysyłane, nie zdarzenia zmiany stanu Jeśli formant nadrzędny nie przechowuje stanu jego elementy podrzędne, jeśli zwinięte, może formantu zniszczyć wszystkie elementy podrzędne, które nie są już widoczne i wywołaj zdarzenie niszczone; lub może go zmienić <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego obiektu podrzędnego i zgłoś zdarzenie zmiany widoczności.  
  
-   Aby zagwarantować nawigacji, jest pożądane dla obiekt w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (z odpowiednią widoczność stanu), niezależnie od jego obiektów nadrzędnych <xref:System.Windows.Automation.ExpandCollapseState>. Jeśli elementy podrzędne są generowane na żądanie, mogą występować jedynie w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa po będzie wyświetlany dla czasu lub najpierw tylko, gdy są one widoczne.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Wymagane elementy IExpandCollapseProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Zdarzenie|Ten formant nie ma żadnych skojarzonych zdarzeń; Użyj tego Delegat ogólny.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Albo <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływane, gdy <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
