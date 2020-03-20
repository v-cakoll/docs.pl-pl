---
title: Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180115"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ITableProvider>i konwencje dotyczące implementacji, w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.TablePattern> formantu służy do obsługi formantów, które działają jako kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego <xref:System.Windows.Automation.Provider.ITableItemProvider> elementu muszą implementować i być zorganizowane w dwuwymiarowym logicznym układzie współrzędnych, który może być przemierzany przez wiersze i kolumnę. Ten wzorzec formantu jest analogiczne <xref:System.Windows.Automation.Provider.IGridProvider>do <xref:System.Windows.Automation.Provider.ITableProvider> , z rozróżnieniem, że wszelkie formanty implementacji musi również uwidaczniać relację nagłówka kolumny i/lub wiersza dla każdego elementu podrzędnego. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli tabeli należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Dostęp do zawartości poszczególnych komórek odbywa się za pośrednictwem dwuwymiarowego logicznego układu <xref:System.Windows.Automation.Provider.IGridProvider>współrzędnych lub tablicy dostarczanej przez wymaganą równoczesną implementację programu .  
  
- Nagłówek kolumny lub wiersza może znajdować się w obiekcie tabeli lub być oddzielnym obiektem nagłówka skojarzonym z obiektem tabeli.  
  
- Nagłówki kolumn i wierszy mogą zawierać zarówno nagłówek podstawowy, jak i wszystkie nagłówki pomocnicze.  
  
> [!NOTE]
> Ta koncepcja staje się widoczna w arkuszu kalkulacyjnym programu Microsoft Excel, w którym użytkownik zdefiniował kolumnę "Imię". Ta kolumna ma teraz dwa nagłówki — nagłówek "Imię" zdefiniowany przez użytkownika i oznaczenie alfanumeryczne dla tej kolumny przypisanej przez aplikację.  
  
- Zobacz [implementowanie wzorca kontroli siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md) dla powiązanych funkcji siatki.  
  
 ![Tabela ze złożonymi elementami nagłówka.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Przykład tabeli ze złożonymi nagłówkami kolumn  
  
 ![Tabela z niejednoznaczną właściwością RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>Wymagana liczba członków dla iTableProvider  
 Następujące właściwości i metody są wymagane dla interfejsu ITableProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu nie ma skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
