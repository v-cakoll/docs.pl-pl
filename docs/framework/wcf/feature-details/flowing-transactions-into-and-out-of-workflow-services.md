---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185277"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="98d54-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98d54-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="98d54-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="98d54-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="98d54-104">Aby operacja usługi stała się częścią transakcji <xref:System.ServiceModel.Activities.Receive> otoczenia, <xref:System.ServiceModel.Activities.TransactedReceiveScope> umieść działanie w działaniu.</span><span class="sxs-lookup"><span data-stu-id="98d54-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="98d54-105">Wszelkie połączenia wykonane <xref:System.ServiceModel.Activities.Send> przez <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania w ramach będą również dokonywane w ramach transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="98d54-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="98d54-106">Aplikacja kliencka przepływu pracy można utworzyć <xref:System.Activities.Statements.TransactionScope> transakcję otoczenia przy użyciu operacji działania i wywołania usługi przy użyciu transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="98d54-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="98d54-107">W tym temacie opracowywanie tworzenia usługi przepływu pracy i klienta przepływu pracy, które uczestniczą w transakcjach.</span><span class="sxs-lookup"><span data-stu-id="98d54-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="98d54-108">Jeśli wystąpienie usługi przepływu pracy jest ładowane <xref:System.Activities.Statements.Persist> w ramach transakcji, a przepływ pracy zawiera działanie, wystąpienie przepływu pracy zostanie zablokowane, dopóki nie wydłuży się limit czasu transakcji.</span><span class="sxs-lookup"><span data-stu-id="98d54-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="98d54-109">Za każdym razem, gdy używasz <xref:System.ServiceModel.Activities.TransactedReceiveScope> zaleca się umieścić <xref:System.ServiceModel.Activities.TransactedReceiveScope> wszystkie odbiera w przepływie pracy w działaniach.</span><span class="sxs-lookup"><span data-stu-id="98d54-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="98d54-110">Podczas <xref:System.ServiceModel.Activities.TransactedReceiveScope> korzystania i wiadomości przychodzą w niewłaściwej kolejności, przepływ pracy zostanie przerwana podczas próby dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="98d54-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="98d54-111">Należy upewnić się, że przepływ pracy jest zawsze w spójnym punkcie zatrzymania, gdy przepływ pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="98d54-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="98d54-112">Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości w przypadku przerwania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="98d54-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="98d54-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="98d54-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="98d54-114">Utwórz nowe puste rozwiązanie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98d54-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="98d54-115">Dodaj nowy projekt biblioteki klas o nazwie `Common`.</span><span class="sxs-lookup"><span data-stu-id="98d54-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="98d54-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="98d54-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="98d54-117">Plik System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="98d54-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="98d54-119">Plik System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="98d54-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="98d54-121">Dodaj nową klasę `PrintTransactionInfo` wywoływaną `Common` do projektu.</span><span class="sxs-lookup"><span data-stu-id="98d54-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="98d54-122">Ta klasa jest <xref:System.Activities.NativeActivity> pochodną i <xref:System.Activities.NativeActivity.Execute%2A> przeciąża metodę.</span><span class="sxs-lookup"><span data-stu-id="98d54-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="98d54-123">Jest to działanie macierzyste, które wyświetla informacje o transakcji otoczenia i jest używany zarówno w przepływach pracy usługi i klienta używane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="98d54-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="98d54-124">Skompiluj rozwiązanie, aby udostępnić to działanie w sekcji **Wspólne** **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="98d54-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="98d54-125">Implementowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98d54-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="98d54-126">Dodaj nową usługę przepływu pracy WCF, wywoływaną `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="98d54-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="98d54-127">Aby to zrobić, `Common` kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**, **Nowy element ...**, Wybierz przepływ **pracy** w obszarze **Zainstalowane szablony** i wybierz pozycję Usługa przepływu pracy **WCF**.</span><span class="sxs-lookup"><span data-stu-id="98d54-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="98d54-129">Usuń ustawienia `ReceiveRequest` `SendResponse` domyślne i działania.</span><span class="sxs-lookup"><span data-stu-id="98d54-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="98d54-130">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść aktywność do `Sequential Service` działania.</span><span class="sxs-lookup"><span data-stu-id="98d54-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="98d54-131">Ustaw właściwość `"Workflow Service starting ..."` text, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="98d54-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="98d54-132">! [Dodawanie działania WriteLine do działania Sekwencyjnej usługi(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="98d54-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="98d54-133">Przeciągnij i <xref:System.ServiceModel.Activities.TransactedReceiveScope> upuść po <xref:System.Activities.Statements.WriteLine> aktywności.</span><span class="sxs-lookup"><span data-stu-id="98d54-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="98d54-134">Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> można znaleźć w sekcji **Wiadomości** w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="98d54-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="98d54-135">Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> składa się z dwóch sekcji **Żądanie** i **Treść**.</span><span class="sxs-lookup"><span data-stu-id="98d54-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="98d54-136">Sekcja **Żądanie** zawiera <xref:System.ServiceModel.Activities.Receive> działanie.</span><span class="sxs-lookup"><span data-stu-id="98d54-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="98d54-137">**Treść** Sekcja zawiera działania do wykonania w ramach transakcji po odebraniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="98d54-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="98d54-139">Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działanie i kliknij przycisk **Zmienne.**</span><span class="sxs-lookup"><span data-stu-id="98d54-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="98d54-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="98d54-140">Add the following variables.</span></span>  
  
     ![Dodawanie zmiennych do skrytu TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="98d54-142">Zmienną danych, która jest tam domyślnie.</span><span class="sxs-lookup"><span data-stu-id="98d54-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="98d54-143">Można również użyć istniejącej zmiennej dojścia.</span><span class="sxs-lookup"><span data-stu-id="98d54-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="98d54-144">Przeciągnij i <xref:System.ServiceModel.Activities.Receive> upuść działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> w sekcji **Żądanie** działania.</span><span class="sxs-lookup"><span data-stu-id="98d54-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="98d54-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="98d54-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="98d54-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="98d54-146">Property</span></span>|<span data-ttu-id="98d54-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d54-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="98d54-148">Cancreateinstance</span><span class="sxs-lookup"><span data-stu-id="98d54-148">CanCreateInstance</span></span>|<span data-ttu-id="98d54-149">Prawda (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="98d54-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="98d54-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="98d54-150">OperationName</span></span>|<span data-ttu-id="98d54-151">PoczątekPróby</span><span class="sxs-lookup"><span data-stu-id="98d54-151">StartSample</span></span>|  
    |<span data-ttu-id="98d54-152">Nazwa kontraktu servicecontract</span><span class="sxs-lookup"><span data-stu-id="98d54-152">ServiceContractName</span></span>|<span data-ttu-id="98d54-153">ITransactionPróbuj</span><span class="sxs-lookup"><span data-stu-id="98d54-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="98d54-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-154">The workflow should look like this:</span></span>  
  
     ![Dodawanie działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="98d54-156">Kliknij **łącze Definiuj...** w <xref:System.ServiceModel.Activities.Receive> działaniu i wykonuj następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="98d54-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatu dla działania Odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="98d54-158">Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść aktywność <xref:System.ServiceModel.Activities.TransactedReceiveScope>do sekcji Treść .</span><span class="sxs-lookup"><span data-stu-id="98d54-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="98d54-159">W <xref:System.Activities.Statements.Sequence> ramach działania przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działania i ustaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="98d54-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="98d54-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="98d54-160">Activity</span></span>|<span data-ttu-id="98d54-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d54-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="98d54-162">1. WriteLine</span><span class="sxs-lookup"><span data-stu-id="98d54-162">1st WriteLine</span></span>|<span data-ttu-id="98d54-163">"Usługa: Odbiór zakończony"</span><span class="sxs-lookup"><span data-stu-id="98d54-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="98d54-164">2. WriteLine</span><span class="sxs-lookup"><span data-stu-id="98d54-164">2nd WriteLine</span></span>|<span data-ttu-id="98d54-165">"Usługa: Odebrane = " + requestMessage</span><span class="sxs-lookup"><span data-stu-id="98d54-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="98d54-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-166">The workflow should now look like this:</span></span>  
  
     ![Sekwencja po dodaniu działań WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="98d54-168">Przeciągnij i `PrintTransactionInfo` upuść <xref:System.Activities.Statements.WriteLine> aktywność po <xref:System.ServiceModel.Activities.TransactedReceiveScope> drugim działaniu w **treści** w działaniu.</span><span class="sxs-lookup"><span data-stu-id="98d54-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="98d54-170">Przeciągnij i <xref:System.Activities.Statements.Assign> upuść działanie po `PrintTransactionInfo` działaniu i ustaw jej właściwości zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="98d54-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="98d54-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="98d54-171">Property</span></span>|<span data-ttu-id="98d54-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d54-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="98d54-173">Do</span><span class="sxs-lookup"><span data-stu-id="98d54-173">To</span></span>|<span data-ttu-id="98d54-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="98d54-174">replyMessage</span></span>|  
    |<span data-ttu-id="98d54-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d54-175">Value</span></span>|<span data-ttu-id="98d54-176">"Usługa: Wysyłanie odpowiedzi".</span><span class="sxs-lookup"><span data-stu-id="98d54-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="98d54-177">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Usługa: Rozpocznij odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="98d54-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="98d54-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-178">The workflow should now look like this:</span></span>  
  
     ![Po dodaniu Przypisz i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="98d54-180">Kliknij prawym <xref:System.ServiceModel.Activities.Receive> przyciskiem myszy działanie i wybierz polecenie **Utwórz wyślijReply** i wklej je po ostatnim <xref:System.Activities.Statements.WriteLine> działaniu.</span><span class="sxs-lookup"><span data-stu-id="98d54-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="98d54-181">Kliknij **łącze Definiuj...** w `SendReplyToReceive` działaniu i wykonuj następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="98d54-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Ustawienia wiadomości odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="98d54-183">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po `SendReplyToReceive` <xref:System.Activities.Statements.WriteLine.Text%2A> działaniu i ustaw jego właściwość na "Usługa: Odpowiedź wysłana".</span><span class="sxs-lookup"><span data-stu-id="98d54-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="98d54-184">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie u dołu <xref:System.Activities.Statements.WriteLine.Text%2A> przepływu pracy i ustaw jego właściwość na "Service: Workflow ends, press ENTER to exit".</span><span class="sxs-lookup"><span data-stu-id="98d54-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="98d54-185">Ukończony przepływ pracy usługi powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-185">The completed service workflow should look like this:</span></span>  
  
     ![Ukończ przepływ pracy serwisu](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="98d54-187">Zaimplementowanie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98d54-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="98d54-188">Dodaj nową aplikację przepływu pracy WCF, wywoływaną `WorkflowClient` `Common` do projektu.</span><span class="sxs-lookup"><span data-stu-id="98d54-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="98d54-189">Aby to zrobić, `Common` kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**, **Nowy element ...**, Wybierz przepływ **pracy** w obszarze **Zainstalowane szablony** i wybierz **pozycję Aktywność**.</span><span class="sxs-lookup"><span data-stu-id="98d54-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Dodawanie projektu działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="98d54-191">Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść aktywność na powierzchnię projektową.</span><span class="sxs-lookup"><span data-stu-id="98d54-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="98d54-192">W <xref:System.Activities.Statements.Sequence> obrębie działania przeciągnij i <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> upuść działanie i ustaw jego właściwość na `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="98d54-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="98d54-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-193">The workflow should now look like this:</span></span>  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="98d54-195">Przeciągnij i <xref:System.Activities.Statements.TransactionScope> upuść aktywność po działaniu. <xref:System.Activities.Statements.WriteLine></span><span class="sxs-lookup"><span data-stu-id="98d54-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="98d54-196">Wybierz <xref:System.Activities.Statements.TransactionScope> działanie, kliknij przycisk Zmienne i dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="98d54-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Dodawanie zmiennych do transactionscope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="98d54-198">Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść działanie <xref:System.Activities.Statements.TransactionScope> do treści działania.</span><span class="sxs-lookup"><span data-stu-id="98d54-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="98d54-199">Przeciąganie `PrintTransactionInfo` i upuszczanie aktywności w obrębie<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="98d54-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="98d54-200">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po `PrintTransactionInfo` działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Klient: Początek wysyłania".</span><span class="sxs-lookup"><span data-stu-id="98d54-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="98d54-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-201">The workflow should now look like this:</span></span>  
  
     ![Dodawanie klienta: rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="98d54-203">Przeciągnij i <xref:System.ServiceModel.Activities.Send> upuść działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="98d54-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="98d54-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="98d54-204">Property</span></span>|<span data-ttu-id="98d54-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="98d54-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="98d54-206">Nazwa konfiguracji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="98d54-206">EndpointConfigurationName</span></span>|<span data-ttu-id="98d54-207">punkt usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98d54-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="98d54-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="98d54-208">OperationName</span></span>|<span data-ttu-id="98d54-209">PoczątekPróby</span><span class="sxs-lookup"><span data-stu-id="98d54-209">StartSample</span></span>|  
    |<span data-ttu-id="98d54-210">Nazwa kontraktu servicecontract</span><span class="sxs-lookup"><span data-stu-id="98d54-210">ServiceContractName</span></span>|<span data-ttu-id="98d54-211">ITransactionPróbuj</span><span class="sxs-lookup"><span data-stu-id="98d54-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="98d54-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="98d54-212">The workflow should now look like this:</span></span>  
  
     ![Ustawianie właściwości działania Wyślij](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="98d54-214">Kliknij **łącze Definiuj...** i wykonuj następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="98d54-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Ustawienia wiadomości o działaniu](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="98d54-216">Kliknij prawym <xref:System.ServiceModel.Activities.Send> przyciskiem myszy aktywność i wybierz polecenie **Utwórz receivereply**.</span><span class="sxs-lookup"><span data-stu-id="98d54-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="98d54-217">Działanie <xref:System.ServiceModel.Activities.ReceiveReply> zostanie automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> zakończeniu działania.</span><span class="sxs-lookup"><span data-stu-id="98d54-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="98d54-218">Kliknij przycisk Definiuj... łącze do działania ReceiveReplyForSend i wykonuj następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="98d54-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="98d54-220">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść <xref:System.ServiceModel.Activities.ReceiveReply> działanie między <xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.ServiceModel.Activities.Send> i działania i ustawić jego właściwość na "Klient: Wyślij zakończone."</span><span class="sxs-lookup"><span data-stu-id="98d54-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="98d54-221">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Strona klienta: Odpowiedź odebrana = " + replyMessage</span><span class="sxs-lookup"><span data-stu-id="98d54-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="98d54-222">Przeciągnij i `PrintTransactionInfo` upuść aktywność po działaniu. <xref:System.Activities.Statements.WriteLine></span><span class="sxs-lookup"><span data-stu-id="98d54-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="98d54-223">Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie na końcu <xref:System.Activities.Statements.WriteLine.Text%2A> przepływu pracy i ustaw jego właściwość na "Kończy się przepływ pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="98d54-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="98d54-224">Ukończony przepływ pracy klienta powinien wyglądać jak na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="98d54-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="98d54-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="98d54-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="98d54-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="98d54-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="98d54-228">Dodaj nowy projekt aplikacji `Service` konsoli wywoływany do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="98d54-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="98d54-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="98d54-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="98d54-230">Plik System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="98d54-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="98d54-232">Plik System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="98d54-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="98d54-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="98d54-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3. <span data-ttu-id="98d54-234">Dodaj następujący plik app.config do projektu.</span><span class="sxs-lookup"><span data-stu-id="98d54-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="98d54-235">Tworzenie aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="98d54-235">Create the client application</span></span>  
  
1. <span data-ttu-id="98d54-236">Dodaj nowy projekt aplikacji `Client` konsoli wywoływany do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="98d54-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="98d54-237">Dodaj odwołanie do pliku System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="98d54-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="98d54-238">Otwórz plik program.cs i dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="98d54-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98d54-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98d54-239">See also</span></span>

- [<span data-ttu-id="98d54-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98d54-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="98d54-241">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="98d54-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
