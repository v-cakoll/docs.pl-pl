---
title: Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180178"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementacja wzorca formantu RangeValue dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IRangeValueProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.RangeValuePattern> formantu służy do obsługi formantów, które można ustawić na wartość w zakresie. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli wartości zakresu należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Formanty umożliwiają ponowną kalibrację ich obsługiwanych właściwości na podstawie ustawień regionalnych lub preferencji użytkownika. Przykładem tego jest kontrola termometru, którą można ustawić, aby wyświetlić temperaturę w Fahrenheita lub Celsjusza.  
  
- Formanty, które mają niejednoznaczne wartości zakresu, takie jak paski postępu lub suwaki, powinny mieć te wartości znormalizowane.  
  
 ![Pasek postępu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Przykład paska postępu, na którym wartość jest typu Liczba całkowita, a minimalne i maksymalne wartości właściwości są znormalizowane odpowiednio do 0 i 100  
  
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
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>jest wywoływana z wartością, <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> która jest <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>większa lub mniejsza niż .|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
