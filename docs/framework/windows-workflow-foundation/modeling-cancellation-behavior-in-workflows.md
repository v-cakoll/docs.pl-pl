---
title: Zachowanie anulowania modelowania w przepływach pracy
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8bbd746d40e9114eacd5a752481d5316c3f30e57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934709"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Zachowanie anulowania modelowania w przepływach pracy
Działania można anulować w przepływie pracy, na przykład przez <xref:System.Activities.Statements.Parallel> działania anulowanie niekompletne gałęzi po jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> daje w wyniku `true`, lub z poza przepływu pracy, jeśli host nie wywoła <xref:System.Activities.WorkflowApplication.Cancel%2A>. Aby zapewnić obsługę anulowania, przepływ pracy autorzy mogą używać <xref:System.Activities.Statements.CancellationScope> działania <xref:System.Activities.Statements.CompensableActivity> działania lub tworzenie niestandardowych działań, które zapewniają logikę anulowania. Ten temat zawiera omówienie anulowania w przepływach pracy.  
  
## <a name="cancellation-compensation-and-transactions"></a>Anulowanie, wynagrodzenie i transakcji  
 Transakcje zapewniają aplikacji możliwość Przerwij wszystkie zmiany wykonane w ramach transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji (wycofywania). Jednak nie wszystkie prace mogące być anulowane lub cofnąć jest odpowiednia dla transakcji, takich jak pracy długotrwałych lub prac, które nie wiąże się z zasobami transakcyjnych. Kompensacja udostępnia model dla cofanie poprzednio ukończoną nietransakcyjnych w przypadku niepowodzenia kolejnych w przepływie pracy. Anulowanie udostępnia model dla przepływu pracy i autorzy działania do obsługi nietransakcyjnej pracy, które nie zostało zakończone. Jeśli działanie nie zostało ukończone wykonywanie zostanie anulowane, swojej logiki anulowania zostanie wywołany, jeśli jest ona dostępna.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat transakcje i Kompensacja zobacz [transakcji](workflow-transactions.md) i [wynagrodzenie](compensation.md).  
  
## <a name="using-cancellationscope"></a>Używanie działania CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> Działanie ma dwie sekcje, które mogą zawierać działania podrzędne: <xref:System.Activities.Statements.CancellationScope.Body%2A> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Jest, gdzie znajdują się działań, które tworzą logikę działania, a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> jest, gdzie są umieszczone działań, które zapewniają logikę anulowania dla działania. Działania można anulować tylko wtedy, gdy nie została ukończona. W przypadku właściwości <xref:System.Activities.Statements.CancellationScope> działania, uzupełnianie odwołuje się do zakończenia działania w <xref:System.Activities.Statements.CancellationScope.Body%2A>. Jeśli zaplanowano na żądanie anulowania i działaniami w <xref:System.Activities.Statements.CancellationScope.Body%2A> nie została ukończona, a następnie <xref:System.Activities.Statements.CancellationScope> zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> będą wykonywane działania.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Anulowanie z hosta przepływu pracy  
 Host może anulować przepływu pracy przez wywołanie metody <xref:System.Activities.WorkflowApplication.Cancel%2A> metody <xref:System.Activities.WorkflowApplication> wystąpienie hostujące przepływu pracy. W poniższym przykładzie przepływ pracy jest tworzony, który ma <xref:System.Activities.Statements.CancellationScope>. Przepływ pracy jest wywoływana, a następnie tworzy wywołanie przez hosta <xref:System.Activities.WorkflowApplication.Cancel%2A>. Główne wykonywanie przepływu pracy jest zatrzymana, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> jest wywoływana, a następnie kończy przepływ pracy ze stanem <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Uruchamianie przepływu pracy.**  
**CancellationHandler wywołana.**   
**B30ebb30-df46-4d90-a211-e31c38d8db3c przepływu pracy zostało anulowane.**    
> [!NOTE]
>  Gdy <xref:System.Activities.Statements.CancellationScope> działanie zostało anulowane i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> wywołana, to obowiązek autora przepływu pracy, aby określić postęp, że działania anulowane przed zostało anulowane zapewnić logikę anulowania odpowiednie. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Nie dostarcza żadnych informacji o postępie anulowane działania.  
  
 Przepływ pracy może być anulowane z hosta, jeśli wystąpił nieobsługiwany wyjątek propaguje się poza głównym przepływu pracy i <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> metoda obsługi zwraca <xref:System.Activities.UnhandledExceptionAction.Cancel>. W tym przykładzie uruchamia przepływ pracy, a następnie zgłasza <xref:System.ApplicationException>. Ten wyjątek jest nieobsługiwany przez przepływ pracy i dlatego <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> zostanie wywołana procedura obsługi. Program obsługi powoduje, że środowisko uruchomieniowe, aby anulować przepływu pracy i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z obecnie wykonywanych <xref:System.Activities.Statements.CancellationScope> działanie zostanie wywołana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Uruchamianie przepływu pracy.**  
