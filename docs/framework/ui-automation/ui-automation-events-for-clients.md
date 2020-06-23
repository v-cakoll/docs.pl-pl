---
title: Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
description: Dowiedz się więcej o tym, jak zdarzenia automatyzacji interfejsu użytkownika firmy Microsoft są używane przez klientów automatyzacji interfejsu użytkownika w programie .NET. Automatyzacja interfejsu użytkownika umożliwia klientom subskrybowanie interesujących Cię zdarzeń.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: 84568cf228a30535ec603cdad5bddbfd5697be0a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903743"
---
# <a name="ui-automation-events-for-clients"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie opisano [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , jak zdarzenia są używane przez klientów automatyzacji interfejsu użytkownika.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia klientom subskrybowanie interesujących Cię zdarzeń. Ta funkcja zwiększa wydajność, eliminując konieczność ciągłego sondowania wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów w systemie, aby sprawdzić, czy informacje, struktura lub stan zostały zmienione.  
  
 Ulepszona wydajność dzięki możliwości nasłuchiwania zdarzeń tylko w określonym zakresie. Na przykład klient może nasłuchiwać zdarzeń zmiany fokusu na wszystkich [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementach drzewa lub tylko jeden element i jego elementy podrzędne.  
  
> [!NOTE]
> Nie należy zakładać, że wszystkie możliwe zdarzenia są zgłaszane przez [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostawcę. Na przykład nie wszystkie zmiany właściwości powodują, że zdarzenia mają być zgłaszane przez standardowych dostawców proxy dla Windows Forms i formantów Win32.  
  
 Aby uzyskać szerszy widok [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Aplikacje klienckie subskrybują zdarzenia określonego rodzaju przez zarejestrowanie programu obsługi zdarzeń przy użyciu jednej z poniższych metod.  
  
|Metoda|Typ zdarzenia|Typ argumentów zdarzenia|Typ delegata|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Zmiana fokusu|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Zmiana właściwości|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Zmiana struktury|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Wszystkie inne zdarzenia identyfikowane przez<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> lub <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Przed wywołaniem metody należy utworzyć metodę delegata, aby obsłużyć zdarzenie. Jeśli wolisz, możesz obsługiwać różne rodzaje zdarzeń w pojedynczej metodzie i przekazać tę metodę w wielu wywołaniach do jednej z metod w tabeli. Na przykład pojedyncze <xref:System.Windows.Automation.AutomationEventHandler> można skonfigurować do obsługi różnych zdarzeń w różny sposób w zależności od <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> .  
  
> [!NOTE]
> Aby przetworzyć zdarzenia zamknięte z okna, należy rzutować typ argumentu, który jest przesyłany do procedury obsługi zdarzeń jako <xref:System.Windows.Automation.WindowClosedEventArgs> . Ponieważ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] element okna nie jest już prawidłowy, nie można użyć `sender` parametru do pobierania informacji; Użyj <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> zamiast niego.  
  
> [!CAUTION]
> Jeśli aplikacja może odbierać zdarzenia ze swoich własnych potrzeb [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , nie należy używać [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wątku aplikacji do subskrybowania zdarzeń ani do anulowania subskrypcji. Wykonanie tej czynności może prowadzić do nieprzewidywalnego zachowania. Aby uzyskać więcej informacji, zobacz temat [problemy z wątkem automatyzacji interfejsu użytkownika](ui-automation-threading-issues.md).  
  
 Po zamknięciu lub gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia nie są już potrzebne dla aplikacji, klienci automatyzacji interfejsu użytkownika powinni wywołać jedną z poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Wyrejestrowuje procedurę obsługi zdarzeń, która została zarejestrowana przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Wyrejestrowuje procedurę obsługi zdarzeń, która została zarejestrowana przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Wyrejestrowuje procedurę obsługi zdarzeń, która została zarejestrowana przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Wyrejestrowuje wszystkie zarejestrowane procedury obsługi zdarzeń.|  
  
 Na przykład kod można znaleźć w temacie [Subskrybuj zdarzenia automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Zobacz też

- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md)
- [Przegląd zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md)
- [Przegląd właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md)
- [Przykład TrackFocus](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
