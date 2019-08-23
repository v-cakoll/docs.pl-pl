---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 2293dc77369ecf019bd1093808135eeefd99c115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932062"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IToggleProvider>dotyczące wdrażania, w tym informacje o metodach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.TogglePattern> kontrolki służy do obsługi kontrolek, które mogą przechodzić przez zestaw stanów i zachować stan po ustawieniu. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki Przełącz należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki, które nie utrzymują stanu po aktywowaniu, takie jak przyciski, przyciski paska narzędzi i hiperlinki, <xref:System.Windows.Automation.Provider.IInvokeProvider> muszą być implementowane w zamian.  
  
- <xref:System.Windows.Automation.ToggleState> Kontrolka musi przechodzić w następujący sposób w następującej kolejności <xref:System.Windows.Automation.ToggleState.On>: <xref:System.Windows.Automation.ToggleState.Off> , i, jeśli jest <xref:System.Windows.Automation.ToggleState.Indeterminate>obsługiwana,.  
  
- <xref:System.Windows.Automation.TogglePattern>nie zapewnia metody setstate (NewState) z powodu problemów otaczających bezpośrednie ustawienie pola wyboru Tri-State bez przechodzenia przez odpowiednią <xref:System.Windows.Automation.ToggleState> sekwencję.  
  
- Kontrolka RadioButton nie jest zaimplementowana <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest w stanie przechodzić przez prawidłowe Stany.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>Wymagane elementy członkowskie dla IToggleProvider  
 Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Właściwość|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
