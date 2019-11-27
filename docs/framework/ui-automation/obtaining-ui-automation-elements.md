---
title: Uzyskiwanie elementów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 0ae4694e2efb6f6c51b279adf2851baf38785c8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446885"
---
# <a name="obtaining-ui-automation-elements"></a>Uzyskiwanie elementów automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie opisano różne sposoby uzyskiwania <xref:System.Windows.Automation.AutomationElement> obiektów dla [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów.  
  
> [!CAUTION]
> Jeśli aplikacja kliencka może próbować znaleźć elementy w osobnym interfejsie użytkownika, należy wykonać wszystkie wywołania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w osobnym wątku. Aby uzyskać więcej informacji, zobacz temat [problemy z wątkem automatyzacji interfejsu użytkownika](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Element główny  
 Wszystkie wyszukiwania <xref:System.Windows.Automation.AutomationElement> obiektów muszą mieć miejsce początkowe. Może to być dowolny element, łącznie z pulpitem, oknem aplikacji lub kontrolką.  
  
 Element główny pulpitu, z którego są umieszczane wszystkie elementy, jest uzyskiwany ze statycznej właściwości <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType>.  
  
> [!CAUTION]
> Ogólnie rzecz biorąc, należy podjąć próbę uzyskania tylko bezpośrednich elementów podrzędnych <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukiwanie elementów podrzędnych może przechodzić przez setki lub nawet tysiące elementów, co może spowodować przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie od okna aplikacji lub kontenera na niższym poziomie.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Warunki  
 W przypadku większości technik, których można użyć do pobierania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, należy określić <xref:System.Windows.Automation.Condition>, który jest zestawem kryteriów definiujących elementy, które mają zostać pobrane.  
  
 Najprostszym warunkiem jest <xref:System.Windows.Automation.Condition.TrueCondition>, wstępnie zdefiniowany obiekt określający, że wszystkie elementy w zakresie wyszukiwania mają być zwracane. <xref:System.Windows.Automation.Condition.FalseCondition>, odwrotność <xref:System.Windows.Automation.Condition.TrueCondition>, jest mniej przydatna, ponieważ uniemożliwia znalezienie jakichkolwiek elementów.  
  
 Trzy inne wstępnie zdefiniowane warunki mogą być używane autonomicznie lub w połączeniu z innymi warunkami: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>i <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, używane przez siebie, jest odpowiednikiem <xref:System.Windows.Automation.Condition.TrueCondition>, ponieważ nie filtruje elementów według ich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> lub <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> właściwości.  
  
 Inne warunki są kompilowane z co najmniej jednego <xref:System.Windows.Automation.PropertyCondition> obiektów, z których każdy określa wartość właściwości. Na przykład <xref:System.Windows.Automation.PropertyCondition> może określić, że element jest włączony lub że obsługuje określony wzorzec formantu.  
  
 Warunki można łączyć za pomocą logiki logicznej przez Konstruowanie obiektów typów <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>i <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Zakres wyszukiwania  
 Wyszukiwania wykonywane przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> muszą mieć zakres oraz miejsce początkowe.  
  
 Zakres określa miejsce w miejscu, w którym ma być przeszukiwany. Może to dotyczyć samego elementu, jego elementów równorzędnych, jego elementu nadrzędnego, jego obiektów nadrzędnych, bezpośrednich elementów podrzędnych i jego elementów podrzędnych.  
  
 Zakres wyszukiwania jest definiowany przez bitową kombinację wartości z wyliczenia <xref:System.Windows.Automation.TreeScope>.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Znajdowanie znanego elementu  
 Aby znaleźć znany element, identyfikowany przez jego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>lub inną właściwość lub kombinację właściwości, najłatwiej jest użyć metody <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>. Jeśli element szukiwany jest oknem aplikacji, punktem początkowym wyszukiwania może być <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 W ten sposób Znajdowanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów jest najbardziej przydatne w scenariuszach zautomatyzowanych testów.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Znajdowanie elementów w poddrzewie  
 Aby znaleźć wszystkie elementy spełniające określone kryteria dotyczące znanego elementu, można użyć <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Na przykład można użyć tej metody do pobierania elementów listy lub elementów menu z listy lub menu lub do identyfikowania wszystkich kontrolek w oknie dialogowym.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Przechodzenie do poddrzewa  
 Jeśli nie masz wcześniejszej znajomości aplikacji, z którymi może korzystać klient, możesz skonstruować poddrzewo wszystkich interesujących Cię elementów przy użyciu klasy <xref:System.Windows.Automation.TreeWalker>. Aplikacja może to zrobić w odpowiedzi na zdarzenie zmienione fokusem. oznacza to, że gdy aplikacja lub formant otrzymuje fokus wprowadzania, klient automatyzacji interfejsu użytkownika sprawdzi elementy podrzędne i ewentualnie wszystkie elementy podrzędne elementu Focus.  
  
 Innym sposobem, w którym <xref:System.Windows.Automation.TreeWalker> można użyć, jest zidentyfikowanie elementów nadrzędnych elementu. Na przykład poprzez poznanie drzewa można zidentyfikować okno nadrzędne kontrolki.  
  
 <xref:System.Windows.Automation.TreeWalker> można użyć przez utworzenie obiektu klasy (Definiowanie elementów interesujących przez przekazanie <xref:System.Windows.Automation.Condition>) lub użycie jednego z następujących wstępnie zdefiniowanych obiektów, które są zdefiniowane jako pola <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Znajduje tylko elementy, których właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> jest `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Znajduje tylko elementy, których właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> jest `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Znajduje wszystkie elementy.|  
  
 Po uzyskaniu <xref:System.Windows.Automation.TreeWalker>, korzystanie z niego jest proste. Po prostu wywołaj metody `Get`, aby nawigować między elementami poddrzewa.  
  
 Metoda <xref:System.Windows.Automation.TreeWalker.Normalize%2A> może służyć do przechodzenia do elementu w poddrzewie z innego elementu, który nie jest częścią widoku. Załóżmy na przykład, że utworzono widok poddrzewa przy użyciu <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Aplikacja otrzyma powiadomienie o tym, że pasek przewijania otrzymał fokus wprowadzania. Ponieważ pasek przewijania nie jest elementem zawartości, nie jest obecny w widoku poddrzewa. Można jednak przekazać <xref:System.Windows.Automation.AutomationElement> reprezentujące pasek przewijania, aby <xref:System.Windows.Automation.TreeWalker.Normalize%2A> i pobrać najbliższy element nadrzędny, który znajduje się w widoku zawartości.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Inne sposoby pobierania elementu  
 Oprócz wyszukiwania i nawigacji można pobrać <xref:System.Windows.Automation.AutomationElement> w następujący sposób.  
  
### <a name="from-an-event"></a>Ze zdarzenia  
 Gdy aplikacja otrzymuje zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], obiekt źródłowy przesłany do programu obsługi zdarzeń jest <xref:System.Windows.Automation.AutomationElement>. Na przykład Jeśli subskrybujesz zdarzenia ze zmienionym fokusem, źródłem przekazanym do <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> jest element, który otrzymał fokus.  
  
 Aby uzyskać więcej informacji, zobacz [subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z punktu  
 Jeśli masz Współrzędne ekranu (na przykład położenie kursora), możesz pobrać <xref:System.Windows.Automation.AutomationElement> przy użyciu statycznej metody <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>.  
  
### <a name="from-a-window-handle"></a>Z uchwytu okna  
 Aby pobrać <xref:System.Windows.Automation.AutomationElement> z elementu HWND, użyj metody statycznej <xref:System.Windows.Automation.AutomationElement.FromHandle%2A>.  
  
### <a name="from-the-focused-control"></a>Z poziomu formantu ukierunkowanego  
 Można pobrać <xref:System.Windows.Automation.AutomationElement>, która reprezentuje formant ukierunkowany ze statycznej właściwości <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
