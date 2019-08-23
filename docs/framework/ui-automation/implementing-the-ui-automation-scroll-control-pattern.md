---
title: Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 22bb78040b023a59fd46f0a2be45659d6d7220b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914513"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementacja wzorca kontrolki przewijania automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IScrollProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.ScrollPattern> kontrolki służy do obsługi formantu, który działa jako kontener przewijalny dla kolekcji obiektów podrzędnych. Kontrolka nie jest wymagana do obsługi funkcji przewijania przy użyciu pasków przewijania, chociaż często jest to możliwe.  
  
 ![Kontrolka przewijania bez pasków przewijania.](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Przykład kontrolki przewijania, która nie używa pasków przewijania  
  
 Przykłady formantów implementujących ten formant można znaleźć w temacie [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontrolki przewijania należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Elementy podrzędne tego formantu muszą implementować <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
- Paski przewijania kontrolki kontenera nie obsługują <xref:System.Windows.Automation.ScrollPattern> wzorca kontrolki. Muszą one obsługiwać <xref:System.Windows.Automation.RangeValuePattern> wzorzec kontrolki.  
  
- Gdy przewijanie jest mierzone w wartościach procentowych, wszystkie wartości lub kwoty związane ze stopniami przewijania muszą być znormalizowane do zakresu od 0 do 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>i <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> są niezależne <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>od.  
  
- Jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> następnie powinna być ustawiona na 100% i powinna być ustawiona na <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> Podobnie, jeśli <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>wartość powinna byćrówna100%ipowinnabyćustawionanawartość.<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> `false` Dzięki temu klient automatyzacji interfejsu użytkownika może używać tych wartości właściwości w metodzie, <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> unikając [sytuacji wyścigu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) , jeśli kierunek, w którym klient nie jest interesujący, zostanie aktywowany.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>jest specyficzne dla ustawień regionalnych. Ustawienie HorizontalScrollPercent = 100,0 musi ustawić lokalizację przewijania kontrolki na odpowiednik jej pozycji z prawej strony dla języków takich jak angielski, które odczytają od lewej do prawej. Alternatywnie, w przypadku języków takich jak arabski, które odczytują od prawej do lewej, Ustawienie HorizontalScrollPercent = 100,0 musi ustawiać lokalizację przewijania do pozycji z lewej strony.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Wymagane elementy członkowskie dla IScrollProvider  
 Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Ten wzorzec kontrolki nie ma skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>zgłasza ten wyjątek, Jeśli kontrolka <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> obsługuje wartości wyłącznie dla przewijania poziomego lub pionowego <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> , ale wartość jest przenoszona.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza ten wyjątek, gdy wartość, której nie można przekonwertować na Double, jest przenoszona.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>zgłasza ten wyjątek, gdy wartość większa niż 100 lub mniejsza od 0 jest przenoszona (z wyjątkiem-1, który jest <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>odpowiednikiem).|  
|<xref:System.InvalidOperationException>|Oba <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> te <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> wyjątki i generują ten wyjątek, gdy podejmowana jest próba przewijania w nieobsługiwanym kierunku.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
