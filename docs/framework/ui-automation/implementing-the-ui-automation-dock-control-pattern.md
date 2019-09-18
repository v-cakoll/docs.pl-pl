---
title: Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b72d7f9a68c2309f2bd1a73741ac621cde1f3115
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043472"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IDockProvider>dotyczące wdrażania, w tym informacje o właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.DockPattern> kontrolki służy do uwidaczniania właściwości dokowania kontrolki wewnątrz kontenera dokowania. Kontener dokowania jest formantem, który umożliwia rozmieszczenie elementów podrzędnych w poziomie i w pionie względem siebie. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Dokowanie kontenera z dwoma zadokowanymi elementami podrzędnymi.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Przykład dokowania z programu Visual Studio, w którym znajduje się okno "Widok klasy". DockPosition. Right i okno "Lista błędów" to DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli dokowania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>nie uwidacznia żadnych właściwości kontenera Docker ani żadnych właściwości formantów, które są zadokowane sąsiadująco z bieżącą kontrolką w kontenerze dokowania.  
  
- Kontrolki są zadokowane względem siebie w oparciu o ich bieżącą kolejność z. im wyższe położenie porządku osi z, tym więcej są umieszczane z określonej krawędzi kontenera dokowania.  
  
- Jeśli rozmiar kontenera dokowania zostanie zmieniony, wszystkie kontrolki zadokowane w kontenerze zostaną przesunięte do tej samej krawędzi, w której zostały pierwotnie zadokowane. Rozmiar zadokowanych kontrolek również zmieni się, aby wypełnić dowolne miejsce w kontenerze zgodnie z zachowaniem <xref:System.Windows.Automation.DockPosition>dokowania. Na przykład jeśli <xref:System.Windows.Automation.DockPosition.Top> jest określony, po lewej i prawej stronie kontrolki zostanie rozwinięte, aby wypełnić dostępne miejsce. Jeśli <xref:System.Windows.Automation.DockPosition.Fill> jest określony, wszystkie cztery strony kontrolki zostaną rozwinięte w celu wypełnienia dostępnego miejsca.  
  
- W systemie z obsługą kilku monitorów kontrolki powinny być zadokowane po lewej lub prawej stronie bieżącego monitora. Jeśli nie jest to możliwe, powinny one zostać zadokowane po lewej stronie monitora z lewym przyciskiem myszy lub po prawej stronie monitora z najprawej strony.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Wymagane elementy członkowskie dla IDockProvider  
 Do zaimplementowania interfejsu IDockProvider są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> — Gdy kontrolka nie może wykonać żądanego stylu dokowania.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
