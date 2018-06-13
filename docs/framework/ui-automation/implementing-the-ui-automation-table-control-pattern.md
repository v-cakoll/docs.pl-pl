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
ms.openlocfilehash: 955d9f005a45ab805012dd43cbef27877a9dfdb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398583"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementacja wzorca kontrolki tabeli automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITableProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.TablePattern> — Wzorzec formantu jest używana do obsługi formantów, które działają jak kontenery kolekcję elementów podrzędnych. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.ITableItemProvider> i zorganizowane dwuwymiarowa logicznego układu współrzędnych, który można przekształcić według wierszy i kolumn. Ten wzorzec kontroli jest odpowiednikiem <xref:System.Windows.Automation.Provider.IGridProvider>, z rozróżnienie żadnego kontroli wykonania <xref:System.Windows.Automation.Provider.ITableProvider> również musi ujawniać relacji nagłówek kolumny i/lub wiersz dla każdego elementu podrzędnego. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca formantu tabeli, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Dostęp do zawartości komórki jest za pośrednictwem dwuwymiarowa współrzędnych logicznych lub tablicy podał wymagane wdrożenia równoczesnych <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Nagłówek kolumny lub wiersza mogą być zawarte w obiekcie tabeli lub być obiekt oddzielny nagłówek, który jest skojarzony z obiektem tabeli.  
  
-   Nagłówki kolumn i wierszy może obejmować zarówno nagłówek podstawowy, jak i wszelkie nagłówki pomocniczych.  
  
> [!NOTE]
>  To pojęcie staje się widoczna w [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] arkusza kalkulacyjnego, w którym zdefiniowany przez użytkownika kolumny "Imię". Ta kolumna zawiera teraz dwa nagłówki — nagłówek "Imię" zdefiniowany przez użytkownika i oznaczenie alfanumeryczne dla tej kolumny przypisane przez aplikację.  
  
-   Zobacz [implementacja wzorca formantu siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) siatki powiązanych funkcji.  
  
 ![Tabela ze złożonymi elementami nagłówka. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Przykład tabeli z nagłówkami kolumn złożonych  
  
 ![Tabela z niejednoznaczną właściwością RowOrColumnMajor. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Przykład tabeli z niejednoznaczną właściwością RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Wymagane elementy ITableProvider  
 Poniższe właściwości i metody są wymagane dla interfejsu ITableProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Brak|  
  
 Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu ma bez wyjątków skojarzone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca kontrolki TableItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
