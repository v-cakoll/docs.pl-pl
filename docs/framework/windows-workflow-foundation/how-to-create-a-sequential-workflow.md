---
title: 'Instrukcje: Tworzenie sekwencyjnego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 2213d766435aaafbf37b8646a66ea3007bfcb734
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719640"
---
# <a name="how-to-create-a-sequential-workflow"></a>Instrukcje: Tworzenie sekwencyjnego przepływu pracy
Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych. Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Sequence> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu. Przepływ pracy modeli gra odgadnięcia liczb.  
  
> [!NOTE]
>  Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach. Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2.  W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3.  Typ `SequentialNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
4.  Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1.  Kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.  
  
2.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3.  Kliknij przycisk **utworzenia argumentu**.  
  
4.  Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
5.  Kliknij przycisk **utworzenia argumentu**.  
  
6.  Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.  
  
8.  Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk **sekwencji** działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1.  Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je na **sekwencji** działania. Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
2.  Przeciągnij **DoWhile** działanie z **przepływ sterowania** części **przybornika** i upuść je na przepływ pracy, tak aby była poniżej **przypisać** działanie.  
  
3.  Wpisz następujące wyrażenie do **DoWhile** działania **warunek** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> wykonuje działania podrzędne działania, a następnie oblicza jego <xref:System.Activities.Statements.DoWhile.Condition%2A>. Jeśli <xref:System.Activities.Statements.DoWhile.Condition%2A> daje w wyniku `True`, następnie działań w <xref:System.Activities.Statements.DoWhile> wykonywania ponownie. W tym przykładzie jest szacowana wynik użytkownika i <xref:System.Activities.Statements.DoWhile> kontynuowany do momentu odgadnięcia jest poprawna.  
  
4.  Przeciągnij **monitu** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **DoWhile** działania w poprzednim kroku.  
  
5.  W **okno właściwości**, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości dla **monitu** działania. Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekstu** okno właściwości.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.  
  
6.  Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je **DoWhile** działania, tak że następuje po **Monitu** działania.  
  
    > [!NOTE]
    >  Po umieszczeniu **przypisać** aktywności, należy pamiętać, jak automatycznie dodaje projektanta przepływów pracy **sekwencji** działania, które zawierają zarówno **monitu** działanie i nowo dodane **Przypisać** działania.  
  
7.  Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
8.  Przeciągnij **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **sekwencji** działania, tak że następuje po nowo dodane **przypisać** działania.  
  
9. Wpisz następujące wyrażenie do **Jeśli** działania **warunek** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Przeciągnij kolejny **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **następnie** części pierwszego **Jeśli** działania.  
  
11. Wprowadź następujące wyrażenie w nowo dodanym **Jeśli** działania **warunek** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
12. Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je tak, aby jeden **następnie** sekcji nowo dodane **Jeśli** działania i jeden znajduje się w **Else** sekcji.  
  
13. Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     Poniższy przykład ilustruje ukończony przepływ pracy.  
  
     ![Ukończono sekwencyjnego przepływu pracy](./media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Tworzenie przepływu pracy  
  
1.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md). Jeśli wykonano już [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą sekwencyjnego przepływu pracy, w tym kroku, przejdź do sekcji [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Projektowanie przepływów pracy](designing-workflows.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Utwórz działanie](how-to-create-an-activity.md)
- [Instrukcje: Uruchamianie przepływu pracy](how-to-run-a-workflow.md)
