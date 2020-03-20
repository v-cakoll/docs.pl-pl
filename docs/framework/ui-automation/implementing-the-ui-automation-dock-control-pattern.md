---
title: Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b1213791609245209fa37e3cdcb0876c963bfeb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180205"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IDockProvider>i konwencje dotyczące wdrażania, w tym informacje o właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.DockPattern> formantu służy do udostępnienia właściwości doku sterowania w kontenerze dokowania. Kontener dokowania jest formantem, który umożliwia rozmieszczanie elementów podrzędnych poziomo i pionowo względem siebie. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Kontener dokowania z dwoma zadokowanymi dziećmi.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Przykład dokowania z programu Visual Studio, w którym okno "Widok klasy" jest dockposition.Right i "Lista błędów" Okno jest DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli Dock należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>nie udostępnia żadnych właściwości kontenera dokowania lub żadnych właściwości formantów, które są zadokowane w sąsiedztwie bieżącego formantu w kontenerze dokowania.  
  
- Formanty są zadokowane względem siebie na podstawie ich bieżącego zamówienia z; im wyższe jest ich rozmieszczenie z-order, tym dalej są umieszczane od określonej krawędzi kontenera dokującego.  
  
- Jeśli rozmiar kontenera dokowania zostanie przesunięty, wszystkie zadokowane kontrolki w kontenerze zostaną przesunięty równo do tej samej krawędzi, do której zostały pierwotnie zadokowane. Zadokowane formanty zmienią również rozmiar, aby wypełnić dowolne miejsce w kontenerze zgodnie z zachowaniem dokowania ich <xref:System.Windows.Automation.DockPosition>. Na przykład, <xref:System.Windows.Automation.DockPosition.Top> jeśli jest określony, po lewej i prawej stronie formantu zostanie rozwinąć, aby wypełnić wszelkie dostępne miejsce. Jeśli <xref:System.Windows.Automation.DockPosition.Fill> zostanie określony, wszystkie cztery strony formantu rozwinie się, aby wypełnić wszelkie dostępne miejsce.  
  
- W systemie wielomonitorowym elementy sterujące powinny zadokować po lewej lub prawej stronie bieżącego monitora. Jeśli nie jest to możliwe, powinny one zadokować do lewej strony monitora po lewej stronie lub po prawej stronie monitora po prawej stronie.  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a>Wymagana liczba członków dla IDockProvider  
 Następujące właściwości i metody są wymagane do implementowania interfejsu IDockProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> - Gdy formant nie jest w stanie wykonać żądany styl doku.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
