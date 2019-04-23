---
title: Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 44b14c65a5a86b4e56697904b9b013b4daa84479
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110433"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableItemProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.TableItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.ITableProvider>. Dostęp do funkcji pojedyncze komórki jest zapewniany przez wymagane wykonania współbieżnych <xref:System.Windows.Automation.Provider.IGridItemProvider>. Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridItemProvider> z rozróżnienie, że kontrolnych Implementowanie <xref:System.Windows.Automation.Provider.ITableItemProvider> programowo musi ujawniać relacji między pojedyncze komórki i jego informacje wierszy i kolumn. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
  
-   Dla funkcji elementów powiązanych siatki, zobacz [implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Wymagane elementy ITableItemProvider  
  
|Wymagany|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Metoda|Brak|  
  
 Ten wzorzec kontrolka nie ma skojarzonych z nimi właściwości lub zdarzenia.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
