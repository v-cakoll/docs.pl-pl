---
title: "Porady: hostowanie wielu wersji przepływu pracy Side-by-Side"
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
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96ae4d3e02b923187b3e0f88a7b18e84094fa584
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Porady: hostowanie wielu wersji przepływu pracy Side-by-Side
`WorkflowIdentity`Umożliwia deweloperom aplikacji przepływu pracy skojarzyć nazwę i wersję z definicji przepływu pracy, a te informacje mają być skojarzone z wystąpieniem przepływu pracy utrwalonych. Informacje o tożsamości mogą posłużyć deweloperzy aplikacji przepływu pracy na potrzeby scenariuszy, takich jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i udostępnia inne funkcje, takie jak aktualizacja dynamiczna podstawy. Ten krok samouczka przedstawiono sposób użycia `WorkflowIdentity` do obsługi wielu wersji przepływu pracy w tym samym czasie.  
  
> [!NOTE]
>  Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
 W tym kroku samouczka `WriteLine` działań w przepływie pracy są modyfikować, aby uzyskać dodatkowe informacje, a nowy `WriteLine` dodaniu działania. Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta jest aktualizowana, co umożliwia uruchamianie zarówno oryginalny i zaktualizowany przepływ pracy w tym samym czasie.  
  
-   [Aby utworzyć kopię projektu NumberGuessWorkflowActivities](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [Aby zaktualizować przepływy pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [Aby zaktualizować StateMachine przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [Aby zaktualizować schemat blokowy przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [Aby zaktualizować sekwencyjnego przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [Aby zaktualizować WorkflowVersionMap uwzględnienie poprzednie wersje przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  Przed wykonaniem kroków w tym temacie, uruchom aplikację, uruchom kilka przepływy pracy każdego typu, a dzięki jednego lub dwóch prób dla każdego z nich. Te utrwalonych przepływów pracy są używane w tym kroku i następujący krok, [porady: aktualizacji definicji wystąpienia przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
> [!NOTE]
>  Każdy krok samouczka Wprowadzenie zależy od poprzednich kroków. Jeśli poprzednie kroki nie została ukończona, można pobrać ukończoną wersję samouczek z [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
###  <a name="BKMK_BackupCopy"></a>Aby utworzyć kopię projektu NumberGuessWorkflowActivities  
  
1.  Otwórz **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Jeśli nie jest otwarty.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Zamknij **WF45GettingStartedTutorial** rozwiązania.  
  
4.  Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się rozwiązania samouczka plików i folderów projektu.  
  
5.  Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**. Ten folder jest wykorzystywany do zawierają zestawy, które znajdują się różne wersje przepływów pracy, używany w kolejnych krokach samouczka.  
  
6.  Przejdź do **NumberGuessWorkflowActivities\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu). Kopiuj **NumberGuessWorkflowActivities.dll** i wklej ją do **PreviousVersions** folderu.  
  
7.  Zmień nazwę **NumberGuessWorkflowActivities.dll** w **PreviousVersions** folder **NumberGuessWorkflowActivities_v1.dll**.  
  
    > [!NOTE]
    >  Kroki opisane w tym temacie prezentują jednym ze sposobów zarządzania zestawy zawiera wiele wersji przepływów pracy. Ponadto można użyć innych metod, takich jak silnych nazw zestawów i rejestrowania ich w pamięci podręcznej GAC.  
  
8.  Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**i nowo dodaje **PreviousVersions** folderu i skopiuj wszystkie pliki i podfoldery z **NumberGuessWorkflowActivities** do nowego folderu  **NumberGuessWorkflowActivities_du** folderu. Tej kopii zapasowej projektu dla początkowej wersji działania jest używana w [porady: aktualizacji definicji wystąpienia przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
9. Otwórz ponownie **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
###  <a name="BKMK_UpdateWorkflows"></a>Aby zaktualizować przepływy pracy  
 W tej sekcji zaktualizowano definicji przepływu pracy. Dwa `WriteLine` działań, które Prześlij opinię na temat wynik użytkownika są zaktualizowane, a nowy `WriteLine` działania zostanie dodany, który udostępnia dodatkowe informacje o gry po odgadnąć jest liczba.  
  
####  <a name="BKMK_UpdateStateMachine"></a>Aby zaktualizować StateMachine przepływu pracy  
  
1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml**.  
  
2.  Kliknij dwukrotnie **odgadnąć niepoprawne** przejście komputera stanu.  
  
3.  Aktualizacja `Text` z lewej `WriteLine` w `If` działania.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  Aktualizacja `Text` z prawej krawędzi `WriteLine` w `If` działania.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.  
  
6.  Kliknij dwukrotnie **odgadnąć poprawne** przejście komputera stanu.  
  
7.  Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść ją na **akcji Upuść działanie tutaj** etykieta przejście.  
  
8.  Wpisz następujące wyrażenie w `Text` pole właściwości.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a>Aby zaktualizować schemat blokowy przepływu pracy  
  
1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml**.  
  
2.  Aktualizacja `Text` z lewej `WriteLine` działania.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Aktualizacja `Text` z prawej krawędzi `WriteLine` działania.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść go w punkcie upuszczania `True` akcji najwyższy węzeł `FlowDecision` . `WriteLine` Działania zostanie dodane do schematu blokowego i połączony z `True` akcji `FlowDecision`.  
  
5.  Wpisz następujące wyrażenie w `Text` pole właściwości.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a>Aby zaktualizować sekwencyjnego przepływu pracy  
  
1.  W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml**.  
  
2.  Aktualizacja `Text` z lewej `WriteLine` w `If` działania.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Aktualizacja `Text` z prawej krawędzi `WriteLine` działania w `If` działania.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je po **DoWhile** działania, aby  **WriteLine** jest ostatnie działanie w folderze głównym `Sequence` działania.  
  
5.  Wpisz następujące wyrażenie w `Text` pole właściwości.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a>Aby zaktualizować WorkflowVersionMap uwzględnienie poprzednie wersje przepływu pracy  
  
1.  Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.  
  
2.  Dodaj następujące `using` (lub `Imports`) instrukcje na początku pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  Dodaj trzy nowe tożsamości przepływu pracy poniżej trzy deklaracje tożsamości istniejącego przepływu pracy. Te nowe `v1` tożsamości będą używane w przepływie pracy zawierają definicje poprawne przepływu pracy do przepływów pracy zostało uruchomione przed aktualizacje zostały wprowadzone.  
  
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
  
4.  W `WorkflowVersionMap` konstruktora, aktualizacja `Version` właściwości trzy bieżącej tożsamości przepływu pracy do `2.0.0.0`.  
  
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
  
     Kod, który dodaje bieżące wersje przepływy pracy do słownika są używane bieżące wersje, które odwołują się do projektu, więc kod, który inicjuje definicji przepływu pracy musi zostać zaktualizowany.  
  
5.  Dodaj następujący kod w Konstruktorze zaraz po kod, który dodaje bieżącej wersji do słownika.  
  
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
  
     Tymi tożsamościami przepływu pracy są skojarzone z początkowej wersji odpowiedniej definicji przepływu pracy.  
  
6.  Następnie Załaduj zestaw, który zawiera początkowej wersji definicji przepływu pracy i tworzenie i dodawanie odpowiedniej definicji przepływu pracy do słownika.  
  
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
  
     Poniższy przykład jest pełna lista dla zaktualizowanego `WorkflowVersionMap` klasy.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a>Aby skompilować i uruchomić aplikację  
  
1.  Naciśnij klawisze CTRL + SHIFT + B do skompilowania aplikacji, a następnie klawisz CTRL + F5, aby rozpocząć.  
  
2.  Uruchamianie nowego przepływu pracy, klikając **nowej gry**. Wersja tego przepływu pracy jest wyświetlany w oknie stanu i odzwierciedla zaktualizowaną wersję z skojarzony `WorkflowIdentity`. Zanotuj `InstanceId` , można przejrzeć plik śledzenia dla przepływu pracy, po jego ukończeniu, a następnie wprowadź prób, aż do zakończenia gry. Należy zwrócić uwagę, jak wynik użytkownika jest wyświetlany w informacji wyświetlanych w oknie stanu na podstawie aktualizacji do `WriteLine` działań.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**5 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**3 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**1 jest zbyt niski.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**Gratulacje, odgadnąć numer w włącza 4.**    
    > [!NOTE]
    >  Zaktualizowany tekst z `WriteLine` działania jest wyświetlane, ale dane wyjściowe końcowych `WriteLine` nie jest działanie, które zostały dodane w tym temacie. To okno stanu jest aktualizowana przez `PersistableIdle` obsługi. Ponieważ zakończeniu przepływu pracy, a nie przechodzi bezczynności po ostatnie działanie `PersistableIdle` program obsługi nie jest wywoływany. Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` obsługi. W razie potrzeby kodu została dodana do `Completed` obsługi można wyodrębnić tekst z `StringWriter` i wyświetl ją w oknie stanu.  
  
3.  Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Ukończono przepływ pracy. Jeśli nie wprowadzono uwagę `InstanceId`, plik śledzenia poprawne można zidentyfikować przy użyciu **Data modyfikacji** informacji w Eksploratorze Windows.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**5 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**3 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**1 jest zbyt niski.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**2 jest poprawna. Odgadnięto go w włącza 4.**      Zaktualizowany interfejs `WriteLine` danych wyjściowych jest zawarty w pliku śledzenia, w tym dane wyjściowe `WriteLine` , dodanego w tym temacie.  
  
4.  Wrócić do numerów guessing aplikacji i wybierz jedną z przepływów pracy, które zostało uruchomione, zanim aktualizacje zostały wprowadzone. Wersja aktualnie wybranego przepływu pracy można zidentyfikować, analizując informacje o wersji, która jest wyświetlana poniżej oknie stanu. Wprowadź kilka prób i należy pamiętać, że stan aktualizacji dopasowania `WriteLine` działania dane wyjściowe z poprzedniej wersji, a nie dołączaj wynik użytkownika. Wynika to z faktu te przepływy pracy korzystają z poprzednich definicji przepływu pracy, który nie ma `WriteLine` aktualizacji.  
  
     W następnym kroku [porady: aktualizacji definicji wystąpienia przepływu pracy z](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), działanie `v1` wystąpienia przepływu pracy są aktualizowane i zawierają nowe funkcje, co `v2` wystąpień.
