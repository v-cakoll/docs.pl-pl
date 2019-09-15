---
title: 'Instrukcje: Równoczesne hostowanie wielu wersji przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989649"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Instrukcje: Równoczesne hostowanie wielu wersji przepływu pracy

`WorkflowIdentity`umożliwia deweloperom aplikacji przepływu pracy kojarzenie nazwy i wersji z definicją przepływu pracy oraz dla tych informacji do skojarzenia z utrwalonym wystąpieniem przepływu pracy. Te informacje o tożsamości mogą być używane przez deweloperów aplikacji przepływu pracy do włączania scenariuszy, takich jak wykonywanie równoczesne wielu wersji definicji przepływu pracy i udostępniają one podstawę do innych funkcji, takich jak aktualizacja dynamiczna. Ten krok w samouczku pokazuje, jak używać `WorkflowIdentity` do hostowania wielu wersji przepływu pracy w tym samym czasie.

> [!NOTE]
> Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>W tym temacie:

W tym kroku samouczka `WriteLine` działania w przepływie pracy są modyfikowane w celu zapewnienia dodatkowych informacji i dodawane jest nowe `WriteLine` działanie. Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta zostanie zaktualizowana tak, aby mogła jednocześnie uruchamiać zarówno oryginalny, jak i zaktualizowany przepływy pracy.

