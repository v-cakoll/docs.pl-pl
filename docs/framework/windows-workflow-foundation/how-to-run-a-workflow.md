---
title: 'Instrukcje: Uruchamianie przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 3badda7afeb25b44b0de574f97452d05efe75bfc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962286"
---
# <a name="how-to-run-a-workflow"></a>Instrukcje: Uruchamianie przepływu pracy
Ten temat jest kontynuacją samouczka Windows Workflow Foundation wprowadzenie i zawiera opis sposobu tworzenia hosta przepływu pracy i uruchamiania przepływu pracy zdefiniowanego w poprzednich [procedurach: Utwórz temat przepływu](how-to-create-a-workflow.md) pracy.

> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md) i [instrukcje: Utwórz przepływ pracy](how-to-create-a-workflow.md).

> [!NOTE]
> Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Aby utworzyć projekt hosta przepływu pracy  
  
1. Otwórz rozwiązanie z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) przy użyciu programu Visual Studio 2012.  
  
2. Kliknij prawym przyciskiem myszy rozwiązanie **WF45GettingStartedTutorial** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **Nowy projekt**.  
  
    > [!TIP]
    >  Jeśli okno **Eksplorator rozwiązań** nie jest wyświetlane, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .

3. W **zainstalowanym** węźle wybierz pozycję **C#Wizualizacja**, **przepływ pracy** (lub **Visual Basic**, **przepływ pracy**).

    > [!NOTE]
    > W zależności od tego, który język programowania jest skonfigurowany jako język podstawowy w programie Visual Studio, węzeł  **C# wizualizacji** lub **Visual Basic** może znajdować się w węźle **inne języki** w **zainstalowanym** węźle.

     Upewnij się, że na liście rozwijanej wersja .NET Framework została wybrana **.NET Framework 4,5** . Wybierz pozycję **aplikacja konsoli przepływu pracy** z listy **przepływów pracy** . Wpisz `NumberGuessWorkflowHost` tekst w polu **Nazwa** , a następnie kliknij przycisk **OK**. Spowoduje to utworzenie aplikacji typu "Start Workflow" z obsługą podstawowego przepływu pracy. Ten podstawowy kod hostingu jest modyfikowany i używany do uruchamiania aplikacji przepływu pracy.

4. Kliknij prawym przyciskiem myszy nowo dodany projekt **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**. Wybierz **rozwiązanie** z listy **Dodaj odwołanie** , zaznacz pole wyboru obok **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK**.

5. Kliknij prawym przyciskiem myszy **Workflow1. XAML** w **Eksplorator rozwiązań** i wybierz polecenie **Usuń**. Kliknij przycisk **OK** , aby potwierdzić.

### <a name="to-modify-the-workflow-hosting-code"></a>Aby zmodyfikować kod hostingu przepływu pracy

1. Kliknij dwukrotnie pozycję **program.cs** lub **Module1. vb** w **Eksplorator rozwiązań** , aby wyświetlić kod.

    > [!TIP]
    >  Jeśli okno **Eksplorator rozwiązań** nie jest wyświetlane, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .

     Ponieważ ten projekt został utworzony przy użyciu szablonu **aplikacji konsoli przepływu pracy** , **program.cs** lub **Module1. vb** zawiera następujący podstawowy kod hostingu przepływu pracy.

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Ten wygenerowany kod hostingu używa <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker>zapewnia prostą metodę wywoływania przepływu pracy tak, jakby była wywołaniem metody i może być używana tylko dla przepływów pracy, które nie używają trwałości. <xref:System.Activities.WorkflowApplication>zapewnia bogatszy model służący do wykonywania przepływów pracy, które obejmują powiadomienia o zdarzeniach cyklu życia, kontroli wykonywania, wznawianiu zakładek i trwałości. W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> jest on używany do hostowania przepływu pracy. `using` Dodaj następującą instrukcję lub **Imports** w górnej części **program.cs** lub **Module1. vb** poniżej istniejących instrukcji **using** lub **Imports** .

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Zastąp wiersze kodu, który jest <xref:System.Activities.WorkflowInvoker> używany z następującym podstawowym <xref:System.Activities.WorkflowApplication> kodem hostingu. Ten przykładowy kod hostingu pokazuje podstawowe kroki hostingu i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji, aby pomyślnie uruchomić przepływ pracy z tego tematu. W poniższych krokach ten kod podstawowy jest modyfikowany, a dodatkowe funkcje są dodawane do momentu ukończenia aplikacji.

    > [!NOTE]
    > Zastąp `Workflow1` w tych przykładach `FlowchartNumberGuessWorkflow`z `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od tego, który przepływ pracy został ukończony [w poprzednim kroku: Utwórz krok przepływu](how-to-create-a-workflow.md) pracy. Jeśli nie zastąpisz `Workflow1` , podczas próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Ten kod tworzy <xref:System.Activities.WorkflowApplication>, subskrybuje trzy zdarzenia cyklu życia przepływu pracy, uruchamia przepływ pracy z <xref:System.Activities.WorkflowApplication.Run%2A>wywołaniem, a następnie czeka na zakończenie przepływu pracy. Po zakończeniu <xref:System.Threading.AutoResetEvent> przepływu pracy jest ustawiony i aplikacja hosta zostanie zakończona.

### <a name="to-set-input-arguments-of-a-workflow"></a>Aby ustawić argumenty wejściowe przepływu pracy

1. Dodaj następującą instrukcję w górnej części **program.cs** lub **Module1. vb** poniżej istniejących `using` instrukcji lub `Imports` .

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Zastąp wiersz kodu, który tworzy nowy <xref:System.Activities.WorkflowApplication> , przy użyciu następującego kodu, który tworzy i przekazuje słownik parametrów do przepływu pracy podczas jego tworzenia.

    > [!NOTE]
    > Zastąp `Workflow1` w tych przykładach `FlowchartNumberGuessWorkflow`z `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od tego, który przepływ pracy został ukończony [w poprzednim kroku: Utwórz krok przepływu](how-to-create-a-workflow.md) pracy. Jeśli nie zastąpisz `Workflow1` , podczas próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Ten słownik zawiera jeden element z kluczem `MaxNumber`. Klucze w słowniku wejściowym odnoszą się do argumentów wejściowych w głównym działaniu przepływu pracy. `MaxNumber`jest używany przez przepływ pracy do określenia górnej granicy dla losowo wygenerowanego numeru.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Aby pobrać argumenty wyjściowe przepływu pracy

