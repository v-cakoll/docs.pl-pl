---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183003"
---
# <a name="compensation"></a><span data-ttu-id="9ff6e-102">Kompensacja</span><span class="sxs-lookup"><span data-stu-id="9ff6e-102">Compensation</span></span>
<span data-ttu-id="9ff6e-103">Wynagrodzenie w Fundacji Przepływu Pracy systemu Windows (WF) to mechanizm, za pomocą którego wcześniej ukończona praca może zostać cofnięta lub skompensowane (zgodnie z logiką zdefiniowaną przez aplikację) po wystąpieniu kolejnej awarii.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="9ff6e-104">W tej sekcji opisano sposób używania kompensacji w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="9ff6e-105">Rekompensata a transakcje</span><span class="sxs-lookup"><span data-stu-id="9ff6e-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="9ff6e-106">Transakcja umożliwia łączenie wielu operacji w jedną jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="9ff6e-107">Za pomocą transakcji daje aplikacji możliwość przerwania (wycofać) wszystkie zmiany wykonane z wewnątrz transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="9ff6e-108">Jednak przy użyciu transakcji może nie być odpowiednie, jeśli praca jest długotrwała.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="9ff6e-109">Na przykład aplikacja planowania podróży jest implementowana jako przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="9ff6e-110">Kroki przepływu pracy mogą polegać na rezerwacji lotu, oczekiwaniu na zatwierdzenie przez menedżera, a następnie opłaceniu lotu.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="9ff6e-111">Proces ten może potrwać wiele dni i nie jest praktyczne dla kroków rezerwacji i płacenia za lot do udziału w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="9ff6e-112">W takim scenariuszu kompensacja może służyć do cofania kroku rezerwacji przepływu pracy, jeśli w dalszej części przetwarzania wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ff6e-113">W tym temacie opisano wynagrodzenie w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="9ff6e-114">Aby uzyskać więcej informacji o transakcjach [Transactions](workflow-transactions.md) w <xref:System.Activities.Statements.TransactionScope>przepływach pracy, zobacz Transakcje i .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="9ff6e-115">Aby uzyskać więcej informacji <xref:System.Transactions?displayProperty=nameWithType> o <xref:System.Transactions.Transaction?displayProperty=nameWithType>transakcjach, zobacz i .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="9ff6e-116">Korzystanie z compensableActivity</span><span class="sxs-lookup"><span data-stu-id="9ff6e-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="9ff6e-117"><xref:System.Activities.Statements.CompensableActivity>jest podstawową działalnością kompensacyjną w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ff6e-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="9ff6e-118">Wszelkie działania, które wykonują pracę, która może wymagać rekompensaty są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>pliku .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="9ff6e-119">W tym przykładzie etap rezerwacji zakupu lotu <xref:System.Activities.Statements.CompensableActivity.Body%2A> jest <xref:System.Activities.Statements.CompensableActivity> umieszczany w a, a <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>anulowanie rezerwacji jest umieszczane w pliku .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="9ff6e-120">Natychmiast po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekają na zatwierdzenie menedżera, a następnie zakończyć etap zakupu lotu.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="9ff6e-121">Jeśli warunek błędu powoduje, że przepływ pracy <xref:System.Activities.Statements.CompensableActivity> zostanie anulowany po pomyślnym <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> zakończeniu, a następnie działania w programie obsługi są zaplanowane i lot jest anulowany.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="9ff6e-122">Poniższy przykład jest przepływ pracy w XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="9ff6e-123">Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="9ff6e-124">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="9ff6e-125">**ManagerApproval: Otrzymano zatwierdzenie menedżera.** 
 **PurchaseFlight: Bilet jest zakupiony.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="9ff6e-126">Przykładowe działania w tym `ReserveFlight` temacie, takie jak wyświetlanie ich nazwy i celu w konsoli, aby pomóc zilustrować kolejność wykonywania działań w przypadku wystąpienia rekompensaty.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="9ff6e-127">Domyślna kompensacja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff6e-127">Default Workflow Compensation</span></span>  
 <span data-ttu-id="9ff6e-128">Domyślnie, jeśli przepływ pracy zostanie anulowany, logika kompensacji jest uruchamiana dla każdego działania wyrównawczego, które zostało pomyślnie całkowicie potwierdzone i nie zostało jeszcze potwierdzone lub zrekompensowane.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ff6e-129"><xref:System.Activities.Statements.CompensableActivity> Po *potwierdzeniu*, rekompensata za działanie nie może być już wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="9ff6e-130">Proces potwierdzenia jest opisany w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="9ff6e-131">W tym przykładzie wyjątek jest zgłaszany po zarezerwuje lot, ale przed krokiem zatwierdzenia menedżera.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="9ff6e-132">W tym przykładzie jest przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-132">This example is the workflow in XAML.</span></span>  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="9ff6e-133">Po wywołaniu przepływu pracy symulowany wyjątek warunku błędu jest <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>obsługiwany przez aplikację hosta w , przepływ pracy jest anulowany, a logika kompensacji jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="9ff6e-134">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="9ff6e-135">**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **Nieobsługiwał się wyjątek:**
