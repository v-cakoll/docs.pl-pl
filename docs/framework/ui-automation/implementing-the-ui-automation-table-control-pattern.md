---
title: Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
description: Zapoznaj się z wytycznymi i konwencjami w celu zaimplementowania wzorca kontrolki tabeli w automatyzacji interfejsu użytkownika. Znajomość wymaganych członków interfejsu ITableProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168235"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.ITableProvider> , w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 <xref:System.Windows.Automation.TablePattern>Wzorzec kontrolki służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i być zorganizowane w dwuwymiarowej logicznej układzie współrzędnych, który może być przesunięty przez wiersz i kolumnę. Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridProvider> , z rozróżnieniem, że jakakolwiek kontrolka implementująca <xref:System.Windows.Automation.Provider.ITableProvider> musi także uwidaczniać relację nagłówka kolumny i/lub wiersza dla każdego elementu podrzędnego. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli tabeli należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Dostęp do zawartości poszczególnych komórek odbywa się za pomocą dwuwymiarowego układu współrzędnych lub tablicy udostępnionej przez wymaganą współbieżną implementację <xref:System.Windows.Automation.Provider.IGridProvider> .  
  
- Nagłówek kolumny lub wiersza może być zawarty w obiekcie tabeli lub być osobnym obiektem nagłówkowym skojarzonym z obiektem tabeli.  
  
- Nagłówki kolumn i wierszy mogą zawierać zarówno nagłówek podstawowy, jak i nagłówki pomocnicze.  
  
> [!NOTE]
> Pojęcie to jest widoczne w arkuszu kalkulacyjnym programu Microsoft Excel, w którym użytkownik zdefiniował kolumnę "imię Name". Ta kolumna ma teraz dwa nagłówki — nagłówek "First Name" zdefiniowany przez użytkownika i alfanumeryczne oznaczenie tej kolumny przypisanej przez aplikację.  
  
- Zobacz [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md) dla powiązanych funkcji siatki.  
  
 ![Tabela ze złożonymi elementami nagłówka.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Przykład tabeli z złożonymi nagłówkami kolumn  
  
 ![Tabela z niejednoznaczną właściwością RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>Wymagane elementy członkowskie dla ITableProvider  
 Dla interfejsu ITableProvider są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
