---
title: "Porady: uruchamianie przepływu pracy"
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
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5188e6786e7fde85d0e68721af6e31a47caaa441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-run-a-workflow"></a>Porady: uruchamianie przepływu pracy
W tym temacie jest to kontynuacja Samouczek Windows Workflow Foundation wprowadzenie oraz opisano, jak utworzyć hosta przepływów pracy i Uruchom przepływ pracy określone w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tematu.  
  
> [!NOTE]
>  Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów. Do ukończenia tego tematu, należy najpierw wykonać [jak: utworzyć działanie](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) i [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
> [!NOTE]
>  Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Aby utworzyć projekt hosta przepływu pracy  
  
1.  Otwórz rozwiązanie z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu przy użyciu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.  
  
3.  W **zainstalowana** węzła, wybierz opcję **Visual C#**, **przepływu pracy** (lub **Visual Basic**, **przepływu pracy**).  
  
    > [!NOTE]
    >  W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.  
  
     Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Wybierz **Aplikacja konsoli przepływu pracy** z **przepływu pracy** listy. Typ `NumberGuessWorkflowHost` do **nazwa** polu i kliknij przycisk **OK**. Spowoduje to utworzenie aplikacji przepływu pracy starter z hostingu Obsługa podstawowy przepływ pracy. Ten kod obsługi podstawowych został zmodyfikowany i używane do uruchamiania aplikacji przepływu pracy.  
  
4.  Kliknij prawym przyciskiem myszy nowo dodanego **NumberGuessWorkflowHost** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**. Wybierz **rozwiązania** z **Dodaj odwołanie** listy, zaznacz pole wyboru obok **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK** .  
  
5.  Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **usunąć**. Kliknij przycisk **OK** o potwierdzenie.  
  
### <a name="to-modify-the-workflow-hosting-code"></a>Aby zmodyfikować kod obsługującym przepływ pracy  
  
1.  Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** Aby wyświetlić kod.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.  
  
     Ponieważ ten projekt został utworzony przy użyciu **Aplikacja konsoli przepływu pracy** szablonu, **Program.cs** lub **Module1.vb** zawiera następujące hosting podstawowy przepływ pracy Kod.  
  
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
  
     To wygenerowany hostingu używa kod <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker>zapewnia prostą metodę do wywoływania przepływu pracy, tak, jakby były wywołanie metody i można używać tylko w przypadku przepływów pracy, które nie korzystają z trwałości. <xref:System.Activities.WorkflowApplication>zapewnia bardziej rozbudowane model do wykonywania przepływów pracy, które zawiera powiadomienia o zdarzenia cyklu życia, kontrola wykonywania wznowienie zakładek i trwałości. W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> służy do obsługi przepływu pracy. Dodaj następujące `using` lub **importów** instrukcji w górnej części **Program.cs** lub **Module1.vb** poniżej istniejące **przy użyciu** lub **importów** instrukcje.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     Zamień wiersze kodu, które używają <xref:System.Activities.WorkflowInvoker> za pomocą następujących basic <xref:System.Activities.WorkflowApplication> hosting kodu. Ten przykładowy kod hostowania przedstawiono podstawowe czynności w przypadku obsługi i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji do pomyślnego uruchomienia przepływu pracy z tego tematu. W poniższych krokach ten podstawowy kod jest modyfikowany, a dodatkowe funkcje zostaną dodane do czasu ukończenia aplikacji.  
  
    > [!NOTE]
    >  Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     Ten kod tworzy <xref:System.Activities.WorkflowApplication>, subskrybuje trzech zdarzeń cyklu życia przepływu pracy, uruchamia przepływ pracy z wywołaniem do <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie czeka na zakończenie przepływu pracy. Po zakończeniu przepływu pracy, <xref:System.Threading.AutoResetEvent> jest ustawiony, a host zakończeniu aplikacji.  
  
### <a name="to-set-input-arguments-of-a-workflow"></a>Aby ustawić argumenty wejściowe przepływu pracy  
  
1.  Dodaj następującą instrukcję w górnej części **Program.cs** lub **Module1.vb** poniżej istniejące `using` lub `Imports` instrukcje.  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  Zastąp wiersz kodu, która tworzy nowy <xref:System.Activities.WorkflowApplication> następującym kodem, które tworzy i przekazuje słownika parametry do przepływu pracy podczas jego tworzenia.  
  
    > [!NOTE]
    >  Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Ten słownik zawiera jeden element z kluczem `MaxNumber`. Klucze w słowniku wejściowe odpowiadają wejściowych argumentów działania głównego przepływu pracy. `MaxNumber`jest używany przez przepływ pracy do określenia górna granica losowo generowany numer.  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Aby pobrać dane wyjściowe argumenty przepływu pracy  
  
1.  Modyfikowanie <xref:System.Activities.WorkflowApplication.Completed%2A> programu obsługi pobierania i wyświetlania liczba włącza używany przez przepływ pracy.  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a>Aby wznowić zakładki  
  
1.  Dodaj następujący kod w górnej części `Main` metody zaraz po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  Dodaj następujące <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi poniżej istniejących obsługi cyklu życia trzy przepływu pracy w w `Main`.  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     Zawsze przepływu pracy, staje się bezczynności oczekiwanie na następny dopasowanie, ten program obsługi jest nazywany i `idleAction` <xref:System.Threading.AutoResetEvent> jest ustawiona. Kod w następnym kroku używa `idleEvent` i `syncEvent` czy oczekuje na następny wynik przepływu pracy, czy została ukończona.  
  
    > [!NOTE]
    >  W tym przykładzie korzysta z resetowaniem automatycznym zdarzenia w aplikacji hosta <xref:System.Activities.WorkflowApplication.Completed%2A> i <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi synchronizacji aplikacji hosta z postęp przepływu pracy. Nie jest konieczne zablokować i poczekaj, aż przejdzie w stan bezczynności przed wznowieniem zakładki przepływu pracy, ale w tym przykładzie zdarzenia synchronizacji są wymagane, będzie wówczas traktował hosta, czy przepływ pracy jest pełny lub czy oczekuje na więcej danych wejściowych użytkownika przy użyciu <xref:System.Activities.Bookmark>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Zakładki](../../../docs/framework/windows-workflow-foundation/bookmarks.md).  
  
3.  Usuń wywołanie `WaitOne`i Zastąp kod w celu zbierania danych wejściowych od użytkownika i Wznów <xref:System.Activities.Bookmark>.  
  
     Usuń następujący wiersz kodu.  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     Zastąp go następującym przykładzie.  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a>Aby skompilować i uruchomić aplikację  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.  
  
2.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Próbuje odgadnąć numer w jak najmniejszej liczby włącza, jak to możliwe.  
  
     Próby zastosowania jednego z innych stylów przepływu pracy, należy zastąpić `Workflow1` w kodzie, który tworzy <xref:System.Activities.WorkflowApplication> z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`w oparciu o który chcesz styl przepływu pracy.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Instrukcje dotyczące sposobu dodawania trwałości do przepływu pracy aplikacji, można znaleźć następnego tematu [porady: tworzenie i uruchamianie długiego przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest kompletny kod dla `Main` metody.  
  
> [!NOTE]
>  Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku. Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [Windows Workflow Foundation programowania](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [Trwa oczekiwanie na dane wejściowe w przepływie pracy](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [Hosting przepływów pracy](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
