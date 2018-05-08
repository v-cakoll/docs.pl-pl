---
title: 'Porady: tworzenie przepływów pracy schematu blokowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: c483a79a234d175fca63f27b4303b3f087c84e59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-flowchart-workflow"></a>Porady: tworzenie przepływów pracy schematu blokowego
Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych. W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.Flowchart> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu. Przepływ pracy modele numer guessing gier.  
  
> [!NOTE]
>  Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów. Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2.  W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3.  Typ `FlowchartNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
4.  Przeciągnij **schemat blokowy** działania z **schemat blokowy** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchni projektu przepływu pracy.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1.  Kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.  
  
2.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3.  Kliknij przycisk **utworzenia argumentu**.  
  
4.  Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5.  Kliknij przycisk **utworzenia argumentu**.  
  
6.  Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7.  Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.  
  
8.  Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.Flowchart> działania na powierzchni projektanta przepływu pracy, aby go wybrać.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1.  Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i umieść kursor myszy nad **Start** węzła, który znajduje się na początku Schemat blokowy. Gdy **przypisać** działanie znajduje się nad **Start** węzła, trzy trójkąty pojawi się wokół **Start** węzła. Upuść **przypisać** działania na trójkąt, która jest bezpośrednio poniżej **Start** węzła. To będzie połączyć dwóch elementów i wyznacza **przypisać** działania jako pierwsze działanie w schemacie blokowym.  
  
    > [!NOTE]
    >  Działania mogą być wskazywane jako rozpoczęcia działania w przepływie pracy przez ręcznie łączenie ich działania z węzła początkowego. Aby to zrobić, umieść kursor myszy nad **Start** węzła, kliknij jeden z prostokąty, które są wyświetlane, gdy wskaźnik myszy znajduje się nad **Start** węzeł, a następnie przeciągnij połączenie wiersz w dół, aby odpowiednie działanie i upuść ją na jednym z prostokąty, które są wyświetlane. Możesz też określić i działania jako działanie początkowe prawym przyciskiem myszy it i wybierając pozycję **ustawić jako węzeł Start**.  
  
2.  Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
3.  Przeciągnij **monitu** działania z **NumberGuessWorkflowActivities** sekcji **przybornika**, upuść ją poniżej **przypisać** działania od poprzedniego kroku, a następnie połącz **monitu** działanie **przypisać** działania. Istnieją trzy sposoby podłączenia dwóch działań. Pierwszym sposobem jest ich połączenia, ponieważ musisz porzucić **monitu** działania w przepływie pracy. Podczas przeciągania **monitu** działania w przepływie pracy, umieść ją nad **przypisać** działania i upuść ją na jeden z czterech trójkątów widocznych **monitu** działanie znajduje się nad **przypisać** działania. Drugi sposób polega na porzucić **monitu** działania do przepływu pracy w wybranej lokalizacji. Następnie, umieść kursor myszy nad **przypisać** działania i przeciągnij jedną prostokątów występujące w dół do **monitu** działania. Przeciągnij mysz, aby połączyć wiersz z **przypisać** działania połączy się z jednym z prostokątów z **monitu** działania, a następnie zwolnij przycisk myszy. Trzeci sposób jest bardzo podobny do pierwszy sposób, z wyjątkiem przeciąganie **monitu** działania z **przybornika**, przeciągnij ją z lokalizacji na powierzchni projektu przepływu pracy, Aktywuj  **Przypisz** działania i upuść ją na jedną trójkąty, które zostanie wyświetlone.  
  
4.  W **okna właściwości** dla **monitu** działania, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości. Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekst** pole właściwości.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.  
  
5.  Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i podłącz go przy użyciu jednej z metod opisanych w poprzednim kroku, aby była poniżej  **Monituj** działania.  
  
6.  Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.  
  
7.  Przeciągnij **elementu FlowDecision** z **schemat blokowy** sekcji **przybornika** i podłącz go poniżej **przypisać** działania. W **okna właściwości**, wpisz następujące wyrażenie w **warunku** pole wartości właściwości.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Przeciągnij kolejny **elementu FlowDecision** działania z **przybornika** i upuść ją poniżej pierwsza z nich. Połącz dwa działania przez przeciąganie z okna o nazwie **False** u góry **elementu FlowDecision** działanie prostokąt na początku drugiej **elementu FlowDecision**działania.  
  
    > [!TIP]
    >  Jeśli nie widzisz **True** i **False** etykiet na **elementu FlowDecision**, umieść kursor myszy nad **elementu FlowDecision**.  
  
9. Kliknij pozycję drugiego **elementu FlowDecision** działania, aby go wybrać. W **okna właściwości**, wpisz następujące wyrażenie w **warunku** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
10. Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, aby były one obok siebie poniżej dwa **elementu FlowDecision**  działań. Połączyć **True** akcji dolnego **elementu FlowDecision** działania do lewej **WriteLine** działania i **False** akcji po prawej stronie **WriteLine** działania.  
  
11. Kliknij przycisk lewej **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** wartość właściwości pola w **okna właściwości**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Połącz **WriteLine** do lewej strony **monitu** działanie, które jest nad nim.  
  
13. Kliknij przycisk skrajnej **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** wartość właściwości pola w **okna właściwości**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Połącz **WriteLine** do prawej strony działania **monitu** działania powyżej.  
  
     Poniższy przykład przedstawia ukończonych przepływów pracy.  
  
     ![Ukończono Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
     Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą schematu blokowego przepływu pracy z tym kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)części [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programowanie w programie Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Projektowanie przepływów pracy](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Instrukcje: Tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Instrukcje: Uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
