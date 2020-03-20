---
title: Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 083a4bb56fe76c1d65015ffabf741d7e1953d2ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180131"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.ISelectionProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.SelectionPattern> formantu służy do obsługi formantów, które działają jako kontenery dla kolekcji wybieranych elementów podrzędnych. Elementy podrzędne tego <xref:System.Windows.Automation.Provider.ISelectionItemProvider>elementu muszą implementować . Aby zapoznać się z przykładami formantów implementuujnych tego wzorca sterowania, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas wdrażania wzorca kontroli zaznaczenia należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Formanty <xref:System.Windows.Automation.Provider.ISelectionProvider> implementacji umożliwiają zaznaczenie pojedynczych lub wielu elementów podrzędnych. Na przykład pole listy, widok listy i widok drzewa obsługują wiele zaznaczeń, podczas gdy pole kombi, suwak i grupa przycisków opcji obsługują pojedyncze zaznaczenie.  
  
- Formanty o minimalnym, maksymalnym i ciągłym zakresie, takie <xref:System.Windows.Automation.Provider.IRangeValueProvider> jak <xref:System.Windows.Automation.Provider.ISelectionProvider>suwak **głośności,** powinny być implementować zamiast .  
  
- Zaimplementuj kontrolki <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>pojedynczego wyboru, które zarządzają formanty podrzędne, takie jak suwak **Rozdzielczość ekranu** w oknie dialogowym **Właściwości wyświetlania** lub kontrolka wyboru **selektora kolorów** z programu Microsoft Word (ilustracja poniżej), powinna zostać zaimplementowana; <xref:System.Windows.Automation.Provider.ISelectionProvider> ich dzieci powinny <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>wdrożyć zarówno i .  
  
 ![Próbnik kolorów z żółtym podświetlenym.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykład mapowania ciągów próbkowania kolorów  
  
- Menu nie obsługuje <xref:System.Windows.Automation.SelectionPattern>. Jeśli pracujesz z elementami menu, które zawierają zarówno grafikę, jak i tekst (na przykład elementy **okienka podglądu** w menu **Widok** w programie Microsoft Outlook) i musisz przekazać stan, należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider>program .  
  
<a name="Required_Members_for_ISelectionProvider"></a>
## <a name="required-members-for-iselectionprovider"></a>Wymagana liczba członków do iselectionProvider  
 Następujące właściwości, metody i zdarzenia są wymagane <xref:System.Windows.Automation.Provider.ISelectionProvider> dla interfejsu.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Powinien obsługiwać właściwość zmieniono zdarzenia przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Powinien obsługiwać właściwość zmieniono zdarzenia przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Wydarzenie|Wywoływane, gdy zaznaczenie w kontenerze uległo znacznej zmianie <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> i wymaga wysłania większej liczby zdarzeń dodawania i usuwania niż stałe zezwolenia.|  
  
 Właściwości <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> i mogą być dynamiczne. Na przykład stan początkowy formantu może nie mieć żadnych elementów zaznaczonych domyślnie, co oznacza, że <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> jest `false`. Jednak po wybraniu elementu formant musi zawsze mieć co najmniej jeden element zaznaczone. Podobnie w rzadkich przypadkach formant może zezwolić na wiele elementów, które mają być wybrane podczas inicjowania, ale następnie zezwalają na tylko pojedyncze wybory.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|  
|<xref:System.InvalidOperationException>|Jeśli formant jest ukryty.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca formantu SelectionItem dla automatyzacji interfejsu użytkownika](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