1. <xref:System.Activities.WorkflowApplication.Completed%2A> Zmodyfikuj procedurę obsługi, aby pobrać i wyświetlić liczbę zmian używanych przez przepływ pracy.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Aby wznowić zakładkę

1. Dodaj poniższy kod w górnej części `Main` metody tuż po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. Dodaj poniższy <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi tuż poniżej istniejących trzech programów obsługi cyklu życia przepływu pracy w programie `Main`.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Za każdym razem, gdy przepływ pracy przechodzi w stan bezczynności, czeka na kolejne odpuszczenie `idleAction` , ta procedura obsługi jest wywoływana i <xref:System.Threading.AutoResetEvent> jest ustawiona. Kod w poniższym kroku używa `idleEvent` i `syncEvent` do określenia, czy przepływ pracy oczekuje na następne odgadnięcie lub zostało zakończone.

    > [!NOTE]
    > W tym przykładzie aplikacja hosta używa zdarzeń autoresetowania w <xref:System.Activities.WorkflowApplication.Completed%2A> programach i <xref:System.Activities.WorkflowApplication.Idle%2A> , aby zsynchronizować aplikację hosta z postępem przepływu pracy. Nie jest konieczne do blokowania i poczekać na przepływ pracy przejdzie w stan bezczynności przed wznowieniem zakładki, ale w tym przykładzie zdarzenia synchronizacji są wymagane tak przyjmującym wie, czy przepływu pracy zostało ukończone lub czy oczekuje na więcej danych wejściowych użytkownika za pomocą <xref:System.Activities.Bookmark>. Aby uzyskać więcej informacji, zobacz [zakładki](bookmarks.md).

3. Usuń wywołanie do `WaitOne`i zastąp je kodem, aby zebrać dane wejściowe od użytkownika i <xref:System.Activities.Bookmark>wznowić.

     Usuń następujący wiersz kodu.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Zastąp go następującym przykładem.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a>Aby skompilować i uruchomić aplikację

1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.

2. Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić aplikację. Spróbuj złamać liczbę w możliwie najmniejszej liczbie.

     Aby wypróbować aplikację przy użyciu jednego z innych stylów przepływu pracy, `Workflow1` Zastąp kod, który <xref:System.Activities.WorkflowApplication> tworzy za `FlowchartNumberGuessWorkflow`pomocą `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od tego, który styl przepływu pracy.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Aby uzyskać instrukcje dotyczące sposobu dodawania trwałości do aplikacji przepływu pracy, zobacz następny temat, [w jaki sposób: Utwórz i Uruchom długotrwały przepływ pracy](how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Przykład
 Poniższy przykład to kompletna lista kodu dla `Main` metody.

> [!NOTE]
> Zastąp `Workflow1` w tych przykładach `FlowchartNumberGuessWorkflow`z `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od tego, który przepływ pracy został ukończony [w poprzednim kroku: Utwórz krok przepływu](how-to-create-a-workflow.md) pracy. Jeśli nie zastąpisz `Workflow1` , podczas próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programowanie w programie Windows Workflow Foundation](programming.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie przepływu pracy](how-to-create-a-workflow.md)
- [Instrukcje: Utwórz i Uruchom długotrwały przepływ pracy](how-to-create-and-run-a-long-running-workflow.md)
- [Oczekiwanie na dane wejściowe w przepływie pracy](waiting-for-input-in-a-workflow.md)
- [Hostowanie przepływów pracy](hosting-workflows.md)
