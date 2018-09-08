---
title: Implementacja wzorca formantu tabeli automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 7466a7cc25ac742483e21fc1ee4a631bd43bc5a3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181592"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.TablePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które działają jak kontenery dla kolekcji elementów podrzędnych. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i zorganizowane w dwuwymiarowej logiczne współrzędnych być przechodni według wierszy i kolumn. Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridProvider>, za pomocą rozróżnienie, że kontrolnych Implementowanie <xref:System.Windows.Automation.Provider.ITableProvider> również musi ujawniać relację nagłówek kolumny i/lub wiersza dla każdego elementu podrzędnego. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki tabeli, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Dostęp do zawartości poszczególnych komórek jest dwuwymiarowy współrzędnych logicznych lub tablicy, dostarczone przez wymagane wykonania współbieżnych <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Nagłówek kolumny lub wiersza mogą być zawarte w obiekcie tabeli lub być obiekt oddzielny nagłówek, który jest skojarzony z obiektem tabeli.  
  
-   Nagłówki kolumn i wierszy może obejmować zarówno podstawowego nagłówka, jak również wszelkie nagłówki pomocniczych.  
  
> [!NOTE]
>  Takie podejście staje się widoczna w [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusza kalkulacyjnego, gdzie został zdefiniowany przez użytkownika kolumny "Imię". Ta kolumna zawiera teraz dwa nagłówki — nagłówek "Imię" zdefiniowany przez użytkownika i oznaczenie alfanumeryczne dla tej kolumny przypisany przez aplikację.  
  
-   Zobacz [implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) siatki powiązanych funkcji.  
  
 ![Tabela, z elementami complex — nagłówek. ](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Przykład tabeli z nagłówkami kolumn złożonych  
  
 ![Tabela z niejednoznaczną właściwością RowOrColumnMajor. ](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Wymagane elementy ITableProvider  
 Poniższe właściwości i metod są wymagane dla interfejsu ITableProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
