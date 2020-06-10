---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 17c05139b5977c47e20e888e436a311ba145018a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597465"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="5239a-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5239a-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="5239a-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="5239a-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="5239a-104">Aby operacja usługi stała się częścią otoczenia transakcji, umieść <xref:System.ServiceModel.Activities.Receive> działanie w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="5239a-105">Wszystkie wywołania wykonane przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania w ramach programu <xref:System.ServiceModel.Activities.TransactedReceiveScope> zostaną również wykonane w obrębie transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="5239a-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="5239a-106">Aplikacja kliencka przepływu pracy może utworzyć otoczenia transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> operacji działania i wywołania usługi przy użyciu transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="5239a-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="5239a-107">W tym temacie omówiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczy w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="5239a-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="5239a-108">Jeśli wystąpienie usługi przepływu pracy jest załadowane w ramach transakcji, a przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działanie, wystąpienie przepływu pracy zostanie zablokowane do momentu przełączenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="5239a-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5239a-109">Za każdym razem, gdy jest używany, <xref:System.ServiceModel.Activities.TransactedReceiveScope> zaleca się umieszczenie wszystkich odbiorów w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.</span><span class="sxs-lookup"><span data-stu-id="5239a-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5239a-110">Gdy użycie <xref:System.ServiceModel.Activities.TransactedReceiveScope> i komunikaty docierają w niepoprawnej kolejności, przepływ pracy zostanie przerwany przy próbie dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="5239a-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="5239a-111">Musisz się upewnić, że przepływ pracy zawsze ma spójny punkt zatrzymania, gdy przepływ pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="5239a-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="5239a-112">Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości, jeśli przepływ pracy zostanie przerwany.</span><span class="sxs-lookup"><span data-stu-id="5239a-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="5239a-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="5239a-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="5239a-114">Utwórz nowe puste rozwiązanie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5239a-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="5239a-115">Dodaj nowy projekt biblioteki klas o nazwie `Common` .</span><span class="sxs-lookup"><span data-stu-id="5239a-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="5239a-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="5239a-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="5239a-117">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="5239a-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="5239a-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5239a-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="5239a-119">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="5239a-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="5239a-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="5239a-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="5239a-121">Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="5239a-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="5239a-122">Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążania <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5239a-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="5239a-123">Jest to działanie natywne, które wyświetla informacje o otaczającej transakcji i jest używane w przepływach pracy usługi i klienta używanych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="5239a-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="5239a-124">Skompiluj rozwiązanie, aby to działanie było dostępne w sekcji **wspólne** w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="5239a-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="5239a-125">Implementowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5239a-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="5239a-126">Dodaj nową usługę przepływu pracy WCF, która jest wywoływana `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="5239a-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="5239a-127">Aby to zrobić, kliknij `Common` projekt, wybierz pozycję **Dodaj**, **nowy element...**, wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **Usługa przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="5239a-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="5239a-129">Usuń ustawienia domyślne `ReceiveRequest` i `SendResponse` działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="5239a-130">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie do `Sequential Service` działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="5239a-131">Ustaw właściwość Text na `"Workflow Service starting ..."` tak, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5239a-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="5239a-132">! [Dodawanie działania WriteLine do działania sekwencyjnego usługi (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="5239a-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="5239a-133">Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działaniu.</span><span class="sxs-lookup"><span data-stu-id="5239a-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="5239a-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie można znaleźć w sekcji **komunikaty** w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="5239a-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="5239a-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie składa się z dwóch sekcji **żądania** i **treści**.</span><span class="sxs-lookup"><span data-stu-id="5239a-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="5239a-136">Sekcja **żądania** zawiera <xref:System.ServiceModel.Activities.Receive> działanie.</span><span class="sxs-lookup"><span data-stu-id="5239a-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="5239a-137">Sekcja **treść** zawiera działania, które należy wykonać w ramach transakcji po odebraniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5239a-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="5239a-139">Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działanie, a następnie kliknij przycisk **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="5239a-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="5239a-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="5239a-140">Add the following variables.</span></span>  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="5239a-142">Istnieje możliwość usunięcia zmiennej danych, która jest domyślnie dostępna.</span><span class="sxs-lookup"><span data-stu-id="5239a-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="5239a-143">Możesz również użyć istniejącej zmiennej dojścia.</span><span class="sxs-lookup"><span data-stu-id="5239a-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="5239a-144">Przeciągnij i upuść <xref:System.ServiceModel.Activities.Receive> działanie w sekcji **żądanie** <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="5239a-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5239a-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="5239a-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5239a-146">Property</span></span>|<span data-ttu-id="5239a-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="5239a-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5239a-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="5239a-148">CanCreateInstance</span></span>|<span data-ttu-id="5239a-149">True (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="5239a-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="5239a-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="5239a-150">OperationName</span></span>|<span data-ttu-id="5239a-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="5239a-151">StartSample</span></span>|  
    |<span data-ttu-id="5239a-152">Samych ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="5239a-152">ServiceContractName</span></span>|<span data-ttu-id="5239a-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="5239a-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="5239a-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-154">The workflow should look like this:</span></span>  
  
     ![Dodawanie działania Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="5239a-156">Kliknij link **Definiuj...** w <xref:System.ServiceModel.Activities.Receive> działaniu i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="5239a-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatów dla działania Odbierz](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="5239a-158">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie do sekcji treść <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="5239a-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="5239a-159">W ramach <xref:System.Activities.Statements.Sequence> działania przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działania, a następnie ustaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5239a-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="5239a-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="5239a-160">Activity</span></span>|<span data-ttu-id="5239a-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="5239a-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5239a-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="5239a-162">1st WriteLine</span></span>|<span data-ttu-id="5239a-163">"Usługa: odbieranie ukończone"</span><span class="sxs-lookup"><span data-stu-id="5239a-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="5239a-164">Druga WriteLine</span><span class="sxs-lookup"><span data-stu-id="5239a-164">2nd WriteLine</span></span>|<span data-ttu-id="5239a-165">"Usługa: Received =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="5239a-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="5239a-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-166">The workflow should now look like this:</span></span>  
  
     ![Sekwencja po dodaniu operacji WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="5239a-168">Przeciągnij i upuść `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działaniu w **treści** <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="5239a-170">Przeciągnij i upuść <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działaniu i ustaw jego właściwości zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="5239a-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="5239a-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5239a-171">Property</span></span>|<span data-ttu-id="5239a-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="5239a-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5239a-173">Do</span><span class="sxs-lookup"><span data-stu-id="5239a-173">To</span></span>|<span data-ttu-id="5239a-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="5239a-174">replyMessage</span></span>|  
    |<span data-ttu-id="5239a-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="5239a-175">Value</span></span>|<span data-ttu-id="5239a-176">"Usługa: wysyłanie odpowiedzi".</span><span class="sxs-lookup"><span data-stu-id="5239a-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="5239a-177">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na wartość "Service: BEGIN Reply".</span><span class="sxs-lookup"><span data-stu-id="5239a-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="5239a-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-178">The workflow should now look like this:</span></span>  
  
     ![Po dodaniu elementu Assign i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="5239a-180">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działanie i wybierz polecenie **Utwórz SendReply** i wklej je po ostatnim <xref:System.Activities.Statements.WriteLine> działaniu.</span><span class="sxs-lookup"><span data-stu-id="5239a-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="5239a-181">Kliknij link **Definiuj...** w `SendReplyToReceive` działaniu, a następnie wprowadź następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5239a-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Ustawienia komunikatu odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="5239a-183">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na wartość "Usługa: odpowiedź wysłana".</span><span class="sxs-lookup"><span data-stu-id="5239a-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="5239a-184">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie u dołu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na wartość "Usługa: przepływ pracy Zakończ, naciśnij klawisz ENTER, aby wyjść".</span><span class="sxs-lookup"><span data-stu-id="5239a-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="5239a-185">Ukończony przepływ pracy usługi powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-185">The completed service workflow should look like this:</span></span>  
  
     ![Pełny przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="5239a-187">Implementowanie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5239a-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="5239a-188">Dodaj nową aplikację przepływu pracy WCF, która jest wywoływana `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="5239a-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="5239a-189">Aby to zrobić, kliknij `Common` projekt, wybierz pozycję **Dodaj**, **nowy element...**, wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **działanie**.</span><span class="sxs-lookup"><span data-stu-id="5239a-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="5239a-191">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="5239a-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="5239a-192">W ramach <xref:System.Activities.Statements.Sequence> działania przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na `"Client: Workflow starting"` .</span><span class="sxs-lookup"><span data-stu-id="5239a-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="5239a-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-193">The workflow should now look like this:</span></span>  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="5239a-195">Przeciągnij i upuść <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działaniu.</span><span class="sxs-lookup"><span data-stu-id="5239a-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="5239a-196">Wybierz <xref:System.Activities.Statements.TransactionScope> działanie, kliknij przycisk zmienne i Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="5239a-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="5239a-198">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie do treści <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="5239a-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="5239a-199">Przeciągnij i upuść `PrintTransactionInfo` działanie w ramach<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="5239a-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="5239a-200">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na wartość "klient: Rozpoczynanie wysyłania".</span><span class="sxs-lookup"><span data-stu-id="5239a-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="5239a-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-201">The workflow should now look like this:</span></span>  
  
     ![Dodawanie klienta: Rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="5239a-203">Przeciągnij i upuść <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5239a-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="5239a-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5239a-204">Property</span></span>|<span data-ttu-id="5239a-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="5239a-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="5239a-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="5239a-206">EndpointConfigurationName</span></span>|<span data-ttu-id="5239a-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="5239a-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="5239a-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="5239a-208">OperationName</span></span>|<span data-ttu-id="5239a-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="5239a-209">StartSample</span></span>|  
    |<span data-ttu-id="5239a-210">Samych ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="5239a-210">ServiceContractName</span></span>|<span data-ttu-id="5239a-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="5239a-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="5239a-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5239a-212">The workflow should now look like this:</span></span>  
  
     ![Ustawianie właściwości działania wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="5239a-214">Kliknij link **Definiuj...** i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="5239a-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Ustawienia wysyłania komunikatu dotyczącego działania](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="5239a-216">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działanie i wybierz pozycję **Utwórz ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="5239a-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="5239a-217"><xref:System.ServiceModel.Activities.ReceiveReply>Działanie zostanie automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działaniu.</span><span class="sxs-lookup"><span data-stu-id="5239a-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="5239a-218">Kliknij przycisk Definiuj... Połącz się z działaniem ReceiveReplyForSend i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="5239a-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="5239a-220">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie między <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> działaniami i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na wartość "Client: Send Complete".</span><span class="sxs-lookup"><span data-stu-id="5239a-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="5239a-221">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na "po stronie klienta: odebrano odpowiedź =" + ReplyMessage</span><span class="sxs-lookup"><span data-stu-id="5239a-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="5239a-222">Przeciągnij i upuść `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działaniu.</span><span class="sxs-lookup"><span data-stu-id="5239a-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="5239a-223">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie na końcu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> Właściwość na "zakończenie przepływu pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="5239a-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="5239a-224">Ukończony przepływ pracy klienta powinien wyglądać podobnie do poniższego diagramu.</span><span class="sxs-lookup"><span data-stu-id="5239a-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="5239a-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5239a-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="5239a-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="5239a-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="5239a-228">Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5239a-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="5239a-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="5239a-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="5239a-230">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="5239a-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="5239a-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5239a-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="5239a-232">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="5239a-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="5239a-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5239a-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="5239a-234">Dodaj do projektu następujący plik App. config.</span><span class="sxs-lookup"><span data-stu-id="5239a-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="5239a-235">Tworzenie aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="5239a-235">Create the client application</span></span>  
  
1. <span data-ttu-id="5239a-236">Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5239a-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="5239a-237">Dodaj odwołanie do elementu System. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="5239a-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="5239a-238">Otwórz plik program.cs i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="5239a-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5239a-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5239a-239">See also</span></span>

- [<span data-ttu-id="5239a-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5239a-240">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="5239a-241">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="5239a-241">Windows Communication Foundation Transactions Overview</span></span>](transactions-overview.md)
