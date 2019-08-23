---
title: Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0852e904414ac4af6777b9476b4b6ad504a09ef3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935706"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.ITableProvider>dotyczące wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.TablePattern> kontrolki służy do obsługi kontrolek, które działają jako kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego elementu muszą implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i być zorganizowane w dwuwymiarowej logicznej układzie współrzędnych, który może być przesunięty przez wiersz i kolumnę. Ten wzorzec kontrolki jest analogiczny do <xref:System.Windows.Automation.Provider.IGridProvider>, z rozróżnieniem, że jakakolwiek kontrolka implementująca <xref:System.Windows.Automation.Provider.ITableProvider> musi także uwidaczniać relację nagłówka kolumny i/lub wiersza dla każdego elementu podrzędnego. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli tabeli należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Dostęp do zawartości poszczególnych komórek odbywa się za pomocą dwuwymiarowego układu współrzędnych lub tablicy udostępnionej przez wymaganą współbieżną <xref:System.Windows.Automation.Provider.IGridProvider>implementację.  
  
- Nagłówek kolumny lub wiersza może być zawarty w obiekcie tabeli lub być osobnym obiektem nagłówkowym skojarzonym z obiektem tabeli.  
  
- Nagłówki kolumn i wierszy mogą zawierać zarówno nagłówek podstawowy, jak i nagłówki pomocnicze.  
  
> [!NOTE]
> Pojęcie to jest [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] widoczne w arkuszu kalkulacyjnym, w którym użytkownik zdefiniował kolumnę "imię Name". Ta kolumna ma teraz dwa nagłówki — nagłówek "First Name" zdefiniowany przez użytkownika i alfanumeryczne oznaczenie tej kolumny przypisanej przez aplikację.  
  
- Zobacz [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) dla powiązanych funkcji siatki.  
  
 ![Tabela ze złożonymi elementami nagłówka.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Przykład tabeli z złożonymi nagłówkami kolumn  
  
 ![Tabela z niejednoznaczną właściwością RowOrColumnMajor.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
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

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
