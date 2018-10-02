---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: f53bfa3c745a0d487a8daf23f399c1420e36c8ec
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036055"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="c25cb-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c25cb-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="c25cb-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="c25cb-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="c25cb-104">Dla operacji usługowej, które staną się częścią otoczenia transakcji, należy umieścić <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="c25cb-105">Wywołania przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wprowadzone w ramach transakcji otoczenia.</span><span class="sxs-lookup"><span data-stu-id="c25cb-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="c25cb-106">Aplikacja kliencka przepływu pracy można utworzyć otoczenia transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działania i wywoływać operacje usługi, za pomocą otoczenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="c25cb-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="c25cb-107">Ten temat przeprowadzi Cię przez tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="c25cb-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c25cb-108">Jeśli wystąpienie usługi przepływu pracy jest ładowany w obrębie transakcji i przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania ulegnie zawieszeniu wystąpienia przepływu pracy, dopóki nie upłynie limit czasu transakcji.</span><span class="sxs-lookup"><span data-stu-id="c25cb-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c25cb-109">Zawsze, gdy używasz <xref:System.ServiceModel.Activities.TransactedReceiveScope> zalecane jest umieszczenie wszystkich odbiera w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.</span><span class="sxs-lookup"><span data-stu-id="c25cb-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c25cb-110">Korzystając z <xref:System.ServiceModel.Activities.TransactedReceiveScope> i dociera nieprawidłowa kolejność, przepływ pracy zostanie przerwany podczas próby dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="c25cb-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="c25cb-111">Upewnij się, że przepływ pracy jest zawsze w spójny punktu zatrzymania podczas idles przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c25cb-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="c25cb-112">Pozwoli to ponowne uruchomienie przepływu pracy od poprzedniego punktu trwałości powinien przerwanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c25cb-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="c25cb-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="c25cb-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="c25cb-114">Utwórz nowe puste rozwiązanie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c25cb-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="c25cb-115">Dodaj nowy projekt biblioteki klas o nazwie `Common`.</span><span class="sxs-lookup"><span data-stu-id="c25cb-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="c25cb-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="c25cb-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="c25cb-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="c25cb-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="c25cb-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="c25cb-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="c25cb-121">Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="c25cb-122">Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążenia <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c25cb-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="c25cb-123">Jest to działania natywnego, wyświetla informacje o otoczenia transakcji, która jest używana w przepływach pracy usługa i klient używaną w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c25cb-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="c25cb-124">Kompiluj rozwiązanie, aby udostępnić to działanie w **typowe** części **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="c25cb-125">Implementowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c25cb-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="c25cb-126">Dodaj nową usługę przepływu pracy WCF, o nazwie `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="c25cb-127">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **usługi przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     <span data-ttu-id="c25cb-128">![Dodawanie usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span><span class="sxs-lookup"><span data-stu-id="c25cb-128">![Adding a Workflow Service](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span></span>  
  
2.  <span data-ttu-id="c25cb-129">Usuń domyślną `ReceiveRequest` i `SendResponse` działań.</span><span class="sxs-lookup"><span data-stu-id="c25cb-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="c25cb-130">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie do `Sequential Service` działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="c25cb-131">Ustawienie właściwości text `"Workflow Service starting ..."` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c25cb-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="c25cb-132">![Dodawanie działań WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="c25cb-132">![Adding a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span></span>  
  
4.  <span data-ttu-id="c25cb-133">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="c25cb-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania można znaleźć w **komunikatów** części **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="c25cb-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania składa się z dwóch części **żądania** i **treści**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="c25cb-136">**Żądania** sekcja zawiera <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="c25cb-137">**Treści** sekcja zawiera czynności do wykonania w ramach transakcji po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     <span data-ttu-id="c25cb-138">![Dodawanie działań TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TR, Technical Router")</span><span class="sxs-lookup"><span data-stu-id="c25cb-138">![Adding a TransactedReceiveScope activity](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span></span>  
  
5.  <span data-ttu-id="c25cb-139">Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania i kliknij przycisk **zmienne** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c25cb-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="c25cb-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="c25cb-140">Add the following variables.</span></span>  
  
     <span data-ttu-id="c25cb-141">![Dodawanie zmiennych do TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span><span class="sxs-lookup"><span data-stu-id="c25cb-141">![Adding Variables to the TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c25cb-142">Można usunąć zmiennej danych, która jest domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c25cb-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="c25cb-143">Można również użyć istniejącą zmienną dojście.</span><span class="sxs-lookup"><span data-stu-id="c25cb-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="c25cb-144">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Receive> działania w ramach **żądania** części <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="c25cb-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c25cb-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="c25cb-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c25cb-146">Property</span></span>|<span data-ttu-id="c25cb-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="c25cb-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c25cb-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="c25cb-148">CanCreateInstance</span></span>|<span data-ttu-id="c25cb-149">Wartość true (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="c25cb-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="c25cb-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="c25cb-150">OperationName</span></span>|<span data-ttu-id="c25cb-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="c25cb-151">StartSample</span></span>|  
    |<span data-ttu-id="c25cb-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="c25cb-152">ServiceContractName</span></span>|<span data-ttu-id="c25cb-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="c25cb-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="c25cb-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-154">The workflow should look like this:</span></span>  
  
     <span data-ttu-id="c25cb-155">![Dodawanie działania odbierania](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span><span class="sxs-lookup"><span data-stu-id="c25cb-155">![Adding a Receive activity](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span></span>  
  
7.  <span data-ttu-id="c25cb-156">Kliknij przycisk **zdefiniować...**  łącze w <xref:System.ServiceModel.Activities.Receive> działania i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="c25cb-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     <span data-ttu-id="c25cb-157">![Konfigurowanie ustawień wiadomości dla działania Odbierz](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="c25cb-157">![Setting message settings for the Recieve activity](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span></span>  
  
8.  <span data-ttu-id="c25cb-158">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działanie do sekcji Body <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="c25cb-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="c25cb-159">W ramach <xref:System.Activities.Statements.Sequence> działanie przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działań i zestaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c25cb-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c25cb-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="c25cb-160">Activity</span></span>|<span data-ttu-id="c25cb-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="c25cb-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c25cb-162">WriteLine 1.</span><span class="sxs-lookup"><span data-stu-id="c25cb-162">1st WriteLine</span></span>|<span data-ttu-id="c25cb-163">"Usługa: odbieranie ukończone"</span><span class="sxs-lookup"><span data-stu-id="c25cb-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="c25cb-164">WriteLine 2</span><span class="sxs-lookup"><span data-stu-id="c25cb-164">2nd WriteLine</span></span>|<span data-ttu-id="c25cb-165">"Usługa: odebrano =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="c25cb-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="c25cb-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-166">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="c25cb-167">![Dodawanie działań WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span><span class="sxs-lookup"><span data-stu-id="c25cb-167">![Adding WriteLine activities](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span></span>  
  
9. <span data-ttu-id="c25cb-168">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działania w **treści** w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     <span data-ttu-id="c25cb-169">![Po dodaniu PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span><span class="sxs-lookup"><span data-stu-id="c25cb-169">![After adding PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span></span>  
  
10. <span data-ttu-id="c25cb-170">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działania i ustaw jego właściwości, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="c25cb-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="c25cb-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c25cb-171">Property</span></span>|<span data-ttu-id="c25cb-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="c25cb-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c25cb-173">Zadanie</span><span class="sxs-lookup"><span data-stu-id="c25cb-173">To</span></span>|<span data-ttu-id="c25cb-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="c25cb-174">replyMessage</span></span>|  
    |<span data-ttu-id="c25cb-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="c25cb-175">Value</span></span>|<span data-ttu-id="c25cb-176">"Usługa: wysyłanie odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="c25cb-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="c25cb-177">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: Rozpocznij odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="c25cb-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="c25cb-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-178">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="c25cb-179">![Po dodaniu Przypisywanie i WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span><span class="sxs-lookup"><span data-stu-id="c25cb-179">![After adding Assign and WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span></span>  
  
12. <span data-ttu-id="c25cb-180">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działania, a następnie wybierz pozycję **tworzenie SendReply** i wkleić go po ostatnim <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="c25cb-181">Kliknij przycisk **zdefiniować...**  łącze w `SendReplyToReceive` działania i wprowadź następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c25cb-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     <span data-ttu-id="c25cb-182">![Ustawienia wiadomości odpowiedzi](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="c25cb-182">![Reply message settings](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span></span>  
  
13. <span data-ttu-id="c25cb-183">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działanie i zestaw ma <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: odpowiedź wysłana."</span><span class="sxs-lookup"><span data-stu-id="c25cb-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="c25cb-184">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania w dolnej części przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: przepływ pracy zostaje zakończona, naciśnij klawisz ENTER, aby zakończyć."</span><span class="sxs-lookup"><span data-stu-id="c25cb-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="c25cb-185">Przepływu pracy zakończonych usługi powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-185">The completed service workflow should look like this:</span></span>  
  
     <span data-ttu-id="c25cb-186">![Ukończ przepływ pracy usługi](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span><span class="sxs-lookup"><span data-stu-id="c25cb-186">![Complete Service Workflow](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span></span>  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="c25cb-187">Implementowanie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c25cb-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="c25cb-188">Dodaj nową aplikację przepływu pracy WCF o nazwie `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="c25cb-189">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **działania**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     <span data-ttu-id="c25cb-190">![Dodaj projekt działania](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span><span class="sxs-lookup"><span data-stu-id="c25cb-190">![Add an Activity project](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span></span>  
  
2.  <span data-ttu-id="c25cb-191">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="c25cb-192">W ramach <xref:System.Activities.Statements.Sequence> działania przeciągania i upuszczania <xref:System.Activities.Statements.WriteLine> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="c25cb-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="c25cb-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-193">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="c25cb-194">![Dodaj działanie WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="c25cb-194">![Add a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span></span>  
  
4.  <span data-ttu-id="c25cb-195">Przeciąganie i upuszczanie <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="c25cb-196">Wybierz <xref:System.Activities.Statements.TransactionScope> działania, kliknij przycisk Zmienne i dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="c25cb-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     <span data-ttu-id="c25cb-197">![Dodaj zmienne do elementu TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span><span class="sxs-lookup"><span data-stu-id="c25cb-197">![Add variables to the TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span></span>  
  
5.  <span data-ttu-id="c25cb-198">Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania w treści <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="c25cb-199">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie <xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="c25cb-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="c25cb-200">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Klient: Wyślij początku".</span><span class="sxs-lookup"><span data-stu-id="c25cb-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="c25cb-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-201">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="c25cb-202">![Dodawanie działań](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span><span class="sxs-lookup"><span data-stu-id="c25cb-202">![Adding activities](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span></span>  
  
8.  <span data-ttu-id="c25cb-203">Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c25cb-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="c25cb-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c25cb-204">Property</span></span>|<span data-ttu-id="c25cb-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="c25cb-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c25cb-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c25cb-206">EndpointConfigurationName</span></span>|<span data-ttu-id="c25cb-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="c25cb-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="c25cb-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="c25cb-208">OperationName</span></span>|<span data-ttu-id="c25cb-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="c25cb-209">StartSample</span></span>|  
    |<span data-ttu-id="c25cb-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="c25cb-210">ServiceContractName</span></span>|<span data-ttu-id="c25cb-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="c25cb-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="c25cb-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c25cb-212">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="c25cb-213">![Ustawianie właściwości działania wysyłania](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span><span class="sxs-lookup"><span data-stu-id="c25cb-213">![Setting the Send activity properties](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span></span>  
  
9. <span data-ttu-id="c25cb-214">Kliknij przycisk **zdefiniować...**  połączyć, a następnie wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="c25cb-214">Click the **Define...** link and make the following settings:</span></span>  
  
     <span data-ttu-id="c25cb-215">![Wysyłanie działania ustawień komunikatów](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="c25cb-215">![Send activity message settings](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span></span>  
  
10. <span data-ttu-id="c25cb-216">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działania, a następnie wybierz pozycję **tworzenie ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="c25cb-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="c25cb-217"><xref:System.ServiceModel.Activities.ReceiveReply> Działania zostaną automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="c25cb-218">Kliknij przycisk Definiuj... link działanie ReceiveReplyForSend i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="c25cb-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     <span data-ttu-id="c25cb-219">![Konfigurowanie ustawień wiadomości ReceiveForSend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="c25cb-219">![Setting the ReceiveForSend message settings](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span></span>  
  
12. <span data-ttu-id="c25cb-220">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania między <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "klienta: Wyślij pełne."</span><span class="sxs-lookup"><span data-stu-id="c25cb-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="c25cb-221">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "po stronie klienta: odebrano odpowiedzi na =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="c25cb-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="c25cb-222">Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="c25cb-223">Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania na końcu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Kończy się przepływu pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="c25cb-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="c25cb-224">Przepływ pracy ukończonej klienta powinien wyglądać jak poniższy diagram.</span><span class="sxs-lookup"><span data-stu-id="c25cb-224">The completed client workflow should look like the following diagram.</span></span>  
  
     <span data-ttu-id="c25cb-225">![Workfliow ukończone klienta](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span><span class="sxs-lookup"><span data-stu-id="c25cb-225">![The completed client workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span></span>  
  
16. <span data-ttu-id="c25cb-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c25cb-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="c25cb-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="c25cb-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="c25cb-228">Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="c25cb-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="c25cb-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="c25cb-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="c25cb-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="c25cb-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c25cb-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="c25cb-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="c25cb-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="c25cb-234">Dodaj następujący plik app.config do projektu.</span><span class="sxs-lookup"><span data-stu-id="c25cb-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="c25cb-235">Tworzenie aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="c25cb-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="c25cb-236">Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c25cb-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="c25cb-237">Dodaj odwołanie do System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="c25cb-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="c25cb-238">Otwórz plik program.cs i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="c25cb-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c25cb-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c25cb-239">See Also</span></span>  

- [<span data-ttu-id="c25cb-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c25cb-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
- [<span data-ttu-id="c25cb-241">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="c25cb-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)