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
ms.openlocfilehash: b770b4ff4a4ad144928defd84d3917082a91505d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611439"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.GridPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które działają jak kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.IGridItemProvider> i zorganizowane w dwuwymiarowej logiczne współrzędnych być przechodni według wierszy i kolumn. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki siatki, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Współrzędne siatki są oparte na zerze z lewym górnym rogu (lub górną prawa komórka w zależności od ustawień regionalnych), o współrzędnych (0, 0).  
  
-   Jeśli komórka jest pusta, element automatyzacji interfejsu użytkownika nadal musi zostać zwrócony w celu obsługi <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> właściwości dla tej komórki. Jest to możliwe, gdy układu elementów podrzędnych siatki jest podobna do niewyrównanych tablicy (zobacz poniższy przykład).  
  
 ![Eksplorator Windows umożliwia wyświetlanie niewyrównanym układem. ](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Przykład formantu siatki z pustym służy do koordynowania  
  
-   Siatka zawierająca pojedynczy element jest nadal wymagane, aby zaimplementować <xref:System.Windows.Automation.Provider.IGridProvider> Jeśli logicznie jest uważana za siatki. Liczba elementów podrzędnych siatki jest bez znaczenia.  
  
-   Ukryte wierszy i kolumn, w zależności od implementacji dostawcy może zostać załadowany w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa i w związku z tym zostaną odzwierciedlone w <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> i <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> właściwości. Jeśli ukryte wiersze i kolumny nie zostały jeszcze zostały załadowane, nie należy ich liczony.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> nie obsługuje aktywnego manipulowania siatki; <xref:System.Windows.Automation.Provider.ITransformProvider> musi zaimplementować tak, aby włączyć tę funkcję.  
  
-   Użyj <xref:System.Windows.Automation.StructureChangedEventHandler> do nasłuchiwania zmian strukturalnych, ani układu siatki, takich jak komórki, które zostały dodane, usunięte lub scalony.  
  
-   Użyj <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> do śledzenia przechodzenie przez elementy lub komórki siatki.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Wymagane elementy IGridProvider  
 Poniższe właściwości i metod są wymagane do implementowania interfejsu IGridProvider.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Jeśli współrzędne żądany wiersz jest większy niż <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> lub współrzędne kolumny jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> — Jeśli żądany wiersz lub kolumnę współrzędnych jest mniejsza niż zero.|  
  
## <a name="see-also"></a>Zobacz także
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
