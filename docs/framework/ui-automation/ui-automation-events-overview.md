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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2190e404479a940e638d6ee8b9fd7135d8fc0109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399581"
---
# <a name="ui-automation-events-overview"></a>Przegląd zdarzeń automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] powiadomienie o zdarzeniu jest kluczowym elementem technologiami ułatwień dostępu, takich jak czytniki i powiększające. Te zdarzenia śledzenia klientów automatyzacji interfejsu użytkownika, zgłaszanych przez dostawców automatyzacji interfejsu użytkownika, gdy wydarzy się coś w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i użyć tych informacji w celu powiadomienia użytkowników końcowych.  
  
 Zwiększona wydajność zezwalając dostawcy aplikacjom wywoływanie zdarzeń selektywnie, w zależności od tego, czy wszyscy klienci subskrybowanych z tymi zdarzeniami lub wcale, jeśli klienci nie nasłuchują żadnych zdarzeń.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy zdarzeń  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia można podzielić na następujące kategorie.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Zmiana właściwości|Wywoływane, gdy właściwość [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu lub formant zmiany wzorca. Na przykład, jeśli klient wymaga do monitorowania aplikacji kontrolkę pola wyboru, umożliwia rejestrację do nasłuchiwania na zdarzenie zmiany właściwości <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> właściwości. Kontrolka pola wyboru jest zaznaczone lub zaznaczenie opcji, dostawca zgłasza zdarzenie, a klient może działać w razie potrzeby.|  
|Akcja elementu|Wywoływane, gdy zmiana [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wyniki od użytkownika końcowego lub programowe działania, np. po kliknięciu przycisku lub wywoływane za pośrednictwem <xref:System.Windows.Automation.InvokePattern>.|  
|Zmiana struktury|Wywoływane, gdy struktura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa zmiany. Struktura zostanie zmieniona, gdy nowy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy stają się widoczne, ukryty lub usuniętych na pulpicie.|  
|Globalne zmiany pulpitu|Wywoływane, gdy globalne przydatne do klienta są wykonywane działania, np. gdy fokus zostanie przeniesiony z jednego elementu na inny lub po zamknięciu okna.|  
  
 Niektóre zdarzenia nie musi oznaczać, że stan interfejsu użytkownika nie została zmieniona. Na przykład, jeśli użytkownik karty do pole wprowadzania tekstu, a następnie klika przycisk przycisk, aby zaktualizować pola `TextChangedEvent` jest uruchamiany nawet wtedy, gdy użytkownik nie zmienił faktycznie tekst. Podczas przetwarzania zdarzenia, może być konieczne dla aplikacji klienckiej sprawdzić, czy wszystko rzeczywiste zmiany przed wykonaniem akcji.  
  
 Następujące zdarzenia może zostać zgłoszone, nawet wtedy, gdy stan interfejsu użytkownika nie została zmieniona.  
  
-   `AutomationPropertyChangedEvent` (w zależności od właściwości, które uległy zmianie)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identyfikatory zdarzeń automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zdarzenia są identyfikowane za pomocą <xref:System.Windows.Automation.AutomationEvent> obiektów. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Właściwość zawiera wartość, która unikatowo identyfikuje rodzaj zdarzenia.  
  
 Możliwe wartości <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> są podane w poniższej tabeli, wraz z typ użyty dla argumentów zdarzenia. Należy pamiętać, że identyfikatory używane przez klientów i dostawców, są tak samo o nazwie pola z różnych klas.  
  
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
 Następujące klasy hermetyzować argumentów zdarzenia.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Zawiera informacje o asynchroniczne ładowanie zawartości, łącznie z wartością procentową ładowanie ukończone.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Zawiera informacje dotyczące zdarzenia prostego, która wymaga żadnych dodatkowych danych.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Zawiera informacje o zmianie w fokus wprowadzania z jednego elementu na inny. Zdarzenia tego typu są wywoływane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systemu, a nie przez dostawców.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Zawiera informacje dotyczące zmiany wartości właściwości elementu lub formant wzorca.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Zawiera informacje o zmianie w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Zawiera informacje o zamknięcia okna.|  
  
 Zawiera wszystkie klasy argument zdarzenia <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> elementu członkowskiego. Ten identyfikator jest hermetyzowany w <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Obiekty używane do identyfikowania zdarzenia są uzyskiwane przez dostawców w polach <xref:System.Windows.Automation.AutomationElementIdentifiers> i kontrolowania takich jak wzorzec identyfikator klasy <xref:System.Windows.Automation.DockPatternIdentifiers>. Odpowiednik pola są uzyskiwane przez aplikacje klienckie w polach <xref:System.Windows.Automation.AutomationElement> i kontrolować wzorzec klas takich jak <xref:System.Windows.Automation.DockPattern>.  
  
 Aby uzyskać listę identyfikatorów zdarzeń, zobacz [zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
