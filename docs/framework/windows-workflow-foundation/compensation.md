---
title: kompensacji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ed51d14c56358e283d6c014f036a8aff73d2bfe
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="compensation"></a><span data-ttu-id="f6fa4-102">kompensacji</span><span class="sxs-lookup"><span data-stu-id="f6fa4-102">Compensation</span></span>
<span data-ttu-id="f6fa4-103">W systemie Windows Workflow Foundation (WF) kompensacji jest mechanizm, za pomocą której wcześniej ukończona Praca można cofnąć lub Skompensowane (po logiki zdefiniowane przez aplikację) po wystąpieniu awarii kolejne.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="f6fa4-104">W tej sekcji opisano sposób użycia kompensacji w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="f6fa4-105">Vs kompensacji. Transakcje</span><span class="sxs-lookup"><span data-stu-id="f6fa4-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="f6fa4-106">Transakcja umożliwia łączenie wielu operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="f6fa4-107">Przy użyciu transakcji daje możliwość przerwania (wycofywania), wszystkie zmiany wykonane z w obrębie transakcji, jeśli wystąpią błędy podczas realizowania transakcji dowolnej części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="f6fa4-108">Jednak przy użyciu transakcji nie może być odpowiednie, jeśli praca jest długo działające.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="f6fa4-109">Na przykład aplikację planowania podróży jest implementowany jako przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="f6fa4-110">Czynności przepływu pracy może składać się z rezerwacji lot, oczekiwanie na zatwierdzenie przez menedżera i następnie płatność za lot.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="f6fa4-111">Ten proces może zająć wiele dni i nie jest praktyczne instrukcje rezerwacji i płatności dla transmitowane do udziału w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="f6fa4-112">W przypadku takich jak ta kompensacji może służyć do cofnąć krok rezerwacji przepływu pracy w przypadku awarii później podczas przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6fa4-113">W tym temacie omówiono kompensacji w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="f6fa4-114">Aby uzyskać więcej informacji o transakcji w przepływach pracy, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) i <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-114">For more information about transactions in workflows, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="f6fa4-115">Aby uzyskać więcej informacji na temat transakcji, zobacz <xref:System.Transactions?displayProperty=nameWithType> i <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="f6fa4-116">Za pomocą działania CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="f6fa4-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="f6fa4-117"><xref:System.Activities.Statements.CompensableActivity> działanie kompensacji core w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6fa4-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="f6fa4-118">Każde działanie, które wykonywania pracy, który może być konieczne kompensowane są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="f6fa4-119">W tym przykładzie umieszczane rezerwacji krok zakupu lot <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> i anulowania rezerwacji jest umieszczany w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="f6fa4-120">Bezpośrednio po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekać na zatwierdzenie manager, a następnie Zakończ zakupów kroku lot.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="f6fa4-121">Jeśli warunek błędu powoduje uruchomienie przepływu pracy można anulować po <xref:System.Activities.Statements.CompensableActivity> została pomyślnie zakończona, następnie działania w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsługi są zaplanowane i połączenie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="f6fa4-122">Poniższy przykład jest przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="f6fa4-123">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="f6fa4-124">**ReserveFlight: Biletu jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="f6fa4-125">**ManagerApproval: Zgoda menedżera Odebrano.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="f6fa4-126">**PurchaseFlight: Biletu została zakupiona.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="f6fa4-127">**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="f6fa4-128">Przykładowe działania w tym temacie, takich jak `ReserveFlight` wyświetlić nazwy użytkownika i cel w konsoli, ułatwiające zidentyfikowanie kolejność wykonywania działań, gdy wystąpi kompensacji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="f6fa4-129">Domyślne kompensacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f6fa4-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="f6fa4-130">Domyślnie jeśli przepływu pracy zostało anulowane, logiki kompensacji jest wykonywane dla compensable działalności, która została pomyślnie całkowicie i nie jest jeszcze potwierdzenia lub skompensowane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6fa4-131">Gdy <xref:System.Activities.Statements.CompensableActivity> jest *potwierdzone*, nie można wywołać kompensacji działania.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="f6fa4-132">Proces potwierdzenia jest opisano wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="f6fa4-133">W tym przykładzie jest zgłaszany wyjątek, po lot jest zarezerwowana, ale przed wykonaniem kroku zatwierdzenia menedżera.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="f6fa4-134">W tym przykładzie przedstawiono przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-134">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="f6fa4-135">Po wywołaniu przepływu pracy obsługi wyjątku warunku błędu symulowane przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logiki kompensacji jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="f6fa4-136">**ReserveFlight: Biletu jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="f6fa4-137">**SimulatedErrorCondition: Zgłaszanie ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="f6fa4-138">**Przepływ pracy nieobsługiwany wyjątek:** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="f6fa4-139">**System.ApplicationException: Symulowane błąd w przepływie pracy.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="f6fa4-140">**CancelFlight: Biletu zostało anulowane.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="f6fa4-141">**Przepływ pracy został ukończony pomyślnie o stanie: anulowane.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="f6fa4-142">Anulowanie i działanie CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="f6fa4-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="f6fa4-143">Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> ma nie zostało ukończone i działanie zostało anulowane, działania w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6fa4-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Jest wywoływana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nie została ukończona i działanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="f6fa4-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Jest wykonywana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostały pomyślnie ukończone i kompensacji następnie jest wywoływana w działaniu.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="f6fa4-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Daje możliwość zapewnienia wszelka logika anulowania odpowiednie autorów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="f6fa4-147">W poniższym przykładzie jest zgłaszany wyjątek podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="f6fa4-148">W tym przykładzie przedstawiono przepływ pracy w języku XAML</span><span class="sxs-lookup"><span data-stu-id="f6fa4-148">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="f6fa4-149">Po wywołaniu przepływu pracy obsługi wyjątku warunku błędu symulowane przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływu pracy zostało anulowane, a logika anulowania <xref:System.Activities.Statements.CompensableActivity> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="f6fa4-150">W tym przykładzie logiki kompensacji i logiki anulowania mają różnych celów.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="f6fa4-151">Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> zakończyła się pomyślnie, a następnie oznacza to, karta kredytowa została obciążona i lot rezerwacji, więc rekompensaty należy cofnąć obu czynności.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="f6fa4-152">(W tym przykładzie anulowanie lot automatycznie anuluje obciążenia karty kredytowej.) Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> zostało anulowane, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> została nie pełny i tak logiki <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musi być możliwe ustalenie sposobu obsługi najlepiej anulowania.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="f6fa4-153">W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłaty karty kredytowej, ale ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lot.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="f6fa4-154">Ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, jeśli pomyślnie ukończył, a następnie <xref:System.Activities.Statements.CompensableActivity.Body%2A> czy wykonali i anulowania nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="f6fa4-155">**ChargeCreditCard: Karty kredytowej opłat transmitowane.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="f6fa4-156">**SimulatedErrorCondition: Zgłaszanie ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="f6fa4-157">**Przepływ pracy nieobsługiwany wyjątek:** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="f6fa4-158">**System.ApplicationException: Symulowane błąd w przepływie pracy.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="f6fa4-159">**CancelCreditCard: Anulowanie obciążenia karty kredytowej.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="f6fa4-160">**Przepływ pracy został ukończony pomyślnie o stanie: anulowane.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="f6fa4-161">Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="f6fa4-161">For more information about cancellation, see [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="f6fa4-162">Za pomocą jawnego kompensacji kompensacji działania</span><span class="sxs-lookup"><span data-stu-id="f6fa4-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="f6fa4-163">W poprzedniej sekcji objęte niejawne kompensacji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="f6fa4-164">Niejawne kompensacji może być odpowiednie dla scenariuszy prostego, ale jeśli dokładniejsze wymagana jest kontrola nad planowaniem następnie Obsługa kompensacji <xref:System.Activities.Statements.Compensate> działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="f6fa4-165">Aby zainicjować proces kompensacji z <xref:System.Activities.Statements.Compensate> działania, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> dla których kompensacji jest pożądane jest używana.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="f6fa4-166"><xref:System.Activities.Statements.Compensate> Działanie może być używane do inicjowania kompensacji na dowolnym ukończone <xref:System.Activities.Statements.CompensableActivity> który nie został potwierdzone lub skompensowane.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="f6fa4-167">Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="f6fa4-168">W tym przykładzie <xref:System.Activities.Statements.Compensate> działania jest używana w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji <xref:System.Activities.Statements.TryCatch> działania, aby odwrócić akcję <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="f6fa4-169">W tym przykładzie przedstawiono przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-169">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="f6fa4-170">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="f6fa4-171">**ReserveFlight: Biletu jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="f6fa4-172">**SimulatedErrorCondition: Zgłaszanie ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="f6fa4-173">**CancelFlight: Biletu zostało anulowane.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="f6fa4-174">**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="f6fa4-175">Potwierdzenie kompensacji</span><span class="sxs-lookup"><span data-stu-id="f6fa4-175">Confirming Compensation</span></span>  
 <span data-ttu-id="f6fa4-176">Domyślnie compensable działania kompensowane mogą być dowolnym momencie po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="f6fa4-177">W niektórych scenariuszach to może nie być odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="f6fa4-178">W poprzednim przykładzie kompensacji do rezerwowania bilet był anulowania rezerwacji.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="f6fa4-179">Jednak po ukończeniu lot ten krok kompensacji nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="f6fa4-180">Potwierdzenie compensable działania wywołuje aktywność, określony przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="f6fa4-181">Jedno możliwe użycie tego jest umożliwienie wszystkie zasoby, które są niezbędne do wykonania kompensacji do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="f6fa4-182">Po potwierdzeniu compensable działania, nie jest możliwe na jej kompensowane i to próbie <xref:System.InvalidOperationException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="f6fa4-183">Po pomyślnym zakończeniu przepływu pracy, wszystkich potwierdzone — równoważone compensable działań i pomyślnie wykonanych zostało potwierdzone w odwrotnej kolejności wykonania.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="f6fa4-184">W tym przykładzie lot jest zastrzeżone, zakupione i ukończone, a następnie compensable działania został potwierdzony.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="f6fa4-185">Aby potwierdzić <xref:System.Activities.Statements.CompensableActivity>, użyj <xref:System.Activities.Statements.Confirm> działania i określ <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="f6fa4-186">W tym przykładzie przedstawiono przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-186">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
 <span data-ttu-id="f6fa4-187">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="f6fa4-188">**ReserveFlight: Biletu jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="f6fa4-189">**ManagerApproval: Zgoda menedżera Odebrano.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="f6fa4-190">**PurchaseFlight: Biletu została zakupiona.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="f6fa4-191">**TakeFlight: Transmitowane zostanie ukończona.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="f6fa4-192">**ConfirmFlight: Transmitowane nie podjęto, nie kompensacji możliwe.** </span><span class="sxs-lookup"><span data-stu-id="f6fa4-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="f6fa4-193">**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="f6fa4-193">**Workflow completed successfully with status: Closed.**</span></span>   
