---
title: Implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0038202fb7c7f1a6e0b4f21592d7a1056c4dfa2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.GridPattern> — Wzorzec formantu jest używana do obsługi formantów, które działają jak kontenery kolekcję elementów podrzędnych. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.IGridItemProvider> i zorganizowane dwuwymiarowa logicznego układu współrzędnych, który można przekształcić według wierszy i kolumn. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca formantu siatki, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Współrzędne siatki są liczony od zera o konieczności współrzędne (0, 0) u góry z lewej (lub górna prawa komórka w zależności od ustawień regionalnych).  
  
-   Jeśli komórka jest pusta, nadal musi zostać zwrócona elementu automatyzacji interfejsu użytkownika w celu zapewnienia obsługi <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> właściwości dla komórki. Jest to możliwe, gdy układ elementów podrzędnych siatki jest podobna do tablicy niewyrównane (zobacz poniższy przykład).  
  
 ![Widok Eksploratora Windows z niewyrównanym układem. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Przykład formantu siatki o pustym współrzędnych  
  
-   Siatkę z pojedynczego elementu jest nadal wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IGridProvider> Jeśli logicznie jest uważany za siatki. Liczba elementów podrzędnych siatki jest bez znaczenia.  
  
-   Ukryte wiersze i kolumny, w zależności od implementacji dostawcy mogą być ładowane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, a w związku z tym zostaną odzwierciedlone w <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> i <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> właściwości. Jeśli ukryte wiersze i kolumny nie zostały jeszcze zostały załadowane, ich nie powinno być liczone.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> nie obsługuje aktywnego manipulowania siatki; <xref:System.Windows.Automation.Provider.ITransformProvider> musi zostać wdrożona, aby włączyć tę funkcję.  
  
-   Użyj <xref:System.Windows.Automation.StructureChangedEventHandler> do nasłuchiwania zmian strukturalnych lub układ do siatki, takich jak komórki, które zostały dodane, usunięte lub scalone.  
  
-   Użyj <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> do śledzenia przechodzenie przez elementy lub komórki siatki.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Wymagane elementy IGridProvider  
 Poniższe właściwości i metody są wymagane do implementowania interfejsu IGridProvider.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Brak|  
  
 Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Jeśli Współrzędna żądanego wiersza jest większy niż <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> lub Współrzędna kolumny jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Jeśli żądany wiersz lub kolumnę współrzędnych jest mniejsza od zera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
