---
title: 'Porady: tworzenie sekwencyjnego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d7379e6e4d24ccc23d57486c3271c482a7f17edd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-sequential-workflow"></a>Porady: tworzenie sekwencyjnego przepływu pracy
Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych. W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.Sequence> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu. Przepływ pracy modele numer guessing gier.  
  
> [!NOTE]
>  Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów. Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2.  W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3.  Typ `SequentialNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
4.  Przeciągnij **sekwencji** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchni projektu przepływu pracy.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1.  Kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.  
  
2.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3.  Kliknij przycisk **utworzenia argumentu**.  
  
4.  Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5.  Kliknij przycisk **utworzenia argumentu**.  
  
6.  Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7.  Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.  
  
8.  Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk **sekwencji** działania na powierzchni projektanta przepływu pracy, aby go wybrać.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1.  Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść ją na **sekwencji** działania. Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
2.  Przeciągnij **DoWhile** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na przepływu pracy, aby była ona poniżej **przypisać** działanie.  
  
3.  Wpisz następujące wyrażenie w **DoWhile** działania **warunku** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> działania wykonuje działania podrzędne, a następnie oblicza jego <xref:System.Activities.Statements.DoWhile.Condition%2A>. Jeśli <xref:System.Activities.Statements.DoWhile.Condition%2A> daje w wyniku `True`, następnie działań w <xref:System.Activities.Statements.DoWhile> wykonać ponownie. W tym przykładzie wynik użytkownika jest obliczane i <xref:System.Activities.Statements.DoWhile> będzie wykonywany do momentu wynik jest poprawna.  
  
4.  Przeciągnij **monitu** działania z **NumberGuessWorkflowActivities** sekcji **przybornika** i upuść je w **DoWhile** działania w poprzednim kroku.  
  
5.  W **okna właściwości**, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości dla **monitu** działania. Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekst** pole właściwości.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.  
  
6.  Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść je w **DoWhile** działania, którego nie jest zgodny **Monitu** działania.  
  
    > [!NOTE]
    >  Po upuszczeniu **przypisać** działanie, należy pamiętać, jak automatycznie dodaje projektanta przepływów pracy **sekwencji** działania zawiera zarówno **monitu** działania i nowo dodany **Przypisać** działania.  
  
7.  Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
8.  Przeciągnij **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **sekwencji** działania, którego nie jest zgodny nowo dodana **przypisać** działania.  
  
9. Wpisz następujące wyrażenie w **Jeśli** działania **warunku** pole wartości właściwości.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Przeciągnij kolejny **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **następnie** sekcji pierwszego **Jeśli** działania.  
  
11. Wpisz poniższe wyrażenie w nowo dodanym **Jeśli** działania **warunku** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
12. Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, tak aby jedna jest **następnie** sekcji nowo dodany **Jeśli** działania, a druga jest **Else** sekcji.  
  
13. Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     Poniższy przykład przedstawia ukończonych przepływów pracy.  
  
     ![Ukończono sekwencyjnego przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
     Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą sekwencyjnego przepływu pracy z tym kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)części [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programowanie w programie Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Projektowanie przepływów pracy](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Instrukcje: Tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Instrukcje: Uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