**Elemencie OnUnhandledException w 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 przepływu pracy**   
**Applicationexception — został zgłoszony.**   
**CancellationHandler wywołana.**   
**6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 przepływu pracy zostało anulowane.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Trwa anulowanie działania z wewnątrz przepływu pracy  
 Działanie może być anulowane przez jego obiektu nadrzędnego. Na przykład jeśli <xref:System.Activities.Statements.Parallel> działanie ma wiele gałęzi wykonywania i jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> daje w wyniku `true` , a następnie niekompletne gałęzi zostaną anulowane. W tym przykładzie <xref:System.Activities.Statements.Parallel> utworzeniu działania, który ma dwie gałęzie. Jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ustawiono `true` więc <xref:System.Activities.Statements.Parallel> kończy tak szybko, jak jeden z jego gałęzi zostanie ukończona. W tym przykładzie kończy gałęzi 2, a więc gałęzi 1 zostało anulowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Rozgałęzienie, rozpoczynanie 1.**  
**Gałęzi 2 ukończone.**   
**Gałąź 1 zostało anulowane.**   
**Ukończono e0685e24-18ef-4a47-acf3-5c638732f3be przepływu pracy.**  Jeśli wyjątek przechodzić w górę ostatnie głównego działania, ale odbywa się na wyższym poziomie w przepływie pracy, również zostaną anulowane działania. W tym przykładzie głównego logikę przepływu pracy składa się z <xref:System.Activities.Statements.Sequence> działania. <xref:System.Activities.Statements.Sequence> Jest określony jako <xref:System.Activities.Statements.CancellationScope.Body%2A> z <xref:System.Activities.Statements.CancellationScope> działania, który jest zawarty w <xref:System.Activities.Statements.TryCatch> działania. Wyjątek jest generowany z treści <xref:System.Activities.Statements.Sequence>, jest obsługiwane przez nadrzędne <xref:System.Activities.Statements.TryCatch> działania i <xref:System.Activities.Statements.Sequence> zostało anulowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Sekwencja uruchamiania.**  
**Sekwencja zostało anulowane.**   
**Przechwycono wyjątek.**   
**Ukończono e3c18939-121e-4c43-af1c-ba1ce977ce55 przepływu pracy.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Zgłaszanie wyjątków z CancellationHandler  
 Wyjątki zgłaszane z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> są krytyczny do przepływu pracy. Jeśli istnieje możliwość anulowania zapewnianego element z wyjątków <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, użyj <xref:System.Activities.Statements.TryCatch> w <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> zdołały wychwycić i obsłużyć tych wyjątków.  
  
