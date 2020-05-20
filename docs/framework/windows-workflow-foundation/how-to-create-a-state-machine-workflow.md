---
title: 'Instrukcje: Tworzenie przepływu pracy automatu stanów'
description: W tym artykule opisano tworzenie przepływu pracy korzystającego z obu wbudowanych działań, takich jak działanie StateMachine i działania niestandardowe.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419658"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Instrukcje: Tworzenie przepływu pracy automatu stanów
Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych. W tym temacie przedstawiono procedurę tworzenia przepływu pracy korzystającego z obu wbudowanych działań, takich jak <xref:System.Activities.Statements.StateMachine> działanie, oraz działań niestandardowych z poprzednich instrukcji [: Create a Activity](how-to-create-an-activity.md) . Przepływ pracy modeluje grę z liczbą odgadnąć.  
  
> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw wykonać [instrukcje: tworzenie działania](how-to-create-an-activity.md).  
  
> [!NOTE]
> Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
2. W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**. Wybierz **działanie** z listy **przepływów pracy** .  
  
3. Wpisz tekst `StateMachineNumberGuessWorkflow` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
4. Przeciągnij działanie **StateMachine** z sekcji **stan automatu** **przybornika** i upuść je na etykiecie **działania upuść** na powierzchni projektowej przepływu pracy.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne i argumenty przepływu pracy  
  
1. Kliknij dwukrotnie pozycję **StateMachineNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.  
  
2. Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .  
  
3. Kliknij przycisk **Utwórz argument**.  
  
4. Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5. Kliknij przycisk **Utwórz argument**.  
  
6. Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu **Out** , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.  
  
7. Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .  
  
8. Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .  
  
9. Kliknij pozycję **Utwórz zmienną**.  
  
    > [!TIP]
    > Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij <xref:System.Activities.Statements.StateMachine> działanie na powierzchni projektanta przepływu pracy, aby je wybrać.  
  
10. Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij pozycję **Utwórz zmienną**.  
  
12. Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1. Kliknij pozycję **State1** , aby ją zaznaczyć. W **oknie właściwości**Zmień wartość parametru **DisplayName** na `Initialize Target` .  
  
    > [!TIP]
    > Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .  
  
2. Kliknij dwukrotnie nowo zmieniono nazwę stanu **docelowego inicjalizacji** w Projektancie przepływu pracy, aby go rozwinąć.  
  
3. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w sekcji **wpis** stanu. Wpisz `Target` w polu **do** i poniższe wyrażenie w polu **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .  
  
4. Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.  
  
5. Przeciągnij działanie **stanu** z sekcji **stan komputera** **przybornika** do projektanta przepływów pracy i umieść je na stanie **inicjalizacji docelowej** . Należy zauważyć, że cztery Trójkąty będą widoczne wokół stanu **inicjowania elementu docelowego** , gdy nowy stan jest na nim. Upuść nowy stan w trójkącie, który znajduje się bezpośrednio poniżej stanu **inicjalizacji docelowej** . Spowoduje to umieszczenie nowego stanu w przepływie pracy i utworzenie przejścia z stanu **inicjowania docelowego** do nowego stanu.  
  
6. Kliknij pozycję **State1** , aby ją zaznaczyć, Zmień wartość parametru **DisplayName** na `Enter Guess` , a następnie kliknij dwukrotnie stan w Projektancie przepływu pracy, aby go rozwinąć.  
  
7. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je do sekcji **wejście** stanu.  
  
8. Wpisz następujące wyrażenie w polu właściwości **Text** **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w **przyborniku** i upuść je na sekcję **wyjście** stanu.  
  
10. Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie w języku VB** .  
  
11. Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.  
  
12. Przeciągnij działanie **FinalState** z sekcji **stan automatu** **przybornika**, umieść kursor nad **odpowiednim stanem** , a następnie upuść je na Trójkąt, który pojawia się po prawej stronie stanu " **wprowadź zgadywanie** ", aby można było utworzyć przejście między **klawiszami Enter** i **FinalState**.  
  
13. Domyślną nazwą przejścia jest **T2**. Kliknij przejście w Projektancie przepływu pracy, aby je zaznaczyć, a następnie ustaw jego **Właściwość DisplayName** na wartość **odgadnięcia poprawne**. Następnie kliknij i wybierz **FinalState**i przeciągnij go w prawo, aby zapewnić, że istnieje pomieszczenie dla nazwy pełnego przejścia, które ma być wyświetlane bez nakładania jednego z tych dwóch stanów. Ułatwi to ukończenie pozostałych kroków samouczka.  
  
14. Kliknij dwukrotnie nowo zmieniono nazwę **odgadnięcia odpowiednie** przejście w Projektancie przepływu pracy, aby je rozwinąć.  
  