**System.ApplicationException: Symulowany warunek błędu w przepływie pracy.** 
 **CancelFlight: Bilet został anulowany.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Anulowano.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="9ff6e-136">Anulowanie i wyrównawcza aktywność</span><span class="sxs-lookup"><span data-stu-id="9ff6e-136">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="9ff6e-137">Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> a <xref:System.Activities.Statements.CompensableActivity> nie zostały zakończone, a działanie zostanie anulowane, działania w są <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> wykonywane.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ff6e-138">Wywoływane <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest tylko wtedy, gdy <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania <xref:System.Activities.Statements.CompensableActivity> w nie zostały zakończone, a działanie zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="9ff6e-139">Jest <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> wykonywany tylko wtedy, gdy <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania <xref:System.Activities.Statements.CompensableActivity> w pomyślnie zakończone i rekompensata jest następnie wywoływana na działanie.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="9ff6e-140">Daje <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> autorom przepływu pracy możliwość zapewnienia odpowiedniej logiki anulowania.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="9ff6e-141">W poniższym przykładzie wyjątek jest zgłaszany podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="9ff6e-142">W tym przykładzie jest przepływ pracy w języku XAML</span><span class="sxs-lookup"><span data-stu-id="9ff6e-142">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="9ff6e-143">Gdy przepływ pracy jest wywoływany, symulowany wyjątek warunku <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.Statements.CompensableActivity> , przepływ pracy jest anulowany, a logika anulowania jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="9ff6e-144">W tym przykładzie logiki wynagrodzeń i logiki anulowania mają różne cele.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="9ff6e-145">Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> ukończono pomyślnie, oznacza to, że karta kredytowa została obciążona i lot zarezerwowany, więc odszkodowanie powinno cofnąć oba kroki.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="9ff6e-146">(W tym przykładzie anulowanie lotu powoduje automatyczne anulowanie opłat za kartę kredytową). Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> jest anulowane, oznacza <xref:System.Activities.Statements.CompensableActivity.Body%2A> to, że nie została <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> ukończona, a więc logika musi być w stanie określić, jak najlepiej obsługiwać anulowanie.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="9ff6e-147">W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje obciążenie kartą kredytową, ale ponieważ `ReserveFlight` była to ostatnia czynność w <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lotu.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="9ff6e-148">Ponieważ `ReserveFlight` była to ostatnia działalność w <xref:System.Activities.Statements.CompensableActivity.Body%2A>, <xref:System.Activities.Statements.CompensableActivity.Body%2A> gdyby została pomyślnie zakończona, to by się zakończyła i nie byłoby możliwe anulowanie.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="9ff6e-149">**ChargeCreditCard: Obciąż kartę kredytową za lot.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="9ff6e-150">**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **Nieobsługiwał się wyjątek:**
**System.ApplicationException: Symulowany warunek błędu w przepływie pracy.** 
 **CancelCreditCard: Anuluj opłaty za karty kredytowe.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Anulowano.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="9ff6e-151">Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="9ff6e-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="9ff6e-152">Jawna kompensacja przy użyciu działania kompensacji</span><span class="sxs-lookup"><span data-stu-id="9ff6e-152">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="9ff6e-153">W poprzedniej sekcji uwzględniono niejawną rekompensatę.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="9ff6e-154">Niejawna kompensacja może być odpowiednia dla prostych scenariuszy, ale jeśli <xref:System.Activities.Statements.Compensate> bardziej jawna kontrola jest wymagana w harmonogramie obsługi wynagrodzeń, działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="9ff6e-155">Aby rozpocząć proces rekompensaty <xref:System.Activities.Statements.Compensate> z <xref:System.Activities.Statements.CompensationToken> działalnością, stosuje się rekompensatę, <xref:System.Activities.Statements.CompensableActivity> dla której wymagana jest rekompensata.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="9ff6e-156">Działanie <xref:System.Activities.Statements.Compensate> może służyć do inicjowania <xref:System.Activities.Statements.CompensableActivity> rekompensaty za wszystkie ukończone, które nie zostały potwierdzone lub zrekompensowane.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="9ff6e-157">Na przykład <xref:System.Activities.Statements.Compensate> działanie może być <xref:System.Activities.Statements.TryCatch.Catches%2A> używane w <xref:System.Activities.Statements.TryCatch> sekcji działania lub <xref:System.Activities.Statements.CompensableActivity> w dowolnym momencie po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="9ff6e-158">W <xref:System.Activities.Statements.Compensate> tym przykładzie działanie jest <xref:System.Activities.Statements.TryCatch.Catches%2A> używane <xref:System.Activities.Statements.TryCatch> w sekcji działania, <xref:System.Activities.Statements.CompensableActivity>aby odwrócić akcję .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="9ff6e-159">W tym przykładzie jest przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-159">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="9ff6e-160">Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="9ff6e-161">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="9ff6e-162">**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **CancelFlight: Bilet został anulowany.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>
