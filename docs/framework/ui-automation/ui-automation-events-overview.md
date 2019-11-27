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
ms.openlocfilehash: 5f9362814eb671a6d7a111cadb96be6d06f5cb3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441494"
---
# <a name="ui-automation-events-overview"></a>Przegląd zdarzeń automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 powiadomienie o zdarzeniu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jest kluczową funkcją dla technologii pomocniczych, takich jak czytniki ekranu i programy powiększające. Ci klienci automatyzacji interfejsu użytkownika śledzą zdarzenia, które są zgłaszane przez dostawców automatyzacji interfejsu użytkownika, gdy coś się dzieje w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i użyją tych informacji w celu powiadomienia użytkowników końcowych.  
  
 Ulepszona wydajność dzięki umożliwieniu aplikacjom dostawcy w celu selektywnego zgłaszania zdarzeń, w zależności od tego, czy klienci są subskrybowani do tych zdarzeń, czy nie w ogóle, jeśli żaden klient nie nasłuchuje żadnych zdarzeń.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy zdarzeń  
 zdarzenia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] należą do następujących kategorii.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Zmiana właściwości|Uruchamiany, gdy zmieni się właściwość elementu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lub wzorca kontrolki. Na przykład jeśli klient musi monitorować formant pola wyboru aplikacji, może zarejestrować się, aby nasłuchiwać zdarzenia zmiany właściwości właściwości <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A>. Gdy pole wyboru jest zaznaczone lub niezaznaczone, dostawca zgłasza zdarzenie i klient może działać w razie potrzeby.|  
|Akcja elementu|Uruchamiany, gdy zmiana w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wynika z użytkownika końcowego lub działania programowego; na przykład po kliknięciu przycisku lub wywołaniu go za pomocą <xref:System.Windows.Automation.InvokePattern>.|  
|Zmiana struktury|Uruchamiany, gdy zmieni się struktura drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Struktura zmienia się, gdy nowe elementy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] stają się widoczne, ukryte lub usunięte na pulpicie.|  
|Globalna zmiana pulpitu|Uruchamiany, gdy wystąpią akcje elementu globalnego dla klienta, na przykład gdy fokus jest przenoszony z jednego elementu do drugiego lub gdy okno zostanie zamknięte.|  
  
 Niektóre zdarzenia nie muszą oznaczać, że stan interfejsu użytkownika został zmieniony. Na przykład, jeśli na karcie użytkownika do pola wprowadzania tekstu, a następnie klikniesz przycisk w celu zaktualizowania pola, zostanie wywołane `TextChangedEvent`, nawet jeśli użytkownik nie zmieni tekstu. Podczas przetwarzania zdarzenia może być konieczne, aby aplikacja kliencka mogła sprawdzić, czy wszystkie elementy zostały rzeczywiście zmienione przed podjęciem działania.  
  
 Następujące zdarzenia mogą zostać zgłoszone nawet wtedy, gdy stan interfejsu użytkownika nie został zmieniony.  
  
- `AutomationPropertyChangedEvent` (w zależności od właściwości, która została zmieniona)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identyfikatory zdarzeń automatyzacji interfejsu użytkownika  
 zdarzenia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] są identyfikowane przez obiekty <xref:System.Windows.Automation.AutomationEvent>. Właściwość <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> zawiera wartość, która jednoznacznie identyfikuje rodzaj zdarzenia.  
  
 Możliwe wartości <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> są przedstawione w poniższej tabeli wraz z typem używanym dla argumentów zdarzeń. Należy zauważyć, że identyfikatory używane przez klientów i dostawców są identycznie nazwanymi polami z różnych klas.  
  
|Identyfikator klienta|Identyfikator dostawcy|Typ argumentów zdarzenia|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>Argumenty zdarzeń automatyzacji interfejsu użytkownika  
 Poniższe klasy hermetyzują argumenty zdarzenia.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Zawiera informacje o asynchronicznym ładowaniu zawartości, w tym o procencie załadowania.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Zawiera informacje o prostym zdarzeniu, które nie wymaga żadnych dodatkowych danych.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Zawiera informacje o zmianie fokusu wprowadzania z jednego elementu na inny. Zdarzenia tego typu są wywoływane przez system [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], a nie przez dostawców.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Zawiera informacje o zmianie wartości właściwości elementu lub wzorca kontrolki.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Zawiera informacje o zmianie w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Zawiera informacje o zamknięciu okna.|  
  
 Wszystkie klasy argumentów zdarzeń zawierają <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> składową. Ten identyfikator jest hermetyzowany w <xref:System.Windows.Automation.AutomationEvent>.  
  
 Obiekty <xref:System.Windows.Automation.AutomationEvent> używane do identyfikowania zdarzeń są uzyskiwane przez dostawców z pól w <xref:System.Windows.Automation.AutomationElementIdentifiers> i klasy identyfikatorów wzorców kontroli, takich jak <xref:System.Windows.Automation.DockPatternIdentifiers>. Równoważne pola są uzyskiwane przez aplikacje klienckie z pól w <xref:System.Windows.Automation.AutomationElement> i klasy wzorców formantów, takie jak <xref:System.Windows.Automation.DockPattern>.  
  
 Aby uzyskać listę identyfikatorów zdarzeń, zobacz [zdarzenia automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](ui-automation-events-for-clients.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](server-side-ui-automation-provider-implementation.md)
- [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md)
