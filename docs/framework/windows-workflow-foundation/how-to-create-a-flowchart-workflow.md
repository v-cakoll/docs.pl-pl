---
title: 'Instrukcje: Tworzenie przepływu pracy schematu blokowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 10483c747e0f86816db6f03dd8df17472f31f15c
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063766"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Instrukcje: Tworzenie przepływu pracy schematu blokowego
Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych. Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Flowchart> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu. Przepływ pracy modeli gra odgadnięcia liczb.  
  
> [!NOTE]
>  Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach. Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Aby utworzyć przepływ pracy  
  
1. Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.  
  
2. W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
3. Typ `FlowchartNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
4. Przeciągnij **schemat blokowy** działanie z **schemat blokowy** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Aby utworzyć zmienne przepływu pracy i argumenty  
  
1. Kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.  
  
2. Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
3. Kliknij przycisk **utworzenia argumentu**.  
  
4. Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
5. Kliknij przycisk **utworzenia argumentu**.  
  
6. Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
7. Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.  
  
8. Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.  
  
9. Kliknij przycisk **utworzyć zmienną**.  
  
    > [!TIP]
    >  Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.Flowchart> działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.  
  
10. Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
11. Kliknij przycisk **utworzyć zmienną**.  
  
12. Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.  
  
13. Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.  
  
### <a name="to-add-the-workflow-activities"></a>Aby dodać działania przepływu pracy  
  
1. Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i zatrzymaj wskaźnik myszy nad **Start** węzła, który znajduje się w górnej części Schemat blokowy. Gdy **przypisać** działań znajduje się nad **Start** węzła, trzy trójkąty wokół niego pojawią **Start** węzła. Upuść **przypisać** działania na trójkąt, który jest bezpośrednio poniżej **Start** węzła. To łączenie ze sobą dwa elementy, ustawiając **przypisać** działań jako pierwsze działanie w schemacie blokowym.  
  
    > [!NOTE]
    >  Działania mogą być wskazywane jako wyjścia działania w przepływie pracy tworząc ręcznie ich działanie węzeł początkowy. Aby to zrobić, umieść kursor myszy nad **Start** węzła, kliknij jeden z prostokątami, które są wyświetlane, gdy wskaźnik myszy znajduje się nad **Start** węzeł, a następnie przeciągnij w nawiązywaniu połączenia wiersz w dół do żądanej działania i upuść je na jednym z prostokąty, które są wyświetlane. Działania można wyznaczyć jako działanie początkowe, klikając prawym przyciskiem myszy it i wybierając polecenie **ustawiona jako węzeł Start**.  
  
2. Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
3. Przeciągnij **monitu** działanie z **NumberGuessWorkflowActivities** części **przybornika**, upuść go poniżej **przypisać** działania z poprzedniego kroku, a następnie połącz **monitu** działanie **przypisać** działania. Istnieją trzy sposoby, aby połączyć dwa działania. Pierwszy sposób to ich połączenia, ponieważ usuniesz **monitu** działania w przepływie pracy. Podczas przeciągania **monitu** działania w przepływie pracy, jego Zatrzymaj wskaźnik myszy **przypisać** działania i upuść je na jeden z czterech trójkątów, widocznych **monitu** działanie jest nad **przypisać** działania. Drugi sposób polega na upuszczanie **monitu** działanie do przepływu pracy w dowolnym miejscu. Następnie umieść kursor myszy nad **przypisać** działania i przeciągnij jeden z prostokątami, które pojawia się w dół do **monitu** działania. Przeciągnij myszą, aby łączenie wierszy z **przypisać** działania nawiązanie połączenia z jednym z nich z **monitu** działania, a następnie zwolnij przycisk myszy. Trzeci sposób jest bardzo podobna do pierwszej sposób, chyba że zamiast przeciągania **monitu** działanie z **przybornika**, przeciągnij ją z lokalizacji na powierzchni projektowej przepływu pracy, kursor  **Przypisz** działania i upuść je na jeden z trójkątów, które pojawia się.  
  
4. W **okno właściwości** dla **monitu** działania, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości. Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekstu** okno właściwości.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.  
  
5. Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i połączyć ją przy użyciu jednej z metod opisanych w poprzednim kroku, tak aby była poniżej  **Monituj** działania.  
  
6. Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.  
  
7. Przeciągnij **FlowDecision** z **schemat blokowy** części **przybornika** i połączyć ją poniżej **przypisać** działania. W **okno właściwości**, wpisz następujące wyrażenie do **warunek** pole wartości właściwości.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Przeciągnij kolejny **FlowDecision** działanie z **przybornika** i upuść ją poniżej pierwszej. Łączenie dwóch działań, przeciągając je z prostokąt, która jest oznaczona etykietą **False** u góry **FlowDecision** działania obszar przycinania na prostokąt na początku drugiej **FlowDecision**działania.  
  
    > [!TIP]
    >  Jeśli nie widzisz **True** i **False** etykiet na **FlowDecision**, umieść kursor myszy nad **FlowDecision**.  
  
9. Kliknij drugą **FlowDecision** działania, aby go zaznaczyć. W **okno właściwości**, wpisz następujące wyrażenie do **warunek** pole wartości właściwości.  
  
    ```
    Guess < Target  
    ```  
  
10. Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je, aby były one obok siebie poniżej dwa **FlowDecision**  działań. Połącz **True** akcji w dolnej części **FlowDecision** najdalej z lewej strony działania **WriteLine** działania i **False** akcji po prawej stronie **WriteLine** działania.  
  
11. Kliknij przycisk najdalej z lewej strony **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** wartość właściwości pola **okno właściwości**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Połącz **WriteLine** się po lewej stronie **monitu** działania stanowiący nad nim.  
  
13. Kliknij przycisk po prawej stronie **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** wartość właściwości pola **okno właściwości**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Połącz **WriteLine** działanie po prawej stronie **monitu** działania nad nim.  
  
     Poniższy przykład ilustruje ukończony przepływ pracy.  
  
     ![Diagram przedstawiający ukończone blokowy Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>Tworzenie przepływu pracy  
  
1. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md). Jeśli wykonano już [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą przepływu pracy schematu blokowego, w tym kroku, przejdź do sekcji [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Projektowanie przepływów pracy](designing-workflows.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Utwórz działanie](how-to-create-an-activity.md)
- [Instrukcje: Uruchamianie przepływu pracy](how-to-run-a-workflow.md)
