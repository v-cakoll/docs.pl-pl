---
title: Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447076"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementacja wzorca formantu przełącznika automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IToggleProvider>, w tym informacje o metodach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 <xref:System.Windows.Automation.TogglePattern> wzorzec kontroli służy do obsługi kontrolek, które mogą przechodzić przez zestaw stanów i zachować stan po ustawieniu. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki Przełącz należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Kontrolki, które nie utrzymują stanu po aktywowaniu, takie jak przyciski, przyciski paska narzędzi i hiperlinki, muszą implementować <xref:System.Windows.Automation.Provider.IInvokeProvider> zamiast tego.  
  
- Kontrolka musi przechodzić przez <xref:System.Windows.Automation.ToggleState> w następującej kolejności: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> i, jeśli jest obsługiwana, <xref:System.Windows.Automation.ToggleState.Indeterminate>.  
  
- <xref:System.Windows.Automation.TogglePattern> nie zapewnia metody setstate (newState) z powodu problemów otaczających bezpośrednie ustawienie pola wyboru Tri-State bez przechodzenia przez odpowiedni <xref:System.Windows.Automation.ToggleState> sekwencję.  
  
- Kontrolka RadioButton nie implementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, ponieważ nie jest w stanie cyklicznie przechodzić przez prawidłowe Stany.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>Wymagane elementy członkowskie dla IToggleProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.IToggleProvider>są wymagane następujące właściwości i metody.  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Właściwość|Brak|  
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Pobieranie stanu przełączenia pola wyboru przy użyciu automatyzacji interfejsu użytkownika](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
