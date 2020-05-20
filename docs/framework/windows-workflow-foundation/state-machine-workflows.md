---
title: Przepływy pracy automatu stanów
description: Ten artykuł zawiera omówienie tworzenia przepływów pracy automatu Stanów przy użyciu działania StateMachine.
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 2b259f315e0186c13ca44c5eed50d861bce3668a
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421335"
---
# <a name="state-machine-workflows"></a>Przepływy pracy automatu stanów
Komputer stanu jest dobrze znanym modelem do tworzenia programów. <xref:System.Activities.Statements.StateMachine>Działania, <xref:System.Activities.Statements.State> <xref:System.Activities.Statements.Transition> a także inne działania mogą służyć do kompilowania programów przepływu pracy automatu Stanów. Ten temat zawiera omówienie tworzenia przepływów pracy automatu Stanów.  
  
## <a name="state-machine-workflow-overview"></a>Przepływ pracy automatu Stanów — Omówienie  
 Przepływy pracy automatu Stanów udostępniają styl modelowania, za pomocą którego można modelować przepływ pracy w sposób oparty na zdarzeniach. <xref:System.Activities.Statements.StateMachine>Działanie zawiera Stany i przejścia, które składają się na logikę automatu stanów i mogą być używane wszędzie tam, gdzie działanie może być używane. W środowisku uruchomieniowym automatu Stanów istnieje kilka klas:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Aby utworzyć przepływ pracy automatu Stanów, Stany są dodawane do <xref:System.Activities.Statements.StateMachine> działania, a przejścia są używane do sterowania przepływem między Stanami. Poniższy zrzut ekranu, w [samouczku wprowadzenie](getting-started-tutorial.md) , krok po kroku [: tworzenie przepływu pracy automatu Stanów](how-to-create-a-state-machine-workflow.md), pokazuje przepływ pracy automatu Stanów z trzema stanami i trzema przejściami. **Inicjalizacja elementu docelowego** jest stanem początkowym i reprezentuje pierwszy stan w przepływie pracy. Jest to wskazane w wierszu, który zaczyna się od węzła **początkowego** . Końcowy stan w przepływie pracy nosi nazwę **FinalState**i reprezentuje punkt, w którym przepływ pracy został ukończony.  
  
 ![Ilustracja przedstawiająca ukończony przepływ pracy automatu Stanów.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Przepływ pracy automatu Stanów musi mieć jeden i tylko jeden stan początkowy oraz co najmniej jeden stan końcowy. Każdy stan, który nie jest stanem końcowym, musi mieć co najmniej jedno przejście. Poniższe sekcje dotyczą tworzenia i konfigurowania stanów i przejść.  
  
## <a name="creating-and-configuring-states"></a>Tworzenie i Konfigurowanie Stanów  
 <xref:System.Activities.Statements.State>Reprezentuje stan, w którym może znajdować się komputer stanu. Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij projektanta działań **stanu** z sekcji **stan automatu** w **przyborniku** i upuść go na <xref:System.Activities.Statements.StateMachine> działanie na powierzchni Projektant przepływu pracy systemu Windows.  
  
 ![Zrzut ekranu przedstawiający sekcję State Machine w przyborniku.](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Aby skonfigurować stan jako **stan początkowy**, kliknij prawym przyciskiem myszy stan i wybierz pozycję **Ustaw jako stan początkowy**. Ponadto jeśli nie ma bieżącego stanu początkowego, początkowy stan można wyznaczyć, przeciągając wiersz z węzła **Start** w górnej części przepływu pracy do żądanego stanu. Gdy <xref:System.Activities.Statements.StateMachine> działanie zostanie usunięte do projektanta przepływu pracy, jest wstępnie skonfigurowane ze stanem początkowym o nazwie **State1**. Przepływ pracy automatu Stanów musi mieć jeden i tylko jeden stan początkowy.  
  
 Stan, który reprezentuje stan zakończenia na komputerze stanu, jest nazywany stanem końcowym. Stan końcowy to stan, który ma <xref:System.Activities.Statements.State.IsFinal%2A> ustawioną właściwość na `true` , nie ma <xref:System.Activities.Statements.State.Exit%2A> działania ani nie pochodzą z niego przejścia. Aby dodać stan końcowy do przepływu pracy, przeciągnij projektanta działań **FinalState** z sekcji **stan automatu** w **przyborniku** i upuść go na <xref:System.Activities.Statements.StateMachine> działanie na powierzchni Projektant przepływu pracy systemu Windows. Przepływ pracy automatu Stanów musi mieć co najmniej jeden końcowy stan.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurowanie akcji wejścia i wyjścia  
 Stan może mieć <xref:System.Activities.Statements.State.Entry%2A> <xref:System.Activities.Statements.State.Exit%2A> akcję i. (Stan skonfigurowany jako stan końcowy może mieć tylko akcję wejścia). Gdy wystąpienie przepływu pracy przejdzie do stanu, wszystkie działania w ramach akcji wpisu są wykonywane. Gdy akcja wejścia zostanie zakończona, wyzwalacze dla przejść stanu są zaplanowane. Po potwierdzeniu przejścia do innego stanu działania w akcji Zakończ są wykonywane, nawet jeśli stan przechodzi z powrotem do tego samego stanu. Po zakończeniu akcji Zakończ działania wykonywane w akcji przejścia, a następnie nowy stan zostanie przeniesiony do, a jego akcje wejścia są zaplanowane.  
  
> [!NOTE]
> Podczas debugowania przepływu pracy automatu Stanów punkty przerwania mogą być umieszczane na głównym stanie komputera stanu i Stanach w ramach przepływu pracy automatu Stanów. Punkty przerwania nie mogą być umieszczane bezpośrednio w przejściach, ale mogą być umieszczane na wszelkich działaniach zawartych w Stanach i przejściach.  
  
## <a name="creating-and-configuring-transitions"></a>Tworzenie i Konfigurowanie przejść  
 Wszystkie Stany muszą mieć co najmniej jedno przejście, z wyjątkiem stanu końcowego, który może nie mieć żadnych przejść. Przejścia mogą zostać dodane po dodaniu stanu do przepływu pracy automatu stanów lub można je utworzyć, gdy stan zostanie usunięty.  
  
 Aby dodać <xref:System.Activities.Statements.State> i utworzyć przejście w jednym kroku, przeciągnij działanie **stanu** z sekcji **stan automatu** **przybornika** i umieść je w innym stanie w Projektancie przepływu pracy. Gdy przeciągany <xref:System.Activities.Statements.State> jest nad innym <xref:System.Activities.Statements.State> , cztery Trójkąty będą widoczne wokół siebie <xref:System.Activities.Statements.State> . Jeśli <xref:System.Activities.Statements.State> zostanie porzucone na jeden z czterech trójkątów, zostanie dodany do komputera stanu i zostanie utworzone przejście z lokalizacji źródłowej <xref:System.Activities.Statements.State> do porzuconego miejsca docelowego <xref:System.Activities.Statements.State> . Aby uzyskać więcej informacji, zobacz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Aby utworzyć przejście po dodaniu stanu, dostępne są dwie opcje. Pierwsza opcja polega na przeciągnięciu stanu z powierzchni projektanta przepływu pracy i umieszczeniu go na istniejącym stanie i porzucenie go na jednym z punktów upuszczania. Jest to podobne do metody opisanej w poprzedniej sekcji. Możesz również ustawić wskaźnik myszy nad żądanym stanem źródłowym i przeciągnąć linię do żądanego stanu docelowego.  
  
> [!NOTE]
> Pojedynczy stan na komputerze stanu może obejmować maksymalnie 76 przejść utworzonych przy użyciu projektanta przepływu pracy. Limit przejść dla stanu dla przepływów pracy utworzonych poza projektantem jest ograniczony tylko przez zasoby systemowe.  
  
 Przejście może mieć, a <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.Transition.Condition%2A> i <xref:System.Activities.Statements.Transition.Action%2A> . <xref:System.Activities.Statements.Transition.Trigger%2A>Zaplanowano przejście, gdy akcja stanu źródła przejścia <xref:System.Activities.Statements.State.Entry%2A> zostanie zakończona. Zwykle <xref:System.Activities.Statements.Transition.Trigger%2A> jest to działanie, które czeka na wystąpienie pewnego typu zdarzenia, ale może to być dowolne działanie lub nie działa wcale. Po <xref:System.Activities.Statements.Transition.Trigger%2A> zakończeniu działania jest <xref:System.Activities.Statements.Transition.Condition%2A> oceniane, jeśli jest obecny. Jeśli nie ma żadnych <xref:System.Activities.Statements.Transition.Trigger%2A> działań, zostanie ona <xref:System.Activities.Statements.Transition.Condition%2A> natychmiast oceniona. Jeśli warunek ma wartość `false` , przejście zostanie anulowane, a <xref:System.Activities.Statements.Transition.Trigger%2A> działanie wszystkich przejść ze stanu jest ponownie planowane. Jeśli istnieją inne przejścia, które współużytkują ten sam stan źródła co bieżące przejście, te <xref:System.Activities.Statements.Transition.Trigger%2A> akcje są anulowane i ponownie planowane. Jeśli wartość <xref:System.Activities.Statements.Transition.Condition%2A> jest równa `true` lub nie jest spełniony, <xref:System.Activities.Statements.State.Exit%2A> Akcja stanu źródła jest wykonywana, a następnie <xref:System.Activities.Statements.Transition.Action%2A> wykonywane jest przejście. Po <xref:System.Activities.Statements.Transition.Action%2A> zakończeniu sterowanie przechodzi do stanu **docelowego**  
  
 Przejścia, które korzystają ze wspólnego wyzwalacza, są nazywane przejściami wyzwalaczy udostępnionych. Każde przejście w grupie przejść wyzwalacza udostępnionego ma ten sam wyzwalacz, ale unikatowy <xref:System.Activities.Statements.Transition.Condition%2A> i akcja. Aby dodać kolejne akcje do przejścia i utworzyć wspólne przejście, kliknij kółko wskazujące początek żądanego przejścia i przeciągnij je do żądanego stanu. Nowe przejście spowoduje udostępnienie tego samego wyzwalacza co początkowe przejście, ale będzie miało unikatowy warunek i akcję. Współużytkowane przejścia można także utworzyć z poziomu projektanta przejścia, klikając pozycję **Dodaj przechodzenie wyzwalacza udostępnionego** u dołu projektanta przejścia, a następnie wybierając żądany stan docelowy z listy rozwijanej **dostępne Stany do połączenia** .  
  
> [!NOTE]
> Należy zauważyć, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> Przechodzenie jest szacowane do `False` (lub wszystkie warunki przejścia wyzwalacza udostępnionego jest oceniane do `False` ), przejście nie zostanie wykonane, a wszystkie wyzwalacze dla wszystkich przejść ze stanu zostaną ponownie zaplanowane.  
  
 Aby uzyskać więcej informacji o tworzeniu przepływów pracy automatu Stanów, zobacz [jak: tworzenie przepływu pracy automatu](how-to-create-a-state-machine-workflow.md)Stanów, [Projektant działań](/visualstudio/workflow-designer/statemachine-activity-designer), działanie, Projektant działań [stanu](/visualstudio/workflow-designer/state-activity-designer), Projektant działań [FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)oraz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologia automatu Stanów  
 Ta sekcja zawiera definicję słownika automatu Stanów używanego w tym temacie.  
  
 Stan  
 Jednostka podstawowa, która składa maszynę stanu. Komputer stanu może znajdować się w jednym stanie w określonym czasie.  
  
 Akcja Wejścia  
 Działanie wykonywane podczas wprowadzania stanu  
  
 Akcja kończenia  
 Działanie wykonywane podczas kończenia stanu  
  
 Transition  
 Relacja skierowana między dwoma stanami, która reprezentuje pełną odpowiedź komputera stanu do wystąpienia zdarzenia określonego typu.  
  
 Przejście udostępnione  
 Przejście, które udostępnia stan źródłowy i wyzwalacz z co najmniej jednym przejściem, ale ma unikatowy warunek i akcję.  
  
 Wyzwalacz  
 Działanie wyzwalające, które powoduje wystąpienie przejścia.  
  
 Warunek  
 Ograniczenie, które musi zostać oszacowane `true` po wystąpieniu wyzwalacza w celu zakończenia przejścia.  
  
 Akcja przejścia  
 Działanie, które jest wykonywane podczas wykonywania pewnego przejścia.  
  
 Przejście warunkowe  
 Przejście z jawnym warunkiem.  
  
 Samodzielne przejście  
 Przejście, które przesyła ze stanu do samego siebie.  
  
 Stan początkowy  
 Stan, który reprezentuje punkt początkowy automatu Stanów.  
  
 Stan końcowy  
 Stan, który reprezentuje ukończenie automatu Stanów.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie przepływu pracy automatu stanów](how-to-create-a-state-machine-workflow.md)
- [StateMachine, projektant działań](/visualstudio/workflow-designer/statemachine-activity-designer)
- [State, projektant działań](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState, projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Transition, projektant działań](/visualstudio/workflow-designer/transition-activity-designer)
