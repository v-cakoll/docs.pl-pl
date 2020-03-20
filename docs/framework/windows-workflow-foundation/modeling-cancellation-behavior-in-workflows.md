---
title: Zachowanie anulowania modelowania w przepływach pracy
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8738afa838f1d0ca36b7fd6def00f0794bcf47ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143047"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Zachowanie anulowania modelowania w przepływach pracy
Działania można anulować wewnątrz przepływu pracy, na <xref:System.Activities.Statements.Parallel> przykład przez działanie anulujące `true`niekompletne gałęzie, gdy ma ocenę <xref:System.Activities.WorkflowApplication.Cancel%2A> <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> do lub spoza przepływu pracy, jeśli host wywołuje . Aby zapewnić obsługę anulowania, autorzy przepływu pracy mogą używać <xref:System.Activities.Statements.CancellationScope> działania, <xref:System.Activities.Statements.CompensableActivity> działania lub tworzyć niestandardowe działania, które zapewniają logikę anulowania. Ten temat zawiera omówienie anulowania w przepływach pracy.  
  
## <a name="cancellation-compensation-and-transactions"></a>Anulowanie, rekompensata i transakcje  
 Transakcje dają aplikacji możliwość przerwania (wycofać) wszystkie zmiany wykonane w ramach transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji. Jednak nie wszystkie prace, które mogą wymagać anulowania lub cofnięcia, są odpowiednie dla transakcji, takich jak długotrwała praca lub praca, która nie obejmuje zasobów transakcyjnych. Wynagrodzenie zapewnia model cofania wcześniej ukończonych prac nietransakcyjnych, jeśli wystąpi kolejny błąd w przepływie pracy. Anulowanie udostępnia model dla autorów przepływu pracy i działań do obsługi pracy nietransakcyjnej, która nie została ukończona. Jeśli działanie nie zostało ukończone jego wykonanie i zostanie anulowane, jego logika anulowania zostanie wywołana, jeśli jest dostępna.  
  
> [!NOTE]
> Aby uzyskać więcej informacji o transakcjach i kompensacji, zobacz [Transakcje](workflow-transactions.md) i [rekompensata](compensation.md).  
  
## <a name="using-cancellationscope"></a>Używanie działania CancellationScope  
 Działanie <xref:System.Activities.Statements.CancellationScope> ma dwie sekcje, które mogą <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>zawierać działania podrzędne: i . Jest, <xref:System.Activities.Statements.CancellationScope.Body%2A> gdzie działania, które tworzą logikę działania są <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> umieszczane i jest, gdzie działania, które zapewniają logikę anulowania dla działania są umieszczane. Działanie można anulować tylko wtedy, gdy nie zostało ukończone. W przypadku <xref:System.Activities.Statements.CancellationScope> działania, ukończenie odnosi się do zakończenia działań w . <xref:System.Activities.Statements.CancellationScope.Body%2A> Jeśli żądanie anulowania jest zaplanowane, a <xref:System.Activities.Statements.CancellationScope.Body%2A> działania w nie <xref:System.Activities.Statements.CancellationScope> zostały zakończone, a następnie zostaną oznaczone jako <xref:System.Activities.ActivityInstanceState.Canceled> i <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działania zostaną wykonane.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Anulowanie przepływu pracy z hosta  
 Host może anulować przepływ pracy, <xref:System.Activities.WorkflowApplication.Cancel%2A> wywołując <xref:System.Activities.WorkflowApplication> metodę wystąpienia, które hostuje przepływ pracy. W poniższym przykładzie tworzony jest <xref:System.Activities.Statements.CancellationScope>przepływ pracy, który ma plik . Wywołany jest przepływ pracy, a następnie host <xref:System.Activities.WorkflowApplication.Cancel%2A>nawiązuje połączenie z programem . Główne wykonanie przepływu pracy jest zatrzymywane, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> wywoływane <xref:System.Activities.Statements.CancellationScope> jest, a następnie przepływ <xref:System.Activities.ActivityInstanceState.Canceled>pracy kończy się stanem .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Po wywołaniu tego przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **Uruchamianie przepływu pracy.**  
**CancellationHandler wywoływane.** 
 **Przepływ pracy b30ebb30-df46-4d90-a211-e31c38d8db3c Anulowano.**