### <a name="confirming-compensation"></a><span data-ttu-id="9ff6e-163">Potwierdzenie odszkodowania</span><span class="sxs-lookup"><span data-stu-id="9ff6e-163">Confirming Compensation</span></span>  
 <span data-ttu-id="9ff6e-164">Domyślnie działania podlegające kompensacji można zrekompensować w dowolnym momencie po ich zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="9ff6e-165">W niektórych scenariuszach może to nie być właściwe.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="9ff6e-166">W poprzednim przykładzie rekompensatą za rezerwację biletu było anulowanie rezerwacji.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="9ff6e-167">Jednak po zakończeniu lotu ten etap rekompensaty nie jest już ważny.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="9ff6e-168">Potwierdzenie działania kompensacyjnego wywołuje działanie określone <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>przez .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="9ff6e-169">Jednym z możliwych zastosowań jest umożliwienie wszelkich zasobów, które są niezbędne do wykonania rekompensaty, które mają zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="9ff6e-170">Po potwierdzenie działania kompensacyjnego nie jest możliwe, aby uzyskać rekompensatę, <xref:System.InvalidOperationException> a jeśli jest to próba wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="9ff6e-171">Po pomyślnym zakończeniu przepływu pracy wszystkie nieuwarzanowane i niekompensowane działania kompensacyjne, które zakończyły się pomyślnie, są potwierdzane w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="9ff6e-172">W tym przykładzie lot jest zarezerwowany, zakupiony i ukończony, a następnie działanie wyrównawalne zostaje potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="9ff6e-173">Aby <xref:System.Activities.Statements.CompensableActivity>potwierdzić , <xref:System.Activities.Statements.Confirm> użyj działania <xref:System.Activities.Statements.CompensationToken> i <xref:System.Activities.Statements.CompensableActivity> określ to, aby potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="9ff6e-174">W tym przykładzie jest przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-174">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="9ff6e-175">Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="9ff6e-176">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="9ff6e-177">**ManagerApproval: Otrzymano zatwierdzenie menedżera.** 
 **PurchaseFlight: Bilet jest zakupiony.** 
 **TakeFlight: Lot jest zakończony.** 
 **Potwierdź Lot: Lot został wykonany, nie ma możliwości odszkodowania.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**</span><span class="sxs-lookup"><span data-stu-id="9ff6e-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="9ff6e-178">Zagnieżdżanie działań kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="9ff6e-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="9ff6e-179">A <xref:System.Activities.Statements.CompensableActivity> można umieścić <xref:System.Activities.Statements.CompensableActivity.Body%2A> w sekcji <xref:System.Activities.Statements.CompensableActivity>innego .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="9ff6e-180">A <xref:System.Activities.Statements.CompensableActivity> nie mogą być umieszczone <xref:System.Activities.Statements.CompensableActivity>w obsłudze innego .</span><span class="sxs-lookup"><span data-stu-id="9ff6e-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="9ff6e-181">Obowiązkiem rodzica <xref:System.Activities.Statements.CompensableActivity> jest zapewnienie, że po anulowaniu, potwierdzeniu lub wypłacie odszkodowania wszystkie czynności podlegające wyrównaniu dziecka, które zostały zakończone pomyślnie i nie zostały jeszcze potwierdzone lub zrekompensowane, muszą zostać potwierdzone lub zrekompensowane przed zakończeniem przez rodzica anulowania, potwierdzenia lub odszkodowania.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="9ff6e-182">Jeśli nie jest to modelowane <xref:System.Activities.Statements.CompensableActivity> jawnie nadrzędny będzie niejawnie kompensować podrzędnych compensable działań, jeśli rodzic otrzymał anuluj lub kompensować sygnał.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="9ff6e-183">Jeśli rodzic otrzymał sygnał potwierdzenia, rodzic niejawnie potwierdzi podrzędne działania podlegające kompensacjom.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="9ff6e-184">Jeśli logika do obsługi anulowania, potwierdzenia lub odszkodowania jest jawnie wzorowany w programie obsługi nadrzędnego, <xref:System.Activities.Statements.CompensableActivity>każdy element podrzędny nie jawnie obsługiwane zostaną niejawnie potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="9ff6e-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff6e-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ff6e-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
