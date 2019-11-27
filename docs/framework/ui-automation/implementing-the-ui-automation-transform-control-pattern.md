---
title: Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: c0a46580ad2673b56fefe7228f2549a2e19d2c14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447059"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITransformProvider>, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 <xref:System.Windows.Automation.TransformPattern> wzorzec kontroli służy do obsługi kontrolek, które można przenosić, zmieniać rozmiar lub obracać w obrębie przestrzeni dwuwymiarowej. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli transformacji należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Obsługa tego wzorca kontroli nie jest ograniczona do obiektów na pulpicie. Ten wzorzec kontrolki musi być również obsługiwany przez elementy podrzędne obiektu kontenera, jeśli elementy podrzędne można przenosić, zmieniać rozmiar lub swobodnie obracać w granicach kontenera.  
  
- Nie można przenieść, zmienić rozmiaru ani obrócić obiektu, tak aby jego lokalizacja ekranu była całkowicie poza współrzędnymi kontenera i w związku z tym nie jest dostępna dla klawiatury lub myszy (na przykład gdy okno najwyższego poziomu jest przenoszone poza ekranem lub obiekt podrzędny jest przenoszony poza granice okienka ekranu kontenera. W takich przypadkach obiekt jest umieszczany w pobliżu żądanych współrzędnych ekranu, a współrzędne górne lub lewe są zastępowane w granicach kontenera.  
  
- W przypadku systemów z obsługą kilku monitorów, jeśli obiekt jest przenoszony, zmieniany jest rozmiar lub obracany całkowicie poza połączone Współrzędne ekranu pulpitu, obiekt zostanie umieszczony na monitorze podstawowym jako blisko żądanych współrzędnych.  
  
- Wszystkie parametry i wartości właściwości są bezwzględne i niezależne od ustawień regionalnych.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Wymagane elementy członkowskie dla ITransformProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.ITransformProvider>są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> — Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> — Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> — Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> ma wartość false.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
