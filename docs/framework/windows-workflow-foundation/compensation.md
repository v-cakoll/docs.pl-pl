---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: e8a7140e677b553d07014d0ac5a77dd1c7488f53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607608"
---
# <a name="compensation"></a><span data-ttu-id="e0bff-102">Kompensacja</span><span class="sxs-lookup"><span data-stu-id="e0bff-102">Compensation</span></span>
<span data-ttu-id="e0bff-103">Rekompensaty w Windows Workflow Foundation (WF) to mechanizm, za pomocą którego wcześniej Praca wykonana można cofnąć lub płatne (następujących logiki, zdefiniowany przez aplikację) podczas kolejnych awarii.</span><span class="sxs-lookup"><span data-stu-id="e0bff-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="e0bff-104">W tej sekcji opisano sposób użycia rekompensaty w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="e0bff-105">Vs wynagrodzenia. Transakcje</span><span class="sxs-lookup"><span data-stu-id="e0bff-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="e0bff-106">Transakcja pozwala połączyć wiele operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="e0bff-107">Przy użyciu transakcji daje aplikacji możliwość Przerwij wszystkie zmiany wykonane z w ramach transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji (wycofanie).</span><span class="sxs-lookup"><span data-stu-id="e0bff-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="e0bff-108">Jednak za pomocą transakcji może nie być odpowiednie, jeżeli praca jest długo działające.</span><span class="sxs-lookup"><span data-stu-id="e0bff-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="e0bff-109">Na przykład aplikacja planowania podróży została zaimplementowana jako przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="e0bff-110">Kroki przepływu pracy może składać się z rezerwacji lotu, oczekiwanie na zatwierdzenie przez menedżera i następnie płacić lotu.</span><span class="sxs-lookup"><span data-stu-id="e0bff-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="e0bff-111">Może to zająć wiele dni, a nie jest praktyczne kroki rezerwacji i płacić za lot do wzięcia udziału w ramach jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="e0bff-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="e0bff-112">W przypadku takich wynagrodzenie może służyć do cofnąć kroku rezerwacji przepływu pracy, jeśli wystąpi awaria w dalszej części przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e0bff-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bff-113">W tym temacie omówiono rekompensaty w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="e0bff-114">Aby uzyskać więcej informacji na temat transakcji w przepływach pracy, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) i <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-114">For more information about transactions in workflows, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="e0bff-115">Aby uzyskać więcej informacji na temat transakcji, zobacz <xref:System.Transactions?displayProperty=nameWithType> i <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="e0bff-116">Za pomocą CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="e0bff-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="e0bff-117"><xref:System.Activities.Statements.CompensableActivity> jest podstawowym działaniem rekompensaty w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0bff-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="e0bff-118">Każde działanie, które wykonują pracę, która może być konieczne można skompensować są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="e0bff-119">W tym przykładzie kroku rezerwacji lotu kupowaniu jest umieszczana w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> i anulowania rezerwacji jest umieszczana w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="e0bff-120">Natychmiast po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekać na zatwierdzenie przez menedżera, a następnie Zakończ zakupu kroku podczas lotu.</span><span class="sxs-lookup"><span data-stu-id="e0bff-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="e0bff-121">Jeśli warunek błędu powoduje, że przepływ pracy zostaną anulowane po <xref:System.Activities.Statements.CompensableActivity> zostanie pomyślnie zakończony, następnie działania w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsługi są planowane i lotu zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="e0bff-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="e0bff-122">Poniższy przykład jest przepływ pracy w XAML.</span><span class="sxs-lookup"><span data-stu-id="e0bff-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="e0bff-123">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0bff-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="e0bff-124">**ReserveFlight: Bilet jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="e0bff-125">**ManagerApproval: Odebrane zatwierdzenia przez menedżera.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="e0bff-126">**PurchaseFlight: Bilet jest sprzedawana.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="e0bff-127">**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="e0bff-128">Przykładowe działania w tym temacie, takie jak `ReserveFlight` wyświetlane nazwy użytkownika i przeznaczenia konsoli ilustrujących kolejność wykonywania działań, po wystąpieniu wynagrodzenia.</span><span class="sxs-lookup"><span data-stu-id="e0bff-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="e0bff-129">Domyślne Kompensacja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e0bff-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="e0bff-130">Domyślnie jeśli przepływ pracy zostanie anulowane, logiki wyrównującej jest uruchamiana dla działanie kompensacyjne, który został pomyślnie całkowicie i nie jest jeszcze potwierdzenia lub płatne.</span><span class="sxs-lookup"><span data-stu-id="e0bff-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bff-131">Gdy <xref:System.Activities.Statements.CompensableActivity> jest *potwierdzone*, już nie może być wywoływany wynagrodzenia dla działania.</span><span class="sxs-lookup"><span data-stu-id="e0bff-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="e0bff-132">Proces potwierdzenia jest później opisane w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e0bff-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="e0bff-133">W tym przykładzie wyjątek jest generowany po lotu jest zastrzeżona, ale przed wykonaniem kroku zatwierdzenia menedżera.</span><span class="sxs-lookup"><span data-stu-id="e0bff-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="e0bff-134">W tym przykładzie przedstawiono przepływ pracy w XAML.</span><span class="sxs-lookup"><span data-stu-id="e0bff-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="e0bff-135">Po wywołaniu przepływu pracy wyjątek warunku symulowanego błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logiki wyrównującej jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e0bff-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="e0bff-136">**ReserveFlight: Bilet jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="e0bff-137">**SimulatedErrorCondition: Zgłaszanie applicationexception —.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="e0bff-138">**Przepływ pracy nieobsługiwany wyjątek:** </span><span class="sxs-lookup"><span data-stu-id="e0bff-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="e0bff-139">**System.ApplicationException: Symulowane warunek błędu w przepływie pracy.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="e0bff-140">**CancelFlight: Zgłoszenie zostało anulowane.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="e0bff-141">**Przepływ pracy została pomyślnie ukończona ze stanem: Anulowane.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="e0bff-142">Anulowanie i CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="e0bff-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="e0bff-143">Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mają nie zakończone i zostanie anulowane działania, działania w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e0bff-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bff-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Jest wywoływana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nie została ukończona i działanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="e0bff-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="e0bff-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Jest wykonywana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało wykonane pomyślnie ukończone i rekompensaty jest później wywoływana działania.</span><span class="sxs-lookup"><span data-stu-id="e0bff-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="e0bff-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Zapewnia przedstawienie dowolnej logiki anulowania odpowiednie autorzy przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="e0bff-147">W poniższym przykładzie, zgłaszany jest wyjątek podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="e0bff-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="e0bff-148">W tym przykładzie przedstawiono przepływ pracy w XAML</span><span class="sxs-lookup"><span data-stu-id="e0bff-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="e0bff-149">Po wywołaniu przepływu pracy wyjątek warunku symulowanego błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logikę anulowania <xref:System.Activities.Statements.CompensableActivity> zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="e0bff-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="e0bff-150">W tym przykładzie logiki wyrównującej i logikę anulowania mają inne cele.</span><span class="sxs-lookup"><span data-stu-id="e0bff-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="e0bff-151">Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> zakończone pomyślnie, a następnie oznacza to, karta kredytowa została obciążona i rezerwacji lotu, dlatego rekompensaty należy cofnąć oba kroki.</span><span class="sxs-lookup"><span data-stu-id="e0bff-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="e0bff-152">(W tym przykładzie anulowanie lotu automatycznie anuluje obciążenia karty kredytowej.) Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> zostanie anulowane, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> została nie kompletne i dlatego logiki <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musi być możliwe ustalenie, jak najlepiej obsługiwać anulowanie.</span><span class="sxs-lookup"><span data-stu-id="e0bff-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="e0bff-153">W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłata kartą kredytową, ale ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lotu.</span><span class="sxs-lookup"><span data-stu-id="e0bff-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="e0bff-154">Ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, jeśli pomyślnie ukończył, a następnie <xref:System.Activities.Statements.CompensableActivity.Body%2A> czy zostały wykonane i anulowania nie byłoby możliwe.</span><span class="sxs-lookup"><span data-stu-id="e0bff-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="e0bff-155">**ChargeCreditCard: Opłata za karty kredytowej na potrzeby lotu.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="e0bff-156">**SimulatedErrorCondition: Zgłaszanie applicationexception —.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="e0bff-157">**Przepływ pracy nieobsługiwany wyjątek:** </span><span class="sxs-lookup"><span data-stu-id="e0bff-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="e0bff-158">**System.ApplicationException: Symulowane warunek błędu w przepływie pracy.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="e0bff-159">**CancelCreditCard: Anuluj obciążenia karty kredytowej.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="e0bff-160">**Przepływ pracy została pomyślnie ukończona ze stanem: Anulowane.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="e0bff-161">Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="e0bff-161">For more information about cancellation, see [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="e0bff-162">Za pomocą jawnego wynagrodzenie kompensacji działania</span><span class="sxs-lookup"><span data-stu-id="e0bff-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="e0bff-163">W poprzedniej sekcji objęte niejawne wynagrodzenia.</span><span class="sxs-lookup"><span data-stu-id="e0bff-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="e0bff-164">Niejawne wynagrodzenie może być odpowiednie dla prostych scenariuszy, ale jeśli dokładniejsze wymagana jest kontrola nad planowaniem wynagrodzenie obsługi następnie <xref:System.Activities.Statements.Compensate> działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="e0bff-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="e0bff-165">Aby zainicjować proces odszkodowania za pomocą <xref:System.Activities.Statements.Compensate> działania, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> wynagrodzenie, która jest pożądane jest używany.</span><span class="sxs-lookup"><span data-stu-id="e0bff-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="e0bff-166"><xref:System.Activities.Statements.Compensate> Działanie może być używane do inicjowania rekompensaty w przypadku dowolnego ukończone <xref:System.Activities.Statements.CompensableActivity> który nie został potwierdzony lub płatne.</span><span class="sxs-lookup"><span data-stu-id="e0bff-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="e0bff-167">Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane w <xref:System.Activities.Statements.TryCatch.Catches%2A> części <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="e0bff-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="e0bff-168">W tym przykładzie <xref:System.Activities.Statements.Compensate> działania jest używana w <xref:System.Activities.Statements.TryCatch.Catches%2A> części <xref:System.Activities.Statements.TryCatch> działania, aby odwrócić Akcja <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="e0bff-169">W tym przykładzie przedstawiono przepływ pracy w XAML.</span><span class="sxs-lookup"><span data-stu-id="e0bff-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="e0bff-170">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0bff-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="e0bff-171">**ReserveFlight: Bilet jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="e0bff-172">**SimulatedErrorCondition: Zgłaszanie applicationexception —.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="e0bff-173">**CancelFlight: Zgłoszenie zostało anulowane.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="e0bff-174">**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="e0bff-175">Trwa Potwierdzanie Kompensacja</span><span class="sxs-lookup"><span data-stu-id="e0bff-175">Confirming Compensation</span></span>  
 <span data-ttu-id="e0bff-176">Domyślnie kompensacyjne działań można skompensować dowolnej chwili po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e0bff-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="e0bff-177">W niektórych przypadkach może to nie być odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="e0bff-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="e0bff-178">W poprzednim przykładzie wynagrodzenie do rezerwowania--ticket był anulowania rezerwacji.</span><span class="sxs-lookup"><span data-stu-id="e0bff-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="e0bff-179">Jednak po ukończeniu lotu tego kroku wynagrodzenie nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e0bff-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="e0bff-180">Potwierdzanie działanie kompensacyjne wywołuje działanie określonego przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="e0bff-181">Jedno możliwe użycie tego jest umożliwienie wszystkie zasoby, które są niezbędne do wykonania wynagrodzenie, które mogą być wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="e0bff-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="e0bff-182">Po potwierdzeniu działanie kompensacyjne nie jest możliwe, aby mogła być wyrównane, a jeśli to jest podejmowana próba <xref:System.InvalidOperationException> jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0bff-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="e0bff-183">Po pomyślnym zakończeniu działania przepływu pracy, wszystkie-potwierdzone i skompensować kompensacyjne działania, które zakończyły się pomyślnie potwierdzone w odwrotnej kolejności wykonania.</span><span class="sxs-lookup"><span data-stu-id="e0bff-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="e0bff-184">W tym przykładzie lotu jest zarezerwowana, zakupu i ukończone, a następnie działanie kompensacyjne został potwierdzony.</span><span class="sxs-lookup"><span data-stu-id="e0bff-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="e0bff-185">Aby upewnić się, <xref:System.Activities.Statements.CompensableActivity>, użyj <xref:System.Activities.Statements.Confirm> działania i określ <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="e0bff-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="e0bff-186">W tym przykładzie przedstawiono przepływ pracy w XAML.</span><span class="sxs-lookup"><span data-stu-id="e0bff-186">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="e0bff-187">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0bff-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="e0bff-188">**ReserveFlight: Bilet jest zarezerwowana.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="e0bff-189">**ManagerApproval: Odebrane zatwierdzenia przez menedżera.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="e0bff-190">**PurchaseFlight: Bilet jest sprzedawana.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="e0bff-191">**TakeFlight: Został ukończony lot.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="e0bff-192">**ConfirmFlight: Lotu jest zajęty, żadne wynagrodzenie możliwe.** </span><span class="sxs-lookup"><span data-stu-id="e0bff-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="e0bff-193">**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="e0bff-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="e0bff-194">Zagnieżdżanie działania Kompensacja</span><span class="sxs-lookup"><span data-stu-id="e0bff-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="e0bff-195">A <xref:System.Activities.Statements.CompensableActivity> mogą być umieszczane <xref:System.Activities.Statements.CompensableActivity.Body%2A> części innego <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="e0bff-196">A <xref:System.Activities.Statements.CompensableActivity> nie mogą być wprowadzane do obsługi innego <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="e0bff-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="e0bff-197">Jest odpowiedzialny za elementem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> aby upewnić się, że gdy jest anulowane, potwierdzony lub skompensować, wszystkie działania kompensacyjne podrzędne, które zostały zakończone powodzeniem i nie zostały potwierdzone lub płatne musi zostać potwierdzone lub wyrównane przed zakończeniem obiektu nadrzędnego, wynagrodzenie, potwierdzenie lub anulowania.</span><span class="sxs-lookup"><span data-stu-id="e0bff-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="e0bff-198">Jeśli nie jest to jawnie modelowane nadrzędnego <xref:System.Activities.Statements.CompensableActivity> zostanie niejawnie kompensacji kompensacyjne działania podrzędne, jeśli element nadrzędny otrzymuje anulowanie lub kompensacji sygnału.</span><span class="sxs-lookup"><span data-stu-id="e0bff-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="e0bff-199">Jeśli element nadrzędny otrzymał sygnał Potwierdź nadrzędnego niejawnie potwierdzi kompensacyjne działania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e0bff-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="e0bff-200">Jeśli logika obsługi anulowania, potwierdzenia lub odszkodowania jawnie w modelu obsługi nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, wszystkie podrzędne nie są jawnie obsługiwane zostanie potwierdzone niejawnie.</span><span class="sxs-lookup"><span data-stu-id="e0bff-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bff-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0bff-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
