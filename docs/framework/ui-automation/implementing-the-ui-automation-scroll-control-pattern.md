---
title: "Implementacja wzorca formantu przewijania automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9ad069a4670cc7e4c2281109d8df6afa55ea6dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IScrollProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.ScrollPattern> — Wzorzec formantu jest używana do obsługi formant, który działa jako przewijanego kontener dla kolekcji obiektów podrzędnych. Formant nie jest wymagana na potrzeby pasków przewijania obsługi funkcji przewijania, chociaż często pojawia się.  
  
 ![Przewijanie formantu bez pasków przewijania. ] (../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Przykład przewijania formantu, który nie używa paski przewijania  
  
 Przykłady formantów, które implementują ten formant można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca formantu przewijania, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Elementy podrzędne tego formantu musi implementować <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Paski przewijania formantu kontenera nie obsługują <xref:System.Windows.Automation.ScrollPattern> — wzorzec formantu. Muszą obsługiwać <xref:System.Windows.Automation.RangeValuePattern> kontrolować zamiast tego wzorca.  
  
-   Podczas przewijania jest podawana w procentach, wszystkie wartości lub ilości związane przewijanie klasyfikacji, muszą być znormalizowane do zakresu od 0 do 100.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> są niezależne od <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` następnie <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> powinien być ustawiony na 100% i <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> powinien być ustawiony na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobnie jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` następnie <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> powinien być ustawiony na 100 procent i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> powinien być ustawiony na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Dzięki temu klient automatyzacji interfejsu użytkownika użyć tych wartości właściwości w <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metody unikając [sytuację wyścigu](http://support.microsoft.com/default.aspx?scid=kb;en-us;317723) Jeśli kierunku klienta nie jest zainteresowana przewijanie staje się aktywowany.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>jest specyficzne dla ustawień regionalnych. Ustawienie HorizontalScrollPercent = niż 100,0 musi przewijania jako jego lokalizację Ustaw formantu odpowiednikiem położenia po prawej stronie dla języków, takich jak angielski, które są odczytywane lewej do prawej. Alternatywnie dla języków, takich jak arabski, który prawo do odczytu do lewej, ustawienie HorizontalScrollPercent = niż 100,0 musi przewijania jako jego lokalizację Ustaw położenie po lewej stronie.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Wymagane elementy IScrollProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>zgłasza wyjątek, jeśli formant obsługuje <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> wartości wyłącznie pozioma lub pionowa przewijania, ale <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> w została przekazana wartość.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza tego wyjątku, gdy przekazana wartość, której nie można przekonwertować na wartość typu double.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza wyjątek podczas przekazana wartość większa niż 100 lub mniejszą od 0 (z wyjątkiem -1, który jest odpowiednikiem <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Zarówno <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> i <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> throw tego wyjątku, gdy podejmowana jest próba przewinięcia w kierunku nieobsługiwany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
