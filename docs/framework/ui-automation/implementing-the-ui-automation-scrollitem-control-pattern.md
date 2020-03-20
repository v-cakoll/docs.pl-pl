---
title: Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 3a0647ab98dcb86306573a0e9826fa7232fa9ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180145"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementacja wzorca kontrolki ScrollItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i <xref:System.Windows.Automation.Provider.IScrollItemProvider>konwencje dotyczące implementowania , w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.ScrollItemPattern> kontroli służy do obsługi poszczególnych <xref:System.Windows.Automation.Provider.IScrollProvider>formantów podrzędnych kontenerów, które implementują . Ten wzorzec formantu działa jako kanał komunikacji między formantem podrzędnym a jego kontenerem, aby upewnić się, że kontener może zmienić aktualnie widoczną zawartość (lub region) w jego rzutni, aby wyświetlić formant podrzędny. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca kontroli elementu przewijania należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Elementy zawarte w window lub canvas formant nie są wymagane do zaimplementowania interfejsu IScrollItemProvider. Alternatywnie jednak muszą ujawnić prawidłową lokalizację <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>dla pliku . Umożliwi to aplikacji klienckiej automatyzacji <xref:System.Windows.Automation.ScrollPattern> interfejsu użytkownika do korzystania z metod wzorca kontroli w kontenerze, aby wyświetlić element podrzędny.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a>Wymagana liczba członków dla IScrollItemProvider  
 Następująca metoda jest wymagana do implementowania interfejsu IScrollProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|- Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych właściwości lub zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Jeśli nie można przewinąć elementu do widoku:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
