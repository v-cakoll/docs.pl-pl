---
title: Uzyskiwanie elementów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3e700e7e726b5cb71d3b7d863bdb31951aacd885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="obtaining-ui-automation-elements"></a>Uzyskiwanie elementów automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie opisano różne sposoby uzyskania <xref:System.Windows.Automation.AutomationElement> obiektów na [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów.  
  
> [!CAUTION]
>  Jeśli aplikacja kliencka może podejmować wielokrotne próby Znajdź elementy w interfejsie użytkownika, należy wykonać wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [problemów wątkowości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Element główny  
 Wyszukuje wszystkie <xref:System.Windows.Automation.AutomationElement> obiekty muszą mieć miejsce uruchomienie. Może to być dowolny element, łącznie z pulpitu, okno aplikacji lub formantu.  
  
 Element główny dla komputera stacjonarnego, w którym wszystkie elementy są podrzędne, są uzyskiwane ze statycznego <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> właściwości.  
  
> [!CAUTION]
>  Ogólnie rzecz biorąc, należy uzyskać tylko bezpośrednimi elementami podrzędnymi <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukiwanie elementów podrzędnych może wykonać iterację setki lub nawet tysiące elementów, co prawdopodobnie przepełnienia stosu. Jeśli próbujesz uzyskać określonego elementu na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontener na niższym poziomie.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Warunki  
 Dla większości techniki służy do pobierania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, należy określić <xref:System.Windows.Automation.Condition>, czyli zestawowi kryteria określające, jakie elementy do pobrania.  
  
 Najprostsza warunek jest <xref:System.Windows.Automation.Condition.TrueCondition>, obiekt wstępnie zdefiniowanego określania, czy mają zostać zwrócone wszystkie elementy w zakresie wyszukiwania. <xref:System.Windows.Automation.Condition.FalseCondition>, odwrotnej z <xref:System.Windows.Automation.Condition.TrueCondition>, jest mniej przydatne, ponieważ uniemożliwiłaby elementów z znaleziono.  
  
 Trzy wstępnie zdefiniowane warunki można samodzielnie lub w połączeniu z innymi warunkami: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, i <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, używany przez samego siebie, jest odpowiednikiem <xref:System.Windows.Automation.Condition.TrueCondition>, ponieważ Filtruj elementy według ich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> lub <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> właściwości.  
  
 Inne warunki są tworzone na podstawie co najmniej jeden <xref:System.Windows.Automation.PropertyCondition> obiektów, z których każdy określa wartość właściwości. Na przykład <xref:System.Windows.Automation.PropertyCondition> może określać, czy element jest włączona lub obsługuje wzorca formantu.  
  
 Warunki można łączyć, używając logiczne, tworząc obiekty typów <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, i <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Zakres wyszukiwania  
 Wyszukiwanie wykonywane przy użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> musi mieć zakres, a także uruchamianie miejsce.  
  
 Zakres definiuje obszar wokół uruchamianie — miejsce do wyszukania. Może to obejmować samego elementu, jego elementów równorzędnych, jego element nadrzędny, jego obiektów nadrzędnych, jego bezpośrednie elementy podrzędne i jego obiektów podrzędnych.  
  
 Zakres wyszukiwania jest definiowana za pomocą bitowe połączenie wartości z <xref:System.Windows.Automation.TreeScope> wyliczenia.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Znajdowanie znanego elementu  
 Można znaleźć elementu znane identyfikowane przez jego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, lub pewne inne właściwości lub kombinacji właściwości, jest najprostsza w użyciu <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> metody. Jeśli element poszukiwane okna aplikacji, punkt początkowy wyszukiwania może być <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Ten sposób znajdowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów jest najbardziej przydatna w automatycznych scenariuszy testowych.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Znajdowanie elementów w poddrzewo  
 Aby znaleźć wszystkie elementy spełniających określone kryteria, związanych z elementem znane, można użyć <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Na przykład można użyć tej metody do pobierania listy elementów lub elementów menu z listy lub menu lub do identyfikowania wszystkich kontrolek w oknie dialogowym.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Przejście poddrzewo  
 Jeśli masz znajomość nie aplikacji, które klient może być używana z poddrzewa wszystkich elementów odsetek można skonstruować za pomocą <xref:System.Windows.Automation.TreeWalker> klasy. Aplikacja może to zrobić w odpowiedzi na zdarzenie zmienić fokus; oznacza to gdy aplikacja lub formant zyska fokus wprowadzania, automatyzacji interfejsu użytkownika klienta sprawdza, czy elementy podrzędne i możliwe, że wszystkie elementy podrzędne elementu ukierunkowanych.  
  
 Innym sposobem, w którym <xref:System.Windows.Automation.TreeWalker> może być używany jest zidentyfikowanie elementów nadrzędnych elementu. Na przykład przez krótki w górę drzewa można zidentyfikować okno nadrzędne kontrolki.  
  
 Można użyć <xref:System.Windows.Automation.TreeWalker> poprzez utworzenie obiektu klasy (definiujący elementy odsetek przez przekazanie <xref:System.Windows.Automation.Condition>), lub za pomocą jednej z następujących wstępnie zdefiniowanych obiektów, które są zdefiniowane jako pola <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Wyszukuje tylko elementy, których <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> jest właściwość `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Wyszukuje tylko elementy, których <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> jest właściwość `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Znajduje wszystkie elementy.|  
  
 Po uzyskaniu <xref:System.Windows.Automation.TreeWalker>, używany jest prosta. Po prostu Wywołaj `Get` metody nawigowanie po elementach poddrzewa.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Metoda może być używana do nawigowania do elementu w poddrzewie z innego elementu, który nie jest częścią widoku. Załóżmy na przykład, widok poddrzewo zostały utworzone przy użyciu <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Następnie aplikacja otrzymuje powiadomienie, że pasek przewijania odebrał fokus wprowadzania. Pasek przewijania nie jest element zawartości, nie jest obecny w widoku poddrzewa. Jednak można przekazać <xref:System.Windows.Automation.AutomationElement> reprezentujący pasek przewijania, aby <xref:System.Windows.Automation.TreeWalker.Normalize%2A> i pobrać najbliższym elemencie nadrzędnym, który znajduje się w widoku zawartości.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Inne sposoby pobierania elementu  
 Oprócz wyszukiwania i nawigacji można pobrać <xref:System.Windows.Automation.AutomationElement> w następujący sposób.  
  
### <a name="from-an-event"></a>Od zdarzenia  
 Gdy aplikacja odbiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie, obiekt źródła przekazany do obsługi zdarzenia jest <xref:System.Windows.Automation.AutomationElement>. Na przykład, jeśli subskrybuje zdarzenia zmiany fokusu źródła są przekazywane do Twojej <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> jest element, który otrzymał fokus.  
  
 Aby uzyskać więcej informacji, zobacz [subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z punktu  
 Jeśli masz współrzędne ekranu (na przykład pozycji kursora), możesz pobrać <xref:System.Windows.Automation.AutomationElement> przy użyciu statycznych <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metody.  
  
### <a name="from-a-window-handle"></a>Z uchwytu okna  
 Aby pobrać <xref:System.Windows.Automation.AutomationElement> z właściwością HWND Użyj statycznych <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metody.  
  
### <a name="from-the-focused-control"></a>Z fokusem formantu  
 Możesz pobrać <xref:System.Windows.Automation.AutomationElement> reprezentujący ukierunkowanych formantu z statycznych <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