> [!NOTE]
> Gdy <xref:System.Activities.Statements.CancellationScope> działanie jest anulowane <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> i wywoływane, jest odpowiedzialny za autora przepływu pracy, aby określić postęp, który anulowane działanie zostało anulowane przed jego anulowaniem w celu zapewnienia odpowiedniej logiki anulowania. Nie <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> zawiera żadnych informacji o postępie anulowanego działania.  
  
 Przepływ pracy można również anulować z hosta, jeśli nieobsługiowany wyjątek pęcherzyki się obok katalogu głównego przepływu pracy i <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> program obsługi zwraca <xref:System.Activities.UnhandledExceptionAction.Cancel>. W tym przykładzie uruchamia się przepływ <xref:System.ApplicationException>pracy, a następnie zgłasza plik . Ten wyjątek jest nieobsługiwany <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> przez przepływ pracy i tak jest wywoływany program obsługi. Program obsługi instruuje środowisko wykonawcze, aby <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> anulować przepływ <xref:System.Activities.Statements.CancellationScope> pracy, a aktualnie wykonywane działanie jest wywoływane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Po wywołaniu tego przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **Uruchamianie przepływu pracy.**  
**OnUnhandledException w przepływie pracy 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**
**Została rzucona.** 
 **CancellationHandler wywoływane.** 
 **Przepływ pracy 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 Anulowano.**
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Anulowanie działania z wewnątrz przepływu pracy  
 Działanie może również zostać anulowane przez jego rodzica. Na przykład jeśli <xref:System.Activities.Statements.Parallel> działanie ma wiele gałęzi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wykonywania i `true` jego ocenia następnie jego niekompletne gałęzie zostaną anulowane. W tym <xref:System.Activities.Statements.Parallel> przykładzie tworzone jest działanie, które ma dwie gałęzie. Jego <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> jest `true` ustawiony <xref:System.Activities.Statements.Parallel> tak, aby zakończyć tak szybko, jak jeden z jego oddziałów jest zakończona. W tym przykładzie gałęzi 2 kończy, a więc oddział 1 jest anulowany.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Po wywołaniu tego przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **Odgałęzienie 1 rozpoczęcie.**  
**Oddział 2 kompletny.** 
 **Oddział 1 anulowany.** 
 **Przepływ pracy e0685e24-18ef-4a47-acf3-5c638732f3b Ukończony.**  Działania są również anulowane, jeśli wyjątek pęcherzyki się obok katalogu głównego działania, ale jest obsługiwany na wyższym poziomie w przepływie pracy. W tym przykładzie główna logika przepływu <xref:System.Activities.Statements.Sequence> pracy składa się z działania. Jest <xref:System.Activities.Statements.Sequence> określony jako <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope> działanie, które jest zawarte <xref:System.Activities.Statements.TryCatch> przez działanie. Wyjątek jest generowany z <xref:System.Activities.Statements.Sequence>treści , jest obsługiwany <xref:System.Activities.Statements.TryCatch> przez działanie <xref:System.Activities.Statements.Sequence> nadrzędne, a jest anulowany.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Po wywołaniu tego przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **Uruchamianie sekwencji.**  
**Sekwencja anulowana.** 
 **Wyjątek złapany.** 
 **Zakończono przepływ pracy e3c18939-121e-4c43-af1c-ba1ce977ce55.**
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Zgłaszanie wyjątków od CancellationHandler  
 Wszelkie wyjątki generowane <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> a są krytyczne dla przepływu pracy. Jeśli istnieje możliwość wyjątków ucieczki od <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, <xref:System.Activities.Statements.TryCatch> użyj <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> w catch i obsługi tych wyjątków.  
  
