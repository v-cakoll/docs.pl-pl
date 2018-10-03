---
title: Implementacja wzorca formantu przewijania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 60b2b8b8e07cfec9000ddd974891070b625fde01
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046530"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IScrollProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.ScrollPattern> — Wzorzec kontrolki jest używana do obsługi formant, który działa jako kontener przewijany dla kolekcji obiektów podrzędnych. Kontrolki nie jest wymagana do używania pasków przewijania na potrzeby obsługi funkcji przewijania, mimo że często robi.  
  
 ![Formant przewijania, bez pasków przewijania. ](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Przykład formant przewijania, który nie korzysta z pasków przewijania  
  
 Przykłady formantów, które implementują tę kontrolkę, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki przewijania, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Elementy podrzędne tego formantu musi implementować <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Paski przewijania w kontrolce kontenera nie obsługują <xref:System.Windows.Automation.ScrollPattern> — wzorzec kontrolki. Muszą obsługiwać <xref:System.Windows.Automation.RangeValuePattern> kontrolki wzorca.  
  
-   Podczas przewijania jest mierzona w procentach, wszystkie wartości lub ilości związane z przewiń ukończenia muszą być znormalizowane do zakresu od 0 do 100.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> są niezależne od <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` następnie <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> powinien być ustawiony na 100% i <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> powinna być równa <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Podobnie jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` następnie <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> powinien być ustawiony na 100 procent i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> powinna być równa <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Dzięki temu automatyzacji interfejsu użytkownika klienta do korzystania z tych wartości właściwości w ramach <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> metoda unikając [wyścigu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) jeśli kierunek klienta nie jest zainteresowany przewijanie staje się aktywowany.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> jest specyficzne dla ustawień regionalnych. Ustawienie HorizontalScrollPercent = 100,0 należy ustawić położenie przewijania formantu do równowartości pozycji po prawej stronie dla języków, takich jak angielski, które są odczytywane od lewej do prawej. Alternatywnie dla języków, takich jak arabski, który odczytywany po prawej do lewej, ustawienie HorizontalScrollPercent = 100,0 należy ustawić lokalizację przewiń do pierwszej pozycji.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Wymagane elementy IScrollProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
|Wymagany|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> zgłasza ten wyjątek, jeśli kontrolka obsługuje <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> wartości wyłącznie na poziomą lub pionową przewijania, ale <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> wartość jest przekazywana.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> zgłasza ten wyjątek, gdy wartość, która nie można przekonwertować na wartość o podwójnej precyzji jest przekazywany w.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> zgłasza ten wyjątek, gdy jest przekazywana wartość większą niż 100 lub mniejszą od 0 (z wyjątkiem -1, który jest odpowiednikiem <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Zarówno <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> i <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> generują ten wyjątek, gdy podejmowana jest próba przewijanie w nieobsługiwany kierunek.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
