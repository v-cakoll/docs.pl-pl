---
title: 'Instrukcje: Tworzenie sekwencyjnego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 9c9746305b251e7d48ee34c2cccd5afae174ee90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962364"
---
# <a name="how-to-create-a-sequential-workflow"></a>Instrukcje: Tworzenie sekwencyjnego przepływu pracy
Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych. W tym temacie przedstawiono procedurę tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.Sequence> działania, jak i działań niestandardowych, z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) . Przepływ pracy modeluje grę z liczbą odgadnąć.  
  
> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).  
  
> [!NOTE]
> Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
2. W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**. Wybierz **działanie** z listy **przepływów pracy** .  
  
3. Wpisz `SequentialNumberGuessWorkflow` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
4. Przeciągnij działanie **sekwencji** z sekcji **przepływ sterowania** w przyborniku i upuść je na etykiecie **działania upuść** na powierzchni projektowej przepływu pracy.  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne i argumenty przepływu pracy  
  
1. Kliknij dwukrotnie pozycję **SequentialNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.  
  
2. Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .  
  
3. Kliknij przycisk **Utwórz argument**.  
  
4. Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5. Kliknij przycisk **Utwórz argument**.  
  
6. Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.  
  
7. Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .  
  
8. Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .  
  
9. Kliknij pozycję **Utwórz zmienną**.  
  
    > [!TIP]
    >  Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij działanie **sekwencji** na powierzchni projektanta przepływu pracy, aby je wybrać.  
  
10. Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij pozycję **Utwórz zmienną**.  
  
12. Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .  
  
## <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i upuść je na działanie **sekwencji** . Wpisz `Target` w polu **do** i poniższe wyrażenie w polu  **C# wprowadź wyrażenie** lub **wprowadź wyrażenie w języku VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .  
  
2. Przeciągnij działanie **DoWhile** z sekcji **przepływ sterowania** w przyborniku i upuść je w przepływie pracy, tak aby była niższa od akcji przypisywania.  
  
3. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **DoWhile** .  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     Działanie wykonuje działania podrzędne, a następnie szacuje <xref:System.Activities.Statements.DoWhile.Condition%2A>je. <xref:System.Activities.Statements.DoWhile> Jeśli zostanie <xref:System.Activities.Statements.DoWhile.Condition%2A> obliczona `True`wartość, działania <xref:System.Activities.Statements.DoWhile> wykonywane ponownie. W tym przykładzie oszacowanie użytkownika jest oceniane i <xref:System.Activities.Statements.DoWhile> kontynuuje do momentu poprawienia wartości.  
  
4. Przeciągnij działanie **monitu** z sekcji **NumberGuessWorkflowActivities** w przyborniku i upuść je w działaniu **DoWhile** z poprzedniego kroku.  
  
5. W **oknie właściwości**, w polu `"EnterGuess"` wartość właściwości zakładkiname dla działania monitu wpisz cudzysłowy. Wpisz `Guess` w polu wartość właściwości **wynik** i wpisz następujące wyrażenie w polu właściwości **Text** .  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .  
  
6. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i upuść je w działaniu **DoWhile** , tak aby była zgodna z działaniem **monitu** .  
  
    > [!NOTE]
    > Po porzucenia działania **Przypisz** należy zwrócić uwagę, jak Projektant przepływu pracy automatycznie dodaje działanie **sekwencji** , aby zawierało zarówno działanie **monitu** , jak i nowo dodane działanie przypisywania.  
  
7. Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź C# wyrażenie** lub wprowadź wyrażenie w **języku VB** .  
  
8. Przeciągnij działanie **if** z sekcji **przepływ sterowania** w przyborniku i upuść je w działaniu **sekwencji** , tak aby była zgodna z nowo dodanym działaniem przypisywania.  
  
9. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **if** .  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Przeciągnij inną aktywność w **przypadku** działania z sekcji **przepływ sterowania** w **przyborniku** i upuść ją w sekcji po pierwszej aktywności **if** .  
  
11. Wpisz następujące wyrażenie w polu wartość właściwości **warunek** dla nowo dodanego działania **if** .  
  
    ```
    Guess < Target  
    ```  
  
12. Przeciągnij dwie działania **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je tak, aby były widoczne w sekcji nowo dodanego działania **if** , a jeden z nich znajduje się w sekcji **else** .  
  
13. Kliknij działanie **WriteLine** w sekcji Then, aby je zaznaczyć, a **następnie** wpisz następujące wyrażenie w polu wartość właściwości **Text** .  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. Kliknij działanie **WriteLine** w sekcji **else** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **Text** .  
  
    ```text
    "Your guess is too high."  
    ```  
  
     Poniższy przykład ilustruje ukończony przepływ pracy:  
  
     ![Zrzut ekranu przedstawiający ukończony sekwencyjny przepływ pracy.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a>Aby skompilować przepływ pracy  
  
1. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Instrukcje dotyczące sposobu uruchamiania przepływu pracy można znaleźć w następnym temacie, [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md). Jeśli zostały już wykonane [następujące instrukcje: Uruchom krok przepływu](how-to-run-a-workflow.md) pracy z innym stylem przepływu pracy i chcesz uruchomić go przy użyciu sekwencyjnego przepływu pracy z tego kroku, przejdź do sekcji [Aby skompilować i uruchomić](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [aplikację w temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Projektowanie przepływów pracy](designing-workflows.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie działania](how-to-create-an-activity.md)
- [Instrukcje: Uruchamianie przepływu pracy](how-to-run-a-workflow.md)
