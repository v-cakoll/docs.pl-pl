---
title: Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 04f3ee1e01054df6a13ab2391e14a6a7f7274bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180212"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IGridProvider>i konwencje dotyczące implementacji, w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.GridPattern> formantu służy do obsługi formantów, które działają jako kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego <xref:System.Windows.Automation.Provider.IGridItemProvider> elementu muszą implementować i być zorganizowane w dwuwymiarowym logicznym układzie współrzędnych, który może być przemierzany przez wiersze i kolumnę. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca kontroli siatki należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Współrzędne siatki są oparte na zeru, a górna lewa (lub prawa górna komórka w zależności od ustawień regionalnych) ma współrzędne (0, 0).  
  
- Jeśli komórka jest pusta, element automatyzacji interfejsu użytkownika nadal <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> musi być zwracany w celu obsługi właściwości dla tej komórki. Jest to możliwe, gdy układ elementów podrzędnych w siatce jest podobny do tablicy niewyrównanej (zobacz przykład poniżej).  
  
 ![Widok Eksploratora Windows przedstawiający niewyrównany układ.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Przykład formantu siatki z pustymi współrzędnymi  
  
- Siatka z pojedynczym elementem jest <xref:System.Windows.Automation.Provider.IGridProvider> nadal wymagana do zaimplementowania, jeśli jest logicznie uważana za siatkę. Liczba elementów podrzędnych w siatce jest nieistotna.  
  
- Ukryte wiersze i kolumny, w zależności od implementacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy, mogą być ładowane w drzewie i dlatego zostaną odzwierciedlone w <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> i <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> właściwości. Jeśli ukryte wiersze i kolumny nie zostały jeszcze załadowane, nie powinny być liczone.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>nie umożliwia aktywnej manipulacji siatką; <xref:System.Windows.Automation.Provider.ITransformProvider> należy wdrożyć, aby włączyć tę funkcję.  
  
- A <xref:System.Windows.Automation.StructureChangedEventHandler> służy do nasłuchiwać zmian strukturalnych lub układu w siatce, takich jak komórki, które zostały dodane, usunięte lub scalone.  
  
- A <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> służy do śledzenia przechodzenia przez elementy lub komórki siatki.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>Wymagana liczba członków dla IGridProvider  
 Następujące właściwości i metody są wymagane do implementowania interfejsu IGridProvider.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Jeśli żądana współrzędna wiersza jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> współrzędna lub jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Jeśli jeden z żądanych współrzędnych wiersza lub kolumny jest mniejszy niż zero.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
