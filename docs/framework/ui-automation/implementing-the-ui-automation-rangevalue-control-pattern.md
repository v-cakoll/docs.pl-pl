---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932123"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IRangeValueProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.RangeValuePattern> kontrolki służy do obsługi kontrolek, które mogą być ustawione na wartość z zakresu. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki umożliwiają rekalibrację obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika. Przykładem jest kontrolka termometru, którą można ustawić, aby wyświetlić temperaturę w stopniach Fahrenheita lub Celsjusza.  
  
- Kontrolki, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć normalne wartości.  
  
 ![Pasek postępu.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Przykład paska postępu, gdzie wartość jest typu Integer, a wartości właściwości minimum i maksimum są znormalizowane odpowiednio do 0 i 100.  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Wymagane elementy członkowskie dla IRangeValueProvider  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Metody|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, która jest większa <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> lub mniejsza niż. <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