15. Przeciągnij działanie **ReadInt** z sekcji **NumberGuessWorkflowActivities** w **przyborniku** i upuść je w sekcji **wyzwalacz** przejścia.  
  
16. W **oknie właściwości** działania **ReadInt** , wpisz `"EnterGuess"` w tym cudzysłowy w polu wartość właściwości **zakładkaname** , a następnie wpisz `Guess` w polu wartość właściwości **wynik** .  
  
17. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** **poprawnego** przejścia.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.  
  
    > [!NOTE]
    > Przejście następuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A> , jeśli jest obecny, ma wartość `True` . W przypadku tego przejścia, jeśli użytkownik jest `Guess` zgodny z losowo generowanym `Target` , wówczas kontrola przeszedł do **FinalState** i zakończy przepływ pracy.  
  
19. W zależności od tego, czy wartość odgadnięcia jest poprawna, przepływ pracy powinien przejść do **FinalState** lub z powrotem do stanu **wprowadzenia** dla innej próby. Oba przejścia mają ten sam wyzwalacz, który oczekuje na odebranie użytkownika za pośrednictwem działania **ReadInt** . Jest to nazywane przechodzeniem udostępnionym. Aby utworzyć wspólne przejście, kliknij okrąg, który wskazuje początek **poprawnego** przejścia i przeciągnij go do żądanego stanu. W takim przypadku przejście jest przechodzeniem samodzielnym, dlatego przeciągnij punkt początkowy **przypuszczalnie** i upuść go **ponownie w dolnej części zmiany stanu.** Po utworzeniu przejścia wybierz je w Projektancie przepływów pracy i ustaw właściwość **DisplayName** na **nieprawidłowe**.  
  
    > [!NOTE]
    > Współużytkowane przejścia można także utworzyć z poziomu projektanta przejścia, klikając pozycję **Dodaj przechodzenie wyzwalacza udostępnionego** u dołu projektanta przejścia, a następnie wybierając żądany stan docelowy z listy rozwijanej **dostępne Stany do połączenia** .  
  
    > [!NOTE]
    > Należy zauważyć, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> Przechodzenie jest szacowane do `false` (lub wszystkie warunki przejścia wyzwalacza udostępnionego jest oceniane do `false` ), przejście nie zostanie wykonane, a wszystkie wyzwalacze dla wszystkich przejść ze stanu zostaną ponownie zaplanowane. W tym samouczku ta sytuacja nie może wystąpić ze względu na sposób skonfigurowania warunków (istnieją określone akcje dotyczące tego, czy wartość dopuszczalna jest poprawna czy niepoprawna).  
  
20. Kliknij dwukrotnie **nieprawidłowe** przejście w Projektancie przepływu pracy, aby je rozwinąć. Należy zauważyć, że **wyzwalacz** jest już ustawiony na to samo działanie **ReadInt** , które było używane **przez odpowiednie przechodzenie.**  
  
21. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** .  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Przeciągnij działanie **if** z sekcji **przepływ sterowania** w **przyborniku** i upuść je w sekcji **akcji** przejścia.  
  
23. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **if** .  
  
    ```text
    Guess < Target
    ```  
  
24. Przeciągnij dwie działania **WriteLine** z sekcji **elementy pierwotne** w **przyborniku** i upuść je tak, aby były w sekcji **then** działania **if** , a jeden z nich znajduje się w sekcji **else** .  
  
25. Kliknij działanie **WriteLine** w sekcji Then, aby je zaznaczyć, a **następnie** wpisz następujące wyrażenie w polu wartość właściwości **Text** .  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. Kliknij działanie **WriteLine** w sekcji **else** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **Text** .  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.  
  
     Poniższy przykład ilustruje ukończony przepływ pracy.  
  
     ![Ilustracja przedstawiająca ukończony przepływ pracy automatu Stanów.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>Aby skompilować przepływ pracy  
  
1. Naciśnij kombinację klawiszy CTRL+SHIFT+B w celu skompilowania rozwiązania.  
  
     Aby uzyskać instrukcje dotyczące sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: uruchamianie przepływu pracy](how-to-run-a-workflow.md). Jeśli wykonano już krok [jak: uruchamianie przepływu pracy](how-to-run-a-workflow.md) z innym stylem przepływu pracy i chcesz uruchomić go przy użyciu przepływu pracy automatu Stanów z tego kroku, przejdź do tematu, [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) w temacie [jak uruchomić przepływ pracy](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Projektowanie przepływów pracy](designing-workflows.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie działania](how-to-create-an-activity.md)
- [Instrukcje: Uruchamianie przepływu pracy](how-to-run-a-workflow.md)
