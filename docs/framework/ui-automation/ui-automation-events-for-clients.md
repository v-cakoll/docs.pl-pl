---
title: Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d471ee08f60d6fdd029b2057d629ad824ae9fdcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-events-for-clients"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie opisano sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zdarzenia są używane przez klientów automatyzacji interfejsu użytkownika.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umożliwia klientom subskrybowanie zdarzeń. Ta funkcja poprawia wydajność dzięki wyeliminowaniu konieczności stale sondowanie wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów w systemie, aby sprawdzić, czy wszystkie informacje, struktury lub stan został zmieniony.  
  
 Zdolność do nasłuchiwania zdarzeń tylko w ramach określonego zakresu również poprawia wydajność. Na przykład klient może nasłuchiwać zdarzeń zmiany fokusu na wszystkich [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy w drzewie lub tylko jednego elementu i jego obiektów podrzędnych.  
  
> [!NOTE]
>  Zakłada się, że wszystkie możliwe zdarzenia są generowane przez [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostawcy. Na przykład, nie wszystkie zmiany właściwości powodują zdarzenia, które mają być zgłaszany przez dostawców standardowe serwera proxy dla [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki.  
  
 Dla oglądać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Aplikacje klienckie subskrybowanie zdarzeń określonego typu rejestrując program obsługi zdarzeń przy użyciu jednej z poniższych metod.  
  
|Metoda|Typ zdarzenia|Typ argumentów zdarzenia|Typ delegata|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Zmiana fokusu|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Zmiana właściwości|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Zmiana struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Wszystkie inne zdarzenia, identyfikowane przez <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> lub <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Przed wywołaniem metody, należy utworzyć metody delegata do obsługi zdarzenia. Jeśli wolisz, możesz obsługi różnych rodzajów zdarzeń w jedną metodę i podaj tę metodę wielu wywołań do jednej z metod w tabeli. Na przykład, jeden <xref:System.Windows.Automation.AutomationEventHandler> można skonfigurować do obsługi różnych zdarzeń inaczej stosownie do <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Do przetwarzania zdarzeń zamknięcia okna, rzutowania typu argumentu przekazanego do obsługi zdarzeń jako <xref:System.Windows.Automation.WindowClosedEventArgs>. Ponieważ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementu okna nie jest już prawidłowe, nie można użyć `sender` parametru można pobrać informacji o; użyj <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> zamiast tego.  
  
> [!CAUTION]
>  Jeśli aplikacja może odbierać zdarzenia z jego własnego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], nie należy używać aplikacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku subskrybowanie zdarzeń lub anulować subskrypcję. W ten sposób może spowodować nieprzewidywalne zachowanie. Aby uzyskać więcej informacji, zobacz [problemów wątkowości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Podczas zamykania lub gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia nie są przydatne do aplikacji, klienci automatyzacji interfejsu użytkownika powinny wywoływać jedną z poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany za pomocą <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany za pomocą <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Wyrejestrowuje program obsługi zdarzeń, który został zarejestrowany za pomocą <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Wyrejestrowuje wszystkich procedur obsługi zdarzeń zarejestrowane.|  
  
 Na przykład kodu, zobacz [subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)  
 [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Przykładowe TrackFocus](http://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9)
