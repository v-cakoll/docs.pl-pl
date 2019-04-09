---
title: Wyjątki
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 64a8338133c265ee1b4c7acbd9b4d168318b66a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145993"
---
# <a name="exceptions"></a>Wyjątki
Przepływy pracy można użyć <xref:System.Activities.Statements.TryCatch> działania, aby obsłużyć wyjątki, które są wywoływane podczas wykonywania przepływu pracy. Wyjątki te mogą być obsługiwane lub ich może zostać zgłoszony ponownie przy użyciu <xref:System.Activities.Statements.Rethrow> działania. Działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji są wykonywane, kiedy albo <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji lub <xref:System.Activities.Statements.TryCatch.Catches%2A> kończy sekcji. Przepływy pracy pracujących <xref:System.Activities.WorkflowApplication> wystąpienia można również użyć <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> programu obsługi zdarzeń, aby obsłużyć wyjątki, które nie są obsługiwane przez <xref:System.Activities.Statements.TryCatch> działania.  
  
## <a name="causes-of-exceptions"></a>Przyczyn wyjątków  
 W przepływie pracy wyjątki mogą być generowane w następujący sposób:  
  
-   Limit czasu transakcji w <xref:System.Activities.Statements.TransactionScope>.  
  
-   Jawne wyjątek przy użyciu przepływu pracy <xref:System.Activities.Statements.Throw> działania.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wyjątek z działania.  
  
-   Wyjątek zgłoszony z kodu zewnętrznego, takie jak biblioteki, składników lub usług, które są używane w przepływie pracy.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Jeśli wyjątek jest generowany przez działanie i jest nieobsługiwany, zachowanie domyślne jest zakończenie wystąpienia przepływu pracy. Jeśli niestandardowa <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> program obsługi, można je zastąpić to zachowanie domyślne. Ten program obsługi umożliwia Autor hosta przepływu pracy, aby zapewnić odpowiednią obsługę, takie jak niestandardowe rejestrowania, przerywanie przepływu pracy, anulowanie przepływu pracy lub zakończenie przepływu pracy.  Jeśli przepływ pracy zgłasza wyjątek, który nie jest obsługiwany, <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> zostanie wywołana procedura obsługi. Istnieją trzy możliwe akcje zwróciło <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> który ustalenia końcowego wyniku przepływu pracy.  
  
-   **Anuluj** — wystąpienie anulowane przepływu pracy jest Łagodne wyjście działania gałęzi. Model zachowanie anulowania, (na przykład za pomocą działania CancellationScope). Po zakończeniu procesu anulowania, zostanie wywołany uchwytu ukończone. Anulowano przepływu pracy jest w stanie odwołania.  
  
-   **Zakończenie** — wystąpienie przepływu pracy zakończonych nie może zostać wznowione lub ponownego uruchomienia.  Spowoduje to wyzwolenie zdarzenia zakończony, w którym można podać wyjątek jako powodów, dla którego została przerwana. Program obsługi zwolniony jest wywoływana po zakończeniu procesu zakończenia. Zakończone przepływu pracy jest w stanie Faulted.  
  
