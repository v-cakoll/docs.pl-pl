---
title: Uzyskiwanie elementów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 89c9397ba579f04d81eee7af6363f8fee3abfe1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191279"
---
# <a name="obtaining-ui-automation-elements"></a>Uzyskiwanie elementów automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie opisano różne sposoby uzyskania <xref:System.Windows.Automation.AutomationElement> obiektów dla [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów.  
  
> [!CAUTION]
>  Jeśli Twoja aplikacja kliencka może próbować znajdowanie elementów w interfejsie użytkownika, musisz wprowadzić wszystkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wywołuje w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [problemów wątkowości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Element główny  
 Wyszukuje wszystkie <xref:System.Windows.Automation.AutomationElement> obiekty muszą mieć miejsce uruchomienie. Może to być dowolny element, w tym pulpit, okno aplikacji lub formantu.  
  
 Element główny dla komputerów, w którym wszystkie elementy są podrzędne, są uzyskiwane z statycznej <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> właściwości.  
  
> [!CAUTION]
>  Ogólnie rzecz biorąc, należy spróbować uzyskać tylko bezpośrednie elementy podrzędne <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukaj elementy podrzędne mogą wykonać iterację setek lub nawet tysięcy elementów, które prawdopodobnie spowodowało przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontenerów na niższym poziomie.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Warunki  
 Dla większości metod można użyć do pobrania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów, należy określić <xref:System.Windows.Automation.Condition>, czyli zestawowi kryteria, które definiują elementy, które mają zostać pobrane.  
  
 Najprostsza warunek jest <xref:System.Windows.Automation.Condition.TrueCondition>, wstępnie zdefiniowanych obiektów, określania, czy mają zostać zwrócone wszystkie elementy w zakresie wyszukiwania. <xref:System.Windows.Automation.Condition.FalseCondition>, przeciwny z <xref:System.Windows.Automation.Condition.TrueCondition>, jest mniej przydatne, ponieważ uniemożliwiłyby wszelkie elementy z znalezionych.  
  
 Trzy wstępnie zdefiniowane warunki można samodzielnie lub w połączeniu z inne warunki: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, i <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, używany przez samego siebie, jest odpowiednikiem <xref:System.Windows.Automation.Condition.TrueCondition>, ponieważ Filtruj elementy według ich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> lub <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> właściwości.  
  
 Inne warunki są tworzone na podstawie co najmniej jeden <xref:System.Windows.Automation.PropertyCondition> obiektów, z których każdy określa wartość właściwości. Na przykład <xref:System.Windows.Automation.PropertyCondition> może określić, czy element jest włączona lub że obsługuje ona wzorca kontrolki.  
  
 Warunki można łączyć, używając operatora logicznego tworząc obiektów typów <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, i <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Zakres wyszukiwania  
 Wyszukiwanie za pomocą <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> lub <xref:System.Windows.Automation.AutomationElement.FindAll%2A> musi mieć zakres, a także od miejsca.  
  
 Zakres definiuje miejsce uruchamiania miejsce do wyszukania. Może to obejmować samego elementu, jego elementów równorzędnych, jego element nadrzędny, jego elementów nadrzędnych, jego bezpośrednie elementy podrzędne i jego elementy podrzędne.  
  
 Zakres wyszukiwania jest definiowany przez bitowa kombinacja wartości z <xref:System.Windows.Automation.TreeScope> wyliczenia.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Znajdowanie znanym elementem  
 Można znaleźć elementu znanych identyfikowane przez jego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, lub niektóre inne właściwości lub kombinacji właściwości, jest najprościej jest użyć <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> metody. Jeśli element poszukiwane okna aplikacji, punkt początkowy wyszukiwania może być <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Ten sposób wyszukiwanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementów jest najbardziej przydatne w scenariuszach testów automatycznych.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Znajdowanie elementów w poddrzewo  
 Aby znaleźć wszystkie elementy spełniających określone kryteria, that are related to znanym elementem, można użyć <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Na przykład można użyć tej metody, z można pobrać listy elementów lub elementów menu z listy lub menu lub do identyfikowania wszystkich kontrolek w oknie dialogowym.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Zalet poddrzewo  
 W przypadku nie uprzednia aplikacji, które klient może być używany z można skonstruować poddrzewo wszystkie interesujące Cię elementy, za pomocą <xref:System.Windows.Automation.TreeWalker> klasy. Aplikacja może to zrobić w odpowiedzi na zdarzenie fokus zmieniony; oznacza to gdy aplikacja lub formant uzyskuje fokus wprowadzania, klientów automatyzacji interfejsu użytkownika sprawdza, czy elementy podrzędne i prawdopodobnie wszystkie elementy podrzędne elementu wąsko zdefiniowany.  
  
 Innym sposobem, w którym <xref:System.Windows.Automation.TreeWalker> może służyć polega na określeniu elementów nadrzędnych elementu. Na przykład przez zalet w górę drzewa można zidentyfikować okno nadrzędne kontrolki.  
  
 Możesz użyć <xref:System.Windows.Automation.TreeWalker> przy tworzeniu obiektu klasy (Definiowanie interesujące Cię elementy, przekazując <xref:System.Windows.Automation.Condition>), lub przy użyciu jednej z następujących wstępnie zdefiniowanych obiektów, które są zdefiniowane jako pola <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Umożliwia znalezienie tylko elementy, których <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> właściwość `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Umożliwia znalezienie tylko elementy, których <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> właściwość `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Znajduje wszystkie elementy.|  
  
 Po uzyskaniu <xref:System.Windows.Automation.TreeWalker>, używany jest proste. Po prostu Wywołaj `Get` metody nawigowanie po elementach poddrzewa.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Metoda może być używana do nawigowania do elementu w zainstalowanym poddrzewie z innego elementu, który nie jest częścią tego widoku. Załóżmy, że widok poddrzewo został utworzony przy użyciu <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Następnie aplikacja otrzymuje powiadomienie, czy pasek przewijania otrzymał fokus wprowadzania. Pasek przewijania nie jest element zawartości, nie jest obecny w danym widoku poddrzewa. Jednakże, możesz przekazać <xref:System.Windows.Automation.AutomationElement> reprezentujący pasek przewijania, aby <xref:System.Windows.Automation.TreeWalker.Normalize%2A> i pobieranie najbliższym elemencie nadrzędnym, który znajduje się w widok zawartości.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Inne sposoby pobierania elementu  
 Oprócz wyszukiwania i nawigacji, możesz pobrać <xref:System.Windows.Automation.AutomationElement> w następujący sposób.  
  
### <a name="from-an-event"></a>Ze zdarzenia  
 Kiedy aplikacja otrzymuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie, jest przekazywany do obsługi zdarzenia obiektu źródłowego <xref:System.Windows.Automation.AutomationElement>. Na przykład w przypadku subskrypcji zmienić fokus zdarzenia, źródło są przekazywane do usługi <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> jest elementem, który otrzymał fokus.  
  
 Aby uzyskać więcej informacji, zobacz [subskrybowanie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z punktu  
 Jeśli masz współrzędne ekranu (na przykład pozycja kursora), możesz pobrać <xref:System.Windows.Automation.AutomationElement> przy użyciu statycznej <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metody.  
  
### <a name="from-a-window-handle"></a>Z uchwyt okna  
 Aby pobrać <xref:System.Windows.Automation.AutomationElement> z właściwością HWND, używa się statycznej <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metody.  
  
### <a name="from-the-focused-control"></a>Z fokusem kontroli  
 Możesz pobrać <xref:System.Windows.Automation.AutomationElement> reprezentujący sterowania ukierunkowane ze statycznej <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
