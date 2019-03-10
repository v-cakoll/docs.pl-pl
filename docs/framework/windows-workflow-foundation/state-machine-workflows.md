---
title: Przepływy pracy automatu stanów
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 78ce1124137e3b97978f3522a59ad1febd23135d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724963"
---
# <a name="state-machine-workflows"></a>Przepływy pracy automatu stanów
Komputer stanu jest dobrze znanego modelu do tworzenia programów. <xref:System.Activities.Statements.StateMachine> Działania, wraz z <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, i inne działania może służyć do tworzenia programów przepływu pracy maszyny stanu. Ten temat zawiera omówienie tworzenia przepływów pracy automatu stanów.  
  
## <a name="state-machine-workflow-overview"></a>Omówienie przepływu pracy automatu stanów  
 Przepływy pracy automatu stanów dostarczyć styl modelowania, za pomocą którego można modelować przepływu pracy, w sposób oparte na zdarzeniach. A <xref:System.Activities.Statements.StateMachine> działania zawiera Stany i przejścia, które tworzą logikę automatu stanów i może być używane wszędzie działanie może być używane. Istnieje kilka klas w środowisku uruchomieniowym maszyny stanu:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Aby utworzyć przepływ pracy automatu stanów, Stany są dodawane do <xref:System.Activities.Statements.StateMachine> działania i przejścia są używane sterowanie przepływem między stanami. Poniższy zrzut ekranu z [Samouczek wprowadzający](getting-started-tutorial.md) kroku [jak: Utwórz przepływ pracy automatu stanów](how-to-create-a-state-machine-workflow.md), przedstawia przepływ pracy automatu stanów z trzech stanów i trzy przejścia. **Inicjowanie docelowej** jest wstępny stan i reprezentuje pierwszy stan w przepływie pracy. To jest wyznaczony przez wiersz, co prowadzi do niej **Start** węzła. Stan końcowy w przepływie pracy jest o nazwie **FinalState**i reprezentuje punkt ukończeniu przepływu pracy.  
  
 ![Ukończono przepływ pracy automatu stanów](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Przepływ pracy automatu stanów musi mieć jeden i tylko jeden stan początkowy i co najmniej jeden stan końcowy. Każdy stan, który nie jest stan końcowy musi mieć co najmniej jedno przejście. W poniższych częściach omówiono tworzenie i konfigurowanie Stany i przejścia.  
  
## <a name="creating-and-configuring-states"></a>Tworzenie i konfigurowanie stanów  
 A <xref:System.Activities.Statements.State> reprezentuje stan, w którym mogą mieć automatu stanów. Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij **stanu** projektanta działań z **automatu stanów** części **przybornika** i upuść je na <xref:System.Activities.Statements.StateMachine> działanie na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] powierzchni.  
  
 ![WF4 Stan działania maszyny](./media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Aby skonfigurować stan jako **stan początkowy**, kliknij prawym przyciskiem myszy stanu i wybierz **Ustaw jako stan początkowy**. Ponadto w przypadku nie bieżący stan początkowy stan początkowy może być wyznaczony przez przeciąganie linii z **Start** węzła w górnej części przepływu pracy do określonego żądanego stanu. Gdy <xref:System.Activities.Statements.StateMachine> działania jest przenoszony do projektanta przepływu pracy, jest wstępnie skonfigurowany z początkowym stanem o nazwie **stan1**. Przepływ pracy automatu stanów musi mieć jeden i tylko jeden stan początkowy.  
  
 Stan, który reprezentuje kończący stan w automacie stanów nosi nazwę stanu końcowego. Stan końcowy jest w stanie, który ma jej <xref:System.Activities.Statements.State.IsFinal%2A> właściwością `true`, nie ma przypisanego <xref:System.Activities.Statements.State.Exit%2A> działanie i żadnych przejść pochodzących z niego. Aby dodać stan końcowy do przepływu pracy, przeciągnij **FinalState** projektanta działań z **automatu stanów** części **przybornika** i upuść je na <xref:System.Activities.Statements.StateMachine> działanie [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] powierzchni. Przepływ pracy automatu stanów musi mieć co najmniej jeden stan końcowy.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurowanie wejścia i wyjścia działań  
 Stan może mieć <xref:System.Activities.Statements.State.Entry%2A> i <xref:System.Activities.Statements.State.Exit%2A> akcji. (Stan, skonfigurowany jako stan końcowy może mieć akcję zapisu). Gdy wystąpienie przepływu pracy przechodzi do stanu, wykonać żadnych działań w działaniu wpisu. Po zakończeniu działania zapisu Wyzwalacze dla przejścia stanu są zaplanowane. Po przejściu do innego stanu został potwierdzony, są wykonywane działania w akcji wyjściowej, nawet wtedy, gdy zmianie stanu z powrotem do takiego samego stanu. Po ukończeniu działania zakończenia działania w akcji przejścia są wykonywane, następnie nowy stan jest przenoszone do i jej operacje zapisu są zaplanowane.  
  
> [!NOTE]
>  Podczas debugowania przepływ pracy automatu stanów, można umieścić punkty przerwania działania maszyny stanu głównego i w ramach przepływu pracy stanu komputera. Punkty przerwania nie mogą być wprowadzane bezpośrednio od przejść, ale można umieścić w dowolnym działań zawartych w Stany i przejścia.  
  
## <a name="creating-and-configuring-transitions"></a>Tworzenie i konfigurowanie przejścia  
 Wszystkie stany muszą mieć co najmniej jedno przejście, z wyjątkiem stan końcowy, który nie może mieć żadnych przejścia. Przejścia mogą być dodawane po stan zostanie dodany do przepływ pracy automatu stanów, lub można można utworzyć, ponieważ stan jest porzucany.  
  
 Można dodać <xref:System.Activities.Statements.State> i Utwórz przejścia w jednym kroku, a następnie przeciągnij **stanu** działanie z **automatu stanów** części **przybornika** i zatrzymaj wskaźnik myszy nad innego Państwa, w Projektant przepływu pracy. Gdy przeciąganego <xref:System.Activities.Statements.State> znajduje się nad innym <xref:System.Activities.Statements.State>, cztery trójkąty pojawi się wokół drugiego <xref:System.Activities.Statements.State>. Jeśli <xref:System.Activities.Statements.State> został upuszczony na jeden z czterech trójkątów, jest ona dodawana do automatu stanów i utworzeniu przejścia ze źródła <xref:System.Activities.Statements.State> do lokalizacji docelowej porzuconych <xref:System.Activities.Statements.State>. Aby uzyskać więcej informacji, zobacz [Transaction, Projektant działań](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Aby utworzyć przejścia, po dodaniu stan, dostępne są dwie opcje. Pierwsza opcja jest przeciągnij stan na powierzchni projektanta przepływu pracy i umieszczeniu istniejący stan i upuść je na jednym z listy. Jest to bardzo podobne do metody opisanej w poprzedniej sekcji. Można również umieść kursor myszy nad stan żądaną źródła i przeciągnij linię do stanu docelowej lokalizacji.  
  
> [!NOTE]
>  Pojedynczy stan w automacie stanów może mieć maksymalnie 76 przejścia utworzone za pomocą projektanta przepływów pracy. Limit przejścia dla stanu utworzony poza projektanta przepływów pracy jest ograniczony tylko ilością zasobów systemowych.  
  
 Może być przejście <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>i <xref:System.Activities.Statements.Transition.Action%2A>. Przejście <xref:System.Activities.Statements.Transition.Trigger%2A> zaplanowano gdy stan źródłowy przejścia <xref:System.Activities.Statements.State.Entry%2A> działanie zostało zakończone. Zazwyczaj <xref:System.Activities.Statements.Transition.Trigger%2A> to działanie, które oczekuje na pewien rodzaj zdarzeń, ale może to być dowolne działanie, lub żadnych działań w ogóle. Gdy <xref:System.Activities.Statements.Transition.Trigger%2A> działanie zostanie zakończone, <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, jest obliczane. W przypadku nie <xref:System.Activities.Statements.Transition.Trigger%2A> działania, a następnie <xref:System.Activities.Statements.Transition.Condition%2A> natychmiast jest obliczane. Jeśli warunek jest `false`, przejście zostanie anulowana i <xref:System.Activities.Statements.Transition.Trigger%2A> działania dla wszystkich przejść ze stanu są zaplanowane ponownie. Jeśli istnieją inne przejścia, które współużytkują ten sam stan źródłowy jako bieżące przejście tych <xref:System.Activities.Statements.Transition.Trigger%2A> anulowana i ponownie zaplanowane także akcji. Jeśli <xref:System.Activities.Statements.Transition.Condition%2A> daje w wyniku `true`, lub żadnego warunku, a następnie <xref:System.Activities.Statements.State.Exit%2A> akcji stan źródła jest wykonywane, a następnie <xref:System.Activities.Statements.Transition.Action%2A> przejścia jest wykonywany. Gdy <xref:System.Activities.Statements.Transition.Action%2A> zakończeniu kontrola przechodzi do **docelowej** stanu  
  
 Przejścia, które współużytkują typowego wyzwalacza są określane jako wyzwalacz udostępnionych przejść. Każdego przejścia, w grupie przejścia udostępnionego wyzwalacza ma tego samego wyzwalacza, ale unikatową <xref:System.Activities.Statements.Transition.Condition%2A> i akcji. Aby dodać dodatkowe akcje do przejścia i tworzenia udostępnionych przejść, kliknij przycisk koła, który wskazuje początek żądanego przejścia i przeciągnij go do żądanego stanu. Nowe przejście współużytkują tego samego wyzwalacza jako przejściu początkowym, ale będzie mieć unikatowy warunków i akcji. Udostępnione przejścia można również utworzyć z w Projektancie przejścia, klikając **Dodaj udostępnionych przejść wyzwalaczy** w dolnej części projektanta przejścia, a następnie wybierając stanu wybraną docelową z  **Stany połączyć** listy rozwijanej.  
  
> [!NOTE]
>  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `False` (lub zwrócić wszystkie warunki przejścia udostępnionego wyzwalacza `False`), nie nastąpi przejście, i będą wszystkie wyzwalacze dla wszystkich przejść ze stanu zaplanowane ponownie.  
  
 Aby uzyskać więcej informacji na temat tworzenia przepływów pracy automatu stanów, zobacz [jak: Tworzenie przepływu pracy automatu stanów](how-to-create-a-state-machine-workflow.md), [StateMachine, Projektant działań](/visualstudio/workflow-designer/statemachine-activity-designer), [stanu projektanta działań](/visualstudio/workflow-designer/state-activity-designer), [FinalState, Projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer)i [Przejście projektanta działań](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologia automatu stanów  
 Ta sekcja definiuje słownictwa maszyny stanu, które są używane w tym temacie.  
  
 Stan  
 Podstawowa jednostka, który komponuje się automatu stanów. Komputer stanu może być w jednym stanie w danym momencie.  
  
 Akcja zapisu  
 Działania wykonywane podczas wprowadzania stanu  
  
 Akcja wyjściowa  
 Działania wykonywane przy zamykaniu stanu  
  
 przejścia  
 Kierowanych relacji między dwoma stanami, które reprezentuje pełną odpowiedź automatu stanów wystąpienie zdarzenia określonego typu.  
  
 Udostępnione przejścia  
 Przejścia, które udostępnia stanu źródła i wyzwalacza przejścia co najmniej jeden, ale ma unikatowy warunków i akcji.  
  
 Wyzwalacz  
 Wyzwalająca działanie, które powoduje przejście.  
  
 Warunek  
 Ograniczenia, które musi zwrócić `true` po wystąpieniu wyzwalacz, aby przejść do ukończenia.  
  
 Akcji przejścia  
 Działanie, które jest wykonywane podczas wykonywania pewnych przejścia.  
  
 Warunkowe przejścia  
 Przejście z warunkiem jawnego.  
  
 Proces samodzielnej przejścia  
 W okresie przejściowym tranzytu ze stanu do samego siebie.  
  
 Stan początkowy  
 Stan, który reprezentuje punkt początkowy automatu stanów.  
  
 Stan końcowy  
 Stan, który reprezentuje ukończenie automatu stanów.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie przepływu pracy automatu stanów](how-to-create-a-state-machine-workflow.md)
- [StateMachine, projektant działań](/visualstudio/workflow-designer/statemachine-activity-designer)
- [State, projektant działań](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState, projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Transaction, projektant działań](/visualstudio/workflow-designer/transition-activity-designer)
