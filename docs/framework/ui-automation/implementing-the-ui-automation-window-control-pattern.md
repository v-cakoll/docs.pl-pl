---
title: Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: ad2f84fbde512bb99b213bf3b97f2190091d8576
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042990"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IWindowProvider>dotyczące wdrażania, w <xref:System.Windows.Automation.WindowPattern> tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.WindowPattern> kontrolki służy do obsługi kontrolek, które zapewniają podstawowe funkcje oparte na oknach w tradycyjnym graficznym interfejsie użytkownika (GUI). Przykłady kontrolek, które muszą implementować ten wzorzec kontrolki obejmują okna aplikacji najwyższego poziomu, okna podrzędne interfejsu wielu dokumentów (MDI), okna dialogowe podziału o zmiennym rozmiarze, modalnych okien dialogowych i okien pomocy dymków.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli okna należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Aby zapewnić możliwość modyfikowania rozmiaru okna i położenia ekranu przy użyciu automatyzacji interfejsu użytkownika, formant musi być zaimplementowany <xref:System.Windows.Automation.Provider.ITransformProvider> dodatkowo do. <xref:System.Windows.Automation.Provider.IWindowProvider>  
  
- Formanty, które zawierają paski tytułu i elementy paska tytułu, które umożliwiają przenoszenie formantu, jego rozmiar, zmaksymalizowany, zminimalizowany lub zamknięty są zwykle wymagane do wdrożenia <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Kontrolki, takie jak okienka wyskakujące etykietki narzędzi i pola kombi lub menu rozwijane, <xref:System.Windows.Automation.Provider.IWindowProvider>zazwyczaj nie są implementowane.  
  
- Okna pomocy w dymkach są odróżniane od podstawowych wyskakujących etykietek narzędzi przez udostępnienie przycisku Zamknij podobne do okna.  
  
- Tryb pełnoekranowy nie jest obsługiwany przez program IWindowProvider, ponieważ jest on specyficzny dla aplikacji i nie jest typowym zachowaniem okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Wymagane elementy członkowskie dla IWindowProvider  
 Dla interfejsu IWindowProvider są wymagane następujące właściwości, metody i zdarzenia.  
  
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
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Zdarzenie|Brak|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Zdarzenie|Brak|  
|<xref:System.Windows.Automation.WindowInteractionState>|Zdarzenie|Nie ma gwarancji<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy muszą zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> — Gdy kontrolka nie obsługuje żądanego zachowania.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Jeśli parametr nie jest prawidłową liczbą.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
