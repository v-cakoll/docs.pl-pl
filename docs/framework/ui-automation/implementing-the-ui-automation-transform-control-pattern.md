---
title: Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: 5643bc85972ea33cc31b1a83ecf7615dbb275bc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180049"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ITransformProvider>i konwencje dotyczące implementacji, w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.TransformPattern> formantu służy do obsługi formantów, które mogą być przenoszone, zmieniane lub obracane w przestrzeni dwuwymiarowej. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli przekształcania należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Obsługa tego wzorca formantu nie jest ograniczona do obiektów na pulpicie. Ten wzorzec formantu musi być również obsługiwany przez elementy podrzędne obiektu kontenera, jeśli elementy podrzędne mogą być przenoszone, zmieniane lub obracane swobodnie w granicach kontenera.  
  
- Nie można przenosić, zmieniać jego rozmiarów ani obracać obiektu w taki sposób, aby jego wynikowa lokalizacja ekranu była całkowicie poza współrzędne jego kontenera i w związku z tym była niedostępna dla klawiatury lub myszy (na przykład, gdy okno najwyższego poziomu jest przenoszone poza ekran lub obiekt podrzędny jest przenoszony poza granice rzutni kontenera). W takich przypadkach obiekt jest umieszczany tak blisko żądanych współrzędnych ekranu, jak to możliwe, z górnej lub lewej współrzędne zastąpione być w granicach kontenera.  
  
- W przypadku systemów z wieloma monitorami, jeśli obiekt jest przenoszony, zmieniany lub obracany całkowicie poza połączonymi współrzędnymi ekranu pulpitu, obiekt jest umieszczany na monitorze podstawowym jak najbliżej żądanych współrzędnych.  
  
- Wszystkie parametry i wartości właściwości są bezwzględne i niezależne od ustawień regionalnych.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>Wymagane elementy członkowskie dla ITransformProvider  
 Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.ITransformProvider>do wdrożenia .  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> - Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> jest fałszywy.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> - Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> jest fałszywy.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> - Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> jest fałszywy.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
