---
title: Przepływy pracy automatu stanów
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: a6dedffda6654cb0acb7ab507129cba9f0bdb7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="state-machine-workflows"></a>Przepływy pracy automatu stanów
Komputer stanu jest dobrze znanego modelu programowania programy. <xref:System.Activities.Statements.StateMachine> Działania, wraz z <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, i innych działań może służyć do tworzenia programów przepływu pracy komputera stanu. Ten temat zawiera omówienie tworzenia przepływów pracy komputera stanu.  
  
## <a name="state-machine-workflow-overview"></a>Omówienie przepływu pracy automatu stanów  
 Przepływy pracy automatu stanów dostarczyć styl modelowania, z którym przepływ pracy może modelu w sposób sterowanego zdarzeniami. A <xref:System.Activities.Statements.StateMachine> działania zawiera Stany i przejścia tworzą logiki automatu stanów, które mogą być używane wszędzie działanie może być używane. Istnieje kilka klas w czasie wykonywania komputera stanu:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Aby utworzyć przepływ pracy automatu stanów, stanów są dodawane do <xref:System.Activities.Statements.StateMachine> są używane działania i przejścia sterowanie przepływem między stanami. Poniższy zrzut ekranu z [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [jak: utworzyć przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), przedstawia przepływ pracy automatu stanów z trzech stanów i trzy przejścia. **Inicjowanie docelowej** jest stan początkowy i przedstawia stan pierwszej w przepływie pracy. Wyznacza wiersza prowadzące z nim **Start** węzła. Stan końcowy w przepływie pracy jest o nazwie **stan końcowy**i reprezentuje punkt ukończeniu przepływu pracy.  
  
 ![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Przepływ pracy automatu stanów musi mieć jeden i tylko jeden stan początkowy i co najmniej jeden stan końcowy. Każdy stan, który nie jest stan końcowy musi mieć co najmniej jedno przejście. W poniższych częściach omówiono tworzenie i konfigurowanie tany i przejścia.  
  
## <a name="creating-and-configuring-states"></a>Tworzenie i konfigurowanie stanów  
 A <xref:System.Activities.Statements.State> reprezentuje stan, w którym mogą mieć automatu stanów. Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij **stanu** Projektant działań z **automatu stanów** sekcji **przybornika** i upuść ją na <xref:System.Activities.Statements.StateMachine> działanie na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] powierzchni.  
  
 ![WF4 Stanu działania maszyny](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Aby skonfigurować stan jako **stan początkowy**, kliknij prawym przyciskiem myszy stanu i wybierz **Ustaw jako stan początkowy**. Ponadto, jeśli stan jest niedostępny bieżącego początkowej, stan początkowy może pełnić przez przeciąganie linii z **Start** węzła w górnej części przepływu pracy do pożądanego stanu. Gdy <xref:System.Activities.Statements.StateMachine> działania upuszczeniu na projektanta przepływów pracy, jest wstępnie skonfigurowana z początkowym stanem o nazwie **stan1**. Przepływ pracy automatu stanów musi mieć jeden i tylko jeden stan początkowy.  
  
 Stan, który reprezentuje stan komputera stanu zakończenia jest nazywany stan końcowy. Stan końcowy jest w stanie, który ma jego <xref:System.Activities.Statements.State.IsFinal%2A> ustawioną właściwość `true`, nie ma <xref:System.Activities.Statements.State.Exit%2A> działania, a nie przejścia pochodzącego od niego. Aby dodać stan końcowy w przepływie pracy, przeciągnij **stan końcowy** Projektant działań z **automatu stanów** sekcji **przybornika** i upuść ją na <xref:System.Activities.Statements.StateMachine> aktywności [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] powierzchni. Przepływ pracy automatu stanów musi mieć co najmniej jeden stan końcowy.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurowanie wejścia i wyjścia działań  
 Stan może mieć <xref:System.Activities.Statements.State.Entry%2A> i <xref:System.Activities.Statements.State.Exit%2A> akcji. (Stan skonfigurowany jako stan końcowy może mieć akcję zapisu). W przypadku wystąpienia przepływu pracy przechodzi do stanu, wykonać żadnych działań w akcji zapisu. Po zakończeniu działania zapisu zaplanowane Wyzwalacze dla przejścia stanu. Po przejściu do innego stanu został potwierdzony, działania tego działania zakończenia są wykonywane, nawet w przypadku przejścia do stanu z powrotem do tego samego stanu. Po zakończeniu działania zakończenia działania w przejścia akcji zostanie wykonane, następnie nowy stan jest optymalizowane pod i zaplanowane działania zapisu.  
  
> [!NOTE]
>  Podczas debugowania przepływ pracy automatu stanów, można umieścić punkty przerwania w działaniu maszyny stanu głównego i stanów w przepływ pracy automatu stanów. Punkty przerwania nie może być umieszczany bezpośrednio na przejścia, ale może być umieszczany na żadnych działań zawartych w tany i przejścia.  
  
## <a name="creating-and-configuring-transitions"></a>Tworzenie i konfigurowanie przejścia  
 Wszystkie stany musi mieć co najmniej jedno przejście z wyjątkiem stanu końcowego, który nie może mieć żadnych przejścia. Przejścia mogą być dodawane po stanie jest dodawany do przepływ pracy automatu stanów lub też można tworzyć jako stan zostało porzucone.  
  
 Aby dodać <xref:System.Activities.Statements.State> i utworzyć przejście w jednym kroku, przeciągnij **stanu** działania z **automatu stanów** sekcji **przybornika** i Aktywuj innego Państwa, w Projektant przepływu pracy. Gdy przeciąganego <xref:System.Activities.Statements.State> znajduje się nad innym <xref:System.Activities.Statements.State>, cztery trójkąty pojawi się wokół innych <xref:System.Activities.Statements.State>. Jeśli <xref:System.Activities.Statements.State> jest przerywane na jedną z czterech trójkąty, jest ona dodawana do automatu stanów i utworzeniu przejście ze źródła <xref:System.Activities.Statements.State> porzuconych docelowego <xref:System.Activities.Statements.State>. Aby uzyskać więcej informacji, zobacz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Aby utworzyć przejście po dodaniu stanie, dostępne są dwie opcje. Pierwsza opcja jest przeciągnij stan z powierzchni projektanta przepływów pracy i Aktywuj istniejący stan i upuść ją na jeden z punktów upuszczania. Jest to bardzo podobna do metody opisanej w poprzedniej sekcji. Można również umieść kursor myszy nad stanu żądanego źródła i przeciągnij linię do stanu docelowej lokalizacji.  
  
> [!NOTE]
>  Pojedynczego stanu komputera stanu może zawierać maksymalnie 76 przejścia utworzone za pomocą projektanta przepływów pracy. Limit przejścia dla stanu utworzony poza projektanta przepływów pracy jest ograniczona tylko zasoby systemowe.  
  
 Może być przejście <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>i <xref:System.Activities.Statements.Transition.Action%2A>. Przejście <xref:System.Activities.Statements.Transition.Trigger%2A> zaplanowano gdy stan źródłowy przejścia <xref:System.Activities.Statements.State.Entry%2A> ukończeniu akcji. Zwykle <xref:System.Activities.Statements.Transition.Trigger%2A> to działanie czeka na pewien typ zdarzenia, ale może być żadnego działania lub żadnej aktywności w ogóle. Raz <xref:System.Activities.Statements.Transition.Trigger%2A> zakończeniu działania <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli istnieje, jest obliczane. W przypadku nie <xref:System.Activities.Statements.Transition.Trigger%2A> działania, a następnie <xref:System.Activities.Statements.Transition.Condition%2A> jest oceniane natychmiast. Jeśli wyrażenie `false`, przejście zostało anulowane i <xref:System.Activities.Statements.Transition.Trigger%2A> są zmienił jego działania dla wszystkich przejścia ze stanu. Jeśli istnieją inne przejścia, które współużytkują tego samego stanu źródła jako bieżące przejście tych <xref:System.Activities.Statements.Transition.Trigger%2A> anulowane i zmienił jego również akcji. Jeśli <xref:System.Activities.Statements.Transition.Condition%2A> daje w wyniku `true`, lub nie żadnego warunku, a następnie <xref:System.Activities.Statements.State.Exit%2A> akcji stan źródła jest wykonywane, a następnie <xref:System.Activities.Statements.Transition.Action%2A> przejścia jest wykonywana. Gdy <xref:System.Activities.Statements.Transition.Action%2A> zakończeniu kontroli przekazuje do **docelowej** stanu  
  
 Przejścia, które współużytkują wspólne wyzwalacza są nazywane przejścia z wyzwalaczem udostępnionym. Każdego przejścia w grupie przejścia z wyzwalaczem udostępnionym ma taki sam wyzwalacz, ale unikatowego <xref:System.Activities.Statements.Transition.Condition%2A> i akcji. Aby dodać dodatkowe akcje do przejścia i utworzyć przejście udostępniony, kliknij koło, wskazującą rozpoczęcia żądanego przejścia i przeciągnij go do pożądanego stanu. Nowe przejście współużytkują tego samego wyzwalacza jak przejście początkowej, ale ma unikatowy stan i działań. Udostępniony przejścia można również tworzyć od w Projektancie przejścia, klikając **Dodaj udostępnione przejście z wyzwalaczem** w dolnej części projektanta przejścia, a następnie wybierając stan docelowy z  **Dostępne stany do połączenia** listy rozwijanej.  
  
> [!NOTE]
>  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `False` (lub wszystkie warunki przejście z wyzwalaczem udostępnionym obliczać `False`), nie nastąpi przejście i będzie wszystkich wyzwalaczy dla wszystkich przejścia ze stanu zaplanowane ponownie.  
  
 Aby uzyskać więcej informacji o tworzeniu przepływów pracy maszyny stanu, zobacz [jak: utworzyć przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [Projektant działań StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), [Projektant działań stanu](/visualstudio/workflow-designer/state-activity-designer), [Projektant działań stan końcowy](/visualstudio/workflow-designer/finalstate-activity-designer), i [przejście Projektant działań](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologia automatu stanów  
 Ta sekcja definiuje słownictwa maszyny stanu, które są używane w tym temacie.  
  
 Stan  
 Podstawowa jednostka Redaguj automatu stanów. W dowolnym momencie określonego w stanie co może być automatu stanów.  
  
 Akcja zapisu  
 Działania wykonywane podczas wprowadzania stanu  
  
 Działanie zakończenia  
 Działania wykonywane podczas zamykania stanu  
  
 przejścia  
 Bezpośrednie relacja między dwoma stanami, które reprezentuje pełną odpowiedzi automatu stanów na wystąpienie zdarzenia określonego typu.  
  
 Udostępniony przejścia  
 Przejścia, który współużytkuje stanu źródła i wyzwalacza z jednego lub większej liczby przejść, ale ma unikatowy stan i działań.  
  
 Wyzwalacz  
 Wyzwalająca działanie, które powoduje przejście może zostać przeprowadzone.  
  
 Warunek  
 Ograniczenia, które muszą być `true` po wystąpieniu wyzwalacza, aby przejść do wykonania.  
  
 Akcja przejścia  
 Działanie, które jest wykonywane podczas wykonywania pewnych przejście.  
  
 Przejście warunkowe  
 Przejście z warunkiem jawnego.  
  
 Przejście zwrotne  
 W okresie przejściowym tranzytu ze stanu do samej siebie.  
  
 Stan początkowy  
 Stan, co stanowi punkt początkowy stan maszyny.  
  
 Stan końcowy  
 Stan, który reprezentuje ukończenie automatu stanów.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie przepływu pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 [StateMachine, projektant działań](/visualstudio/workflow-designer/statemachine-activity-designer)  
 [State, projektant działań](/visualstudio/workflow-designer/state-activity-designer)  
 [FinalState, projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer)  
 [Transaction, projektant działań](/visualstudio/workflow-designer/transition-activity-designer)
