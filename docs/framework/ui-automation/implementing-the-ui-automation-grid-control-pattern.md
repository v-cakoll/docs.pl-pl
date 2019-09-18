---
title: Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 222f79934b183b836f74575cdcc611588b41ce2a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043443"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IGridProvider>dotyczące wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.GridPattern> kontrolki służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.IGridItemProvider> i być zorganizowane w dwuwymiarowej logicznej układzie współrzędnych, który może być przesunięty przez wiersz i kolumnę. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli siatki należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Współrzędne siatki są zależne od zera w lewym górnym rogu (lub w prawym górnym rogu w zależności od ustawień regionalnych) ze współrzędnymi (0, 0).  
  
- Jeśli komórka jest pusta, element automatyzacji interfejsu użytkownika musi nadal być zwracany w celu obsługi <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> właściwości tej komórki. Jest to możliwe, gdy układ elementów podrzędnych w siatce jest podobny do niewyrównanej tablicy (Zobacz przykład poniżej).  
  
 ![Widok Eksploratora Windows z niewyrównanym układem.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Przykład kontrolki siatki z pustymi współrzędnymi  
  
- Siatka z pojedynczym elementem jest nadal wymagana do wdrożenia <xref:System.Windows.Automation.Provider.IGridProvider> , jeśli jest on logicznie traktowany jako siatka. Liczba elementów podrzędnych w siatce nie jest istotna.  
  
- Ukryte wiersze i kolumny, w zależności od implementacji dostawcy, mogą zostać załadowane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie i <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> w związku z tym zostaną odzwierciedlone we <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> właściwościach i. Jeśli ukryte wiersze i kolumny nie zostały jeszcze załadowane, nie powinny być zliczane.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>nie włącza aktywnego manipulowania siatką; <xref:System.Windows.Automation.Provider.ITransformProvider> należy zaimplementować, aby włączyć tę funkcję.  
  
- Użyj metody <xref:System.Windows.Automation.StructureChangedEventHandler> , aby nasłuchiwać zmian strukturalnych lub układu w siatce, takich jak komórki, które zostały dodane, usunięte lub scalone.  
  
- Użyj, <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> aby śledzić przechodzenie przez elementy lub komórki siatki.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Wymagane elementy członkowskie dla IGridProvider  
 Do zaimplementowania interfejsu IGridProvider są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Jeśli żądana Współrzędna wierszy jest większa niż <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> lub Współrzędna kolumny jest większa <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>niż.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Jeśli jeden z żądanych współrzędnych wierszy lub kolumn jest mniejszy od zera.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
