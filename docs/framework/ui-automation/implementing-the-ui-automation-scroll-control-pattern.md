---
title: Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 0420adaefb91f0c9f0d34d5bdf5863373a0b652b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180150"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IScrollProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.ScrollPattern> formantu służy do obsługi formantu, który działa jako kontener do przewijania dla kolekcji obiektów podrzędnych. Formant nie jest wymagane do korzystania z pasków przewijania do obsługi funkcji przewijania, chociaż często nie.  
  
 ![Sterowanie przewijane bez pasków przewijania.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Przykład kontrolki przewijania, która nie używa pasków przewijania  
  
 Aby zapoznać się z przykładami formantów implementuujnych tego formantu, zobacz [Mapowanie wzorców sterowania dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca kontroli przewijania należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Dzieci tej kontroli muszą <xref:System.Windows.Automation.Provider.IScrollItemProvider>wdrożyć .  
  
- Paski przewijania formantu kontenera <xref:System.Windows.Automation.ScrollPattern> nie obsługują wzorca formantu. Zamiast tego <xref:System.Windows.Automation.RangeValuePattern> muszą obsługiwać wzorzec kontroli.  
  
- Podczas przewijania jest mierzona w procentach, wszystkie wartości lub kwoty związane z podziałką przewijania muszą być znormalizowane do zakresu od 0 do 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> są niezależne <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>od .  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  Jeśli `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> to powinno być ustawione na <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 100% i powinny być ustawione na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobnie, jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> to powinno być ustawione na <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 100 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>procent i powinny być ustawione na . Dzięki temu klient automatyzacji interfejsu użytkownika do <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> korzystania z tych wartości właściwości w ramach metody przy jednoczesnym unikaniu [sytuacji wyścigu,](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) jeśli kierunek klient nie jest zainteresowany przewijania staje się aktywowany.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>jest specyficzne dla ustawień regionalnych. Ustawienie HorizontalScrollPercent = 100.0 musi ustawić przewijanie lokalizacji formantu do odpowiednika jego prawej pozycji dla języków, takich jak angielski, które czytają od lewej do prawej. Alternatywnie dla języków takich jak arabski, które czytają od prawej do lewej, ustawienie HorizontalScrollPercent = 100.0 musi ustawić lokalizację przewijania do lewej pozycji.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>Wymagana liczba członków dla IScrollProvider  
 Następujące właściwości i metody są wymagane <xref:System.Windows.Automation.Provider.IScrollProvider>do wdrożenia .  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>zgłasza ten wyjątek, <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> jeśli formant obsługuje wartości wyłącznie dla <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> przewijania poziomego lub pionowego, ale wartość jest przekazywana.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza ten wyjątek, gdy wartość, która nie może być przekonwertowana na double jest przekazywana.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza ten wyjątek, gdy wartość większa niż 100 lub mniejsza niż 0 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>jest przekazywana (z wyjątkiem -1, która jest równoważna ).|  
|<xref:System.InvalidOperationException>|Oba <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> i zgłosić ten wyjątek, gdy podejmowana jest próba przewijania w kierunku nieobsługiwać.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