### <a name="cancellation-using-compensableactivity"></a>Anulowanie przy użyciu compensableactivity  
 Podobnie <xref:System.Activities.Statements.CancellationScope> jak działalność, <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>ma . Jeśli <xref:System.Activities.Statements.CompensableActivity> a zostanie anulowany, wszystkie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> działania w jego są wywoływane. Może to być przydatne w przypadku cofania częściowo ukończonej pracy kompensacyjnej. Aby uzyskać informacje <xref:System.Activities.Statements.CompensableActivity> na temat sposobu wykorzystania do odszkodowania i anulowania, zobacz [Wynagrodzenie](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Anulowanie przy użyciu działań niestandardowych  
 Autorzy działań niestandardowych można zaimplementować logikę anulowania do swoich działań niestandardowych na kilka różnych sposobów. Niestandardowe działania, które <xref:System.Activities.Activity> wynikają z można <xref:System.Activities.Statements.CancellationScope> zaimplementować logikę anulowania, umieszczając lub inne działanie niestandardowe, które zawiera logikę anulowania w treści działania. <xref:System.Activities.AsyncCodeActivity>i <xref:System.Activities.NativeActivity> pochodne działania mogą zastąpić <xref:System.Activities.NativeActivity.Cancel%2A> ich odpowiednią metodę i zapewnić logikę anulowania tam. <xref:System.Activities.CodeActivity>działania pochodne nie zapewniają żadnych przepisów dotyczących anulowania, ponieważ wszystkie ich pracy jest <xref:System.Activities.CodeActivity.Execute%2A> wykonywana w jednej serii wykonywania, gdy środowisko uruchomieniowe wywołuje metodę. Jeśli metoda execute nie została jeszcze <xref:System.Activities.CodeActivity> wywołana, a działanie oparte jest anulowane, działanie zamyka się ze <xref:System.Activities.ActivityInstanceState.Canceled> stanem, a <xref:System.Activities.CodeActivity.Execute%2A> metoda nie jest wywoływana.  
  
### <a name="cancellation-using-nativeactivity"></a>Anulowanie przy użyciu NativeActivity  
 <xref:System.Activities.NativeActivity>działania pochodne można zastąpić <xref:System.Activities.NativeActivity.Cancel%2A> metodę, aby zapewnić niestandardową logikę anulowania. Jeśli ta metoda nie jest zastępowana, zostanie zastosowana domyślna logika anulowania przepływu pracy. Domyślne anulowanie jest <xref:System.Activities.NativeActivity> procesem, który występuje dla, który nie zastępuje <xref:System.Activities.NativeActivity.Cancel%2A> metody lub którego <xref:System.Activities.NativeActivity.Cancel%2A> metoda wywołuje metodę podstawową. <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> Gdy działanie zostanie anulowane, środowisko uruchomieniowe oznacza działanie do anulowania i automatycznie obsługuje pewne oczyszczanie. Jeśli działanie ma tylko zaległe zakładki, zakładki zostaną usunięte, <xref:System.Activities.ActivityInstanceState.Canceled>a działanie zostanie oznaczone jako . Wszelkie zaległe zajęcia dla dzieci anulowane działania zostaną z kolei anulowane. Każda próba zaplanowania dodatkowych działań podrzędnych spowoduje zignorowanie próby, <xref:System.Activities.ActivityInstanceState.Canceled>a działanie zostanie oznaczone jako . Jeśli jakakolwiek zaległa aktywność podrzędna zostanie ukończona <xref:System.Activities.ActivityInstanceState.Canceled> w stanie lub <xref:System.Activities.ActivityInstanceState.Faulted> stanie, aktywność zostanie oznaczona jako <xref:System.Activities.ActivityInstanceState.Canceled>. Należy zauważyć, że żądanie anulowania można zignorować. Jeśli działanie nie ma żadnych zaległych zakładek lub wykonywania działań podrzędnych i nie planuje żadnych dodatkowych elementów roboczych po oflagowaniu do anulowania, zakończy się pomyślnie. To domyślne anulowanie wystarcza dla wielu scenariuszy, ale jeśli wymagana jest dodatkowa logika anulowania, można użyć wbudowanych działań anulowania lub działań niestandardowych.  
  
 W poniższym przykładzie <xref:System.Activities.NativeActivity.Cancel%2A> zdefiniowano <xref:System.Activities.NativeActivity> zastąpienie `ParallelForEach` na podstawie działania niestandardowego. Gdy działanie zostanie anulowane, to zastąpienie obsługuje logikę anulowania dla działania. W tym przykładzie jest częścią [próbki Non-Generic ParallelForEach.](./samples/non-generic-parallelforeach.md)  
  
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
  
 <xref:System.Activities.NativeActivity>działania pochodne można określić, czy odwołanie zostało <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> wymagane przez inspekcję właściwości i <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> oznaczyć się jako anulowane przez wywołanie metody. Wywołanie <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> nie natychmiast zakończyć działanie. Jak zwykle środowisko wykonawcze zakończy działanie, gdy nie ma <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> więcej zaległej <xref:System.Activities.ActivityInstanceState.Canceled> pracy, <xref:System.Activities.ActivityInstanceState.Closed>ale jeśli jest nazywany stan końcowy będzie zamiast .  
  
### <a name="cancellation-using-asynccodeactivity"></a>Anulowanie przy użyciu AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>działania oparte na może również zapewnić niestandardowe <xref:System.Activities.AsyncCodeActivity.Cancel%2A> logiki anulowania przez zastąpienie metody. Jeśli ta metoda nie zostanie zastąpiona, nie jest wykonywana obsługa anulowania, jeśli działanie zostało anulowane. W poniższym przykładzie <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zdefiniowano <xref:System.Activities.AsyncCodeActivity> zastąpienie `ExecutePowerShell` na podstawie działania niestandardowego. Gdy działanie zostanie anulowane, wykonuje żądane zachowanie anulowania.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>działania pochodne można określić, czy odwołanie zostało <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> wymagane przez inspekcję właściwości i <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> oznaczyć się jako anulowane przez wywołanie metody.
