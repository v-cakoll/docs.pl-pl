---
title: "Porady: Tworzenie przepływu pracy automatu stanów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b094fd88321ffcf8d3bb5cdefe870bd12524b4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a>Porady: Tworzenie przepływu pracy automatu stanów
Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych. W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.StateMachine> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu. Przepływ pracy modele numer guessing gier.  
  
> [!NOTE]
>  Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów. Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2.  W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3.  Typ `StateMachineNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
4.  Przeciągnij **StateMachine** działania z **automatu stanów** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchnię projektu przepływu pracy.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1.  Kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.  
  
2.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3.  Kliknij przycisk **utworzenia argumentu**.  
  
4.  Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5.  Kliknij przycisk **utworzenia argumentu**.  
  
6.  Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję ** Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7.  Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.  
  
8.  Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.StateMachine> działania na powierzchni projektanta przepływu pracy, aby go wybrać.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1.  Kliknij przycisk **stan1** aby go wybrać. W **okna właściwości**, zmień **DisplayName** do `Initialize Target`.  
  
    > [!TIP]
    >  Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.  
  
2.  Kliknij dwukrotnie nowo zmieniono **zainicjować docelowej** stanu w Projektancie przepływów pracy, aby go rozwinąć.  
  
3.  Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść ją na **wpis** sekcji stanu. Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
4.  Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.  
  
5.  Przeciągnij **stanu** działania z **automatu stanów** sekcji **przybornika** do projektanta przepływów pracy i umieść kursor myszy nad **zainicjować docelowej** stanu. Należy pamiętać, że cztery trójkąty pojawi się wokół **zainicjować docelowej** stan, gdy nowy stan to nad nim. Upuść nowy stan na trójkąt, który znajduje się bezpośrednio pod **zainicjować docelowej** stanu. To umieszcza nowy stan na przepływie pracy i tworzy przejście z **zainicjować docelowej** stanu do nowego stanu.  
  
6.  Kliknij przycisk **stan1** wybierz ją, zmień **DisplayName** do `Enter Guess`, a następnie kliknij dwukrotnie ikonę stanu w Projektancie przepływów pracy, aby go rozwinąć.  
  
7.  Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść ją na **wpis** sekcji stanu.  
  
8.  Wpisz następujące wyrażenie w **tekst** właściwość **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuścić **zakończenia** sekcji stanu.  
  
10. Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
11. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.  
  
12. Przeciągnij **stan końcowy** działania z **automatu stanów** sekcji **przybornika**, umieść kursor myszy nad **wprowadź odgadnąć** stanu i upuść na trójkąt, który pojawia się po prawej stronie **wprowadź odgadnąć** stanu, dzięki czemu tworzone przejścia między **wprowadź odgadnąć** i **stan końcowy**.  
  
13. Domyślna nazwa przejścia to **T2**. Kliknij przycisk przechodzenia w Projektancie przepływów pracy, aby go zaznaczyć, a następnie ustaw jego **DisplayName** do **odgadnąć poprawne**. Następnie kliknij i zaznacz **stan końcowy**i przeciągnij go do prawej, dzięki czemu jest miejsce na nazwę pełne przejście do wyświetlania bez nakładanie albo dwa stany. Spowoduje to ułatwić wykonaj pozostałe kroki samouczka.  
  
14. Kliknij dwukrotnie nowo zmieniono **odgadnąć poprawne** przejścia w Projektancie przepływów pracy, aby go rozwinąć.  
  
15. Przeciągnij **ReadInt** działania z **NumberGuessWorkflowActivities** sekcji **przybornika** i upuść je w **wyzwalacza** sekcji przejścia.  
  
16. W **okna właściwości** dla **ReadInt** działania, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości, a typ `Guess`do **wynik** wartości właściwości — okno  
  
17. Wpisz następujące wyrażenie w **odgadnąć poprawne** przejścia w **warunku** pole wartości właściwości.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.  
  
    > [!NOTE]
    >  Przejście występuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku `True`. Dla tego przejścia Jeśli użytkownika `Guess` odpowiada losowo generowany `Target`, następnie kontrola przechodzi do **stan końcowy** i zakończeniu przepływu pracy.  
  
19. W zależności od tego, czy wynik jest poprawny, przepływu pracy należy przejść do **stan końcowy** lub z powrotem do **Wprowadź wynik** stanu do innego elementu try. Zarówno przejścia udostępnianie tego samego wyzwalacza czekać na dopasowanie użytkownika do odebrania przez **ReadInt** działania. Jest to udostępniony przejścia. Aby utworzyć przejście udostępniony, kliknij koło, która wskazuje początek **odgadnąć poprawne** przejścia i przeciągnij go do pożądanego stanu. W takim przypadku przejście jest przejście zwrotne, więc przeciągnij punkt początkowy **odgadnąć poprawne** przejście i upuść go z powrotem na dole **wprowadź odgadnąć** stanu. Po utworzeniu przejścia, wybierz je w Projektancie przepływów pracy i ustawić jej **DisplayName** właściwości **odgadnąć niepoprawne**.  
  
    > [!NOTE]
    >  Udostępniony przejścia można również tworzyć od w Projektancie przejścia, klikając **Dodaj udostępnione przejście z wyzwalaczem** w dolnej części projektanta przejścia, a następnie wybierając stan docelowy z ** Dostępne stany do połączenia** listy rozwijanej.  
  
    > [!NOTE]
    >  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `false` (lub wszystkie warunki przejście z wyzwalaczem udostępnionym obliczać `false`), nie nastąpi przejście i będzie wszystkich wyzwalaczy dla wszystkich przejścia ze stanu zaplanowane ponownie. W tym samouczku tej sytuacji niemożliwe ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).  
  
20. Kliknij dwukrotnie **odgadnąć niepoprawne** przejścia w Projektancie przepływów pracy, aby go rozwinąć. Należy pamiętać, że **wyzwalacza** jest już ustawione w taki sam **ReadInt** działania, który był używany przez **odgadnąć poprawne** przejścia.  
  
21. Wpisz następujące wyrażenie w **warunku** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Przeciągnij **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **akcji** sekcji przejścia.  
  
23. Wpisz następujące wyrażenie w **Jeśli** działania **warunku** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
24. Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, tak aby jedna jest **następnie** sekcji **Jeśli** działania, a druga jest **Else** sekcji.  
  
25. Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.  
  
     Poniższy przykład przedstawia ukończonych przepływów pracy.  
  
     ![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
     Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą przepływ pracy automatu stanów z tego kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) sekcji [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation programowania](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Projektowanie przepływów pracy](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
