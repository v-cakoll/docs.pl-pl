---
title: Zachowanie anulowania modelowania w przepływach pracy
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: ec0cf810693e2eda01a4c489b6eb938538719228
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965937"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Zachowanie anulowania modelowania w przepływach pracy
Działania mogą być anulowane w przepływie pracy, na przykład <xref:System.Activities.Statements.Parallel> przez działanie anulowania niekompletnych gałęzi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> `true`, gdy jego wynikiem jest wartość lub spoza przepływu pracy, jeśli jest on <xref:System.Activities.WorkflowApplication.Cancel%2A>wywoływany przez hosta. Aby zapewnić obsługę anulowania, autorzy przepływu pracy mogą <xref:System.Activities.Statements.CancellationScope> korzystać z działania <xref:System.Activities.Statements.CompensableActivity> , działania lub tworzyć niestandardowe działania, które udostępniają logikę anulowania. Ten temat zawiera omówienie anulowania w przepływach pracy.  
  
## <a name="cancellation-compensation-and-transactions"></a>Anulowanie, kompensacja i transakcje  
 Transakcje umożliwiają aplikacji przerwanie (wycofywanie) wszystkich zmian wykonywanych w ramach transakcji w przypadku wystąpienia błędów występujących w ramach procesu transakcji. Jednak nie wszystkie zadania, które mogą wymagać anulowania lub cofania, są odpowiednie dla transakcji, takich jak długotrwałe działanie lub pracy, które nie obejmują zasobów transakcyjnych. Kompensacja zapewnia model wycofywania ukończonych wcześniej zadań nietransakcyjnych, jeśli wystąpi kolejny błąd w przepływie pracy. Anulowanie zapewnia model przepływu pracy i autorów działań do obsługi nietransakcyjnej pracy, która nie została ukończona. Jeśli działanie nie zakończyło wykonywania i zostało anulowane, jego logika anulowania zostanie wywołana, jeśli jest dostępna.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat transakcji i kompensacji, zobacz [transakcje](workflow-transactions.md) i [kompensacja](compensation.md).  
  
## <a name="using-cancellationscope"></a>Korzystanie z CancellationScope  
 Działanie ma dwie sekcje, które mogą zawierać działania podrzędne: <xref:System.Activities.Statements.CancellationScope.Body%2A> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope> Jest to miejsce, w którym są umieszczane działania wchodzące w skład logiki działania, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> a to miejsce, w którym są umieszczane działania, które zapewniają logikę anulowania działania. <xref:System.Activities.Statements.CancellationScope.Body%2A> Działanie można anulować tylko wtedy, gdy nie zostało ukończone. W przypadku <xref:System.Activities.Statements.CancellationScope> działania, uzupełnianie odnosi się do ukończenia działań <xref:System.Activities.Statements.CancellationScope.Body%2A>w. Jeśli zaplanowano żądanie anulowania, a działania <xref:System.Activities.Statements.CancellationScope.Body%2A> w nie zostały ukończone, <xref:System.Activities.Statements.CancellationScope> zostanie oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działania zostaną wykonane.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Anulowanie przepływu pracy z hosta  
 Host może anulować przepływ pracy, wywołując <xref:System.Activities.WorkflowApplication.Cancel%2A> metodę <xref:System.Activities.WorkflowApplication> wystąpienia, które obsługuje przepływ pracy. W poniższym przykładzie jest tworzony przepływ pracy, który ma <xref:System.Activities.Statements.CancellationScope>. Przepływ pracy jest wywoływany, a następnie Host wykonuje wywołanie <xref:System.Activities.WorkflowApplication.Cancel%2A>. Główne wykonywanie przepływu pracy zostanie zatrzymane, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> zostanie wywołane, a następnie przepływ pracy zostanie <xref:System.Activities.ActivityInstanceState.Canceled>ukończony ze stanem.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **Uruchamianie przepływu pracy.**  
**CancellationHandler wywołana.**    
**Anulowano przepływ pracy b30ebb30-df46-4d90-a211-e31c38d8db3c.**    
> [!NOTE]
> Gdy działanie zostało anulowane <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> i wywołane, odpowiada autorowi przepływu pracy, aby określić postęp anulowania działania anulowanego przed jego anulowaniem w celu zapewnienia odpowiedniej logiki anulowania. <xref:System.Activities.Statements.CancellationScope> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Nie zawiera żadnych informacji o postępie anulowanych działań.  
  
 Przepływ pracy można również anulować z hosta, jeśli wystąpił nieobsługiwany wyjątek, który znajduje się poza katalogiem głównym przepływu pracy, <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> a procedura <xref:System.Activities.UnhandledExceptionAction.Cancel>obsługi zwraca wartość. W tym przykładzie przepływ pracy zostanie uruchomiony, a następnie <xref:System.ApplicationException>wygeneruje. Ten wyjątek jest nieobsługiwany przez przepływ pracy i dlatego <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> jest wywoływany program obsługi. Program obsługi instruuje środowisko uruchomieniowe, aby anulował przepływ pracy <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , a aktualnie wykonywane <xref:System.Activities.Statements.CancellationScope> działanie jest wywoływane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **Uruchamianie przepływu pracy.**  
