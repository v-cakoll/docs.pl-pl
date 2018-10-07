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
ms.openlocfilehash: ab7e2546ce7267e77e5ea7000e94059e8c162b5d
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840290"
---
# <a name="ui-automation-events-overview"></a>Przegląd zdarzeń automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] powiadomienie o zdarzeniu jest kluczowym elementem obsługę technologii ułatwień dostępu, takich jak czytniki zawartości ekranu i powiększające. Te śledzenie zdarzeń klientów automatyzacji interfejsu użytkownika, które są wywoływane przez dostawców automatyzacji interfejsu użytkownika, gdy coś się dzieje w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i skorzystaj z informacji w celu powiadomienia użytkowników końcowych.  
  
 Zwiększona wydajność, umożliwiając aplikacjom wywoływanie zdarzeń selektywnie, w zależności od tego, czy wszyscy klienci mają subskrypcję tych zdarzeń lub wcale, jeśli klienci nie nasłuchują na wszelkie zdarzenia dostawcy.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Typy zdarzeń  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia można podzielić na następujące kategorie.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Zmiana właściwości|Wywoływane, gdy właściwość [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element lub kontrolka zmiany wzorca. Na przykład, jeśli klient potrzebuje do monitorowania aplikacji, kontrolka pola wyboru, umożliwia rejestrację dla zdarzenia zmiany właściwości nasłuchiwała <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> właściwości. Gdy formant pola wyboru jest zaznaczony lub niezaznaczony, dostawca wywołuje zdarzenie, a klient może działać w razie potrzeby.|  
|Akcja elementu|Wywoływane, gdy zmiana [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] wyniki od użytkownika końcowego lub programowy działania, na przykład, gdy kliknięto przycisk lub wywoływane za pośrednictwem <xref:System.Windows.Automation.InvokePattern>.|  
|Zmiana struktury|Wywołane, gdy struktura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa zmiany. Struktura zmienia się, gdy jest to nowy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy stają się widoczne, ukryte lub usunięto na pulpicie.|  
|Globalne zmiany pulpitu|Wywoływane, gdy globalne zainteresowania klienta są wykonywane działania, np. gdy fokus zostanie przeniesiony z jednego elementu do innego lub po zamknięciu okna.|  
  
 Niektóre zdarzenia nie musi oznaczać, że stan interfejsu użytkownika nie została zmieniona. Na przykład, jeśli użytkownik karty na pole wprowadzania tekstu, a następnie kliknie przycisk, aby zaktualizować pole `TextChangedEvent` jest wywoływane, nawet wtedy, gdy użytkownik faktycznie nie zmienił tekst. Podczas przetwarzania zdarzeń, może być konieczne do aplikacji klienckiej sprawdzić, czy wszystkie rzeczywiste zmiany przed podjęciem działań.  
  
 Następujące zdarzenia może być uruchamiany nawet wtedy, gdy stan interfejsu użytkownika nie został zmieniony.  
  
-   `AutomationPropertyChangedEvent` (w zależności od właściwości, które uległy zmianie)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identyfikatory zdarzeń automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zdarzenia są identyfikowane za pomocą <xref:System.Windows.Automation.AutomationEvent> obiektów. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Właściwość zawiera wartość, która jednoznacznie identyfikuje typ zdarzenia.  
  
 Możliwe wartości parametru <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> są podane w poniższej tabeli, oraz typ używany dla argumentów zdarzeń. Należy pamiętać, że identyfikatory używane przez klientów i dostawców są identyczne nazwy pól z różnych klas.  
  
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
 Następujące klasy hermetyzować argumenty zdarzeń.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Zawiera informacje o asynchroniczne ładowanie zawartości, łącznie z wartością procentową ładowanie ukończone.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Zawiera informacje o prostego zdarzenia, które wymaga żadnych dodatkowych danych.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Zawiera informacje o zmianie fokusu wprowadzania z jednego elementu na inny. Zdarzenia tego typu są inicjowane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systemu, a nie przez dostawców.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Zawiera informacje o zmianie wartości właściwości wzorca element lub kontrolka.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Zawiera informacje o zmianie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Zawiera informacje o zamknięcia okna.|  
  
 Zawierają wszystkie klasy argumentu zdarzenia <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> elementu członkowskiego. Ten identyfikator jest hermetyzowany w <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Obiekty używane do identyfikowania zdarzenia są uzyskiwane przez dostawców z pól w <xref:System.Windows.Automation.AutomationElementIdentifiers> i kontrolować wzorzec identyfikatora klasy takie jak <xref:System.Windows.Automation.DockPatternIdentifiers>. Równoważne pola są uzyskiwane przez aplikacje klienckie z pól w <xref:System.Windows.Automation.AutomationElement> i kontrolować klasy wzorca, takich jak <xref:System.Windows.Automation.DockPattern>.  
  
 Aby uzyskać listę identyfikatorów zdarzeń, zobacz [zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości zdarzeń automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
