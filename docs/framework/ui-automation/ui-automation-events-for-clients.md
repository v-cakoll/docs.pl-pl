---
title: Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: d7105e9211c35e7d6125c3017e8b4b829a25b128
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179904"
---
# <a name="ui-automation-events-for-clients"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] temacie opisano, jak zdarzenia są używane przez klientów automatyzacji interfejsu użytkownika.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia klientom subskrybowanie interesujących wydarzeń. Ta funkcja zwiększa wydajność, eliminując konieczność ciągłego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sondowania wszystkich elementów w systemie, aby sprawdzić, czy zostały zmienione jakiekolwiek informacje, struktura lub stan.  
  
 Wydajność jest również zwiększona przez możliwość nasłuchiwać zdarzeń tylko w określonym zakresie. Na przykład klient może nasłuchiować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń zmiany fokusu na wszystkich elementach w drzewie lub tylko na jeden element i jego elementy podrzędne.  
  
> [!NOTE]
> Nie należy zakładać, że wszystkie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] możliwe zdarzenia są wywoływane przez dostawcę. Na przykład nie wszystkie zmiany właściwości powodują zdarzenia, które mają być wywoływane przez standardowych dostawców serwera proxy dla formantów Windows Forms i Win32.  
  
 Aby uzyskać szerszy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widok zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Subskrybowanie wydarzeń  
 Aplikacje klienckie subskrybują zdarzenia określonego rodzaju, rejestrując program obsługi zdarzeń przy użyciu jednej z następujących metod.  
  
|Metoda|Typ zdarzenia|Typ argumentów zdarzeń|Typ delegowania|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Zmiana ostrości|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Zmiana właściwości|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Zmiana struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Wszystkie inne zdarzenia, zidentyfikowane przez<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> lub <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Przed wywołaniem metody należy utworzyć metodę delegata do obsługi zdarzenia. Jeśli wolisz, można obsługiwać różne rodzaje zdarzeń w jednej metodzie i przekazać tę metodę w wielu wywołań do jednej z metod w tabeli. Na przykład pojedynczy <xref:System.Windows.Automation.AutomationEventHandler> można skonfigurować do obsługi różnych zdarzeń <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>inaczej w zależności od .  
  
> [!NOTE]
> Aby przetworzyć zdarzenia zamknięte przez okno, należy przelać typ argumentu przekazywany do programu obsługi zdarzeń jako <xref:System.Windows.Automation.WindowClosedEventArgs>. Ponieważ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] element okna nie jest już prawidłowy, `sender` nie można użyć parametru do pobierania informacji; zamiast <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> tego użyć.  
  
> [!CAUTION]
> Jeśli aplikacja może odbierać [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]zdarzenia od własnej, nie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] należy używać wątku aplikacji do subskrybowania zdarzeń lub anulowania subskrypcji. Może to prowadzić do nieprzewidywalnego zachowania. Aby uzyskać więcej informacji, zobacz [Problemy z wątkami automatyzacji interfejsu użytkownika](ui-automation-threading-issues.md).  
  
 Po zamknięciu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lub gdy zdarzenia nie są już interesujące dla aplikacji, klienci automatyzacji interfejsu użytkownika należy wywołać jedną z następujących metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Wyrejestrowaj program obsługi <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>zdarzeń, który został zarejestrowany przy użyciu programu .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Wyrejestrowaj program obsługi <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>zdarzeń, który został zarejestrowany przy użyciu programu .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Wyrejestrowaj program obsługi <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>zdarzeń, który został zarejestrowany przy użyciu programu .|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Wyrejestrowaj wszystkie zarejestrowane programy obsługi zdarzeń.|  
  
 Na przykład kod, zobacz [Subskrybuj zdarzenia automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Zobacz też

- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md)
- [Przegląd zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md)
- [Przegląd właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md)
- [TrackFocus Przykład](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