## <a name="nesting-compensation-activities"></a><span data-ttu-id="f6fa4-194">Zagnieżdżanie kompensacji działania</span><span class="sxs-lookup"><span data-stu-id="f6fa4-194">Nesting Compensation Activities</span></span>  
 <span data-ttu-id="f6fa4-195">A <xref:System.Activities.Statements.CompensableActivity> mogą być umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> sekcji innego <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="f6fa4-196">A <xref:System.Activities.Statements.CompensableActivity> nie mogą być wprowadzane do obsługi innego <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="f6fa4-197">Jest odpowiedzialny za elementem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> aby upewnić się, że gdy jest anulowane, potwierdzone lub skompensowane, wszystkie działania compensable podrzędne, które zostały ukończone pomyślnie i jeszcze nie zostały potwierdzone lub skompensowane musi zostać potwierdzone lub Skompensowane przed zakończeniem nadrzędnego kompensacji, potwierdzenia lub anulowania.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="f6fa4-198">Jeśli nie jest to wyraźnie modelowane nadrzędnego <xref:System.Activities.Statements.CompensableActivity> zostanie niejawnie kompensacji działania compensable podrzędne odebranie nadrzędnego Anuluj lub kompensacji sygnału.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="f6fa4-199">Jeśli element nadrzędny Odebrano sygnał Potwierdź nadrzędnego niejawnie potwierdzi compensable działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="f6fa4-200">Jeśli logika obsługi kompensacji, potwierdzenia lub anulowania jawnie w modelu obsługi elementu nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, podrzędny nie jest jawnie obsługiwany zostanie potwierdzone niejawnie.</span><span class="sxs-lookup"><span data-stu-id="f6fa4-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fa4-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6fa4-201">See Also</span></span>  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [<span data-ttu-id="f6fa4-202">Działanie kompensacyjne</span><span class="sxs-lookup"><span data-stu-id="f6fa4-202">Compensable Activity</span></span>](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
