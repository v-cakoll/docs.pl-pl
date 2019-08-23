---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935427"
---
# <a name="compensation"></a><span data-ttu-id="eeb0d-102">Kompensacja</span><span class="sxs-lookup"><span data-stu-id="eeb0d-102">Compensation</span></span>
<span data-ttu-id="eeb0d-103">Kompensacja w Windows Workflow Foundation (WF) to mechanizm, za pomocą którego poprzednio ukończona czynność może zostać cofnięta lub wynagradzana (zgodnie z logiką zdefiniowaną przez aplikację) w przypadku wystąpienia kolejnego błędu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="eeb0d-104">W tej sekcji opisano sposób korzystania z kompensacji w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="eeb0d-105">Kompensacja a Transakcje</span><span class="sxs-lookup"><span data-stu-id="eeb0d-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="eeb0d-106">Transakcja umożliwia łączenie wielu operacji w pojedynczą jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="eeb0d-107">Użycie transakcji umożliwia aplikacji przerwanie (Przywracanie) wszystkich zmian wykonywanych w ramach transakcji w przypadku wystąpienia błędów występujących w ramach procesu transakcji.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="eeb0d-108">Jednak użycie transakcji może być nieodpowiednie, jeśli prace są długotrwałe.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="eeb0d-109">Na przykład aplikacja do planowania podróży jest zaimplementowana jako przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="eeb0d-110">Kroki przepływu pracy mogą obejmować zarezerwowanie lotu, oczekiwanie na zatwierdzenie przez kierownika, a następnie zapłacenie za lot.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="eeb0d-111">Ten proces może potrwać wiele dni i nie jest praktyczny w przypadku czynności związanych z rezerwacją i uiszczeniem opłat za uczestnictwo w tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="eeb0d-112">W takim scenariuszu można użyć kompensacji w celu cofnięcia etapu rezerwacji przepływu pracy w przypadku wystąpienia błędu w dalszej części przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eeb0d-113">W tym temacie omówiono odszkodowanie w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="eeb0d-114">Aby uzyskać więcej informacji o transakcjach w [](workflow-transactions.md) przepływach <xref:System.Activities.Statements.TransactionScope>pracy, zobacz transakcje i.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="eeb0d-115">Aby uzyskać więcej informacji na temat transakcji <xref:System.Transactions?displayProperty=nameWithType> , <xref:System.Transactions.Transaction?displayProperty=nameWithType>Zobacz i.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="eeb0d-116">Korzystanie z działanie CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="eeb0d-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="eeb0d-117"><xref:System.Activities.Statements.CompensableActivity>to podstawowe działanie związane z kompensacją w programie [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eeb0d-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="eeb0d-118">Wszelkie działania wykonujące zadania, które mogą być wymagane do uzyskania wynagrodzenia, są umieszczane <xref:System.Activities.Statements.CompensableActivity.Body%2A> w <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="eeb0d-119">W tym przykładzie etap rezerwacji zakupu lotu jest umieszczany w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> a, a anulowanie <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezerwacji jest umieszczane w.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="eeb0d-120">Natychmiast po <xref:System.Activities.Statements.CompensableActivity> przeniesieniu do przepływu pracy są dwa działania, które oczekują na zatwierdzenie przez Menedżera, a następnie ukończą krok zakupu lotu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="eeb0d-121">Jeśli warunek błędu powoduje, że przepływ pracy zostanie anulowany po <xref:System.Activities.Statements.CompensableActivity> pomyślnym zakończeniu, wówczas działania w ramach <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> programu obsługi są zaplanowane, a lot zostanie anulowany.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="eeb0d-122">Poniższy przykład to przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="eeb0d-123">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="eeb0d-124">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="eeb0d-125">**ManagerApproval: Odebrano zatwierdzenie przez Menedżera.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="eeb0d-126">**PurchaseFlight: Zakupiony bilet.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="eeb0d-127">**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
> <span data-ttu-id="eeb0d-128">Przykładowe działania w tym temacie, takie jak `ReserveFlight` wyświetlanie ich nazwy i przeznaczenia do konsoli programu, aby ułatwić zilustrowanie kolejności, w której działania są wykonywane, gdy nastąpi kompensacja.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="eeb0d-129">Domyślna kompensacja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="eeb0d-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="eeb0d-130">Domyślnie, jeśli przepływ pracy zostanie anulowany, logika kompensacji jest uruchamiana dla wszystkich działań kompensacyjne, które zostały pomyślnie kompletne i nie zostały jeszcze potwierdzone lub wynagradzane.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eeb0d-131">Po potwierdzeniu, nie można już wywołać kompensaty dla działania. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="eeb0d-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="eeb0d-132">Proces potwierdzania został opisany w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="eeb0d-133">W tym przykładzie wyjątek jest zgłaszany po zarezerwacji lotu, ale przed etapem zatwierdzania przez Menedżera.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="eeb0d-134">Ten przykład to przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="eeb0d-135">Gdy przepływ pracy jest wywoływany, wyjątek symulowanego warunku błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowany, a logika kompensacji jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="eeb0d-136">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="eeb0d-137">**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="eeb0d-138">**Nieobsługiwany wyjątek przepływu pracy:**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="eeb0d-139">**System. ApplicationException: Symulowany warunek błędu w przepływie pracy.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="eeb0d-140">**CancelFlight: Bilet został anulowany.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="eeb0d-141">**Przepływ pracy został pomyślnie ukończony ze stanem: Szkodliw.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="eeb0d-142">Anulowanie i działanie CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="eeb0d-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="eeb0d-143">Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> ramach programu nie zostały ukończone i działanie zostało anulowane <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , działania w programie są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eeb0d-144">Jest <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> wywoływana tylko w przypadku, gdy działania <xref:System.Activities.Statements.CompensableActivity.Body%2A> z programu <xref:System.Activities.Statements.CompensableActivity> nie zostały ukończone i działanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="eeb0d-145">Jest wykonywane tylko wtedy, gdy działania <xref:System.Activities.Statements.CompensableActivity.Body%2A> z programu <xref:System.Activities.Statements.CompensableActivity> zostały pomyślnie wykonane i wynagrodzenie jest następnie wywoływane dla działania. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A></span><span class="sxs-lookup"><span data-stu-id="eeb0d-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="eeb0d-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Daje autorom przepływu pracy możliwość zapewnienia odpowiedniej logiki anulowania.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="eeb0d-147">W poniższym przykładzie wyjątek jest zgłaszany podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> następnie wywoływany.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="eeb0d-148">Ten przykład to przepływ pracy w języku XAML</span><span class="sxs-lookup"><span data-stu-id="eeb0d-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="eeb0d-149">Gdy przepływ pracy jest wywoływany, wyjątek symulowanego warunku błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowany, a logika <xref:System.Activities.Statements.CompensableActivity> anulowania jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="eeb0d-150">W tym przykładzie logika kompensacji i logika anulowania mają różne cele.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="eeb0d-151">Jeśli zakończyło się <xref:System.Activities.Statements.CompensableActivity.Body%2A> pomyślnie, oznacza to, że opłata za kartę kredytową została naliczona i jest ona księgowana zgodnie z zapisem, dlatego należy cofnąć obie czynności.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="eeb0d-152">(W tym przykładzie anulowanie lotu automatycznie anuluje opłaty za kartę kredytową). Jeśli <xref:System.Activities.Statements.CompensableActivity> jednak zostanie anulowana, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> nie została ukończona, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> więc logika musi być w stanie określić, jak najlepiej obsłużyć anulowanie.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="eeb0d-153">W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłaty za kartę kredytową, ale od czasu `ReserveFlight` ostatniego działania w programie <xref:System.Activities.Statements.CompensableActivity.Body%2A>nie jest podejmowana próba anulowania lotu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="eeb0d-154">Ponieważ `ReserveFlight` była ostatnią aktywnością <xref:System.Activities.Statements.CompensableActivity.Body%2A>w programie, w przypadku pomyślnego wykonania <xref:System.Activities.Statements.CompensableActivity.Body%2A> operacji zostałaby ukończona i nie będzie możliwe jej anulowanie.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="eeb0d-155">**ChargeCreditCard: Opłata za kartę kredytową dla lotu.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="eeb0d-156">**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="eeb0d-157">**Nieobsługiwany wyjątek przepływu pracy:**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="eeb0d-158">**System. ApplicationException: Symulowany warunek błędu w przepływie pracy.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="eeb0d-159">**CancelCreditCard: Anuluj opłaty za karty kredytowe.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="eeb0d-160">**Przepływ pracy został pomyślnie ukończony ze stanem: Szkodliw.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="eeb0d-161">Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="eeb0d-161">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="eeb0d-162">Jawne wynagrodzenie przy użyciu działania kompensacja</span><span class="sxs-lookup"><span data-stu-id="eeb0d-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="eeb0d-163">W poprzedniej sekcji podano niejawną kompensację.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="eeb0d-164">Niejawne kompensacje mogą być odpowiednie w przypadku prostych scenariuszy, ale jeśli jest wymagana bardziej jawna kontrola nad planowaniem <xref:System.Activities.Statements.Compensate> obsługi kompensacji, działanie może być używane.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="eeb0d-165">W celu zainicjowania procesu <xref:System.Activities.Statements.Compensate> kompensacji działania <xref:System.Activities.Statements.CompensationToken> należy użyć elementu <xref:System.Activities.Statements.CompensableActivity> , dla którego jest wymagana kompensacja.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="eeb0d-166">Działanie może służyć do inicjowania kompensaty dla wszystkich ukończonych <xref:System.Activities.Statements.CompensableActivity> , które nie zostały potwierdzone lub wynagradzane. <xref:System.Activities.Statements.Compensate></span><span class="sxs-lookup"><span data-stu-id="eeb0d-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="eeb0d-167">Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane <xref:System.Activities.Statements.TryCatch.Catches%2A> w sekcji <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="eeb0d-168">W tym przykładzie <xref:System.Activities.Statements.Compensate> działanie jest używane <xref:System.Activities.Statements.TryCatch.Catches%2A> w sekcji <xref:System.Activities.Statements.TryCatch> działania w celu odwrócenia akcji <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="eeb0d-169">Ten przykład to przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="eeb0d-170">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="eeb0d-171">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="eeb0d-172">**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="eeb0d-173">**CancelFlight: Bilet został anulowany.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="eeb0d-174">**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="eeb0d-175">Potwierdzanie kompensaty</span><span class="sxs-lookup"><span data-stu-id="eeb0d-175">Confirming Compensation</span></span>  
 <span data-ttu-id="eeb0d-176">Domyślnie działania kompensacyjne mogą być kompensowane w dowolnym momencie po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="eeb0d-177">W niektórych scenariuszach może to nie być odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="eeb0d-178">W poprzednim przykładzie wynagrodzenie związane z odświadczeniem biletu zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="eeb0d-179">Jednak po ukończeniu lotu ten krok kompensaty nie jest już ważny.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="eeb0d-180">Potwierdzenie działania kompensacyjne wywołuje działanie określone przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="eeb0d-181">Jednym z tych możliwości jest umożliwienie wszelkim zasobom, które są niezbędne do zwolnienia wyrównania.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="eeb0d-182">Po potwierdzeniu działania kompensacyjne nie jest możliwe jego kompensowanie, a jeśli zostanie podjęta próba <xref:System.InvalidOperationException> , zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="eeb0d-183">Gdy przepływ pracy zakończy się pomyślnie, wszystkie niepotwierdzone i niekompensowane działania kompensacyjne, które zostały zakończone pomyślnie, są potwierdzone w odwrotnej kolejności uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="eeb0d-184">W tym przykładzie lot jest zastrzeżony, zakupiony i zakończony, a następnie działanie kompensacyjne zostało potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="eeb0d-185">Aby potwierdzić <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Confirm> Użyj <xref:System.Activities.Statements.CompensationToken> działania<xref:System.Activities.Statements.CompensableActivity> i określ, aby potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="eeb0d-186">Ten przykład to przepływ pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-186">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="eeb0d-187">Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="eeb0d-188">**ReserveFlight: Bilet jest zarezerwowany.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="eeb0d-189">**ManagerApproval: Odebrano zatwierdzenie przez Menedżera.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="eeb0d-190">**PurchaseFlight: Zakupiony bilet.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="eeb0d-191">**TakeFlight: Działanie lotu zostało zakończone.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="eeb0d-192">**ConfirmFlight: Nastąpiło przeprowadzenie lotu, bez możliwości dokonania kompensacji.**  </span><span class="sxs-lookup"><span data-stu-id="eeb0d-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="eeb0d-193">**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**</span><span class="sxs-lookup"><span data-stu-id="eeb0d-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="eeb0d-194">Zagnieżdżanie działań związanych z kompensacją</span><span class="sxs-lookup"><span data-stu-id="eeb0d-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="eeb0d-195">Można umieścić w sekcji innej <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="eeb0d-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="eeb0d-196">Nie może być umieszczony w procedurze obsługi innej <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="eeb0d-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="eeb0d-197">Zadaniem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> jest upewnienie się, że gdy zostanie on anulowany, potwierdzony lub wynagradzany, wszystkie podrzędne działania kompensacyjne, które zostały zakończone pomyślnie i nie zostały jeszcze potwierdzone lub kompensowane, muszą zostać potwierdzone lub kompensowane przed zakończeniem anulowania, potwierdzenia lub kompensacji elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="eeb0d-198">Jeśli nie jest to jawnie modelowane, obiekt <xref:System.Activities.Statements.CompensableActivity> nadrzędny będzie niejawnie kompensować podrzędne działania kompensacyjne, jeśli element nadrzędny otrzymał sygnał Cancel lub kompensacja.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="eeb0d-199">Jeśli element nadrzędny otrzymał sygnał Confirm, element nadrzędny będzie niejawnie potwierdzał podrzędne działania kompensacyjne.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="eeb0d-200">Jeśli logika do obsługi anulowania, potwierdzenia lub kompensacji jest jawnie modelowana w procedurze obsługi elementu nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, wszelkie elementy podrzędne, które nie zostały jawnie obsłużone, zostaną niejawnie potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="eeb0d-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeb0d-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eeb0d-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
