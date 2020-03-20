---
title: Uzyskiwanie elementów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: eab4e59ee219808a4c0ae9ca5331a14928b66b5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180000"
---
# <a name="obtaining-ui-automation-elements"></a>Uzyskiwanie elementów automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie opisano różne <xref:System.Windows.Automation.AutomationElement> sposoby uzyskiwania obiektów dla [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów.  
  
> [!CAUTION]
> Jeśli aplikacja kliencka może próbować znaleźć elementy w swoim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsie użytkownika, należy wykonać wszystkie wywołania w osobnym wątku. Aby uzyskać więcej informacji, zobacz [Problemy z wątkami automatyzacji interfejsu użytkownika](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Element główny  
 Wszystkie wyszukiwania <xref:System.Windows.Automation.AutomationElement> obiektów muszą mieć miejsce początkowe. Może to być dowolny element, w tym pulpit, okno aplikacji lub formant.  
  
 Element główny dla pulpitu, z którego pochodzą wszystkie elementy, <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> uzyskuje się z właściwości statycznej.  
  
> [!CAUTION]
> Ogólnie rzecz biorąc, należy starać się <xref:System.Windows.Automation.AutomationElement.RootElement%2A>uzyskać tylko bezpośrednie dzieci . Wyszukiwanie elementów podrzędnych może iterować przez setki lub nawet tysiące elementów, co może spowodować przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub z kontenera na niższym poziomie.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Warunki  
 W przypadku większości technik, których [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można użyć do <xref:System.Windows.Automation.Condition>pobierania elementów, należy określić , który jest zestawem kryteriów określających, jakie elementy mają zostać pobrane.  
  
 Najprostszym warunkiem <xref:System.Windows.Automation.Condition.TrueCondition>jest , wstępnie zdefiniowany obiekt określający, że wszystkie elementy w zakresie wyszukiwania mają być zwracane. <xref:System.Windows.Automation.Condition.FalseCondition>, odwrotnie <xref:System.Windows.Automation.Condition.TrueCondition>, jest mniej przydatne, ponieważ zapobiegałoby to znalezieniu jakichkolwiek elementów.  
  
 Trzy inne wstępnie zdefiniowane warunki mogą być stosowane samodzielnie <xref:System.Windows.Automation.Automation.ContentViewCondition> <xref:System.Windows.Automation.Automation.ControlViewCondition>lub <xref:System.Windows.Automation.Automation.RawViewCondition>w połączeniu z innymi warunkami: , , i . <xref:System.Windows.Automation.Automation.RawViewCondition>, używane przez siebie, <xref:System.Windows.Automation.Condition.TrueCondition>jest równoważne , ponieważ <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> nie filtruje elementów według ich lub właściwości.  
  
 Inne warunki są tworzone z <xref:System.Windows.Automation.PropertyCondition> jednego lub więcej obiektów, z których każdy określa wartość właściwości. Na przykład <xref:System.Windows.Automation.PropertyCondition> może określić, że element jest włączony lub że obsługuje określony wzorzec kontroli.  
  
 Warunki można łączyć za pomocą logiki <xref:System.Windows.Automation.AndCondition>logicznej, konstruując obiekty typów , <xref:System.Windows.Automation.OrCondition>i <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Zakres wyszukiwania  
 Wyszukiwania wykonywane <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> przy <xref:System.Windows.Automation.AutomationElement.FindAll%2A> użyciu lub muszą mieć zakres, jak również miejsce rozpoczęcia.  
  
 Zakres definiuje przestrzeń wokół miejsca początkowego, który ma być przeszukiwany. Może to obejmować sam element, jego rodzeństwo, jego element nadrzędny, jego przodków, jego bezpośrednie elementy podrzędne i jego elementy podrzędne.  
  
 Zakres wyszukiwania jest definiowany przez bitową kombinację <xref:System.Windows.Automation.TreeScope> wartości z wyliczenia.  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Znajdowanie znanego elementu  
 Aby znaleźć znany element, identyfikowany przez jego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>lub inną właściwość lub kombinację <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> właściwości, najłatwiej jest użyć tej metody. Jeśli poszukiwany element jest oknem aplikacji, punktem początkowym wyszukiwania może być plik <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Ten sposób [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] znajdowania elementów jest najbardziej przydatne w scenariuszach automatycznych testów.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Znajdowanie elementów w poddrzewie  
 Aby znaleźć wszystkie elementy spełniające określone kryteria, które <xref:System.Windows.Automation.AutomationElement.FindAll%2A>są związane ze znanym elementem, można użyć programu . Na przykład można użyć tej metody, aby pobrać elementy listy lub elementy menu z listy lub menu lub zidentyfikować wszystkie formanty w oknie dialogowym.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Chodzenie poddrzewem  
 Jeśli nie masz wcześniejszej wiedzy na temat aplikacji, które klient może być używany z, <xref:System.Windows.Automation.TreeWalker> można utworzyć poddrzewo wszystkich elementów zainteresowania przy użyciu klasy. Aplikacja może to zrobić w odpowiedzi na zdarzenie zmienionego fokusem; oznacza to, że gdy aplikacja lub formant odbiera fokus wejściowy, klient automatyzacji interfejsu użytkownika sprawdza elementy podrzędne i być może wszystkie elementy podrzędne elementu skupionego.  
  
 Innym sposobem, <xref:System.Windows.Automation.TreeWalker> w którym można użyć jest zidentyfikowanie przodków elementu. Na przykład przechodząc w górę drzewa można zidentyfikować okno nadrzędne formantu.  
  
 Można użyć <xref:System.Windows.Automation.TreeWalker> albo przez utworzenie obiektu klasy (definiowanie elementów zainteresowania <xref:System.Windows.Automation.Condition>przez przekazanie ), lub za pomocą jednego z następujących wstępnie <xref:System.Windows.Automation.TreeWalker>zdefiniowanych obiektów, które są zdefiniowane jako pola .  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Znajduje tylko <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> elementy, `true`których właściwość jest .|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Znajduje tylko <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> elementy, `true`których właściwość jest .|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Znajduje wszystkie elementy.|  
  
 Po uzyskaniu <xref:System.Windows.Automation.TreeWalker>, korzystanie z niego jest proste. Wystarczy wywołać `Get` metody, aby poruszać się między elementami poddrzewa.  
  
 Metoda <xref:System.Windows.Automation.TreeWalker.Normalize%2A> może służyć do nawigowania do elementu w poddrzewie z innego elementu, który nie jest częścią widoku. Załóżmy na przykład, że widok poddrzewa został utworzony przy użyciu programu <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Aplikacja następnie odbiera powiadomienie, że pasek przewijania otrzymał fokus wejściowy. Ponieważ pasek przewijania nie jest elementem zawartości, nie jest obecny w widoku poddrzewa. Można jednak przekazać <xref:System.Windows.Automation.AutomationElement> reprezentujący pasek przewijania do <xref:System.Windows.Automation.TreeWalker.Normalize%2A> najbliższego elementa nadrzędnego znajdującego się w widoku zawartości i pobrać go z najbliższego elementa nadrzędnego.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Inne sposoby pobierania elementu  
 Oprócz wyszukiwania i nawigacji, można pobrać <xref:System.Windows.Automation.AutomationElement> w następujący sposób.  
  
### <a name="from-an-event"></a>Z wydarzenia  
 Gdy aplikacja odbiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie, obiekt źródłowy przekazany do <xref:System.Windows.Automation.AutomationElement>programu obsługi zdarzeń jest . Na przykład jeśli subskrybujesz zdarzenia zmienione fokusem, <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> źródło przekazane do Twojego jest elementem, który otrzymał fokus.  
  
 Aby uzyskać więcej informacji, zobacz [Subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z punktu  
 Jeśli masz współrzędne ekranu (na przykład położenie kursora), można pobrać za <xref:System.Windows.Automation.AutomationElement> pomocą metody statycznej. <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
### <a name="from-a-window-handle"></a>Z uchwytu okna  
 Aby pobrać <xref:System.Windows.Automation.AutomationElement> z HWND, należy użyć <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metody statycznej.  
  
### <a name="from-the-focused-control"></a>Z skoncentrowany control  
 Można <xref:System.Windows.Automation.AutomationElement> pobrać, który reprezentuje formant koncentruje się <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> z właściwości statycznej.  
  
## <a name="see-also"></a>Zobacz też

- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