-   **Przerwij** — może być wznowione wystąpienia przepływu pracy zostało przerwane, tylko wtedy, gdy został skonfigurowany jako trwałe.  Bez stanu trwałego nie można wznowić przepływ pracy.  W punkcie przepływu pracy zostało przerwane, pracę wykonaną (w pamięci), od ostatniego punktu trwałości zostaną utracone. Przerwanie przepływu pracy obsługi Aborted jest wywoływana przy użyciu wyjątek jako przyczynę, po zakończeniu procesu przerwania. Jednak w przeciwieństwie do odwołania i zwolniony, ukończono program obsługi nie jest wywoływany. Przerwanie przepływu pracy jest w stanie Przerwano.  
  
 Poniższy przykład przedstawia wywoływanie przepływu pracy, która zgłosiła wyjątek. Wyjątek jest nieobsługiwany przez przepływ pracy i <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> zostanie wywołana procedura obsługi. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Są kontrolowane w celu dostarczenia informacji o wyjątku, a przepływ pracy zostanie zakończony.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>Obsługa wyjątków za pomocą działania TryCatch  
 Obsługa wyjątków w przepływie pracy odbywa się za pomocą <xref:System.Activities.Statements.TryCatch> działania. <xref:System.Activities.Statements.TryCatch> Działanie ma <xref:System.Activities.Statements.TryCatch.Catches%2A> zbiór <xref:System.Activities.Statements.Catch> działania, których każde skojarzone z określonym <xref:System.Exception> typu. Jeśli wyjątek zgłoszony przez działanie, które są zawarte w <xref:System.Activities.Statements.TryCatch.Try%2A> części <xref:System.Activities.Statements.TryCatch> działania odpowiada wyjątek <xref:System.Activities.Statements.Catch%601> działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekcji, a następnie wyjątek jest obsługiwany. Jeśli jawnie ponownie zgłoszony wyjątek lub nowy wyjątek następnie ten wyjątek przekazuje do działania nadrzędnego. Poniższy kod przedstawia przykład <xref:System.Activities.Statements.TryCatch> działanie obsługujące <xref:System.ApplicationException> , jest zgłaszany w <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji przez <xref:System.Activities.Statements.Throw> działania. Komunikat o wyjątku są zapisywane do konsoli przez <xref:System.Activities.Statements.Catch%601> działania, a następnie wiadomości są zapisywane do konsoli w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji są wykonywane, kiedy albo <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji lub <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji pomyślnym ukończeniu. <xref:System.Activities.Statements.TryCatch.Try%2A> Sekcji pomyślnym ukończeniu, jeśli żadne wyjątki są zgłaszane z niego i <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji pomyślnym ukończeniu, jeśli żadne wyjątki są zgłaszane lub zgłaszany ponownie z niego. Jeśli wyjątek jest zgłaszany w <xref:System.Activities.Statements.TryCatch.Try%2A> części <xref:System.Activities.Statements.TryCatch> i albo nie jest obsługiwany przez <xref:System.Activities.Statements.Catch%601> w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji w przeciwnym razie jest zgłaszany ponownie z <xref:System.Activities.Statements.TryCatch.Catches%2A>, działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> nie zostaną wykonane, chyba że wystąpi jedno z następujących czynności.  
  
-   Wyjątek wyższym poziomem <xref:System.Activities.Statements.TryCatch> działanie w przepływie pracy, niezależnie od tego, czy jest on zgłaszany ponownie z tego wyższego poziomu <xref:System.Activities.Statements.TryCatch>.  
  
-   Wyjątek nie jest obsługiwany przez wyższego poziomu <xref:System.Activities.Statements.TryCatch>, wyprowadza głównego przepływu pracy i przepływu pracy jest skonfigurowany do anulowania zamiast zakończenia lub przerwania. Hostowane przy użyciu przepływów pracy <xref:System.Activities.WorkflowApplication> konfigurację można określić obsługi <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> i zwracanie <xref:System.Activities.UnhandledExceptionAction.Cancel>. Przykład obsługi <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> znajduje się wcześniej w tym temacie. Konfigurowanie dla usługi przepływu pracy przy użyciu <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i określając <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Aby uzyskać przykład konfigurowania <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Obsługa i rekompensaty wyjątków  
 Różnica między obsługą wyjątków i Kompensacja jest występowanie wyjątków podczas wykonywania działania. Kompensacja występuje po pomyślnym ukończeniu działania. Obsługa wyjątków umożliwia czyszczenie po działanie zgłasza wyjątek, wynagrodzenie stanowi mechanizm, za pomocą którego pomyślnie ukończono pracę wcześniej zakończonego działania może być cofnięte. Aby uzyskać więcej informacji, zobacz [wynagrodzenie](compensation.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>
