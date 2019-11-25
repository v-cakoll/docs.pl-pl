---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ea14bc651258684fd31940aa6b88f9731348dcd1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978281"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="a5ec7-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a5ec7-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="a5ec7-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="a5ec7-104">Aby operacja usługi była częścią otoczenia transakcji, umieść <xref:System.ServiceModel.Activities.Receive> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="a5ec7-105">Wszystkie wywołania podejmowane przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wykonane w obrębie transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="a5ec7-106">Aplikacja kliencka przepływu pracy może utworzyć otoczenia transakcji przy użyciu działania <xref:System.Activities.Statements.TransactionScope> i operacji wywołania usługi przy użyciu transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="a5ec7-107">W tym temacie omówiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczy w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a5ec7-108">Jeśli wystąpienie usługi przepływu pracy jest załadowane w ramach transakcji, a przepływ pracy zawiera działanie <xref:System.Activities.Statements.Persist>, wystąpienie przepływu pracy będzie blokowane do momentu przełączenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5ec7-109">Za każdym razem, gdy korzystasz z <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zaleca się umieszczenie wszystkich odbiorów w przepływie pracy w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działaniach.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5ec7-110">W przypadku używania <xref:System.ServiceModel.Activities.TransactedReceiveScope> i komunikatów w niepoprawnej kolejności przepływ pracy zostanie przerwany przy próbie dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="a5ec7-111">Musisz się upewnić, że przepływ pracy zawsze ma spójny punkt zatrzymania, gdy przepływ pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="a5ec7-112">Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości, jeśli przepływ pracy zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="a5ec7-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="a5ec7-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="a5ec7-114">Utwórz nowe puste rozwiązanie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="a5ec7-115">Dodaj nowy projekt biblioteki klas o nazwie `Common`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="a5ec7-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="a5ec7-117">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="a5ec7-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="a5ec7-119">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="a5ec7-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="a5ec7-121">Dodaj nową klasę o nazwie `PrintTransactionInfo` do projektu `Common`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="a5ec7-122">Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążania metody <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="a5ec7-123">Jest to działanie natywne, które wyświetla informacje o otaczającej transakcji i jest używane w przepływach pracy usługi i klienta używanych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="a5ec7-124">Skompiluj rozwiązanie, aby to działanie było dostępne w sekcji **wspólne** w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="a5ec7-125">Implementowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a5ec7-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="a5ec7-126">Dodaj nową usługę przepływu pracy WCF o nazwie `WorkflowService` do projektu `Common`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="a5ec7-127">Aby to zrobić, kliknij projekt `Common`, wybierz pozycję **Dodaj**, **nowy element...** , wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **Usługa przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="a5ec7-129">Usuń domyślne działania `ReceiveRequest` i `SendResponse`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="a5ec7-130">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> do działania `Sequential Service`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="a5ec7-131">Ustaw właściwość Text na `"Workflow Service starting ..."`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="a5ec7-132">! [Dodawanie działania WriteLine do działania sekwencyjnego usługi (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="a5ec7-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="a5ec7-133">Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> po działaniu <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="a5ec7-134">Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> można znaleźć w sekcji **komunikaty** w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="a5ec7-135">Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> składa się z dwóch sekcji jako **żądanie** i **treść**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="a5ec7-136">Sekcja **żądania** zawiera działanie <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="a5ec7-137">Sekcja **treść** zawiera działania, które należy wykonać w ramach transakcji po odebraniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="a5ec7-139">Wybierz działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> i kliknij przycisk **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="a5ec7-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="a5ec7-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-140">Add the following variables.</span></span>  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="a5ec7-142">Istnieje możliwość usunięcia zmiennej danych, która jest domyślnie dostępna.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="a5ec7-143">Możesz również użyć istniejącej zmiennej dojścia.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="a5ec7-144">Przeciągnij i upuść działanie <xref:System.ServiceModel.Activities.Receive> w sekcji **żądanie** działania <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="a5ec7-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="a5ec7-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-146">Property</span></span>|<span data-ttu-id="a5ec7-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a5ec7-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="a5ec7-148">CanCreateInstance</span></span>|<span data-ttu-id="a5ec7-149">True (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="a5ec7-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="a5ec7-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="a5ec7-150">OperationName</span></span>|<span data-ttu-id="a5ec7-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="a5ec7-151">StartSample</span></span>|  
    |<span data-ttu-id="a5ec7-152">Samych ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="a5ec7-152">ServiceContractName</span></span>|<span data-ttu-id="a5ec7-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="a5ec7-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="a5ec7-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-154">The workflow should look like this:</span></span>  
  
     ![Dodawanie działania Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="a5ec7-156">Kliknij link **Definiuj...** w działaniu <xref:System.ServiceModel.Activities.Receive> i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatów dla działania Odbierz](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="a5ec7-158">Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> w sekcji treść <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="a5ec7-159">W ramach działania <xref:System.Activities.Statements.Sequence> przeciągnij i upuść dwa działania <xref:System.Activities.Statements.WriteLine> i ustaw właściwości <xref:System.Activities.Statements.WriteLine.Text%2A>, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a5ec7-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="a5ec7-160">Activity</span></span>|<span data-ttu-id="a5ec7-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a5ec7-162">1\. WriteLine</span><span class="sxs-lookup"><span data-stu-id="a5ec7-162">1st WriteLine</span></span>|<span data-ttu-id="a5ec7-163">"Usługa: odbieranie ukończone"</span><span class="sxs-lookup"><span data-stu-id="a5ec7-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="a5ec7-164">Druga WriteLine</span><span class="sxs-lookup"><span data-stu-id="a5ec7-164">2nd WriteLine</span></span>|<span data-ttu-id="a5ec7-165">"Usługa: Received =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="a5ec7-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="a5ec7-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-166">The workflow should now look like this:</span></span>  
  
     ![Sekwencja po dodaniu operacji WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="a5ec7-168">Przeciągnij i upuść działanie `PrintTransactionInfo` po drugim działaniu <xref:System.Activities.Statements.WriteLine> w **treści** w działaniu <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="a5ec7-170">Przeciągnij i upuść działanie <xref:System.Activities.Statements.Assign> po działaniu `PrintTransactionInfo` i ustaw jego właściwości zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="a5ec7-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-171">Property</span></span>|<span data-ttu-id="a5ec7-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a5ec7-173">Do</span><span class="sxs-lookup"><span data-stu-id="a5ec7-173">To</span></span>|<span data-ttu-id="a5ec7-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="a5ec7-174">replyMessage</span></span>|  
    |<span data-ttu-id="a5ec7-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-175">Value</span></span>|<span data-ttu-id="a5ec7-176">"Usługa: wysyłanie odpowiedzi".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="a5ec7-177">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu <xref:System.Activities.Statements.Assign> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "Service: BEGIN Reply".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="a5ec7-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-178">The workflow should now look like this:</span></span>  
  
     ![Po dodaniu elementu Assign i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="a5ec7-180">Kliknij prawym przyciskiem myszy działanie <xref:System.ServiceModel.Activities.Receive> i wybierz polecenie **Utwórz SendReply** i wklej je po ostatnim działaniu <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="a5ec7-181">Kliknij link **Definiuj...** w działaniu `SendReplyToReceive` i wprowadź następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Ustawienia komunikatu odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="a5ec7-183">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu `SendReplyToReceive` i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Usługa: odpowiedź wysłana".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="a5ec7-184">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> u dołu przepływu pracy i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Usługa: przepływ pracy Zakończ, a następnie naciśnij klawisz ENTER, aby wyjść".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="a5ec7-185">Ukończony przepływ pracy usługi powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-185">The completed service workflow should look like this:</span></span>  
  
     ![Pełny przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="a5ec7-187">Implementowanie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a5ec7-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="a5ec7-188">Dodaj nową aplikację przepływu pracy WCF o nazwie `WorkflowClient` do projektu `Common`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="a5ec7-189">Aby to zrobić, kliknij projekt `Common`, wybierz pozycję **Dodaj**, **nowy element...** , wybierz **pozycję przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **działanie**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="a5ec7-191">Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="a5ec7-192">W ramach działania <xref:System.Activities.Statements.Sequence> przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="a5ec7-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-193">The workflow should now look like this:</span></span>  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="a5ec7-195">Przeciągnij i upuść działanie <xref:System.Activities.Statements.TransactionScope> po działaniu <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="a5ec7-196">Wybierz działanie <xref:System.Activities.Statements.TransactionScope>, kliknij przycisk zmienne, a następnie Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="a5ec7-198">Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> w treści <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="a5ec7-199">Przeciągnij i upuść działanie `PrintTransactionInfo` w <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="a5ec7-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="a5ec7-200">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu `PrintTransactionInfo` i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "klient: Rozpoczynanie wysyłania".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="a5ec7-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-201">The workflow should now look like this:</span></span>  
  
     ![Dodawanie klienta: Rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="a5ec7-203">Przeciągnij i upuść działanie <xref:System.ServiceModel.Activities.Send> po działaniu <xref:System.Activities.Statements.Assign> i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="a5ec7-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-204">Property</span></span>|<span data-ttu-id="a5ec7-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="a5ec7-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a5ec7-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="a5ec7-206">EndpointConfigurationName</span></span>|<span data-ttu-id="a5ec7-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="a5ec7-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="a5ec7-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="a5ec7-208">OperationName</span></span>|<span data-ttu-id="a5ec7-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="a5ec7-209">StartSample</span></span>|  
    |<span data-ttu-id="a5ec7-210">Samych ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="a5ec7-210">ServiceContractName</span></span>|<span data-ttu-id="a5ec7-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="a5ec7-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="a5ec7-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-212">The workflow should now look like this:</span></span>  
  
     ![Ustawianie właściwości działania wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="a5ec7-214">Kliknij link **Definiuj...** i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Ustawienia wysyłania komunikatu dotyczącego działania](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="a5ec7-216">Kliknij prawym przyciskiem myszy działanie <xref:System.ServiceModel.Activities.Send> i wybierz pozycję **Utwórz ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="a5ec7-217">Działanie <xref:System.ServiceModel.Activities.ReceiveReply> zostanie automatycznie umieszczone po działaniu <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="a5ec7-218">Kliknij przycisk Definiuj... Połącz się z działaniem ReceiveReplyForSend i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="a5ec7-220">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> między działaniami <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Client: Send Complete".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="a5ec7-221">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu <xref:System.ServiceModel.Activities.ReceiveReply> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "po stronie klienta: odebrano odpowiedź =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="a5ec7-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="a5ec7-222">Przeciągnij i upuść działanie `PrintTransactionInfo` po działaniu <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="a5ec7-223">Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> na końcu przepływu pracy i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "zakończenie przepływu pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="a5ec7-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="a5ec7-224">Ukończony przepływ pracy klienta powinien wyglądać podobnie do poniższego diagramu.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="a5ec7-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="a5ec7-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="a5ec7-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="a5ec7-228">Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="a5ec7-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="a5ec7-230">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="a5ec7-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="a5ec7-232">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="a5ec7-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="a5ec7-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a5ec7-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. <span data-ttu-id="a5ec7-234">Dodaj do projektu następujący plik App. config.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="a5ec7-235">Tworzenie aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="a5ec7-235">Create the client application</span></span>  
  
1. <span data-ttu-id="a5ec7-236">Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="a5ec7-237">Dodaj odwołanie do elementu System. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="a5ec7-238">Otwórz plik program.cs i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a5ec7-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client              
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5ec7-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5ec7-239">See also</span></span>

- [<span data-ttu-id="a5ec7-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a5ec7-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="a5ec7-241">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="a5ec7-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
