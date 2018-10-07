---
title: 'Porady: uruchamianie przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 3b2081cee307e80396a9af4b9cfdbdea001113e6
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836949"
---
# <a name="how-to-run-a-workflow"></a>Porady: uruchamianie przepływu pracy
W tym temacie jest kontynuacją samouczka Windows Workflow Foundation wprowadzenie i w tym artykule omówiono sposób tworzenia hosta przepływu pracy i uruchomić przepływ pracy zdefiniowane w poprzednim [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tematu.

> [!NOTE]
>  Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach. Aby zakończyć w tym temacie, najpierw musisz zakończyć [instrukcje: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) i [jak: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).

> [!NOTE]
>  Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Aby utworzyć projekt hosta przepływu pracy  
  
1.  Otwórz rozwiązanie z poprzedniego [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu przy użyciu programu Visual Studio 2012.  
  
2.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.

3.  W **zainstalowane** węzeł **Visual C#**, **przepływu pracy** (lub **języka Visual Basic**, **przepływu pracy**).

    > [!NOTE]
    >  Zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **języka Visual Basic** węzła może znajdować się w **inne języki** w węźle **zainstalowane** węzła.

     Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Wybierz **Aplikacja konsoli przepływu pracy** z **przepływu pracy** listy. Typ `NumberGuessWorkflowHost` do **nazwa** pole, a następnie kliknij przycisk **OK**. Spowoduje to utworzenie aplikacji przepływu pracy starter z podstawowym przepływem pracy, obsługa hostingu. Ten podstawowy kod hostingu zostanie zmodyfikowana i używane do uruchamiania aplikacji przepływu pracy.

4.  Kliknij prawym przyciskiem myszy nowo dodanych **NumberGuessWorkflowHost** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**. Wybierz **rozwiązania** z **Dodaj odwołanie** listy, zaznacz pole wyboru obok pozycji **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK** .

5.  Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**. Kliknij przycisk **OK** o potwierdzenie.

### <a name="to-modify-the-workflow-hosting-code"></a>Aby zmodyfikować przepływ pracy, kod hostingu

1.  Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** Aby wyświetlić kod.

    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.

     Ponieważ ten projekt został utworzony przy użyciu **Aplikacja konsoli przepływu pracy** szablonu, **Program.cs** lub **Module1.vb** zawiera następujące hostingu podstawowy przepływ pracy Kod.

    ```vb
    ' Create and cache the workflow definition
    Activity workflow1 = new Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Ten wygenerowany kod hostingu, używa <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> zapewnia prostą metodę do wywołania przepływu pracy tak, jakby były wywołania metody i mogą służyć tylko w przypadku przepływów pracy, które nie korzystają z trwałości. <xref:System.Activities.WorkflowApplication> udostępnia bogatszy model do wykonywania przepływów pracy, które zawierają powiadomienie o zdarzenia cyklu życia, kontrola wykonywania, wznowienie zakładki i trwałości. W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> jest używany do hostowania przepływu pracy. Dodaj następujący kod `using` lub **Importy** instrukcji na górze **Program.cs** lub **Module1.vb** poniżej istniejącego **przy użyciu** lub **Importy** instrukcji.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Zamień wiersze kodu, które używają <xref:System.Activities.WorkflowInvoker> za pomocą następujących basic <xref:System.Activities.WorkflowApplication> kod hostingu. Ten przykładowy kod hostingu przedstawiono podstawowe kroki obsługi i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji do pomyślnego uruchomienia przepływu pracy z tego tematu. W poniższych krokach ten podstawowy kod jest modyfikowany, a dodatkowe funkcje zostaną dodane do czasu zakończenia aplikacji.

    > [!NOTE]
    >  Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.

     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Ten kod tworzy <xref:System.Activities.WorkflowApplication>, subskrybuje trzy zdarzenia cyklu życia przepływu pracy, przepływ pracy zaczyna się od wywołania <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie czeka na przepływ pracy zakończy się. Po ukończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiony, host zakończeniu aplikacji.

### <a name="to-set-input-arguments-of-a-workflow"></a>Aby ustawić argumentów wejściowych przepływu pracy

1.  Dodaj następującą instrukcję w górnej części **Program.cs** lub **Module1.vb** poniżej istniejącego `using` lub `Imports` instrukcji.

     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2.  Zastąp wiersz kodu, który tworzy nowy <xref:System.Activities.WorkflowApplication> następującym kodem, które tworzy i przekazuje słownik parametrów do przepływu pracy, podczas jego tworzenia.

    > [!NOTE]
    >  Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.

     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Ten słownik zawiera jeden element z kluczem `MaxNumber`. Klucze w słowniku wejściowe odpowiadają wprowadzanie argumentów działania głównego przepływu pracy. `MaxNumber` jest używany przez przepływ pracy do określenia górną granicę losowo generowany numer.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Aby pobrać argumenty danych wyjściowych przepływu pracy

1.  Modyfikowanie <xref:System.Activities.WorkflowApplication.Completed%2A> program obsługi, aby pobrać i wyświetlić liczbę włącza używane przez przepływ pracy.

     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Wznowienie zakładki

1.  Dodaj następujący kod w górnej części `Main` metoda zaraz po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.

     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2.  Dodaj następujący kod <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi tuż poniżej istniejącego trzy przepływu pracy cyklu życia obsługi w `Main`.

     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Każdorazowo przepływu pracy staje się nieaktywna, oczekiwanie na następnym razem ten program obsługi jest wywoływany i `idleAction` <xref:System.Threading.AutoResetEvent> jest ustawiona. Kod w następnym kroku używa `idleEvent` i `syncEvent` czy czeka na następny wynik przepływu pracy, czy zostało zakończone.

    > [!NOTE]
    >  W tym przykładzie korzysta z resetowaniem automatycznym zdarzenia w aplikacji hosta <xref:System.Activities.WorkflowApplication.Completed%2A> i <xref:System.Activities.WorkflowApplication.Idle%2A> programów obsługi, aby zapewnić synchronizację aplikacji hosta z postęp przepływu pracy. Nie jest konieczne do blokowania i poczekać na przepływ pracy przejdzie w stan bezczynności przed wznowieniem zakładki, ale w tym przykładzie zdarzenia synchronizacji są wymagane tak przyjmującym wie, czy przepływu pracy zostało ukończone lub czy oczekuje na więcej danych wejściowych użytkownika za pomocą <xref:System.Activities.Bookmark>. Aby uzyskać więcej informacji, zobacz [zakładki](../../../docs/framework/windows-workflow-foundation/bookmarks.md).

3.  Usuń wywołanie funkcji `WaitOne`i Zastąp kod w celu zbierania danych wejściowych od użytkownika i Wznów <xref:System.Activities.Bookmark>.

     Usuń następujący wiersz kodu.

     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Zastąp go poniższym przykładzie.

     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

##  <a name="BKMK_ToRunTheApplication"></a> Aby skompilować i uruchomić aplikację

1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.

2.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Próby odgadnięcia numer w tak małą włącza, jak to możliwe.

     Aby wypróbować aplikację przy użyciu jednego z innymi stylami przepływu pracy, należy zastąpić `Workflow1` w kodzie, który tworzy <xref:System.Activities.WorkflowApplication> z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od stylu przepływu pracy użytkowników.

     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Instrukcje dotyczące sposobu dodawania trwałości do poziomu aplikacji przepływu pracy, zobacz następny temat [porady: tworzenie i uruchamianie długiego uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia kompletny kod dla `Main` metody.

> [!NOTE]
>  Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.

 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programowanie w programie Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)
- [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [Instrukcje: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)
- [Oczekiwanie na dane wejściowe w przepływie pracy](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)
- [Hostowanie przepływów pracy](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)