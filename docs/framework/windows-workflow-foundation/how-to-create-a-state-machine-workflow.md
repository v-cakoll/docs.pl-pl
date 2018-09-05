---
title: 'Porady: Tworzenie przepływu pracy automatu stanów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8098ab4b056ad6375c248e803134c35d67e3f27b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519824"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Porady: Tworzenie przepływu pracy automatu stanów
Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych. Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.StateMachine> działanie i działań niestandardowych z poprzedniego [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu. Przepływ pracy modeli gra odgadnięcia liczb.  
  
> [!NOTE]
>  Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach. Aby ukończyć ten temat, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2.  W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3.  Typ `StateMachineNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
4.  Przeciągnij **StateMachine** działanie z **automatu stanów** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1.  Kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.  
  
2.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3.  Kliknij przycisk **utworzenia argumentu**.  
  
4.  Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
5.  Kliknij przycisk **utworzenia argumentu**.  
  
6.  Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.  
  
8.  Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.StateMachine> działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1.  Kliknij przycisk **stan1** aby go zaznaczyć. W **okno właściwości**, zmień **DisplayName** do `Initialize Target`.  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.  
  
2.  Kliknij dwukrotnie nowo zmienionej nazwie **zainicjować docelowej** stanu w Projektancie przepływu pracy, aby ją rozwinąć.  
  
3.  Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je na **wpis** sekcja stanu. Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
4.  Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.  
  
5.  Przeciągnij **stanu** działanie z **automatu stanów** części **przybornika** w Projektancie przepływu pracy i zatrzymaj wskaźnik myszy nad **zainicjować docelowej** stanu. Należy pamiętać, że cztery trójkąty pojawi się wokół **zainicjować docelowej** stan, gdy nowy stan to nad nim. Upuść nowy stan na trójkąt, który znajduje się bezpośrednio pod **zainicjować docelowej** stanu. To umieszcza nowy stan do przepływu pracy i tworzy przejście z **zainicjować docelowej** stanu do nowego stanu.  
  
6.  Kliknij przycisk **stan1** aby ją wybrać, zmienić **DisplayName** do `Enter Guess`, a następnie kliknij dwukrotnie ikonę stanu w Projektancie przepływu pracy, aby ją rozwinąć.  
  
7.  Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **wpis** sekcja stanu.  
  
8.  Wpisz następujące wyrażenie do **tekstu** okno właściwości z **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuścić **zakończenia** sekcja stanu.  
  
10. Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
11. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.  
  
12. Przeciągnij **FinalState** działanie z **automatu stanów** części **przybornika**, Zatrzymaj wskaźnik myszy nad **wprowadź odgadnięcia** stanu i upuść go na trójkąt, który pojawia się po prawej stronie **wprowadź odgadnięcia** stanu, tak aby tworzone przejścia między **wprowadź odgadnięcia** i **FinalState**.  
  
13. Domyślna nazwa przejścia to **T2**. Kliknij przycisk przejścia w Projektancie przepływu pracy, aby go zaznaczyć, a następnie ustaw jego **DisplayName** do **odgadnięcia poprawne**. Następnie kliknij i zaznacz **FinalState**i przeciągnij go do prawej strony, aby miejsca dla nazwy pełne przejście do wyświetlenia bez nałożenie jedną z dwóch stanów. Spowoduje to ułatwić wykonaj pozostałe kroki w tym samouczku.  
  
14. Kliknij dwukrotnie nowo zmienionej nazwie **odgadnięcia poprawne** przejścia w Projektancie przepływu pracy, aby ją rozwinąć.  
  
15. Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **wyzwalacza** sekcji przejścia.  
  
16. W **okno właściwości** dla **readint —** działania, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości i typ `Guess`do **wynik** pole wartości właściwości  
  
17. Wpisz następujące wyrażenie do **odgadnięcia poprawne** firmy przejścia **warunek** pole wartości właściwości.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.  
  
    > [!NOTE]
    >  Przejście występuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku `True`. Dla tego przejścia Jeśli użytkownika `Guess` odpowiada losowo generowany `Target`, kontrola przechodzi do, a następnie **FinalState** i ukończeniu przepływu pracy.  
  
19. W zależności od tego, czy wynik jest poprawny, przepływu pracy należy przejść do **FinalState** lub z powrotem do **wprowadź odgadnięcia** stanu dla innej próby. Zarówno przejścia udostępnianie tego samego wyzwalacza oczekiwania przez dopasowanie użytkownika do odebrania za pośrednictwem **readint —** działania. Jest to udostępniony przejścia. Do tworzenia udostępnionych przejść, kliknij przycisk koła, który wskazuje początek **odgadnięcia poprawne** przejścia i przeciągnij go do żądanego stanu. W tym przypadku przejście jest samodzielnej przejścia, więc przeciągnij punkt początkowy **odgadnięcia poprawne** przejścia i upuść go z powrotem na dolnej części **wprowadź odgadnięcia** stanu. Po utworzeniu przejścia, wybierz ją w Projektancie przepływów pracy i ustaw jego **DisplayName** właściwości **odgadnięcia niepoprawne**.  
  
    > [!NOTE]
    >  Udostępnione przejścia można również utworzyć z w Projektancie przejścia, klikając **Dodaj udostępnionych przejść wyzwalaczy** w dolnej części projektanta przejścia, a następnie wybierając stanu wybraną docelową z  **Stany połączyć** listy rozwijanej.  
  
    > [!NOTE]
    >  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `false` (lub zwrócić wszystkie warunki przejścia udostępnionego wyzwalacza `false`), nie nastąpi przejście, i będą wszystkie wyzwalacze dla wszystkich przejść ze stanu zaplanowane ponownie. W tym samouczku ta sytuacja nie może się zdarzyć, ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).  
  
20. Kliknij dwukrotnie **odgadnięcia niepoprawne** przejścia w Projektancie przepływu pracy, aby ją rozwinąć. Należy pamiętać, że **wyzwalacza** jest już ustawione w taki sam **readint —** działania, który został użyty przez **odgadnięcia poprawne** przejścia.  
  
21. Wpisz następujące wyrażenie do **warunek** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Przeciągnij **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **akcji** sekcji przejścia.  
  
23. Wpisz następujące wyrażenie do **Jeśli** działania **warunek** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
24. Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je tak, aby jeden **następnie** sekcji **Jeśli** działania i jeden znajduje się w **Else** sekcji.  
  
25. Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.  
  
     Poniższy przykład ilustruje ukończony przepływ pracy.  
  
     ![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Tworzenie przepływu pracy  
  
1.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą przepływu pracy stanu komputera z tego kroku, przejdź do sekcji [do kompilowania i uruchamiania aplikacji](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programowanie w programie Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Projektowanie przepływów pracy](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Instrukcje: Tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Instrukcje: Uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
