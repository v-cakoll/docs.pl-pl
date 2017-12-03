---
title: "Porady: aktualizowanie definicji działania wystąpienia przepływu pracy"
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
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb2191482771647bcc2cd1003229e445c320e1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Porady: aktualizowanie definicji działania wystąpienia przepływu pracy
Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperami aplikacji, aby zaktualizować wystąpienia przepływu pracy utrwalonych definicji przepływu pracy. Wymagana zmiana można wdrożyć poprawkę, nowe wymagania lub uwzględnienia nieoczekiwane. Ten krok samouczka przedstawiono sposób użycia aktualizacji dynamicznej można zmodyfikować wystąpienia utrwalonego `v1` numer odgadnięcie przepływu pracy do dopasowania nowych funkcji wprowadzonych w [porady: wiele wersji hosta przepływu pracy Side-by-Side ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
> [!NOTE]
>  Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Aby utworzyć projekt CreateUpdateMaps](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [Aby zaktualizować StateMachineNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [Aby zaktualizować FlowchartNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [Aby zaktualizować SequentialNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [Aby skompilować i uruchomić aplikację CreateUpdateMaps](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [Tworzenie zestawu zaktualizowany przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [Aby zaktualizować WorkflowVersionMap do nowych wersji](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Aby zastosować aktualizacje dynamiczne](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [Aby uruchomić aplikację zaktualizowane przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [Aby włączyć uruchamianie poprzednich wersji przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a>Aby utworzyć projekt CreateUpdateMaps  
  
1.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.  
  
2.  W **zainstalowana** węzła, wybierz opcję **Visual C#**, **Windows** (lub **Visual Basic**, **Windows**).  
  
    > [!NOTE]
    >  W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.  
  
     Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Wybierz **aplikacji konsoli** z **Windows** listy. Typ **CreateUpdateMaps** do **nazwa** polu i kliknij przycisk **OK**.  
  
3.  Kliknij prawym przyciskiem myszy **CreateUpdateMaps** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**.  
  
4.  Wybierz **Framework** z **zestawy** w węźle **Dodaj odwołanie** listy. Typ **elementu System.Activities** do **wyszukiwania zestawów** pole, aby filtrować zestawy i ułatwiają wybierz żądany odwołań.  
  
5.  Zaznacz pole wyboru obok **elementu System.Activities** z **wyniki wyszukiwania** listy.  
  
6.  Typ **serializacji** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Runtime.Serialization** z **wyniki wyszukiwania**  listy.  
  
7.  Typ **System.Xaml** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Xaml** z **wyniki wyszukiwania** listy.  
  
8.  Kliknij przycisk **OK** zamknąć **Menedżera odwołań** i dodać odwołań.  
  
9. Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.Statements  
    Imports System.Xaml  
    Imports System.Reflection  
    Imports System.IO  
    Imports System.Activities.XamlIntegration  
    Imports System.Activities.DynamicUpdate  
    Imports System.Runtime.Serialization  
    Imports Microsoft.VisualBasic.Activities  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.IO;  
    using System.Xaml;  
    using System.Reflection;  
    using System.Activities.XamlIntegration;  
    using System.Activities.DynamicUpdate;  
    using System.Runtime.Serialization;  
    using Microsoft.CSharp.Activities;  
    ```  
  
10. Dodaj następujące dwa parametry elementy członkowskie `Program` klasy (lub `Module1`).  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. Dodaj następujące `StartUpdate` metodę `Program` klasy (lub `Module1`). Ta metoda Ładuje określony xaml definicji przepływu pracy do `ActivityBuilder`, a następnie wywołuje `DynamicUpdate.PrepareForUpdate`. `PrepareForUpdate`Tworzy kopię pliku definicji przepływu pracy wewnątrz `ActivityBuilder`. Po zmodyfikowaniu definicji przepływu pracy tej kopii jest używana wraz z definicji przepływu pracy zmodyfikowane do tworzenia mapy aktualizacji.  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
        'the same project as the XAML. When loading XAML if the currently executing   
        'assembly is not the same assembly that was referred to as "local" in the XAML  
        'LocalAssembly must be set to the assembly containing the artifacts.  
        'Assembly.LoadFile requires an absolute path so convert this relative path  
        'to an absolute path.  
        readerSettings.LocalAssembly = Assembly.LoadFile(  
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
  
        Dim fullPath As String = Path.Combine(definitionPath, name)  
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)  
  
        'Load the workflow definition into an ActivityBuilder.  
        Dim wf As ActivityBuilder = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
  
        'PrepareForUpdate makes a copy of the workflow definition in the  
        'ActivityBuilder that is used for comparison when the update  
        'map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf)  
  
        Return wf  
    End Function  
    ```  
  
    ```csharp  
    private static ActivityBuilder StartUpdate(string name)  
    {  
        // Create the XamlXmlReaderSettings.  
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
        {  
            // In the XAML the "local" namespace referes to artifacts that come from   
            // the same project as the XAML. When loading XAML if the currently executing   
            // assembly is not the same assembly that was referred to as "local" in the XAML  
            // LocalAssembly must be set to the assembly containing the artifacts.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            LocalAssembly = Assembly.LoadFile(  
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
        };  
  
        string path = Path.Combine(definitionPath, name);  
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);  
  
        // Load the workflow definition into an ActivityBuilder.  
        ActivityBuilder wf = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
            as ActivityBuilder;  
  
        // PrepareForUpdate makes a copy of the workflow definition in the  
        // ActivityBuilder that is used for comparison when the update  
        // map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf);  
  
        return wf;  
    }  
    ```  
  
12. Następnie dodaj następujące `CreateUpdateMethod` do `Program` klasy (lub `Module1`). Tworzy mapę aktualizacja dynamiczna przez wywołanie DynamicUpdateServices.CreateUpdateMap, a następnie zapisuje mapy aktualizacji przy użyciu określonej nazwy. Ta mapa aktualizacji zawierają informacje wymagane przez środowisko wykonawcze przepływu pracy można zaktualizować wystąpienia utrwalonego przepływu pracy, która została uruchomiona z użyciem zawarte w oryginalnej definicji przepływu pracy `ActivityBuilder` tak, aby ukończy za pomocą definicji zaktualizowany przepływ pracy.  
  
    ```vb  
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)  
        'Create the UpdateMap.  
        Dim map As DynamicUpdateMap =  
            DynamicUpdateServices.CreateUpdateMap(wf)  
  
        'Serialize it to a file.  
        Dim mapFullPath As String = Path.Combine(mapPath, name)  
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)  
            sz.WriteObject(fs, map)  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)  
    {  
        // Create the UpdateMap.  
        DynamicUpdateMap map =  
            DynamicUpdateServices.CreateUpdateMap(wf);  
  
        // Serialize it to a file.  
        string path = Path.Combine(mapPath, name);  
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));  
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))  
        {  
            sz.WriteObject(fs, map);  
        }  
    }  
    ```  
  
13. Dodaj następujące `SaveUpdatedDefinition` metodę `Program` klasy (lub `Module1`). Taka metoda ogranicza definicji zaktualizowany przepływ pracy po utworzeniu Mapa aktualizacji.  
  
    ```vb  
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)  
        Dim xamlPath As String = Path.Combine(definitionPath, name)  
        Dim sw As StreamWriter = File.CreateText(xamlPath)  
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(  
            New XamlXmlWriter(sw, New XamlSchemaContext()))  
        XamlServices.Save(xw, wf)  
        sw.Close()  
    End Sub  
    ```  
  
    ```csharp  
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)  
    {  
        string xamlPath = Path.Combine(definitionPath, name);  
        StreamWriter sw = File.CreateText(xamlPath);  
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(  
            new XamlXmlWriter(sw, new XamlSchemaContext()));  
        XamlServices.Save(xw, wf);  
        sw.Close();  
    }  
    ```  
  
###  <a name="BKMK_StateMachine"></a>Aby zaktualizować StateMachineNumberGuessWorkflow  
  
1.  Dodaj `CreateStateMachineUpdateMap` do `Program` klasy (lub `Module1`).  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  Wywoływania `StartUpdate` , a następnie pobrać odwołanie do elementu głównego `StateMachine` działania przepływu pracy.  
  
    ```vb  
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
    'Get a reference to the root StateMachine activity.  
    Dim sm As StateMachine = wf.Implementation  
    ```  
  
    ```csharp  
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
    // Get a reference to the root StateMachine activity.  
    StateMachine sm = wf.Implementation as StateMachine;  
    ```  
  
3.  Następnie zaktualizuj wyrażenia dwóch `WriteLine` działań, które stwierdzenie, czy wynik użytkownika jest za duży lub za mały, aby były one zgodne aktualizacje wprowadzone w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
    ```vb  
    'Update the Text of the two WriteLine activities that write the  
    'results of the user's guess. They are contained in the workflow as the  
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
    'Update the "too low" message.  
    Dim tooLow As WriteLine = guessLow.Then  
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
    'Update the "too high" message.  
    Dim tooHigh As WriteLine = guessLow.Else  
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
    ```  
  
    ```csharp  
    // Update the Text of the two WriteLine activities that write the  
    // results of the user's guess. They are contained in the workflow as the  
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    If guessLow = sm.States[1].Transitions[1].Action as If;  
  
    // Update the "too low" message.  
    WriteLine tooLow = guessLow.Then as WriteLine;  
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
    // Update the "too high" message.  
    WriteLine tooHigh = guessLow.Else as WriteLine;  
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
    ```  
  
4.  Następnie dodaj nowe `WriteLine` działania, w którym jest wyświetlany komunikat zamknięcia.  
  
    ```vb  
    'Create the new WriteLine that displays the closing message.  
    Dim wl As New WriteLine() With  
    {  
        .Text = New VisualBasicValue(Of String) _  
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
    }  
  
    'Add it as the Action for the Guess Correct transition. The Guess Correct  
    'transition is the first transition of States[1]. The transitions are listed  
    'at the bottom of the State activity designer.  
    sm.States(1).Transitions(0).Action = wl  
    ```  
  
    ```csharp  
    // Create the new WriteLine that displays the closing message.  
    WriteLine wl = new WriteLine  
    {  
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
    };  
  
    // Add it as the Action for the Guess Correct transition. The Guess Correct  
    // transition is the first transition of States[1]. The transitions are listed  
    // at the bottom of the State activity designer.  
    sm.States[1].Transitions[0].Action = wl;  
    ```  
  
5.  Po zaktualizowaniu przepływu pracy Wywołaj `CreateUpdateMaps` i `SaveUpdatedDefinition`. `CreateUpdateMaps`Tworzy i zapisuje `DynamicUpdateMap`, i `SaveUpdatedDefinition` zapisuje definicji zaktualizowany przepływ pracy.  
  
    ```vb  
    'Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
    'Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    ```  
  
    ```csharp  
    // Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
    // Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    ```  
  
     Poniższy przykład jest wypełniony `CreateStateMachineUpdateMap` metody.  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root StateMachine activity.  
        Dim sm As StateMachine = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
        'Update the "too low" message.  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Add it as the Action for the Guess Correct transition. The Guess Correct  
        'transition is the first transition of States[1]. The transitions are listed  
        'at the bottom of the State activity designer.  
        sm.States(1).Transitions(0).Action = wl  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root StateMachine activity.  
        StateMachine sm = wf.Implementation as StateMachine;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        If guessLow = sm.States[1].Transitions[1].Action as If;  
  
        // Update the "too low" message.  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Create the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Add it as the Action for the Guess Correct transition. The Guess Correct  
        // transition is the first transition of States[1]. The transitions are listed  
        // at the bottom of the State activity designer.  
        sm.States[1].Transitions[0].Action = wl;  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_Flowchart"></a>Aby zaktualizować FlowchartNumberGuessWorkflow  
  
1.  Dodaj następujące `CreateFlowchartUpdateMethod` do `Program` klasy (lub `Module1`). Ta metoda jest podobna do `CreateStateMachineUpdateMap`. Rozpoczyna się wywołanie `StartUpdate`, aktualizacje definicji przepływu pracy schemat blokowy i zakończeniu zapisując mapy aktualizacji, jak i definicja zaktualizowany przepływ pracy.  
  
    ```vb  
    Private Sub CreateFlowchartUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root Flowchart activity.  
        Dim fc As Flowchart = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'True and False action of the "Guess < Target" FlowDecision, which is  
        'Nodes[4].  
        Dim guessLow As FlowDecision = fc.Nodes(4)  
  
        'Update the "too low" message.  
        Dim trueStep As FlowStep = guessLow.True  
        Dim tooLow As WriteLine = trueStep.Action  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim falseStep As FlowStep = guessLow.False  
        Dim tooHigh As WriteLine = falseStep.Action  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Create a FlowStep to hold the WriteLine.  
        Dim closingStep As New FlowStep() With  
        {  
            .Action = wl  
        }  
  
        'Add this new FlowStep to the True action of the   
        '"Guess = Guess" FlowDecision  
        Dim guessCorrect As FlowDecision = fc.Nodes(3)  
        guessCorrect.True = closingStep  
  
        'Add the new FlowStep to the Nodes collection.  
        'If closingStep was replacing an existing node then  
        'we would need to remove that Step from the collection.  
        'In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateFlowchartUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root Flowchart activity.  
        Flowchart fc = wf.Implementation as Flowchart;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // True and False action of the "Guess < Target" FlowDecision, which is  
        // Nodes[4].  
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;  
  
        // Update the "too low" message.  
        FlowStep trueStep = guessLow.True as FlowStep;  
        WriteLine tooLow = trueStep.Action as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        FlowStep falseStep = guessLow.False as FlowStep;  
        WriteLine tooHigh = falseStep.Action as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Create a FlowStep to hold the WriteLine.  
        FlowStep closingStep = new FlowStep  
        {  
            Action = wl  
        };  
  
        // Add this new FlowStep to the True action of the   
        // "Guess == Guess" FlowDecision  
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;  
        guessCorrect.True = closingStep;  
  
        // Add the new FlowStep to the Nodes collection.  
        // If closingStep was replacing an existing node then  
        // we would need to remove that Step from the collection.  
        // In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");  
  
        //  Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_Sequential"></a>Aby zaktualizować SequentialNumberGuessWorkflow  
  
1.  Dodaj następujące `CreateSequentialUpdateMethod` do `Program` klasy (lub `Module1`). Ta metoda jest podobna do innych metod. Rozpoczyna się wywołanie `StartUpdate`, aktualizacje definicji sekwencyjnego przepływu pracy i zakończeniu zapisując mapy aktualizacji, jak i definicja zaktualizowany przepływ pracy.  
  
    ```vb  
    Private Sub CreateSequentialUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root activity in the workflow.  
        Dim rootSequence As Sequence = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the "Guess < Target" If activity.  
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)  
        Dim gameBody As Sequence = gameLoop.Body  
        Dim guessCorrect As Statements.If = gameBody.Activities(2)  
        Dim guessLow As Statements.If = guessCorrect.Then  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateSequentialUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root activity in the workflow.  
        Sequence rootSequence = wf.Implementation as Sequence;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the "Guess < Target" If activity.  
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;  
        Sequence gameBody = gameLoop.Body as Sequence;  
        If guessCorrect = gameBody.Activities[2] as If;  
        If guessLow = guessCorrect.Then as If;  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_CreateUpdateMaps"></a>Aby skompilować i uruchomić aplikację CreateUpdateMaps  
  
1.  Aktualizacja `Main` — metoda i dodaj następujące wywołania trzy metody. Te metody są dodawane w poniższych sekcjach. Każda metoda aktualizacji odpowiedniego przepływu pracy numer argumentu i tworzy `DynamicUpdateMap` opisujący aktualizacji.  
  
    ```vb  
    Sub Main()  
        'Create the update maps for the changes needed to the v1 activities  
        'so they match the v2 activities.  
        CreateSequentialUpdateMap()  
        CreateFlowchartUpdateMap()  
        CreateStateMachineUpdateMap()  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the update maps for the changes needed to the v1 activities  
        // so they match the v2 activities.  
        CreateSequentialUpdateMap();  
        CreateFlowchartUpdateMap();  
        CreateStateMachineUpdateMap();  
    }  
    ```  
  
2.  Kliknij prawym przyciskiem myszy **CreateUpdateMaps** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.  
  
3.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania, a następnie klawisz CTRL + F5, aby uruchomić `CreateUpdateMaps` aplikacji.  
  
    > [!NOTE]
    >  `CreateUpdateMaps` Aplikacji nie są wyświetlane wszystkie informacje o stanie podczas uruchamiania, ale dostępne **NumberGuessWorkflowActivities_du** folderu i **PreviousVersions** folderu zostanie wyświetlony pliki definicji zaktualizowany przepływ pracy i mapowania aktualizacji.  
  
     Po mapy aktualizacji są tworzone i definicji przepływu pracy, zaktualizować, następnym krokiem jest zaktualizowany przepływ pracy zestawu zawierającego aktualizacji definicji kompilacji.  
  
###  <a name="BKMK_BuildAssembly"></a>Tworzenie zestawu zaktualizowany przepływ pracy  
  
1.  Otwórz drugie wystąpienie parametru [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Wybierz **Otwórz**, **projektu/rozwiązania** z **pliku** menu.  
  
3.  Przejdź do **NumberGuessWorkflowActivities_du** folder utworzony w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), wybierz pozycję **NumberGuessWorkflowActivities.csproj**  (lub **vbproj**) i kliknij przycisk **Otwórz**.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **SequentialNumberGuessWorkflow.xaml** i wybierz polecenie **wykluczyć z projektu**. Tak samo postąpić w **FlowchartNumberGuessWorkflow.xaml** i **StateMachineNumberGuessWorkflow.xaml**. Ten krok powoduje usunięcie poprzednich wersji definicji przepływu pracy z projektu.  
  
5.  Wybierz **Dodaj istniejący element** z **projektu** menu.  
  
6.  Przejdź do **NumberGuessWorkflowActivities_du** folder utworzony w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
7.  Wybierz **plików XAML (\*.xaml;\*. xoml)** z **pliki typu** listy rozwijanej.  
  
8.  Wybierz **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, i **StateMachineNumberGuessWorkflow_du.xaml** i kliknij przycisk  **Dodaj**.  
  
    > [!NOTE]
    >  CTRL + kliknięcie, aby zaznaczyć wiele elementów naraz.  
  
     Ten krok powoduje dodanie zaktualizowanych wersji definicji przepływu pracy do projektu.  
  
9. Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany.  
  
10. Wybierz **Zamknij rozwiązanie** z **pliku** menu. Plik rozwiązania dla projektu nie jest wymagana, więc klikamy **nr** zamknąć [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] bez zapisywania pliku rozwiązania. Wybierz **zakończenia** z **pliku** menu, aby zamknąć [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].  
  
11. Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowActivities_du\bin\Debug** folder (lub **bin\Release** w zależności od ustawienia projektu).  
  
12. Zmień nazwę **NumberGuessWorkflowActivities.dll** do **NumberGuessWorkflowActivities_v15.dll**i skopiuj go do **PreviousVersions** folder utworzony w [Porady: hostowanie wielu wersji przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a>Aby zaktualizować WorkflowVersionMap do nowych wersji  
  
1.  Wrócić do początkowej wystąpienie [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.  
  
3.  Dodaj trzy nowe tożsamości przepływu pracy poniżej sześciu istniejących deklaracji tożsamości przepływu pracy. W tym samouczku `1.5.0.0` jest używany jako `WorkflowIdentity.Version` tożsamości aktualizacji dynamicznej. Te nowe `v15` tożsamości będą używane w przepływie pracy zawierają definicje poprawne przepływu pracy dla wystąpień aktualizowany dynamicznie utrwalonych przepływów pracy.  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
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
  
    // v1.5 (Dynamic Update) identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
    ```  
  
4.  Dodaj następujący kod na końcu konstruktora. Ten kod inicjuje tożsamości przepływu pracy aktualizacji dynamicznej, ładuje odpowiedniej definicji przepływu pracy i dodaje je do słownika wersji przepływu pracy.  
  
    ```vb  
    'Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    'Add the dynamic update workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v15 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    // Add the dynamic update workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v15 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     Poniższy przykład jest wypełniony `WorkflowVersionMap` klasy.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        'v1.5 (Dynamimc Update) identities.  
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
  
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
  
            'Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            'Add the dynamic update workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v15 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
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
  
        // v1.5 (Dynamic Update) identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
  
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
  
            // Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            // Add the dynamic update workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v15 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
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
  
5.  Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany.  
  
###  <a name="BKMK_ApplyUpdate"></a>Aby zastosować aktualizacje dynamiczne  
  
1.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.  
  
2.  W **zainstalowana** węzła, wybierz opcję **Visual C#**, **Windows** (lub **Visual Basic**, **Windows**).  
  
    > [!NOTE]
    >  W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.  
  
     Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Wybierz **aplikacji konsoli** z **Windows** listy. Typ **ApplyDynamicUpdate** do **nazwa** polu i kliknij przycisk **OK**.  
  
3.  Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**.  
  
4.  Kliknij przycisk **rozwiązania** i zaznacz pole wyboru obok pozycji **NumberGuessWorkflowHost**. To odwołanie jest wymagane, aby `ApplyDynamicUpdate` można użyć `NumberGuessWorkflowHost.WorkflowVersionMap` klasy.  
  
5.  Wybierz **Framework** z **zestawy** w węźle **Dodaj odwołanie** listy. Typ **elementu System.Activities** do **wyszukiwania zestawów** pole. Spowoduje to Filtrowanie zestawów i ułatwiają wybierz żądane odwołania.  
  
6.  Zaznacz pole wyboru obok **elementu System.Activities** z **wyniki wyszukiwania** listy.  
  
7.  Typ **serializacji** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Runtime.Serialization** z **wyniki wyszukiwania**  listy.  
  
8.  Typ **DurableInstancing** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Activities.DurableInstancing** i  **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy.  
  
9. Kliknij przycisk **OK** zamknąć **Menedżera odwołań** i dodać odwołań.  
  
10. Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w Eksploratorze rozwiązań i wybierz polecenie **Dodaj**, **klasy**. Typ `DynamicUpdateInfo` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
11. Dodaj następujące dwa elementy członkowskie `DynamicUpdateInfo` klasy. Poniższy przykład jest wypełniony `DynamicUpdateInfo` klasy. Ta klasa zawiera informacje na temat mapy aktualizacji i nowy identyfikator przepływu pracy używane po zaktualizowaniu wystąpienia przepływu pracy.  
  
    ```vb  
    Public Class DynamicUpdateInfo  
        Public updateMap As DynamicUpdateMap  
        Public newIdentity As WorkflowIdentity  
    End Class  
    ```  
  
    ```csharp  
    class DynamicUpdateInfo  
    {  
        public DynamicUpdateMap updateMap;  
        public WorkflowIdentity newIdentity;  
    }  
    ```  
  
12. Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. Kliknij dwukrotnie **Program.cs** (lub **Module1.vb**) w Eksploratorze rozwiązań.  
  
14. Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports NumberGuessWorkflowHost  
    Imports System.Data.SqlClient  
    Imports System.Activities.DynamicUpdate  
    Imports System.IO  
    Imports System.Runtime.Serialization  
    Imports System.Activities  
    Imports System.Activities.DurableInstancing  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowHost;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    using System.IO;  
    using System.Runtime.Serialization;  
    using System.Activities.DurableInstancing;  
    ```  
  
15. Dodaj następujący element członkowski ciąg połączenia do `Program` klasy (lub `Module1`).  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być różne.  
  
16. Dodaj następujące `GetIDs` metodę `Program` klasy (lub `Module1`). Ta metoda zwraca listę identyfikatorów wystąpienia utrwalonego przepływu pracy.  
  
    ```vb  
    Function GetIds() As IList(Of Guid)  
        Dim Ids As New List(Of Guid)  
        Dim localCmd = _  
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")  
        Using localCon = New SqlConnection(connectionString)  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
                While reader.Read()  
                    'Get the InstanceId of the persisted Workflow  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
  
                    'Add it to the list.  
                    Ids.Add(id)  
                End While  
            End Using  
        End Using  
  
        Return Ids  
    End Function  
    ```  
  
    ```csharp  
    static IList<Guid> GetIds()  
    {  
        List<Guid> Ids = new List<Guid>();  
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");  
        using (SqlConnection localCon = new SqlConnection(connectionString))  
        {  
            SqlCommand cmd = localCon.CreateCommand();  
            cmd.CommandText = localCmd;  
            localCon.Open();  
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
            {  
                while (reader.Read())  
                {  
                    // Get the InstanceId of the persisted Workflow  
                    Guid id = Guid.Parse(reader[0].ToString());  
  
                    // Add it to the list.  
                    Ids.Add(id);  
                }  
            }  
        }  
  
        return Ids;  
    }  
    ```  
  
17. Dodaj następujące `LoadMap` metodę `Program` klasy (lub `Module1`). Ta metoda tworzy słownik, który mapuje `v1` tożsamości mapy aktualizacji przepływu pracy i nowej tożsamości przepływu pracy używane do aktualizowania odpowiadającego utrwalone wystąpienia przepływu pracy.  
  
    ```vb  
    Function LoadMap(mapName As String) As DynamicUpdateMap  
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)  
  
        Dim map As DynamicUpdateMap  
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)  
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
            Dim updateMap = serializer.ReadObject(fs)  
            If updateMap Is Nothing Then  
                Throw New ApplicationException("DynamicUpdateMap is null.")  
            End If  
  
            map = updateMap  
        End Using  
  
        Return map  
    End Function  
    ```  
  
    ```csharp  
    static DynamicUpdateMap LoadMap(string mapName)  
    {  
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);  
  
        DynamicUpdateMap map;  
        using (FileStream fs = File.Open(path, FileMode.Open))  
        {  
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
            object updateMap = serializer.ReadObject(fs);  
            if (updateMap == null)  
            {  
                throw new ApplicationException("DynamicUpdateMap is null.");  
            }  
  
            map = updateMap as DynamicUpdateMap;  
        }  
  
        return map;  
    }  
    ```  
  
18. Dodaj następujące `LoadMaps` metodę `Program` klasy (lub `Module1`). Ta metoda ładuje trzy mapy aktualizacji i tworzy słownik mapujący `v1` tożsamości mapy aktualizacji przepływu pracy.  
  
    ```vb  
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)  
        'There are 3 update maps to describe the changes to update v1 workflows,  
        'one for reach of the 3 workflow types in the tutorial.  
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()  
  
        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")  
        Dim sequentialInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = sequentialMap,  
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)  
  
        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")  
        Dim stateInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = stateMap,  
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)  
  
        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")  
        Dim flowchartInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = flowchartMap,  
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)  
  
        Return maps  
    End Function  
    ```  
  
    ```csharp  
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()  
    {  
        // There are 3 update maps to describe the changes to update v1 workflows,  
        // one for reach of the 3 workflow types in the tutorial.  
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =  
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();  
  
        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");  
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo  
        {  
            updateMap = sequentialMap,  
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);  
  
        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");  
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo  
        {  
            updateMap = stateMap,  
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);  
  
        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");  
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo  
        {  
            updateMap = flowchartMap,  
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);  
  
        return maps;              
    }  
    ```  
  
19. Dodaj następujący kod do `Main`. Ten kod iteruje utrwalonych przepływów pracy wystąpień i sprawdza, czy każdy `WorkflowIdentity`. Jeśli `WorkflowIdentity` mapuje `v1` wystąpienia przepływu pracy `WorkflowApplication` skonfigurowano definicji zaktualizowany przepływ pracy i tożsamością zaktualizowany przepływ pracy. Następnie `WorkflowApplication.Load` nosi nazwę wystąpienia i Mapa aktualizacji, która ma zastosowanie mapy aktualizacji dynamicznej. Po zastosowaniu aktualizacji zaktualizowane wystąpienie jest utrwalone w wyniku wywołania `Unload`.  
  
    ```vb  
    Dim store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()  
  
    For Each id As Guid In GetIds()  
        'Get a proxy to the instance.   
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)  
  
        'Only update v1 workflows.  
        If Not instance.DefinitionIdentity Is Nothing AndAlso _  
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then  
  
            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)  
  
            'Associate the persisted WorkflowApplicationInstance with  
            'a WorkflowApplication that is configured with the updated  
            'definition and updated WorkflowIdentity.  
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)  
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)  
  
            'Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap)  
  
            'Persist the updated instance.  
            wfApp.Unload()  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity)  
        Else  
            'Not updating this instance, so unload it.  
            instance.Abandon()  
        End If  
    Next  
    ```  
  
    ```csharp  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();  
  
    foreach (Guid id in GetIds())  
    {  
        // Get a proxy to the instance.   
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(id, store);  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);  
  
        // Only update v1 workflows.  
        if (instance.DefinitionIdentity != null &&  
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))  
        {  
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];  
  
            // Associate the persisted WorkflowApplicationInstance with  
            // a WorkflowApplication that is configured with the updated  
            // definition and updated WorkflowIdentity.  
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);  
            WorkflowApplication wfApp =  
                new WorkflowApplication(wf, info.newIdentity);  
  
            // Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap);  
  
            // Persist the updated instance.  
            wfApp.Unload();  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity);  
        }  
        else  
        {  
            // Not updating this instance, so unload it.  
            instance.Abandon();  
        }  
    }  
    ```  
  
20. Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.  
  
21. Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania, a następnie naciśnij kombinację klawiszy CTRL + F5, aby uruchomić `ApplyDynamicUpdate` aplikacji i zaktualizować wystąpień utrwalonych przepływów pracy. Powinny pojawić się dane wyjściowe podobne do następującego. Przepływy pracy w wersji 1.0.0.0 są zaktualizowany do wersji 1.5.0.0, gdy wersji 2.0.0.0 przepływy pracy nie zostały zaktualizowane.  
  
 **Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0**  
**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0**   
**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0**   
**Sprawdzanie: StateMachineNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Sprawdzanie: StateMachineNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Sprawdzanie: FlowchartNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Sprawdzanie: FlowchartNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Sprawdzanie: SequentialNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Sprawdzanie: SequentialNumberGuessWorkflow; Wersja = 2.0.0.0**   
**Naciśnij dowolny klawisz, aby kontynuować...**  
  
###  <a name="BKMK_BuildAndRun"></a>Aby uruchomić aplikację zaktualizowane przepływów pracy  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.  
  
2.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
3.  Kliknij przycisk **nowej gry** można uruchomić nowego przepływu pracy i Zapisz informacje o wersji poniżej okno stanu, która wskazuje przepływu pracy jest `v2` przepływu pracy.  
  
4.  Wybierz jedną z `v1` przepływy pracy na początku [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tematu. Należy pamiętać, że informacje o wersji w obszarze okno stanu wskazuje, że przepływ pracy jest wersja **1.5.0.0** przepływu pracy. Należy pamiętać, że nie ma żadnych informacji wskazane o poprzednich prób innych niż czy był zbyt duży lub za mały.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**Twoje wynik jest za mała.**  
  
5.  Zanotuj `InstanceId` , a następnie wprowadź liczbę prób do momentu ukończenia przepływu pracy. Okno stanu wyświetla informacje o zawartości argumentu, ponieważ `WriteLine` działania zostały zaktualizowane przez aktualizację dynamiczną.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**Twoje wynik jest za mała.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**5 jest zbyt niski.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**7 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**Gratulacje, odgadnąć numer w włącza 4.**  
  
6.  Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Ukończono przepływ pracy. Jeśli nie wprowadzono uwagę `InstanceId` można zidentyfikować przy użyciu pliku śledzenia poprawne **Data modyfikacji** informacji w Eksploratorze Windows. Informacje o śledzeniu ostatni wiersz zawiera dane wyjściowe nowo dodanego `WriteLine` działania.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**Twoje wynik jest za mała.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**5 jest zbyt niski.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**7 jest zbyt duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**6 jest poprawna. Odgadnięto go w włącza 4.**  
  
###  <a name="BKMK_StartPreviousVersions"></a>Aby włączyć uruchamianie poprzednich wersji przepływów pracy  
 Po uruchomieniu poza przepływy pracy do aktualizacji, można zmodyfikować `NumberGuessWorkflowHost` aplikacji, aby umożliwić uruchamianie poprzednich wersji przepływów pracy.  
  
1.  Kliknij dwukrotnie **WorkflowHostForm** w **Eksploratora rozwiązań**i wybierz **WorkflowType** pola kombi.  
  
2.  W **właściwości** wybierz **elementów** właściwości i kliknij przycisk wielokropka, aby edytować **elementów** kolekcji.  
  
3.  Dodaj następujące trzy elementy do kolekcji.  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     Wypełniony `Items` kolekcji będą mieć sześć elementów.  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  Kliknij dwukrotnie **WorkflowHostForm** w **Eksploratora rozwiązań**i wybierz **kod widoku**.  
  
5.  Dodaj trzy nowych przypadków `switch` (lub `Select Case`) instrukcji w `NewGame_Click` obsługi do mapowania nowych elementów w **WorkflowType** pola kombi do dopasowania tożsamości przepływu pracy.  
  
    ```vb  
    Case "SequentialNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
    Case "StateMachineNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
    Case "FlowchartNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    ```  
  
    ```csharp  
    case "SequentialNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
        break;  
  
    case "StateMachineNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
        break;  
  
    case "FlowchartNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
        break;  
    ```  
  
     Poniższy przykład zawiera pełną `switch` (lub `Select Case`) instrukcji.  
  
    ```vb  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
  
        Case "SequentialNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
        Case "StateMachineNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
        Case "FlowchartNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    End Select  
    ```  
  
    ```csharp  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
  
        case "SequentialNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
            break;  
  
        case "StateMachineNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
            break;  
  
        case "FlowchartNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
            break;  
    };  
    ```  
  
6.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Można teraz uruchomić `v1` wersji przepływu pracy, jak również w bieżącej wersji. Aby dynamicznie aktualizować te nowe wystąpienia, należy uruchomić **ApplyDynamicUpdate** aplikacji.
