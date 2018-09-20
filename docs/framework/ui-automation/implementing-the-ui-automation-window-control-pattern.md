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
ms.openlocfilehash: 551e4ac5dc8917931e41d7aaa7dca1f8613852bd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46321343"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IWindowProvider>, łącznie z informacjami o <xref:System.Windows.Automation.WindowPattern> właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.WindowPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które zapewnia podstawowe funkcje oparte na oknie, w ramach tradycyjnego [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Formanty, które należy zaimplementować ten wzorzec kontroli przykłady okien najwyższego poziomu aplikacji, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] okien podrzędnych, Podziel o zmiennym rozmiarze okienka kontrolki, modalne okna dialogowe i dymek Pomoc systemu windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki okna, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Aby zapewnić obsługę możliwość modyfikowania zarówno rozmiaru okna i ekranu pozycję przy użyciu automatyzacji interfejsu użytkownika, musi implementować kontrolki <xref:System.Windows.Automation.Provider.ITransformProvider> oprócz <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Formanty, które zawierają paski tytułu i tytuł paska elementów, które umożliwiają formant, który ma zostać przeniesiona, rozmiar, zmaksymalizowane, zminimalizowane lub zamknięciu są zwykle wymagane do wdrożenia <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Formanty, takie jak wyskakujących okienek etykietki narzędzi i pole kombi pola lub menu rozwijanych, zazwyczaj nie implementują <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Windows pomocy w dymku różnią się od wyskakujące okienka basic etykietka narzędzia poprzez dostarczanie podobne okno przycisk Zamknij.  
  
-   Tryb pełnoekranowy nie jest obsługiwana przez IWindowProvider, ponieważ jest specyficzne dla funkcji do aplikacji i nie jest zachowanie typowe okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Wymagane elementy IWindowProvider  
 Następujące właściwości, metody i zdarzenia są wymagane dla interfejsu IWindowProvider.  
  
|Wymagany|Typ elementu członkowskiego|Uwagi|  
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
|<xref:System.Windows.Automation.WindowInteractionState>|Zdarzenie|Nie musi być <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> — W przypadku formantu nie obsługuje żądane zachowanie.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> — W przypadku parametru nie jest prawidłową liczbą.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
