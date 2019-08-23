---
title: 'Instrukcje: Tworzenie przepływu pracy schematu blokowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 6d67629503d5acfeff7e14e1889a047444a8d399
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962394"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Instrukcje: Tworzenie przepływu pracy schematu blokowego
Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych. W tym temacie przedstawiono procedurę tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.Flowchart> działania, jak i działań niestandardowych, z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) . Przepływ pracy modeluje grę z liczbą odgadnąć.  
  
> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).  
  
> [!NOTE]
> Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
2. W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**. Wybierz **działanie** z listy **przepływów pracy** .  
  
3. Wpisz `FlowchartNumberGuessWorkflow` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
4. Przeciągnij działanie **Flowchart** z sekcji **Flowchart** w przyborniku i upuść je do **działania Drop tutaj** etykieta na powierzchni projektowej przepływu pracy.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne i argumenty przepływu pracy  
  
1. Kliknij dwukrotnie pozycję **FlowchartNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.  
  
2. Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .  
  
3. Kliknij przycisk **Utwórz argument**.  
  
4. Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
5. Kliknij przycisk **Utwórz argument**.  
  
6. Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.  
  
7. Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .  
  
8. Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .  
  
9. Kliknij pozycję **Utwórz zmienną**.  
  
    > [!TIP]
    >  Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij <xref:System.Activities.Statements.Flowchart> działanie na powierzchni projektanta przepływu pracy, aby je wybrać.  
  
10. Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij pozycję **Utwórz zmienną**.  
  
12. Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i umieść je nad węzłem **początkowym** znajdującym się w górnej części schematu blokowego. Gdy działanie **Assign** znajduje się nad węzłem **startowym** , zostaną wyświetlone trzy trójkąty wokół węzła **Start** . Upuść działanie **Assign** na trójkącie, które znajduje się bezpośrednio pod węzłem **początkowym** . Spowoduje to połączenie dwóch elementów i wyznaczenie działania **przypisania** jako pierwszego działania w schemacie blokowym.  
  
    > [!NOTE]
    > Działania mogą być również wskazywane jako działanie uruchamiania w przepływie pracy przez ręczne łączenie z tym działaniem z węzłem początkowym. Aby to zrobić, umieść kursor myszy nad węzłem **startowym** , kliknij jeden z prostokątów, który pojawia się, gdy wskaźnik myszy znajduje się nad węzłem **startowym** , i przeciągnij linię łączącą w dół do żądanego działania i upuść ją na jednym z prostokątów, które są wyświetlane. Możesz również wyznaczyć działanie jako działanie uruchamiania, klikając je prawym przyciskiem myszy i wybierając pozycję **Ustaw jako węzeł startowy**.  
  
2. Wpisz `Target` w polu **do** i poniższe wyrażenie w polu  **C# wprowadź wyrażenie** lub **wprowadź wyrażenie w języku VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .  
  
3. Przeciągnij działanie **monitu** z sekcji **NumberGuessWorkflowActivities** w przyborniku, upuść je poniżej akcji **Przypisz** z poprzedniego kroku, a następnie połącz działanie monitu z przypisaniem działania. Istnieją trzy sposoby łączenia tych dwóch działań. Pierwszy sposób polega na nawiązaniu połączenia w trakcie upuszczania działania **monitu** w przepływie pracy. Przeciągając działanie monitu do przepływu pracy, umieść je nad przydziałem **Assign** i upuść je na jednym z czterech trójkątów, które pojawiają się, gdy działanie **monitu** znajduje się nad przypisaniem. Drugi sposób polega na porzucenia działania **monitu** na przepływ pracy w odpowiedniej lokalizacji. Następnie przesuń wskaźnik myszy nad działanie przypisywania i przeciągnij jeden z prostokątów, które pojawiają się w dół do działania **monitu** . Przeciągnij myszą tak, aby linia łącząca z działania **Assign** łączyła się z jednym z prostokątów działania **monitu** , a następnie zwolnij przycisk myszy. Trzeci sposób jest bardzo podobny do pierwszego, z tą różnicą, że zamiast przeciągać działanie **monitu** z **przybornika**, przeciągasz go z jego lokalizacji na powierzchni projektowej przepływu pracy, przesuwaj go na działanie przypisywania i upuść je na jedną z widoczne trójkąty.  
  
4. W **oknie właściwości** działania monitu wpisz `"EnterGuess"` , w tym cudzysłowy w polu wartość właściwości **zakładkaname** . Wpisz `Guess` w polu wartość właściwości **wynik** i wpisz następujące wyrażenie w polu właściwości **Text** .  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .  
  
5. Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i połącz je przy użyciu jednej z metod opisanych w poprzednim kroku, tak aby była niższa od działania **monitu** .  
  
6. Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź C# wyrażenie** lub wprowadź wyrażenie w **języku VB** .  
  
7. Przeciągnij element **FlowDecision** z sekcji **Flowchart** w przyborniku i połącz go pod działaniem **Assign** . W **oknie właściwości**wpisz następujące wyrażenie w polu wartość właściwości **warunek** .  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Przeciągnij kolejną aktywność **FlowDecision** z **przybornika** i upuść ją poniżej pierwszego. Połącz dwa działania, przeciągając od prostokąta, który jest oznaczony jako **false** w górnym działaniu **FlowDecision** do prostokąta w górnej części drugiego działania **FlowDecision** .  
  
    > [!TIP]
    >  Jeśli nie widzisz etykiet **prawda** i **Fałsz** w **FlowDecision**, umieść wskaźnik myszy nad **FlowDecisionem**.  
  
9. Kliknij drugie działanie **FlowDecision** , aby je wybrać. W **oknie właściwości**wpisz następujące wyrażenie w polu wartość właściwości **warunek** .  
  
    ```
    Guess < Target  
    ```  
  
10. Przeciągnij dwie działania **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je tak, aby znajdowały się obok dwóch działań **FlowDecision** . Połącz **rzeczywistą** akcję dolnego działania **FlowDecision** do lewego działania **WriteLine** i **wartość false** dla działania **WriteLine** z prawej strony.  
  
11. Kliknij z lewej strony działanie **WriteLine** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **tekst** w **oknie właściwości**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Połącz metodę **WriteLine** z lewą stroną działania monitu o powyższego poziomu.  
  
13. Kliknij prawym przyciskiem, aby go zaznaczyć, i wpisz następujące wyrażenie w polu wartość właściwości **tekst** w **oknie właściwości**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Połącz działanie **WriteLine** z prawą stroną działania monitu.  
  
     Poniższy przykład ilustruje ukończony przepływ pracy.  
  
     ![Diagram przedstawiający ukończony schemat blokowy Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>Aby skompilować przepływ pracy  
  
1. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Instrukcje dotyczące sposobu uruchamiania przepływu pracy można znaleźć w następnym temacie, [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md). Jeśli zostały już wykonane [następujące instrukcje: Uruchom krok przepływu](how-to-run-a-workflow.md) pracy z innym stylem przepływu pracy i chcę uruchomić go za pomocą przepływu pracy Flowchart z tego kroku, przejdź do tematu [ [w celu skompilowania i uruchomienia aplikacji](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) w temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Projektowanie przepływów pracy](designing-workflows.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie działania](how-to-create-an-activity.md)
- [Instrukcje: Uruchamianie przepływu pracy](how-to-run-a-workflow.md)
