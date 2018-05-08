---
title: Implementacja wzorca formantu okna automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73a484ea6165b4e38901630730c7ba985a5608ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IWindowProvider>, wraz z informacjami o <xref:System.Windows.Automation.WindowPattern> właściwości, metod i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.WindowPattern> — Wzorzec formantu jest używana do obsługi formantów, które zapewniają podstawowe funkcje oparte na okna w tradycyjny [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Formanty, które muszą implementować ten wzorzec kontroli przykładów okien najwyższego poziomu aplikacji, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] okno podrzędne, podziału o zmiennym rozmiarze okienka kontrolki, modalne okna dialogowe i dymki Pomoc systemu windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca kontrolki okna, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Aby obsługiwać możliwość modyfikowania zarówno rozmiaru okna i ekranu pozycji przy użyciu automatyzacji interfejsu użytkownika, musi implementować formantu <xref:System.Windows.Automation.Provider.ITransformProvider> oprócz <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Formanty, które zawierają paski tytułu i elementy paska tytułu, które umożliwiają formantu do przeniesienia, zmiany rozmiaru, zmaksymalizowane, zminimalizowane lub zamknięty są zwykle wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Formanty, takie jak wyskakujących okienek etykietki narzędzia i kombi pola lub menu rozwijane zwykle nie implementują <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Windows pomocy w dymku różnią się od podstawowego tooltip wyskakujące okienka poprzez dostarczanie okna przypominającej przycisk Zamknij.  
  
-   Tryb pełnoekranowy nie jest obsługiwana przez IWindowProvider, ponieważ jest on właściwych dla funkcji do aplikacji i nie jest zachowanie typowego okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Wymagane elementy IWindowProvider  
 Poniższe właściwości, metod i zdarzeń są wymagane dla interfejsu IWindowProvider.  
  
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
|<xref:System.Windows.Automation.WindowInteractionState>|Zdarzenie|Nie gwarantuje to <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> — Gdy formantu nie obsługuje żądanego zachowania.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Gdy parametr nie jest prawidłową liczbą.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
