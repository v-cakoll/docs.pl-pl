---
title: Przegląd zdarzeń automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
ms.openlocfilehash: 495e7d29c814164f4235d18569477b856cb09045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179894"
---
# <a name="ui-automation-events-overview"></a>Przegląd zdarzeń automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]powiadomienie o zdarzeniach jest kluczową funkcją dla technologii wspomagających, takich jak czytniki ekranu i lupy ekranu. Tych klientów automatyzacji interfejsu użytkownika śledzić zdarzenia, które są [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wywoływane przez dostawców automatyzacji interfejsu użytkownika, gdy coś się dzieje w informacji i używać informacji do powiadamiania użytkowników końcowych.  
  
 Wydajność jest lepsza, umożliwiając aplikacjom dostawcy selektywne podnoszenie zdarzeń, w zależności od tego, czy klienci są subskrybowani do tych zdarzeń, czy w ogóle, jeśli żaden klient nie nasłuchuje żadnych zdarzeń.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Rodzaje zdarzeń  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zdarzenia dzielą się na następujące kategorie.  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|Zmiana właściwości|Wywoływane, gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwość na element lub wzorzec kontroli zmiany. Na przykład jeśli klient musi monitorować formant pola wyboru aplikacji, można zarejestrować, <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> aby nasłuchiwać zdarzenia zmiany właściwości we właściwości. Gdy formant pola wyboru jest zaznaczone lub niezaznaczone, dostawca wywołuje zdarzenie i klient może działać w razie potrzeby.|  
|Akcja elementu|Wywoływane, gdy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zmiana wyników z użytkownika końcowego lub działania programowego; na przykład, gdy przycisk jest klikany lub wywoływany za pośrednictwem <xref:System.Windows.Automation.InvokePattern>.|  
|Zmiana struktury|Wywoływana, gdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zmienia się struktura drzewa. Struktura zmienia się, gdy nowe [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy stają się widoczne, ukryte lub usunięte na pulpicie.|  
|Globalna zmiana pulpitu|Wywoływane, gdy wystąpią akcje o globalnym znaczeniu dla klienta, na przykład gdy fokus przesuwa się z jednego elementu do drugiego lub gdy okno zostanie zamknięte.|  
  
 Niektóre zdarzenia nie muszą oznaczać, że stan interfejsu użytkownika uległ zmianie. Na przykład jeśli użytkownik karty do pola wpisu tekstu, a następnie kliknie przycisk, aby zaktualizować pole, a `TextChangedEvent` jest wywoływana, nawet jeśli użytkownik nie faktycznie zmienić tekst. Podczas przetwarzania zdarzenia może być konieczne dla aplikacji klienckiej, aby sprawdzić, czy coś rzeczywiście się zmieniło przed podjęciem działania.  
  
 Następujące zdarzenia mogą być wywoływane nawet wtedy, gdy stan interfejsu użytkownika nie uległ zmianie.  
  
- `AutomationPropertyChangedEvent`(w zależności od właściwości, która uległa zmianie)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>Identyfikatory zdarzeń automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]zdarzenia są identyfikowane przez <xref:System.Windows.Automation.AutomationEvent> obiekty. Właściwość <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> zawiera wartość, która jednoznacznie identyfikuje rodzaj zdarzenia.  
  
 Możliwe wartości <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> dla są podane w poniższej tabeli, wraz z typem używanym dla argumentów zdarzeń. Należy zauważyć, że identyfikatory używane przez klientów i dostawców są o identycznej nazwie pól z różnych klas.  
  
|Identyfikator klienta|Identyfikator dostawcy|Typ argumentów zdarzeń|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>
## <a name="ui-automation-event-arguments"></a>Argumenty zdarzeń automatyzacji interfejsu użytkownika  
 Następujące klasy hermetyzują argumenty zdarzenia.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Zawiera informacje o asynchroniiowym ładowaniu zawartości, w tym procent ukończonego ładowania.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Zawiera informacje o prostym zdarzeniu, które nie wymaga dodatkowych danych.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Zawiera informacje o zmianie fokusu wejściowego z jednego elementu do drugiego. Zdarzenia tego typu są [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywoływane przez system, a nie przez dostawców.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Zawiera informacje o zmianie wartości właściwości elementu lub wzorca formantu.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Zawiera informacje o zmianie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w drzewie.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Zawiera informacje o zamknięciu okna.|  
  
 Wszystkie klasy argumentu <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> zdarzenia zawierają element członkowski. Ten identyfikator jest hermetyzowany <xref:System.Windows.Automation.AutomationEvent>w pliku .  
  
 Obiekty <xref:System.Windows.Automation.AutomationEvent> używane do identyfikowania zdarzeń są <xref:System.Windows.Automation.AutomationElementIdentifiers> uzyskiwane przez <xref:System.Windows.Automation.DockPatternIdentifiers>dostawców z pól i kontroli klas identyfikatorów wzorców, takich jak . Równoważne pola są uzyskiwane <xref:System.Windows.Automation.AutomationElement> przez aplikacje <xref:System.Windows.Automation.DockPattern>klienckie z pól i klas wzorca kontroli, takich jak .  
  
 Aby uzyskać listę identyfikatorów zdarzeń, zobacz [Zdarzenia automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Zobacz też

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md)
