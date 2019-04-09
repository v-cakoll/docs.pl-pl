---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: aeb14bddf98adf53a52c8897994bd0fb6fa498ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175802"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IRangeValueProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.RangeValuePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które mogą być ustawione na wartość w zakresie. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki wartości zakresu, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Formanty umożliwiają przekalibrowanie ich obsługiwanych właściwości, w zależności od preferencji użytkownika lub ustawień regionalnych. Na przykład jest formantem termometru ustawioną wyświetlający temperaturę w stopniach Celsjusza lub w Fahrenheita.  
  
-   Formanty, które mają wartości zakresu niejednoznaczny, takich jak paski postępu lub suwaki, powinien mieć tych wartości znormalizowane.  
  
 ![Pasek postępu. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Przykład pasek postępu, gdy wartość jest typu Integer i właściwości minimalne i maksymalne wartości są znormalizowane zgodnie z 0-100, odpowiednio  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Wymagane elementy IRangeValueProvider  
  
|Wymagany|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Metody|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> jest wywoływana z wartością, która jest większa niż <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniej niż <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
