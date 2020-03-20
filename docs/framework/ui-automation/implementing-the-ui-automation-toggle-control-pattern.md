---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180063"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IToggleProvider>i konwencje dotyczące wdrażania, w tym informacje o metodach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.TogglePattern> formantu służy do obsługi formantów, które mogą przełączać się między zestawem stanów i utrzymywać stan po ustawieniu. Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca sterowania przełącz, należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Formanty, które nie zachowują stanu po aktywacji, takie jak przyciski, przyciski paska narzędzi i hiperłącza, muszą zaimplementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.  
  
- Formant musi przechodzić przez <xref:System.Windows.Automation.ToggleState> jego <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> w następującej kolejności: , a jeśli jest obsługiwany, <xref:System.Windows.Automation.ToggleState.Indeterminate>.  
  
- <xref:System.Windows.Automation.TogglePattern>nie zapewnia SetState(newState) metoda ze względu na problemy związane z bezpośrednim ustawieniem <xref:System.Windows.Automation.ToggleState> trójstanowego CheckBox bez przechodzenia na rowerze przez jego odpowiedniej sekwencji.  
  
- Sterowanie RadioButton nie <xref:System.Windows.Automation.Provider.IToggleProvider>implementuje , ponieważ nie jest w stanie jeździć na rowerze przez jego prawidłowe stany.  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a>Wymagana liczba członków dla iToggleProvider  
 Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IToggleProvider>do wdrożenia .  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Właściwość|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec formantu nie ma skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Pobierz stan przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
