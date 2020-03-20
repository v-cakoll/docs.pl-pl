---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180190"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IGridItemProvider>i konwencje dotyczące wdrażania, w tym informacje o właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu przeglądu.  
  
 Wzorzec <xref:System.Windows.Automation.GridItemPattern> kontroli służy do obsługi poszczególnych <xref:System.Windows.Automation.Provider.IGridProvider>formantów podrzędnych kontenerów, które implementują . Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania <xref:System.Windows.Automation.Provider.IGridProvider>należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Współrzędne siatki są oparte na wartości zerowej, a lewa górna komórka ma współrzędne (0, 0).  
  
- Scalone komórki <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> będą <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> raportować swoje i właściwości na podstawie ich podstawowej komórki kotwicy zdefiniowanej przez dostawcę automatyzacji interfejsu użytkownika. Zazwyczaj będzie to najwyższy i najbardziej wysunięty do lewej wiersz lub kolumna.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>nie przewiduje aktywnej manipulacji siatką, takiej jak scalanie lub dzielenie komórek.  
  
- Formanty, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> zazwyczaj mogą być przechodzione (czyli klient automatyzacji interfejsu użytkownika można przenieść do sąsiednich formantów) za pomocą klawiatury.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>Wymagana liczba członków dla IGridItemProvider  
 Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IGridItemProvider>do wdrożenia .  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Właściwość|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych metod ani zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu nie ma skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
