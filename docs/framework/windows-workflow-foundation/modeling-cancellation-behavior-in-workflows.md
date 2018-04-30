---
title: Zachowanie anulowania modelowania w przepływach pracy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e455bf4d74f77c6cd87301dc9a21f56117777ecf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Zachowanie anulowania modelowania w przepływach pracy
Działania mogą zostać anulowane w przepływie pracy, na przykład przez <xref:System.Activities.Statements.Parallel> działania anulowanie niekompletne gałęzie po jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> daje w wyniku `true`, lub z poza przepływu pracy, jeśli host wywołuje <xref:System.Activities.WorkflowApplication.Cancel%2A>. Aby zapewnić anulowania obsługi, przepływ pracy autorzy mogą używać <xref:System.Activities.Statements.CancellationScope> działania, <xref:System.Activities.Statements.CompensableActivity> działania, lub tworzenia niestandardowych działań, które zapewniają logiki anulowania. Ten temat zawiera omówienie anulowania w przepływach pracy.  
  
## <a name="cancellation-compensation-and-transactions"></a>Anulowanie, kompensacji i transakcji  
 Transakcje dać aplikacji możliwość do przerwania (wycofywania). wszystkie zmiany wykonane w obrębie transakcji, jeśli wystąpią błędy podczas dowolną część procesu transakcji. Jednak nie wszystkie pracy, który może być konieczne może być anulowana lub cofnąć jest odpowiednia dla transakcji, takie jak pracy długotrwałe lub pracy, który nie obejmuje zasoby transakcyjne. Kompensacji udostępnia model cofanie poprzednio ukończoną nietransakcyjnej pracy w przypadku awarii kolejnych w przepływie pracy. Anulowanie udostępnia model dla przepływu pracy i autorom działania obsługi nietransakcyjnej pracy, które nie zostało zakończone. Jeśli działanie nie zostało ukończone działania, anulowaniu jej logiki anulowania zostanie wywołany, jeśli jest dostępny.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o transakcji i kompensacji, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) i [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="using-cancellationscope"></a>Przy użyciu CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> Działanie ma dwie sekcje, które mogą zawierać działań podrzędnych: <xref:System.Activities.Statements.CancellationScope.Body%2A> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Jest rozmieszczenia działania, które tworzą logiki działania, a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> jest rozmieszczenia działań, które zapewniają logiki anulowania działania. Działania mogą zostać anulowane tylko wtedy, gdy nie zostało ukończone. W przypadku liczby <xref:System.Activities.Statements.CancellationScope> działania, ukończenia odwołuje się do zakończenia działania w <xref:System.Activities.Statements.CancellationScope.Body%2A>. Jeśli żądanie anulowania zostało zaplanowane i działań w <xref:System.Activities.Statements.CancellationScope.Body%2A> nie zostały wykonane, a następnie <xref:System.Activities.Statements.CancellationScope> zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działań zostanie wykonane.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Anulowanie przepływu pracy z hosta  
 Hosta można anulować przepływu pracy, wywołując <xref:System.Activities.WorkflowApplication.Cancel%2A> metody <xref:System.Activities.WorkflowApplication> wystąpienia obsługującego przepływ pracy. W poniższym przykładzie jest tworzony przepływu pracy mającej <xref:System.Activities.Statements.CancellationScope>. Przepływ pracy jest wywoływany, a następnie nawiązuje połączenie przez hosta <xref:System.Activities.WorkflowApplication.Cancel%2A>. Główne wykonywania przepływu pracy jest zatrzymana, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> jest wywoływany, a następnie kończy przepływu pracy ze stanem <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Uruchamianie przepływu pracy.**  
**CancellationHandler wywołany.**   
**Anulowane b30ebb30-df46-4d90-a211-e31c38d8db3c przepływu pracy.**    
> [!NOTE]
>  Gdy <xref:System.Activities.Statements.CancellationScope> działania zostanie anulowane i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> wywołany, jest odpowiedzialny za Autor przepływu pracy, aby określić, czy zapewnić logiki anulowania odpowiednie Anulowano anulowane działania przed jego postęp. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Nie zawierają żadnych informacji o postępie anulowane działania.  
  
 Przepływ pracy również mogą zostać anulowane z hosta, jeśli wystąpił nieobsługiwany wyjątek propaguje zapasowej późniejsza pierwiastek przepływu pracy i <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obsługi zwraca <xref:System.Activities.UnhandledExceptionAction.Cancel>. W tym przykładzie rozpoczyna się przepływu pracy, a następnie generuje <xref:System.ApplicationException>. Ten wyjątek jest nieobsługiwany przez przepływ pracy i dlatego element <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obsługi jest wywoływany. Program obsługi nakazuje środowiska uruchomieniowego przepływu pracy, Anuluj i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktualnie wykonywanych <xref:System.Activities.Statements.CancellationScope> działania jest wywoływany.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Uruchamianie przepływu pracy.**  
**OnUnhandledException w 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 przepływu pracy**   
**ApplicationException został zgłoszony.**   
**CancellationHandler wywołany.**   
**Anulowane 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 przepływu pracy.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Anulowanie działania z wewnątrz przepływu pracy  
 Działanie również mogą zostać anulowane przez jego elementu nadrzędnego. Na przykład jeśli <xref:System.Activities.Statements.Parallel> działanie ma kilka gałęzi wykonywania i jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> daje w wyniku `true` , a następnie jego niekompletne oddziałów zostanie anulowane. W tym przykładzie <xref:System.Activities.Statements.Parallel> utworzeniu działania, która ma dwa oddziały. Jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ustawiono `true` więc <xref:System.Activities.Statements.Parallel> zakończeniu zaraz po zakończeniu jednego z jego oddziałów. W tym przykładzie kończy gałęzi 2, a więc gałęzi 1 zostało anulowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Rozgałęzienie uruchamianie 1.**  
**Rozgałęzienie 2 ukończone.**   
**Rozgałęzienie 1 anulowane.**   
**Ukończono e0685e24-18ef-4a47-acf3-5c638732f3be przepływu pracy.**  Jeśli wyjątek propaguje zapasowej późniejsza pierwiastek działania, ale odbywa się na wyższym poziomie w przepływie pracy, również zostaną anulowane działania. W tym przykładzie logiki główny przepływ pracy składa się z <xref:System.Activities.Statements.Sequence> działania. <xref:System.Activities.Statements.Sequence> Jest określony jako <xref:System.Activities.Statements.CancellationScope.Body%2A> z <xref:System.Activities.Statements.CancellationScope> działania, który jest zawarty w <xref:System.Activities.Statements.TryCatch> działania. Wyjątek z treści <xref:System.Activities.Statements.Sequence>, jest obsługiwane przez element nadrzędny <xref:System.Activities.Statements.TryCatch> działania i <xref:System.Activities.Statements.Sequence> zostało anulowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Sekwencja uruchamiania.**  
**Sekwencja anulowane.**   
**Wystąpił wyjątek.**   
**Ukończono e3c18939-121e-4c43-af1c-ba1ce977ce55 przepływu pracy.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Zgłaszanie wyjątków z CancellationHandler  
 Wszelkie wyjątki zgłaszane z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> są krytyczny w przepływie pracy. Jeśli istnieje możliwość anulowania z wyjątków <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, użyj <xref:System.Activities.Statements.TryCatch> w <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> zdołały wychwycić i obsłużyć te wyjątki.  
  
### <a name="cancellation-using-compensableactivity"></a>Za pomocą działania CompensableActivity anulowania  
 Podobnie jak <xref:System.Activities.Statements.CancellationScope> działania, <xref:System.Activities.Statements.CompensableActivity> ma <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Jeśli <xref:System.Activities.Statements.CompensableActivity> zostaną anulowane wszystkie działania w jego <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wywoływane. Może to być przydatne w przypadku cofanie częściowo ukończona Praca compensable. Aby uzyskać informacje o sposobie używania <xref:System.Activities.Statements.CompensableActivity> kompensacji i anulowania, zobacz [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Anulowanie przy użyciu działań niestandardowych  
 Autorzy działania niestandardowego można zaimplementować logiki anulowania ich niestandardowe działania programu na kilka różnych sposobów. Działania niestandardowe, które pochodzą z <xref:System.Activities.Activity> można zaimplementować logiki anulowania przez umieszczenie <xref:System.Activities.Statements.CancellationScope> lub innych działań niestandardowych, zawierający logiki anulowania w treści działania. <xref:System.Activities.AsyncCodeActivity> i <xref:System.Activities.NativeActivity> pochodzące od działania można zmienić ich odpowiednich <xref:System.Activities.NativeActivity.Cancel%2A> — metoda i podaj logiki anulowania. <xref:System.Activities.CodeActivity> pochodzące od działania nie udostępniają udostępniania żadnego anulowania ich pracy jest wykonywana w pojedynczej serii wykonywania, gdy środowisko urchomieniowe wywołuje <xref:System.Activities.CodeActivity.Execute%2A> metody. Jeśli nie ma jeszcze wywoływać metody execute oraz <xref:System.Activities.CodeActivity> oparte na działanie zostało anulowane, zamyka działanie ze stanem <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.CodeActivity.Execute%2A> nie jest wywoływana metoda.  
  
### <a name="cancellation-using-nativeactivity"></a>Za pomocą działania NativeActivity anulowania  
 <xref:System.Activities.NativeActivity> można zastąpić pochodzące od działania <xref:System.Activities.NativeActivity.Cancel%2A> metodę w celu zapewnienia logiki anulowania niestandardowych. Jeśli ta metoda nie jest zastępowany, domyślna logika anulowania przepływu pracy została zastosowana. Anulowanie domyślny jest proces wykonywany dla <xref:System.Activities.NativeActivity> nie powoduje zastąpienia <xref:System.Activities.NativeActivity.Cancel%2A> metody lub których <xref:System.Activities.NativeActivity.Cancel%2A> metoda wywołuje podstawowym <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> — metoda. Po anulowaniu działania środowiska uruchomieniowego flagi działania dotyczące anulowania i automatycznie obsługuje niektórych oczyszczania. Jeśli działanie ma tylko zakładki oczekujące, zakładki zostaną usunięte i działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Wszystkie działania podrzędne oczekujących anulowane działania z kolei zostaną anulowane. Każda próba planować działań podrzędnych dodatkowe spowoduje próbę są ignorowane i działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Po zakończeniu działania żadnych oczekujących podrzędnego w <xref:System.Activities.ActivityInstanceState.Canceled> lub <xref:System.Activities.ActivityInstanceState.Faulted> stanu, a następnie działania zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled>. Należy pamiętać, że żądanie anulowania można zignorować. Jeśli działanie nie ma żadnych oczekujących zakładki lub wykonywania działań podrzędnych i nie zaplanować dowolne elementy pracy dodatkowe po oznaczona flagą anulowania, zostanie wykonane pomyślnie. Anulowanie to domyślne sufiksy w różnych scenariuszach, ale w razie potrzeby logiki anulowania dodatkowe następnie działania anulowania wbudowanych lub niestandardowych działań może być używany.  
  
 W poniższym przykładzie <xref:System.Activities.NativeActivity.Cancel%2A> zastąpienie <xref:System.Activities.NativeActivity> na podstawie niestandardowych `ParallelForEach` zdefiniowano działania. Gdy działanie zostało anulowane, to zastąpienie obsługuje logiki anulowania działania. Ten przykład jest częścią [inne niż ogólne działania ParallelForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md) próbki.  
  
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
  
 <xref:System.Activities.NativeActivity> pochodzące od działania można określić, czy zażądano anulowania, sprawdzając <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> właściwości oraz się zostać oznaczone jako anulowane przez wywołanie metody <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> — metoda. Wywoływanie <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> nie zostanie od razu zakończone działania. W zwykły sposób, środowisko wykonawcze będzie kończyć działanie, jeśli nie ma już zaległe pracy, ale jeśli <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> jest nazywany ostatni stan zostanie <xref:System.Activities.ActivityInstanceState.Canceled> zamiast <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Przy użyciu AsyncCodeActivity anulowania  
 <xref:System.Activities.AsyncCodeActivity> na podstawie działań można też podać logiki anulowania niestandardowych przez zastąpienie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> metody. Jeśli ta metoda nie jest zastępowany, nie obsługi anulowania jest wykonywana, jeśli działanie zostało anulowane. W poniższym przykładzie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zastąpienie <xref:System.Activities.AsyncCodeActivity> na podstawie niestandardowych `ExecutePowerShell` zdefiniowano działania. Gdy działanie zostało anulowane, wykonuje zachowanie żądaną anulowania. Ten przykład jest częścią [za pomocą działania InvokePowerShell](../../../docs/framework/windows-workflow-foundation/samples/using-the-invokepowershell-activity.md) próbki.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> pochodzące od działania można określić, czy zażądano anulowania, sprawdzając <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> właściwości oraz się zostać oznaczone jako anulowane przez wywołanie metody <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> — metoda.
