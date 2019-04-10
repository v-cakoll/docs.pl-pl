---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 25ab4e415ce2cd6044cedef4841c1ba88254542e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315117"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="78b2e-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="78b2e-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="78b2e-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="78b2e-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="78b2e-104">Dla operacji usługowej, które staną się częścią otoczenia transakcji, należy umieścić <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="78b2e-105">Wywołania przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wprowadzone w ramach transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="78b2e-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="78b2e-106">Aplikacja kliencka przepływu pracy można utworzyć otoczenia transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działania i wywoływać operacje usługi, za pomocą otoczenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="78b2e-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="78b2e-107">Ten temat przeprowadzi Cię przez tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="78b2e-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="78b2e-108">Jeśli wystąpienie usługi przepływu pracy jest ładowany w obrębie transakcji i przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania ulegnie zawieszeniu wystąpienia przepływu pracy, dopóki nie upłynie limit czasu transakcji.</span><span class="sxs-lookup"><span data-stu-id="78b2e-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78b2e-109">Zawsze, gdy używasz <xref:System.ServiceModel.Activities.TransactedReceiveScope> zalecane jest umieszczenie wszystkich odbiera w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.</span><span class="sxs-lookup"><span data-stu-id="78b2e-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78b2e-110">Korzystając z <xref:System.ServiceModel.Activities.TransactedReceiveScope> i dociera nieprawidłowa kolejność, przepływ pracy zostanie przerwany podczas próby dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="78b2e-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="78b2e-111">Upewnij się, że przepływ pracy jest zawsze w spójny punktu zatrzymania podczas idles przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="78b2e-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="78b2e-112">Pozwoli to ponowne uruchomienie przepływu pracy od poprzedniego punktu trwałości powinien przerwanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="78b2e-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="78b2e-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="78b2e-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="78b2e-114">Utwórz nowe puste rozwiązanie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78b2e-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="78b2e-115">Dodaj nowy projekt biblioteki klas o nazwie `Common`.</span><span class="sxs-lookup"><span data-stu-id="78b2e-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="78b2e-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="78b2e-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="78b2e-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="78b2e-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="78b2e-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="78b2e-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="78b2e-121">Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="78b2e-122">Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążenia <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="78b2e-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="78b2e-123">Jest to działania natywnego, wyświetla informacje o otoczenia transakcji, która jest używana w przepływach pracy usługa i klient używaną w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="78b2e-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="78b2e-124">Kompiluj rozwiązanie, aby udostępnić to działanie w **typowe** części **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="78b2e-125">Implementowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="78b2e-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="78b2e-126">Dodaj nową usługę przepływu pracy WCF, o nazwie `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="78b2e-127">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **usługi przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="78b2e-129">Usuń domyślną `ReceiveRequest` i `SendResponse` działań.</span><span class="sxs-lookup"><span data-stu-id="78b2e-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="78b2e-130">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie do `Sequential Service` działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="78b2e-131">Ustawienie właściwości text `"Workflow Service starting ..."` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="78b2e-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="78b2e-132">! [Dodawanie działań WriteLine activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) usługa Sekwencyjna</span><span class="sxs-lookup"><span data-stu-id="78b2e-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="78b2e-133">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="78b2e-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania można znaleźć w **komunikatów** części **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="78b2e-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania składa się z dwóch części **żądania** i **treści**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="78b2e-136">**Żądania** sekcja zawiera <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="78b2e-137">**Treści** sekcja zawiera czynności do wykonania w ramach transakcji po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Dodawanie działania elementu TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="78b2e-139">Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania i kliknij przycisk **zmienne** przycisku.</span><span class="sxs-lookup"><span data-stu-id="78b2e-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="78b2e-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="78b2e-140">Add the following variables.</span></span>  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  <span data-ttu-id="78b2e-142">Można usunąć zmiennej danych, która jest domyślnie.</span><span class="sxs-lookup"><span data-stu-id="78b2e-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="78b2e-143">Można również użyć istniejącą zmienną dojście.</span><span class="sxs-lookup"><span data-stu-id="78b2e-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="78b2e-144">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Receive> działania w ramach **żądania** części <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="78b2e-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="78b2e-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="78b2e-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="78b2e-146">Property</span></span>|<span data-ttu-id="78b2e-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="78b2e-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="78b2e-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="78b2e-148">CanCreateInstance</span></span>|<span data-ttu-id="78b2e-149">Wartość true (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="78b2e-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="78b2e-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="78b2e-150">OperationName</span></span>|<span data-ttu-id="78b2e-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="78b2e-151">StartSample</span></span>|  
    |<span data-ttu-id="78b2e-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="78b2e-152">ServiceContractName</span></span>|<span data-ttu-id="78b2e-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="78b2e-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="78b2e-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-154">The workflow should look like this:</span></span>  
  
     ![Dodawanie działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="78b2e-156">Kliknij przycisk **zdefiniować...**  łącze w <xref:System.ServiceModel.Activities.Receive> działania i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="78b2e-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Konfigurowanie ustawień wiadomości działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="78b2e-158">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działanie do sekcji Body <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="78b2e-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="78b2e-159">W ramach <xref:System.Activities.Statements.Sequence> działanie przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działań i zestaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="78b2e-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="78b2e-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="78b2e-160">Activity</span></span>|<span data-ttu-id="78b2e-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="78b2e-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="78b2e-162">WriteLine 1.</span><span class="sxs-lookup"><span data-stu-id="78b2e-162">1st WriteLine</span></span>|<span data-ttu-id="78b2e-163">"Usługa: Otrzymywać ukończone"</span><span class="sxs-lookup"><span data-stu-id="78b2e-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="78b2e-164">WriteLine 2</span><span class="sxs-lookup"><span data-stu-id="78b2e-164">2nd WriteLine</span></span>|<span data-ttu-id="78b2e-165">"Usługa: Odebrano = "+ requestMessage</span><span class="sxs-lookup"><span data-stu-id="78b2e-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="78b2e-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-166">The workflow should now look like this:</span></span>  
  
     ![Sekwencja po dodaniu działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="78b2e-168">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działania w **treści** w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="78b2e-170">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działania i ustaw jego właściwości, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="78b2e-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="78b2e-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="78b2e-171">Property</span></span>|<span data-ttu-id="78b2e-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="78b2e-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="78b2e-173">Zadanie</span><span class="sxs-lookup"><span data-stu-id="78b2e-173">To</span></span>|<span data-ttu-id="78b2e-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="78b2e-174">replyMessage</span></span>|  
    |<span data-ttu-id="78b2e-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="78b2e-175">Value</span></span>|<span data-ttu-id="78b2e-176">"Usługa: Wysyłanie odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="78b2e-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="78b2e-177">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: Rozpocznij odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="78b2e-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="78b2e-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-178">The workflow should now look like this:</span></span>  
  
     ![Po dodaniu Przypisywanie i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="78b2e-180">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działania, a następnie wybierz pozycję **tworzenie SendReply** i wkleić go po ostatnim <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="78b2e-181">Kliknij przycisk **zdefiniować...**  łącze w `SendReplyToReceive` działania i wprowadź następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="78b2e-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Ustawienia wiadomości odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="78b2e-183">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działanie i zestaw ma <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: Odpowiedź wysłana".</span><span class="sxs-lookup"><span data-stu-id="78b2e-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="78b2e-184">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania w dolnej części przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Service: Przepływ pracy zostaje zakończona, naciśnij klawisz ENTER, aby zakończyć pracę."</span><span class="sxs-lookup"><span data-stu-id="78b2e-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="78b2e-185">Przepływu pracy zakończonych usługi powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-185">The completed service workflow should look like this:</span></span>  
  
     ![Ukończ przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="78b2e-187">Implementowanie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="78b2e-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="78b2e-188">Dodaj nową aplikację przepływu pracy WCF o nazwie `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="78b2e-189">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **działania**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="78b2e-191">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="78b2e-192">W ramach <xref:System.Activities.Statements.Sequence> działania przeciągania i upuszczania <xref:System.Activities.Statements.WriteLine> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="78b2e-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="78b2e-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-193">The workflow should now look like this:</span></span>  
  
     ![Dodaj działanie WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="78b2e-195">Przeciąganie i upuszczanie <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="78b2e-196">Wybierz <xref:System.Activities.Statements.TransactionScope> działania, kliknij przycisk Zmienne i dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="78b2e-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="78b2e-198">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania w treści <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="78b2e-199">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie</span><span class="sxs-lookup"><span data-stu-id="78b2e-199">Drag and drop a `PrintTransactionInfo` activity within the</span></span> <xref:System.Activities.Statements.Sequence>  
  
7. <span data-ttu-id="78b2e-200">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "klienta: Rozpoczynanie wysyłania".</span><span class="sxs-lookup"><span data-stu-id="78b2e-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="78b2e-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-201">The workflow should now look like this:</span></span>  
  
     ![Dodawanie klienta: Począwszy od działań wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="78b2e-203">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="78b2e-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="78b2e-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="78b2e-204">Property</span></span>|<span data-ttu-id="78b2e-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="78b2e-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="78b2e-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="78b2e-206">EndpointConfigurationName</span></span>|<span data-ttu-id="78b2e-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="78b2e-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="78b2e-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="78b2e-208">OperationName</span></span>|<span data-ttu-id="78b2e-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="78b2e-209">StartSample</span></span>|  
    |<span data-ttu-id="78b2e-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="78b2e-210">ServiceContractName</span></span>|<span data-ttu-id="78b2e-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="78b2e-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="78b2e-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="78b2e-212">The workflow should now look like this:</span></span>  
  
     ![Ustawianie właściwości działań wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="78b2e-214">Kliknij przycisk **zdefiniować...**  połączyć, a następnie wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="78b2e-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Wysyłanie działania ustawienia wiadomości](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="78b2e-216">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działania, a następnie wybierz pozycję **tworzenie ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="78b2e-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="78b2e-217"><xref:System.ServiceModel.Activities.ReceiveReply> Działania zostaną automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="78b2e-218">Kliknij przycisk Definiuj... link działanie ReceiveReplyForSend i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="78b2e-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Konfigurowanie ustawień wiadomości ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="78b2e-220">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania między <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "klienta: Wyślij pełne."</span><span class="sxs-lookup"><span data-stu-id="78b2e-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="78b2e-221">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "po stronie klienta: Otrzymana odpowiedź = "+ replyMessage</span><span class="sxs-lookup"><span data-stu-id="78b2e-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="78b2e-222">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="78b2e-223">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania na końcu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Kończy się przepływu pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="78b2e-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="78b2e-224">Przepływ pracy ukończonej klienta powinien wyglądać jak poniższy diagram.</span><span class="sxs-lookup"><span data-stu-id="78b2e-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Przepływ pracy ukończonej klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="78b2e-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="78b2e-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="78b2e-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="78b2e-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="78b2e-228">Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="78b2e-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="78b2e-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="78b2e-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="78b2e-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="78b2e-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="78b2e-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="78b2e-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="78b2e-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```  
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
  
3. <span data-ttu-id="78b2e-234">Dodaj następujący plik app.config do projektu.</span><span class="sxs-lookup"><span data-stu-id="78b2e-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="78b2e-235">Tworzenie aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="78b2e-235">Create the client application</span></span>  
  
1. <span data-ttu-id="78b2e-236">Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="78b2e-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="78b2e-237">Dodaj odwołanie do System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="78b2e-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="78b2e-238">Otwórz plik program.cs i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="78b2e-238">Open the program.cs file and add the following code.</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="78b2e-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78b2e-239">See also</span></span>

- [<span data-ttu-id="78b2e-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="78b2e-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="78b2e-241">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="78b2e-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