- [Aby utworzyć kopię projektu NumberGuessWorkflowActivities](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [Aby zaktualizować przepływy pracy](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [Aby zaktualizować przepływ pracy StateMachine](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [Aby zaktualizować przepływ pracy Flowchart](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [Aby zaktualizować sekwencyjny przepływ pracy](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [Aby zaktualizować WorkflowVersionMap w celu uwzględnienia poprzednich wersji przepływu pracy](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [Aby skompilować i uruchomić aplikację](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> Przed wykonaniem kroków opisanych w tym temacie należy uruchomić aplikację, uruchomić kilka przepływów pracy każdego typu i wprowadzić jedną lub dwie wartości dla każdego z nich. Te utrwalone przepływy pracy są używane w tym kroku i w [następujących krokach: Zaktualizuj definicję uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy.

> [!NOTE]
> Każdy krok w samouczku Wprowadzenie zależy od poprzednich kroków. Jeśli poprzednie kroki nie zostały wykonane, możesz pobrać ukończoną wersję samouczka z [Windows Workflow Foundation (WF45) — wprowadzenie samouczka](https://go.microsoft.com/fwlink/?LinkID=248976).

### <a name="BKMK_BackupCopy"></a>Aby utworzyć kopię projektu NumberGuessWorkflowActivities

1. Otwórz rozwiązanie **WF45GettingStartedTutorial** w programie Visual Studio 2012, jeśli nie jest otwarte.

2. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.

3. Zamknij rozwiązanie **WF45GettingStartedTutorial** .

4. Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się pliki rozwiązania samouczka i foldery projektu.

5. Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze, co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**. Ten folder służy do przechowywania zestawów zawierających różne wersje przepływów pracy używanych w kolejnych krokach samouczka.

6. Przejdź do folderu **NumberGuessWorkflowActivities\bin\debug** (lub **bin\Release** w zależności od ustawień projektu). Skopiuj plik **NumberGuessWorkflowActivities. dll** i wklej go do folderu **PreviousVersions** .

7. Zmień nazwę **NumberGuessWorkflowActivities. dll** w folderze **PreviousVersions** na **NumberGuessWorkflowActivities_v1. dll**.

    > [!NOTE]
    > Kroki przedstawione w tym temacie przedstawiają jeden ze sposobów zarządzania zestawami używanymi do przechowywania wielu wersji przepływów pracy. Można również użyć innych metod, takich jak silne nazewnictwo zestawów i rejestrowanie ich w globalnej pamięci podręcznej zestawów.

8. Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze, co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**i nowo dodany folder **PreviousVersions** , a następnie skopiuj wszystkie pliki i podfoldery z folderu **NumberGuessWorkflowActivities** do nowego folderu **NumberGuessWorkflowActivities_du** . Ta kopia zapasowa projektu dla początkowej wersji działań jest używana w [następujący sposób: Zaktualizuj definicję uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy.

9. Otwórz ponownie rozwiązanie **WF45GettingStartedTutorial** w programie Visual Studio 2012.

### <a name="BKMK_UpdateWorkflows"></a>Aby zaktualizować przepływy pracy

W tej sekcji definicje przepływów pracy zostaną zaktualizowane. Dwa `WriteLine` działania, które dają opinię na temat odgadnięcia użytkownika, są aktualizowane i dodawane jest `WriteLine` nowe działanie, które zapewnia dodatkowe informacje o grze, gdy nastąpi odpuszczenie liczby.

#### <a name="BKMK_UpdateStateMachine"></a>Aby zaktualizować przepływ pracy StateMachine

1. W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **StateMachineNumberGuessWorkflow. XAML**.

2. Kliknij dwukrotnie **nieprawidłowe** przejście na komputerze stanu.

3. Zaktualizuj część z lewej strony `WriteLine` `If` działania. `Text`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. Zaktualizuj część z prawej strony `WriteLine` `If` działania. `Text`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.

6. Kliknij dwukrotnie **odpowiednie przejście na** komputerze stanu.

7. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w **działaniu akcji upuść tutaj** etykieta przejścia.

8. Wpisz następujące wyrażenie w `Text` polu właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a>Aby zaktualizować przepływ pracy Flowchart

1. W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **FlowchartNumberGuessWorkflow. XAML**.

2. Zaktualizuj wartość `Text` `WriteLine` działania z lewej strony.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. `Text` Zaktualizuj część `WriteLine` działania z prawej strony.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w punkcie `True` upuszczania akcji najwyższego `FlowDecision`poziomu. Działanie jest dodawane do schematu blokowego i połączone `True` z akcją `FlowDecision`. `WriteLine`

5. Wpisz następujące wyrażenie w `Text` polu właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a>Aby zaktualizować sekwencyjny przepływ pracy

1. W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **SequentialNumberGuessWorkflow. XAML**.

2. Zaktualizuj część z lewej strony `WriteLine` `If` działania. `Text`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. `WriteLine` Zaktualizuj działanie `If` z prawej strony `Text` w działaniu.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je po działaniu **DoWhile** , tak aby Metoda **WriteLine** była ostatnim działaniem w działaniu `Sequence` głównym.

5. Wpisz następujące wyrażenie w `Text` polu właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a>Aby zaktualizować WorkflowVersionMap w celu uwzględnienia poprzednich wersji przepływu pracy

1. Kliknij dwukrotnie pozycję **WorkflowVersionMap.cs** (lub **WorkflowVersionMap. vb**) w projekcie **NumberGuessWorkflowHost** , aby go otworzyć.

2. Dodaj następujące `using` instrukcje (lub `Imports`) na początku pliku z innymi `using` instrukcjami (lub `Imports`).

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. Dodaj trzy nowe tożsamości przepływu pracy tuż poniżej trzech istniejących deklaracji tożsamości przepływu pracy. Te nowe `v1` tożsamości przepływu pracy będą używane do zapewnienia, że przepływy pracy zostały uruchomione przed wprowadzeniem aktualizacji.

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. W konstruktorze `Version` zaktualizuj właściwość trzech bieżących tożsamości przepływu pracy do `2.0.0.0`. `WorkflowVersionMap`

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    Kod w programie, który dodaje bieżące wersje przepływów pracy do słownika używa bieżących wersji, do których odwołuje się projekt, więc kod inicjujący definicje przepływu pracy nie musi zostać zaktualizowany.

5. Dodaj następujący kod w konstruktorze bezpośrednio po kodzie, który dodaje bieżące wersje do słownika.

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    Te tożsamości przepływu pracy są skojarzone z początkowymi wersjami odpowiednich definicji przepływu pracy.

6. Następnie Załaduj zestaw zawierający początkową wersję definicji przepływu pracy i Utwórz i Dodaj odpowiednie definicje przepływów pracy do słownika.

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    Poniższy przykład to kompletna lista dla zaktualizowanej `WorkflowVersionMap` klasy.

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="BKMK_BuildAndRun"></a>Aby skompilować i uruchomić aplikację

1. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować aplikację, a następnie naciśnij klawisze CTRL + F5, aby rozpocząć.

2. Uruchom nowy przepływ pracy, klikając pozycję **Nowa gra**. Wersja przepływu pracy jest wyświetlana w oknie stanu i odzwierciedla zaktualizowaną wersję ze skojarzonego `WorkflowIdentity`. Zanotuj `InstanceId` , aby można było wyświetlić plik śledzenia dla przepływu pracy po jego zakończeniu, a następnie wprowadzić wartości odgadnięcia do momentu zakończenia gry. Zwróć uwagę, w jaki sposób odgadnięcie użytkownika jest wyświetlane w informacjach wyświetlanych w oknie stanu na podstawie aktualizacji `WriteLine` działań.

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > Wyświetlany jest zaktualizowany tekst `WriteLine` działań, ale dane wyjściowe działania końcowego `WriteLine` , które zostało dodane w tym temacie, nie są obsługiwane. Wynika to z faktu, że okno stanu jest `PersistableIdle` aktualizowane przez program obsługi. Ponieważ przepływ pracy kończy się i nie przechodzi bezczynnie po zakończeniu działania końcowego `PersistableIdle` , program obsługi nie zostanie wywołany. Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` program obsługi. W razie potrzeby kod można dodać do `Completed` programu obsługi, aby wyodrębnić tekst `StringWriter` z i wyświetlić go w oknie stanu.

3. Otwórz Eksploratora Windows i przejdź do folderu **NumberGuessWorkflowHost\bin\debug** (lub **bin\Release** w zależności od ustawień projektu) i Otwórz plik śledzenia przy użyciu Notatnika odpowiadającego zakończonemu przepływowi pracy. Jeśli nie zanotujesz tego `InstanceId`, możesz zidentyfikować prawidłowy plik śledzenia przy użyciu informacji o **dacie modyfikacji** w Eksploratorze Windows.

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    Zaktualizowane `WriteLine` dane wyjściowe są zawarte w pliku śledzenia, łącznie z danymi wyjściowymi `WriteLine` , które zostały dodane w tym temacie.

4. Przełącz się z powrotem do aplikacji umożliwiającej odgadnięcie i wybierz jeden z przepływów pracy, które zostały uruchomione przed wprowadzeniem aktualizacji. Wersję aktualnie wybranego przepływu pracy można zidentyfikować, przeglądając informacje o wersji, które są wyświetlane poniżej okna stanu. Wprowadź kilka prób i zwróć uwagę na to, że aktualizacje stanu `WriteLine` są zgodne z danymi wyjściowymi działania z poprzedniej wersji i nie uwzględniają odgadnięcia użytkownika. Wynika to z faktu, że te przepływy pracy używają poprzedniej definicji przepływu pracy `WriteLine` , która nie ma aktualizacji.

    W następnym kroku, [jak: Aktualizacja definicji uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy, uruchomione `v1` wystąpienia przepływu pracy są aktualizowane, aby zawierały nowe funkcje jako `v2` wystąpienia.
