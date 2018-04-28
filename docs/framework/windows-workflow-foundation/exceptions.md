---
title: Wyjątki
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e78546a10e1a8cdff780c44898fd209ca829c6c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions"></a>Wyjątki
Przepływy pracy można użyć <xref:System.Activities.Statements.TryCatch> działanie obsługi wyjątków, które są wywoływane podczas wykonywania przepływu pracy. Wyjątki te mogą być obsługiwane lub ich może zostać zgłoszony ponownie przy użyciu <xref:System.Activities.Statements.Rethrow> działania. Działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji są wykonywane, kiedy albo <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji lub <xref:System.Activities.Statements.TryCatch.Catches%2A> zakończeniu sekcji. Przepływy pracy na użytek <xref:System.Activities.WorkflowApplication> wystąpienia można również użyć <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> program obsługi zdarzeń do obsługi wyjątków, które nie są obsługiwane przez <xref:System.Activities.Statements.TryCatch> działania.  
  
## <a name="causes-of-exceptions"></a>Przyczyny wyjątków  
 W przepływie pracy wyjątki mogą być generowane w następujący sposób:  
  
-   Limit czasu transakcji w <xref:System.Activities.Statements.TransactionScope>.  
  
-   Jawne wyjątek przy użyciu przepływu pracy <xref:System.Activities.Statements.Throw> działania.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wyjątek z działania.  
  
-   Wyjątek zgłoszony z kodu zewnętrznego, takich jak biblioteki, składników i usług, które są używane w przepływie pracy.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Jeśli wyjątek jest zgłaszany przez działanie i nie jest obsługiwany, domyślne zachowanie jest przerwanie wystąpienia przepływu pracy. Jeśli niestandardowego <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obsługi, można zastąpić to zachowanie domyślne. Ten program obsługi zapewnia Autor hosta przepływu pracy zapewnić odpowiednią obsługę, takich jak niestandardowe rejestrowania, przerwanie przepływu pracy, anulowanie przepływu pracy lub zakończenie przepływu pracy.  Jeśli przepływ pracy zgłasza wyjątek, który nie jest obsługiwana, <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> program obsługi jest wywoływany. Istnieją trzy możliwe działania zwrócony z <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> określają końcowego wyniku przepływu pracy.  
  
-   **Anuluj** -łagodne zakończenia wykonywania gałęzi jest wystąpienia przepływu pracy zostało anulowane. Zachowanie anulowania można modelu (na przykład za pomocą działania CancellationScope). Programu obsługi zdarzeń Completed jest wywoływana po zakończeniu procesu anulowania. Anulowane przepływu pracy jest w stanie odwołania.  
  
-   **Przerwanie** — wystąpienia zakończone przepływu pracy nie można wznowić lub ponownego uruchomienia.  Spowoduje to zainicjowanie zdarzenia zakończony, w którym można podać wyjątek jako przyczyny, dla której została przerwana. Program obsługi zwolniony jest wywoływana po zakończeniu procesu zakończenia. Zakończone przepływu pracy jest w stanie Faulted.  
  
-   **Przerwij** -wystąpień przerwanych przepływów pracy można wznawiać tylko, jeśli został on skonfigurowany jako trwałe.  Bez trwałości nie można wznowić przepływ pracy.  W punkcie przepływ pracy został przerwany, pracy wykonanej (w pamięci), od ostatniego punktu trwałości zostaną utracone. Przerwane przepływu pracy obsługi przerwania jest wywoływana przy użyciu wyjątek jako przyczynę po zakończeniu procesu przerwania. Jednak w przeciwieństwie do odwołania i zwolniony programu obsługi zdarzeń Completed nie jest wywoływany. Przepływ pracy przerwanych jest w stanie przerwania.  
  
 Poniższy przykład przedstawia wywoływanie przepływu pracy, który zgłasza wyjątek. Wyjątek jest nieobsługiwany przez przepływ pracy i <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obsługi jest wywoływany. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Są kontrolowane w celu podania informacji o wyjątku, a przepływ pracy zostanie zakończony.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>Obsługa wyjątków z działaniem Trycatch  
 Obsługa wyjątków w przepływie pracy jest wykonywane z <xref:System.Activities.Statements.TryCatch> działania. <xref:System.Activities.Statements.TryCatch> Działanie ma <xref:System.Activities.Statements.TryCatch.Catches%2A> Kolekcja <xref:System.Activities.Statements.Catch> działań, których każde skojarzone z określonym <xref:System.Exception> typu. Jeśli wyjątek zgłoszony przez działanie zawarte w <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji <xref:System.Activities.Statements.TryCatch> działania odpowiada wyjątek <xref:System.Activities.Statements.Catch%601> działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekcji, a następnie wyjątek jest obsługiwany. Jeśli wyjątek jest jawnie zgłoszony ponownie lub nowy wyjątek następnie tego wyjątku przekazuje do działania nadrzędnego. Poniższy kod przedstawia przykład <xref:System.Activities.Statements.TryCatch> działania, która obsługuje <xref:System.ApplicationException> który jest zgłaszany <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji przez <xref:System.Activities.Statements.Throw> działania. Komunikat o wyjątku jest wyświetlony w konsoli przez <xref:System.Activities.Statements.Catch%601> działania, a następnie wiadomości są zapisywane do konsoli w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> sekcji są wykonywane, kiedy albo <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji lub <xref:System.Activities.Statements.TryCatch.Catches%2A> pomyślnie ukończy sekcji. <xref:System.Activities.Statements.TryCatch.Try%2A> Sekcji pomyślnie ukończy, jeśli żadne wyjątki są zgłaszane z niego oraz <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji pomyślnie ukończy, jeśli żadne wyjątki są zgłaszane lub zgłoszony z niego. Jeśli wyjątek <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji <xref:System.Activities.Statements.TryCatch> i albo nie jest obsługiwany przez <xref:System.Activities.Statements.Catch%601> w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji lub jest zgłoszony z <xref:System.Activities.Statements.TryCatch.Catches%2A>, działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> nie zostanie wykonany, chyba że wystąpi jedno z następujących czynności.  
  
-   Wyjątek wyższym poziomem <xref:System.Activities.Statements.TryCatch> działania w przepływie pracy, niezależnie od tego, czy jest zgłoszony z tego wyższego poziomu <xref:System.Activities.Statements.TryCatch>.  
  
-   Wyjątek nie jest obsługiwany przez wyższego poziomu <xref:System.Activities.Statements.TryCatch>, specjalne głównego przepływu pracy i przepływ pracy jest skonfigurowany do anulowania zamiast przerwania lub przerwania. Przepływy pracy hostowane przy użyciu <xref:System.Activities.WorkflowApplication> można skonfigurować to obsługa <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> i zwracanie <xref:System.Activities.UnhandledExceptionAction.Cancel>. Przykład obsługa <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> znajduje się wcześniej w tym temacie. Konfigurowanie dla usługi przepływu pracy przy użyciu <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i określając <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Aby uzyskać przykład konfigurowania <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Obsługa i kompensacji wyjątków  
 Różnica między wyjątków i kompensacji jest, że obsługa wyjątków odbywa się podczas wykonywania działania. Kompensacji występuje, gdy działanie zostało zakończone pomyślnie. Obsługa wyjątków umożliwia czyszczenie po działania zgłasza wyjątek, kompensacji stanowi mechanizm, za pomocą którego można cofnąć pomyślnie ukończona Praca poprzednio ukończoną działania. Aby uzyskać więcej informacji, zobacz [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.TryCatch>  
 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>  
 <xref:System.Activities.Statements.CompensableActivity>