### <a name="cancellation-using-compensableactivity"></a>Unieważnieniu przy użyciu CompensableActivity  
 Podobnie jak <xref:System.Activities.Statements.CancellationScope> działania <xref:System.Activities.Statements.CompensableActivity> ma <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Jeśli <xref:System.Activities.Statements.CompensableActivity> zostanie anulowane, wszelkie działania w jego <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wywoływane. Może to być przydatne w przypadku cofanie pracy kompensacyjne częściowo ukończone. Aby uzyskać informacje o sposobie używania <xref:System.Activities.Statements.CompensableActivity> wynagrodzenie i anulowania, zobacz [wynagrodzenie](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Unieważnieniu przy użyciu niestandardowych działań  
 Autorzy działania niestandardowego można zaimplementować logikę anulowania ich niestandardowe działania programu na kilka różnych sposobów. Działania niestandardowe, które wynikają z <xref:System.Activities.Activity> można zaimplementować logikę anulowania, umieszczając <xref:System.Activities.Statements.CancellationScope> lub innych działań niestandardowych, który zawiera logikę anulowania w treści działania. <xref:System.Activities.AsyncCodeActivity> i <xref:System.Activities.NativeActivity> działania pochodny może zastąpić odpowiednich <xref:System.Activities.NativeActivity.Cancel%2A> metody i zapewnić logikę anulowania istnieje. <xref:System.Activities.CodeActivity> pochodne działania nie są oferowane w dowolnej obsługi administracyjnej anulowania, ponieważ gdy środowisko uruchomieniowe wywołuje swoją pracę odbywa się w pojedynczej serii wykonywania <xref:System.Activities.CodeActivity.Execute%2A> metody. Jeśli nie ma jeszcze wywoływać metody execute i a <xref:System.Activities.CodeActivity> działania na podstawie zostanie anulowane, działanie zostanie zamknięte ze stanem <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.CodeActivity.Execute%2A> nie jest wywoływana metoda.  
  
### <a name="cancellation-using-nativeactivity"></a>Unieważnieniu przy użyciu klasy NativeActivity  
 <xref:System.Activities.NativeActivity> działania pochodny może zastąpić <xref:System.Activities.NativeActivity.Cancel%2A> metodę, aby zapewnić logikę niestandardowego anulowania. Jeśli ta metoda nie zostanie zastąpiona, stosowany jest domyślną logikę anulowania przepływu pracy. Anulowanie domyślny jest proces wykonywany dla <xref:System.Activities.NativeActivity> nie powoduje zastąpienia <xref:System.Activities.NativeActivity.Cancel%2A> metody lub których <xref:System.Activities.NativeActivity.Cancel%2A> metoda wywołuje base <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> metody. Gdy działanie zostało anulowane, środowisko uruchomieniowe flagi działania dotyczące anulowania i automatycznie obsługuje niektóre oczyszczania. Jeśli działanie tylko ma oczekujące zakładek, zakładek, zostaną usunięte i działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Wszystkie działania podrzędne oczekujących anulowane działania z kolei zostaną anulowane. Każda próba zaplanować działania podrzędne dodatkowe spowoduje próbę są ignorowane i działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Jeśli działanie żadnych oczekujących podrzędne zakończy się w <xref:System.Activities.ActivityInstanceState.Canceled> lub <xref:System.Activities.ActivityInstanceState.Faulted> stanu, a następnie działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Należy pamiętać, że żądanie anulowania można zignorować. Jeśli działanie nie ma żadnych oczekujących zakładek lub wykonywanie działania podrzędne i nie planować wszystkie elementy robocze dodatkowe po oflagowana anulowania, zostanie ono ukończone pomyślnie. Anulowanie tego domyślnego sufiksy umożliwia obsługę wielu scenariuszy, ale w razie potrzeby logiki anulowania dodatkowe wówczas anulowania wbudowane działania lub działania niestandardowe mogą być używane.  
  
 W poniższym przykładzie <xref:System.Activities.NativeActivity.Cancel%2A> zastępowania <xref:System.Activities.NativeActivity> na podstawie niestandardowego `ParallelForEach` działania jest zdefiniowana. Gdy działanie zostało anulowane, to zastąpienie obsługuje logikę anulowania działania. W tym przykładzie jest częścią [inne niż nieogólne działanie ParallelForEach](./samples/non-generic-parallelforeach.md) próbki.  
  
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
  
 <xref:System.Activities.NativeActivity> pochodne działania można określić, jeśli zażądano anulowania, sprawdzając <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> właściwości i oznaczy się jako anulowane przez wywołanie metody <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> metody. Wywoływanie <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> natychmiast zakończy działanie. W zwykły sposób, środowisko uruchomieniowe zostanie ukończone działania, jeśli nie ma oczekujących ma więcej pracy, ale jeśli <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> nosi nazwę ostatni stan zostanie <xref:System.Activities.ActivityInstanceState.Canceled> zamiast <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Unieważnieniu przy użyciu AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity> działaniami opartymi na oferuje również logikę niestandardowego anulowania przez zastąpienie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> metody. Jeśli ta metoda nie zostanie zastąpiona, nie obsługi anulowania jest wykonywana, jeśli działanie zostanie anulowane. W poniższym przykładzie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zastępowania <xref:System.Activities.AsyncCodeActivity> na podstawie niestandardowego `ExecutePowerShell` działania jest zdefiniowana. Gdy działanie zostało anulowane, wykonuje anulowania żądane zachowanie.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> pochodne działania można określić, jeśli zażądano anulowania, sprawdzając <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> właściwości i oznaczy się jako anulowane przez wywołanie metody <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> metody.
