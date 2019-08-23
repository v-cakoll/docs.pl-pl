---
title: Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: f561f67aed1d024a73d78da26e86110e4cddab2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932004"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.ITransformProvider>dotyczące wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.TransformPattern> kontrolki służy do obsługi kontrolek, które można przenosić, zmieniać rozmiar lub obracać w przestrzeni dwuwymiarowej. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli transformacji należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Obsługa tego wzorca kontroli nie jest ograniczona do obiektów na pulpicie. Ten wzorzec kontrolki musi być również obsługiwany przez elementy podrzędne obiektu kontenera, jeśli elementy podrzędne można przenosić, zmieniać rozmiar lub swobodnie obracać w granicach kontenera.  
  
- Nie można przenieść, zmienić rozmiaru ani obrócić obiektu, tak aby jego lokalizacja ekranu była całkowicie poza współrzędnymi kontenera i w związku z tym nie jest dostępna dla klawiatury lub myszy (na przykład gdy okno najwyższego poziomu jest przenoszone poza ekranem lub obiekt podrzędny jest przenoszony poza granice okienka ekranu kontenera. W takich przypadkach obiekt jest umieszczany w pobliżu żądanych współrzędnych ekranu, a współrzędne górne lub lewe są zastępowane w granicach kontenera.  
  
- W przypadku systemów z obsługą kilku monitorów, jeśli obiekt jest przenoszony, zmieniany jest rozmiar lub obracany całkowicie poza połączone Współrzędne ekranu pulpitu, obiekt zostanie umieszczony na monitorze podstawowym jako blisko żądanych współrzędnych.  
  
- Wszystkie parametry i wartości właściwości są bezwzględne i niezależne od ustawień regionalnych.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Wymagane elementy członkowskie dla ITransformProvider  
 Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
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
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> ma wartość false.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