**OnUnhandledException w przepływie pracy 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**   
**Zgłoszono wyjątek ApplicationException.**    
**CancellationHandler wywołana.**    
**Anulowano przepływ pracy 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Anulowanie działania z wewnątrz przepływu pracy  
 Działanie może być również anulowane przez jego element nadrzędny. Jeśli <xref:System.Activities.Statements.Parallel> na przykład działanie ma wiele wykonanych gałęzi, a jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wartość zostanie wyznaczona `true` , jego niekompletne gałęzie zostaną anulowane. W tym przykładzie <xref:System.Activities.Statements.Parallel> tworzone jest działanie, które ma dwie gałęzie. Jest ustawiona na `true` tak<xref:System.Activities.Statements.Parallel> , aby zakończyć działanie zaraz po zakończeniu jednego z jego gałęzi. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> W tym przykładzie rozgałęzienie 2 kończy działanie, a gałąź 1 została anulowana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **Początek gałęzi 1.**  
**Ukończono rozgałęzienie 2.**    
**Anulowano rozgałęzienie 1.**    
**Ukończono e0685e24-18ef-4a47-acf3-5c638732f3be przepływu pracy.**  Działania są również anulowane, jeśli wyjątek występuje w górę od elementu głównego działania, ale jest obsługiwany na wyższym poziomie w przepływie pracy. W tym przykładzie główna logika przepływu pracy składa się z <xref:System.Activities.Statements.Sequence> działania. Jest określony <xref:System.Activities.Statements.TryCatch> jako <xref:System.Activities.Statements.CancellationScope.Body%2A> działanie,którejestzawarte<xref:System.Activities.Statements.CancellationScope>wdziałaniu. <xref:System.Activities.Statements.Sequence> Wyjątek jest generowany z treści <xref:System.Activities.Statements.Sequence>, jest obsługiwany przez działanie nadrzędne <xref:System.Activities.Statements.TryCatch> i <xref:System.Activities.Statements.Sequence> jest anulowany.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **Rozpoczynanie sekwencji.**  
**Anulowano sekwencję.**    
**Przechwycono wyjątek.**    
**Ukończono e3c18939-121e-4c43-af1c-ba1ce977ce55 przepływu pracy.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Zgłaszanie wyjątków z CancellationHandler  
 Wszystkie wyjątki zgłoszone z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> elementu są krytyczne dla przepływu pracy. Jeśli istnieje możliwość występowania wyjątków ucieczki z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, <xref:System.Activities.Statements.TryCatch> należy użyć instrukcji w <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> celu przechwycenia i obsłużenia tych wyjątków.  
  
