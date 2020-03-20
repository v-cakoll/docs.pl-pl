---
title: Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180030"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IWindowProvider>i konwencje <xref:System.Windows.Automation.WindowPattern> dotyczące implementacji, w tym informacje o właściwościach, metodach i zdarzeniach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.WindowPattern> formantu służy do obsługi formantów, które zapewniają podstawowe funkcje oparte na oknach w tradycyjnym graficznym interfejsie użytkownika (GUI). Przykłady formantów, które muszą implementować ten wzorzec sterowania obejmują okna aplikacji najwyższego poziomu, okna podrzędne interfejsu wielu dokumentów (MDI), kontrolki okienka podziału o zmiennym rozmiarze, okna dialogowe modalne i okna pomocy odnośnika.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca kontroli okna, należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- Aby obsługiwać możliwość modyfikowania zarówno rozmiaru okna, jak i <xref:System.Windows.Automation.Provider.ITransformProvider> położenia ekranu za pomocą automatyzacji interfejsu użytkownika, formant musi implementować oprócz <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Formanty zawierające paski tytułu i elementy paska tytułu, które umożliwiają przenoszenie, rozmiar, maksymalizację, <xref:System.Windows.Automation.Provider.IWindowProvider>minimalizację lub zamykanie formantu, są zazwyczaj wymagane do zaimplementowania .  
  
- Formanty, takie jak wyskakujące okienka etykietek narzędzi i <xref:System.Windows.Automation.Provider.IWindowProvider>listy rozwijane pola kombi lub menu, zazwyczaj nie implementują .  
  
- Okna pomocy odnośnika różnią się od podstawowych wyskakujących okienek przez udostępnienie przycisku Zamknij w kształcie okna.  
  
- Tryb pełnoekranowy nie jest obsługiwany przez IWindowProvider, ponieważ jest specyficzny dla aplikacji i nie jest typowym zachowaniem okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>Wymaganych członków dla iwindowProvider  
 Następujące właściwości, metody i zdarzenia są wymagane dla interfejsu IWindowProvider.  
  
|Wymagany element członkowski|Typ elementu członkowskiego|Uwagi|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Wydarzenie|Brak|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Wydarzenie|Brak|  
|<xref:System.Windows.Automation.WindowInteractionState>|Wydarzenie|Nie gwarantuje się, że<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - Gdy formant nie obsługuje żądanego zachowania.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - Gdy parametr nie jest prawidłową liczbą.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
