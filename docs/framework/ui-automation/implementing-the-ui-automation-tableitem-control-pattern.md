---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f35b491c31e8725eac0025dfd6815079d0ea9b79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180074"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ITableItemProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.TableItemPattern> kontroli służy do obsługi formantu podrzędnego kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>. Dostęp do poszczególnych funkcji komórek zapewnia wymagana jednoczesna <xref:System.Windows.Automation.Provider.IGridItemProvider>implementacja programu . Ten wzorzec formantu jest analogiczne <xref:System.Windows.Automation.Provider.IGridItemProvider> <xref:System.Windows.Automation.Provider.ITableItemProvider> do rozróżnienia, że wszelkie formanty implementacji musi programowo uwidaczniać relację między poszczególnych komórek i jej wiersza i kolumny informacji. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
  
- Aby zapoznać się z funkcją elementów siatki pokrewne, zobacz [Implementowanie wzorca sterowania interfejsem użytkownika automatyzacji](implementing-the-ui-automation-griditem-control-pattern.md)interfejsu użytkownika .  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a>Wymagane elementy członkowskie dla ITableItemProvider  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych właściwości lub zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu nie ma skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika](implementing-the-ui-automation-table-control-pattern.md)
- [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-griditem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