### <a name="cancellation-using-compensableactivity"></a>Anulowanie przy użyciu działanie CompensableActivity  
 Podobnie jak <xref:System.Activities.Statements.CancellationScope> w przypadku działania <xref:System.Activities.Statements.CompensableActivity> , ma <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Jeśli element <xref:System.Activities.Statements.CompensableActivity> zostanie anulowany, wszystkie działania w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> nim są wywoływane. Może to być przydatne do cofania pracy częściowo ukończonej kompensacyjne. Aby uzyskać informacje o sposobach <xref:System.Activities.Statements.CompensableActivity> korzystania z kompensacji i anulowania, zobacz [kompensacja](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Anulowanie przy użyciu działań niestandardowych  
 Autorzy działań niestandardowych mogą implementować logikę anulowania w swoich działaniach niestandardowych na kilka różnych sposobów. Działania niestandardowe, które pochodzą <xref:System.Activities.Activity> od mogą implementować logikę anulowania <xref:System.Activities.Statements.CancellationScope> przez umieszczenie lub inne niestandardowe działanie, które zawiera logikę anulowania w treści działania. <xref:System.Activities.AsyncCodeActivity>i <xref:System.Activities.NativeActivity> działania pochodne mogą przesłonić <xref:System.Activities.NativeActivity.Cancel%2A> odpowiednią metodę i zapewnić logikę anulowania. <xref:System.Activities.CodeActivity>działania pochodne nie zapewniają żadnych prowizji do anulowania, ponieważ cała ich praca odbywa się w ramach jednej serii wykonywania, gdy środowisko uruchomieniowe wywołuje <xref:System.Activities.CodeActivity.Execute%2A> metodę. Jeśli metoda EXECUTE nie została jeszcze wywołana, a <xref:System.Activities.CodeActivity> działanie na podstawie zostało anulowane, działanie zostanie zamknięte ze <xref:System.Activities.ActivityInstanceState.Canceled> stanem i <xref:System.Activities.CodeActivity.Execute%2A> Metoda nie jest wywoływana.  
  
### <a name="cancellation-using-nativeactivity"></a>Anulowanie przy użyciu natywnego  
 <xref:System.Activities.NativeActivity>działania pochodne mogą przesłonić <xref:System.Activities.NativeActivity.Cancel%2A> metodę, aby zapewnić niestandardową logikę anulowania. Jeśli ta metoda nie zostanie zastąpiona, zostanie zastosowana domyślna logika anulowania przepływu pracy. Domyślne anulowanie to proces, który występuje dla elementu <xref:System.Activities.NativeActivity> , który nie <xref:System.Activities.NativeActivity.Cancel%2A> przesłania metody lub którego <xref:System.Activities.NativeActivity.Cancel%2A> metoda wywołuje metodę bazową <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity.Cancel%2A> Gdy działanie zostanie anulowane, środowisko uruchomieniowe flaguje działanie anulowania i automatycznie obsługuje określone czyszczenie. Jeśli działanie zawiera tylko zakładki oczekujące, zakładki zostaną usunięte, a działanie zostanie oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Wszystkie zaległe działania podrzędne anulowanego działania zostaną anulowane. Każda próba zaplanowania dodatkowych działań podrzędnych spowoduje zignorowanie próby, a działanie zostanie oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Jeśli wszystkie zaległe działania podrzędne zostaną zakończone <xref:System.Activities.ActivityInstanceState.Canceled> w <xref:System.Activities.ActivityInstanceState.Faulted> stanie lub, działanie zostanie oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Zwróć uwagę, że można zignorować żądanie anulowania. Jeśli działanie nie zawiera żadnych zaległych zakładek lub wykonuje działania podrzędne i nie planuje żadnych dodatkowych elementów roboczych po oflagowaniu do anulowania, zakończy się pomyślnie. To domyślne anulowanie jest wystarczające dla wielu scenariuszy, ale jeśli jest wymagana dodatkowa logika anulowania, można użyć wbudowanych działań anulowania lub działań niestandardowych.  
  
 W poniższym przykładzie <xref:System.Activities.NativeActivity.Cancel%2A> zdefiniowano przesłonięcie <xref:System.Activities.NativeActivity> działania niestandardowego `ParallelForEach` opartego na elemencie. Gdy działanie zostanie anulowane, to przesłonięcie obsługuje logikę anulowania działania. Ten przykład jest częścią nieogólnego przykładu [ParallelForEach](./samples/non-generic-parallelforeach.md) .  
  
```csharp  
protected override void Cancel(NativeActivityContext context)  
{  
    // If we do not have a completion condition then we can just  
    // use default logic.  
    if (this.CompletionCondition == null)  
    {  
        base.Cancel(context);  
    }  
    else  
    {  
        context.CancelChildren();  
    }  
}  
```  
  
 <xref:System.Activities.NativeActivity>działania pochodne mogą określić, czy żądanie anulowania zostało zażądane, sprawdzając <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> Właściwość i Oznacz jako anulowane przez <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> wywołanie metody. Wywołanie <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> nie powoduje natychmiastowego wykonania działania. Jak zwykle, środowisko uruchomieniowe ukończy działanie, gdy nie będzie więcej zaległych zadań, ale jeśli <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> jest wywoływana <xref:System.Activities.ActivityInstanceState.Canceled> , zamiast <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Anulowanie przy użyciu metoda AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>działania bazujące mogą również dostarczyć niestandardowe logike anulowania, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zastępując metodę. Jeśli ta metoda nie zostanie przesłonięta, obsługa anulowania nie zostanie wykonana, jeśli działanie zostało anulowane. W poniższym przykładzie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zdefiniowano przesłonięcie działania <xref:System.Activities.AsyncCodeActivity> niestandardowego `ExecutePowerShell` opartego na elemencie. Gdy działanie zostanie anulowane, wykonuje żądane zachowanie anulowania.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>działania pochodne mogą określić, czy żądanie anulowania zostało zażądane, sprawdzając <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> Właściwość i Oznacz jako anulowane przez <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> wywołanie metody.
