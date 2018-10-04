---
title: 'Instrukcje: hostowanie wielu wersji przepływu pracy Side-by-Side'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 721ab72ab1f67d2dc42574ed0147fa7686e02fd1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780313"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Instrukcje: hostowanie wielu wersji przepływu pracy Side-by-Side
`WorkflowIdentity` Umożliwia deweloperom aplikacji przepływu pracy skojarzyć nazwę i wersję z definicji przepływu pracy i te informacje, które ma zostać skojarzony z istniejącym wystąpieniem przepływu pracy. Informacje o tożsamości może służyć przez deweloperów aplikacji przepływu pracy można obsługiwać scenariusze takie jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i zapewnia podstawę dla innych funkcji, takich jak aktualizacja dynamiczna. Ten krok, w tym samouczku przedstawiono sposób użycia `WorkflowIdentity` do hostowania wielu wersji przepływu pracy w tym samym czasie.

> [!NOTE]
>  Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
 W tym kroku samouczka `WriteLine` działań w przepływie pracy są modyfikowane w celu dodatkowe informacje i nową `WriteLine` dodanym działaniem. Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta zostanie zaktualizowana, dzięki czemu można uruchamiać zarówno oryginał, jak i zaktualizowano przepływów pracy w tym samym czasie.  
  
-   [Aby utworzyć kopię projektu NumberGuessWorkflowActivities](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [Aby zaktualizować przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [Aktualizacja Automat stanów przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [Aktualizacja przepływu pracy schematu blokowego](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [Aby zaktualizować sekwencyjnego przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [Aby zaktualizować WorkflowVersionMap obejmujący poprzednich wersji przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  Przed wykonaniem kroków w tym temacie, uruchom aplikację, uruchom wiele przepływów pracy dla każdego typu, a dzięki jednej lub dwóch prób dla każdego z nich. Tych utrwalonych przepływów pracy są używane w tym kroku i następny krok [porady: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).

> [!NOTE]
>  Poszczególne kroki samouczka Wprowadzenie zależy od poprzednich kroków. Jeśli nie została ukończona poprzednich kroków możesz pobrać pełną wersję z samouczka w [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
###  <a name="BKMK_BackupCopy"></a> Aby utworzyć kopię projektu NumberGuessWorkflowActivities  
  
1.  Otwórz **WF45GettingStartedTutorial** rozwiązania programu Visual Studio 2012, jeśli nie jest otwarty.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Zamknij **WF45GettingStartedTutorial** rozwiązania.  
  
4.  Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się w pliku rozwiązania samouczka i folderów projektu.  
  
5.  Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**. Ten folder jest używany do zawierają zestawy, które zawierają różne wersje przepływy pracy, wykorzystywane w kolejnych krokach samouczka.  
  
6.  Przejdź do **NumberGuessWorkflowActivities\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu). Kopiuj **NumberGuessWorkflowActivities.dll** i wklej go w **PreviousVersions** folderu.  
  
7.  Zmień nazwę **NumberGuessWorkflowActivities.dll** w **PreviousVersions** folder **NumberGuessWorkflowActivities_v1.dll**.  
  
    > [!NOTE]
    >  Kroki opisane w tym temacie pokazują jeden sposób zarządzania zestawów zawiera wiele wersji przepływów pracy. Można również zmienić innych metod, takich jak silnych nazw zestawów i rejestrowania ich w globalnej pamięci podręcznej.

8.  Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, a nowo dodano **PreviousVersions** folder, a następnie skopiuj wszystkie pliki i podfoldery z **NumberGuessWorkflowActivities** do nowego folderu  **NumberGuessWorkflowActivities_du** folderu. Ta kopia zapasowa projektu dla początkowej wersji działania jest używana w [porady: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).

9. Otwórz ponownie **WF45GettingStartedTutorial** rozwiązania w programie Visual Studio 2012.

###  <a name="BKMK_UpdateWorkflows"></a> Aby zaktualizować przepływów pracy
 W tej sekcji definicji przepływu pracy są aktualizowane. Dwa `WriteLine` działań, które Prześlij opinię na temat odgadnięcia użytkownika są aktualizowane i nowej `WriteLine` dodanym działaniem, zawiera dodatkowe informacje o gry, gdy liczba jest złamać.

####  <a name="BKMK_UpdateStateMachine"></a> Aktualizacja Automat stanów przepływu pracy

1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml**.

2.  Kliknij dwukrotnie **odgadnięcia niepoprawne** przejście maszyny stanu.

3.  Aktualizacja `Text` z lewym skrajnym `WriteLine` w `If` działania.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4.  Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` w `If` działania.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5.  Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.

6.  Kliknij dwukrotnie **odgadnięcia poprawne** przejście maszyny stanu.

7.  Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **działania Upuść działanie tutaj** etykiety przejście.

8.  Wpisz następujące wyrażenie do `Text` okno właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

####  <a name="BKMK_UpdateFlowchart"></a> Aktualizacja przepływu pracy schematu blokowego

1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml**.

2.  Aktualizacja `Text` z lewym skrajnym `WriteLine` działania.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` działania.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je w punkcie listy `True` akcji najwyższy `FlowDecision` . `WriteLine` Działania zostaną dodane do schematu blokowego i połączone z `True` akcji `FlowDecision`.

5.  Wpisz następujące wyrażenie do `Text` okno właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

####  <a name="BKMK_UpdateSequential"></a> Aby zaktualizować sekwencyjnego przepływu pracy

1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml**.

2.  Aktualizacja `Text` z lewym skrajnym `WriteLine` w `If` działania.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` działania w `If` działania.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je po **DoWhile** działanie tak, aby  **WriteLine** jest ostatnie działanie w katalogu głównym `Sequence` działania.

5.  Wpisz następujące wyrażenie do `Text` okno właściwości.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

###  <a name="BKMK_UpdateWorkflowVersionMap"></a> Aby zaktualizować WorkflowVersionMap obejmujący poprzednich wersji przepływu pracy

1.  Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.

2.  Dodaj następujący kod `using` (lub `Imports`) instrukcji na górze pliku razem z innymi `using` (lub `Imports`) instrukcji.

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3.  Dodaj trzy nowe tożsamości przepływu pracy po prostu poniższe trzy deklaracje tożsamość istniejącego przepływu pracy. Te nowe `v1` przepływu pracy będą używane tożsamości udostępniają definicje poprawne przepływu pracy do przepływów pracy uruchomionych przed aktualizacje zostały wprowadzone.

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

4.  W `WorkflowVersionMap` Konstruktor, aktualizacja `Version` właściwość trzy bieżącej tożsamości przepływu pracy do `2.0.0.0`.

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

     Kod, który dodaje aktualne wersje przepływy pracy do słownika używa bieżące wersje, które są określone w projekcie, więc kod, który inicjuje definicji przepływu pracy nie musi zostać zaktualizowany.

5.  Dodaj następujący kod w Konstruktorze zaraz po kod, który dodaje bieżące wersje do słownika.

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

     Te tożsamości przepływu pracy są skojarzone z odpowiedniej definicji przepływu pracy w wersji początkowej.

6.  Następnie Załaduj zestaw, który zawiera wstępną wersję definicji przepływu pracy i tworzenie i dodawanie odpowiedniej definicji przepływu pracy do słownika.

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

     Poniższy przykład przedstawia pełną listę, aby uzyskać zaktualizowany `WorkflowVersionMap` klasy.

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

###  <a name="BKMK_BuildAndRun"></a> Aby skompilować i uruchomić aplikację

1.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację i CTRL + F5, aby rozpocząć.

2.  Rozpocznij nowy przepływ pracy, klikając **nową grę**. Wersja przepływu pracy jest wyświetlany w oknie stanu i uwzględnia zaktualizowaną wersję z powiązanego `WorkflowIdentity`. Zwróć uwagę na `InstanceId` , można wyświetlić pliku śledzenia dla przepływu pracy po jego ukończeniu, a następnie wprowadź liczbę prób, aż do zakończenia gry. Należy zauważyć, jak odgadnięcia użytkownika jest wyświetlany w informacjach wyświetlanych w oknie stanu na podstawie aktualizacji do `WriteLine` działań.

 **Wprowadź liczbę między 1 a 10**
**5 jest zbyt wysoka.** 
 **Wprowadź liczbę między 1 a 10**
**3 jest zbyt wysoka.** 
 **Wprowadź liczbę między 1 a 10**
**ma zbyt niską wartość 1.** 
 **Wprowadź liczbę między 1 a 10**
**Gratulacje, można złamać numer w włącza 4.**
    > [!NOTE]
    >  Zaktualizowany tekst z `WriteLine` działania jest wyświetlane, ale dane wyjściowe końcowe `WriteLine` braku aktywności, który został dodany w tym temacie. Wynika to z okna stanu jest aktualizowana przez `PersistableIdle` programu obsługi. Ponieważ przepływ pracy zakończy i nie przechodzi bezczynności po ostatnim działaniu `PersistableIdle` nie zostanie wywołana procedura obsługi. Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` programu obsługi. Jeśli to konieczne, kod może zostać dodany do `Completed` obsługi do wyodrębniania tekstu z `StringWriter` i wyświetl ją w oknie stanu.

3.  Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Aby ukończony przepływ pracy. Jeśli nie została wprowadzona Zanotuj `InstanceId`, plik śledzenia poprawne można zidentyfikować za pomocą **Data modyfikacji** informacji w Eksploratorze Windows.

 **Wprowadź liczbę między 1 a 10**
**5 jest zbyt wysoka.** 
 **Wprowadź liczbę między 1 a 10**
**3 jest zbyt wysoka.** 
 **Wprowadź liczbę między 1 a 10**
**ma zbyt niską wartość 1.** 
 **Wprowadź liczbę między 1 a 10**
**2 jest poprawna. Odgadnięto go w 4 wyłącza.**      Zaktualizowany interfejs `WriteLine` danych wyjściowych jest zawarty w pliku śledzenia, w tym dane wyjściowe `WriteLine` , dodanego w tym temacie.

4.  Przejdź z powrotem do odgadnięcia liczba aplikacji, a następnie wybierz jedno z przepływów pracy, które zostało uruchomione, zanim aktualizacje zostały wprowadzone. Wersję aktualnie wybranego przepływu pracy można zidentyfikować, sprawdzając informacje o wersji, która jest wyświetlana poniżej oknie stanu. Wprowadź kilka prób i należy pamiętać, że stan aktualizacji dopasowanie `WriteLine` działania dane wyjściowe z poprzedniej wersji i nie obejmują odgadnięcia użytkownika. To dlatego te przepływy pracy korzystają z poprzednią definicję przepływu pracy, który nie ma `WriteLine` aktualizacji.

     W następnym kroku [instrukcje: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), uruchomienie `v1` wystąpienia przepływu pracy są aktualizowane i zawierają nową funkcjonalność w postaci `v2` wystąpień.
