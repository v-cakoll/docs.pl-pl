---
title: Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: fdd192f7ba6273cb4f7927ccb6b34963b3aaea7d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070561"
---
# <a name="ui-automation-events-for-clients"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie opisano sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zdarzenia są używane przez klientów automatyzacji interfejsu użytkownika.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umożliwia klientom subskrybowanie interesujących Cię wydarzeń. Ta funkcja zwiększa wydajność, eliminując konieczność łączenia się stale sondowanie wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów w systemie, aby sprawdzić, czy wszystkie informacje, struktury lub stan się zmienił.  
  
 Zdolność do nasłuchiwania zdarzeń tylko w obrębie określonego zakresu również poprawia wydajność. Na przykład, klient może nasłuchiwać zdarzeń zmiany skoncentrować się na wszystkich [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy w drzewie lub na tylko jeden element i jego obiektów podrzędnych.  
  
> [!NOTE]
>  Nie należy zakładać, że wszystkie możliwe zdarzenia są wywoływane przez [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostawcy. Na przykład, nie wszystkie zmiany właściwości spowodować zdarzeń zostać wywołane przez dostawców standardowy serwer proxy dla [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki.  
  
 Uzyskać szersze spojrzenie z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Aplikacje klienckie subskrybować zdarzenia określonego typu, rejestrując program obsługi zdarzeń, przy użyciu jednej z następujących metod.  
  
|Metoda|Typ zdarzenia|Typ argumentów zdarzenia|Typ delegata|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Zmień fokus|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Zmiana właściwości|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Zmiana struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Inne zdarzenia, identyfikowany przez <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> lub <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Przed wywołaniem metody, należy utworzyć metody delegata do obsługi zdarzeń. Jeśli wolisz, możesz obsługiwać różne rodzaje zdarzeń w pojedynczej metody i przekazać tę metodę w wielu wywołaniach do jednej z metod w tabeli. Na przykład pojedynczy <xref:System.Windows.Automation.AutomationEventHandler> można skonfigurować do obsługi różnych zdarzeń inaczej zgodnie z opisem w <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Na potrzeby przetwarzania zdarzeń zamknięcia okna, Rzutuj typ argumentu, który jest przekazywany do narzędzia obsługi zdarzeń jako <xref:System.Windows.Automation.WindowClosedEventArgs>. Ponieważ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] element okna nie jest już prawidłowy, nie można użyć `sender` parametru, aby pobrać informacje; użyj <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> zamiast tego.  
  
> [!CAUTION]
>  Jeśli aplikacja może odbierać zdarzenia z jego własnego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nie należy używać aplikacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku do subskrybowania zdarzenia lub do anulowania subskrypcji. To może prowadzić do nieprzewidywalne zachowanie. Aby uzyskać więcej informacji, zobacz [problemów wątkowości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Podczas zamykania lub gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia nie są już zainteresowania w aplikacji, klienci automatyzacji interfejsu użytkownika wywołać jedną z następujących metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Wyrejestrowuje wszystkich zarejestrowanych obsług zdarzeń.|  
  
 Przykładowy kod, zobacz [subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)  
 [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Przykładowe TrackFocus](https://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9)
