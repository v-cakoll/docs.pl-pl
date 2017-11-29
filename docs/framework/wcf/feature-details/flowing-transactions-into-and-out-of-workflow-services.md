---
title: "Przepływy transakcji do i z usług przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a093c2bfb0d7e60c3edc4a6ab04c8a7b7e38601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="f401d-102">Przepływy transakcji do i z usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f401d-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="f401d-103">Usługi przepływu pracy i klienci mogą uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="f401d-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="f401d-104">Dla operacji usługi stać się częścią transakcja otoczenia, umieść <xref:System.ServiceModel.Activities.Receive> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="f401d-105">Wywołań przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wprowadzone w ramach transakcja otoczenia.</span><span class="sxs-lookup"><span data-stu-id="f401d-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="f401d-106">Aplikacja kliencka przepływu pracy można utworzyć transakcja otoczenia przy użyciu <xref:System.Activities.Statements.TransactionScope> działania i wywołania operacji usługi przy użyciu transakcja otoczenia.</span><span class="sxs-lookup"><span data-stu-id="f401d-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="f401d-107">W tym temacie przedstawiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="f401d-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f401d-108">Jeśli wystąpienie usługi przepływu pracy jest ładowany w ramach transakcji i przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania wystąpienia przepływu pracy zawiesza się dopóki nie upłynie limit czasu transakcji.</span><span class="sxs-lookup"><span data-stu-id="f401d-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f401d-109">Zawsze, gdy używana <xref:System.ServiceModel.Activities.TransactedReceiveScope> zaleca się umieścić wszystkie działania Receive w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.</span><span class="sxs-lookup"><span data-stu-id="f401d-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f401d-110">Korzystając z <xref:System.ServiceModel.Activities.TransactedReceiveScope> i nadchodzą komunikaty w niepoprawna kolejność, przepływ pracy zostanie przerwany podczas próby dostarczenia pierwszego komunikatu poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="f401d-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="f401d-111">Należy się upewnić, że przepływ pracy jest zawsze na spójną punktu zatrzymania podczas idles przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f401d-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="f401d-112">Umożliwi to ponowne uruchomienie przepływu pracy od poprzedniego punktu trwałości powinien przerwanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f401d-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="f401d-113">Tworzenie biblioteki udostępnionej</span><span class="sxs-lookup"><span data-stu-id="f401d-113">Create a shared library</span></span>  
  
1.  <span data-ttu-id="f401d-114">Utwórz nowe puste rozwiązanie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f401d-114">Create a new empty Visual Studio Solution.</span></span>  
  
2.  <span data-ttu-id="f401d-115">Dodawanie nowego projektu biblioteki klas o nazwie `Common`.</span><span class="sxs-lookup"><span data-stu-id="f401d-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="f401d-116">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="f401d-116">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="f401d-117">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-117">System.Activities.dll</span></span>  
  
    -   <span data-ttu-id="f401d-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-118">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="f401d-119">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-119">System.ServiceModel.Activities.dll</span></span>  
  
    -   <span data-ttu-id="f401d-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-120">System.Transactions.dll</span></span>  
  
3.  <span data-ttu-id="f401d-121">Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="f401d-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="f401d-122">Ta klasa pochodzi od <xref:System.Activities.NativeActivity> i overloads <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f401d-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="f401d-123">Jest to działania natywnego, która wyświetla informacje o transakcja otoczenia i jest używany w przepływach pracy usługa i klient używane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f401d-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="f401d-124">Skompiluj rozwiązanie, aby udostępnić to działanie w **typowe** sekcji **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="f401d-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="f401d-125">Wdrożenie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f401d-125">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="f401d-126">Dodaj nową [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przepływu pracy, o nazwie `WorkflowService` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="f401d-126">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="f401d-127">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, zaznacz **Dodaj**, **nowy element...** , Wybierz pozycję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **usługi przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="f401d-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     <span data-ttu-id="f401d-128">![Dodawanie usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span><span class="sxs-lookup"><span data-stu-id="f401d-128">![Adding a Workflow Service](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")</span></span>  
  
2.  <span data-ttu-id="f401d-129">Usunąć domyślną `ReceiveRequest` i `SendResponse` działań.</span><span class="sxs-lookup"><span data-stu-id="f401d-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3.  <span data-ttu-id="f401d-130">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania do `Sequential Service` działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="f401d-131">Wartość właściwości text `"Workflow Service starting ..."` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f401d-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="f401d-132">![Dodawanie działania WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="f401d-132">![Adding a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")</span></span>  
  
4.  <span data-ttu-id="f401d-133">Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="f401d-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania można znaleźć w **wiadomości** sekcji **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="f401d-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="f401d-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania składa się z dwóch części **żądania** i **treści**.</span><span class="sxs-lookup"><span data-stu-id="f401d-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="f401d-136">**Żądania** sekcja zawiera <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="f401d-137">**Treści** sekcja zawiera działania, które można wykonać w ramach transakcji po otrzymaniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f401d-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     <span data-ttu-id="f401d-138">![Dodawanie działania TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TR, Technical Router")</span><span class="sxs-lookup"><span data-stu-id="f401d-138">![Adding a TransactedReceiveScope activity](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")</span></span>  
  
5.  <span data-ttu-id="f401d-139">Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania i kliknij przycisk **zmienne** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f401d-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="f401d-140">Dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="f401d-140">Add the following variables.</span></span>  
  
     <span data-ttu-id="f401d-141">![Dodawanie zmiennych do TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span><span class="sxs-lookup"><span data-stu-id="f401d-141">![Adding Variables to the TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f401d-142">Można usunąć zmiennej danych, która jest domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f401d-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="f401d-143">Umożliwia także istniejącą zmienną dojścia.</span><span class="sxs-lookup"><span data-stu-id="f401d-143">You can also use the existing handle variable.</span></span>  
  
6.  <span data-ttu-id="f401d-144">Przeciągnij i upuść <xref:System.ServiceModel.Activities.Receive> działania w ramach **żądania** sekcji <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="f401d-145">Ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f401d-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="f401d-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f401d-146">Property</span></span>|<span data-ttu-id="f401d-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="f401d-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f401d-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="f401d-148">CanCreateInstance</span></span>|<span data-ttu-id="f401d-149">Wartość true (zaznacz pole wyboru)</span><span class="sxs-lookup"><span data-stu-id="f401d-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="f401d-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="f401d-150">OperationName</span></span>|<span data-ttu-id="f401d-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="f401d-151">StartSample</span></span>|  
    |<span data-ttu-id="f401d-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="f401d-152">ServiceContractName</span></span>|<span data-ttu-id="f401d-153">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="f401d-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="f401d-154">Przepływ pracy powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-154">The workflow should look like this:</span></span>  
  
     <span data-ttu-id="f401d-155">![Dodawanie działania Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span><span class="sxs-lookup"><span data-stu-id="f401d-155">![Adding a Receive activity](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")</span></span>  
  
7.  <span data-ttu-id="f401d-156">Kliknij przycisk **zdefiniuj...**  łącze w <xref:System.ServiceModel.Activities.Receive> działania i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="f401d-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     <span data-ttu-id="f401d-157">![Konfigurowanie ustawień wiadomości dla działania Odbierz](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="f401d-157">![Setting message settings for the Recieve activity](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")</span></span>  
  
8.  <span data-ttu-id="f401d-158">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania w sekcji Body <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="f401d-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="f401d-159">W ramach <xref:System.Activities.Statements.Sequence> działania przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działań i zestaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f401d-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f401d-160">Działanie</span><span class="sxs-lookup"><span data-stu-id="f401d-160">Activity</span></span>|<span data-ttu-id="f401d-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="f401d-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f401d-162">WriteLine 1.</span><span class="sxs-lookup"><span data-stu-id="f401d-162">1st WriteLine</span></span>|<span data-ttu-id="f401d-163">"Usługa: odbieranie ukończone"</span><span class="sxs-lookup"><span data-stu-id="f401d-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="f401d-164">WriteLine 2</span><span class="sxs-lookup"><span data-stu-id="f401d-164">2nd WriteLine</span></span>|<span data-ttu-id="f401d-165">"Usługa: odebrano =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="f401d-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="f401d-166">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-166">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="f401d-167">![Dodawanie działań WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span><span class="sxs-lookup"><span data-stu-id="f401d-167">![Adding WriteLine activities](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")</span></span>  
  
9. <span data-ttu-id="f401d-168">Przeciągnij i upuść `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działania w **treści** w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     <span data-ttu-id="f401d-169">![Po dodaniu PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span><span class="sxs-lookup"><span data-stu-id="f401d-169">![After adding PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")</span></span>  
  
10. <span data-ttu-id="f401d-170">Przeciągnij i upuść <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działania i ustawienia swoich właściwości zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="f401d-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="f401d-171">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f401d-171">Property</span></span>|<span data-ttu-id="f401d-172">Wartość</span><span class="sxs-lookup"><span data-stu-id="f401d-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f401d-173">Do</span><span class="sxs-lookup"><span data-stu-id="f401d-173">To</span></span>|<span data-ttu-id="f401d-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="f401d-174">replyMessage</span></span>|  
    |<span data-ttu-id="f401d-175">Wartość</span><span class="sxs-lookup"><span data-stu-id="f401d-175">Value</span></span>|<span data-ttu-id="f401d-176">"Usługa: wysyłania odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="f401d-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="f401d-177">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "usługi: rozpocząć odpowiedzi."</span><span class="sxs-lookup"><span data-stu-id="f401d-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="f401d-178">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-178">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="f401d-179">![Po dodaniu przypisania i WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span><span class="sxs-lookup"><span data-stu-id="f401d-179">![After adding Assign and WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")</span></span>  
  
12. <span data-ttu-id="f401d-180">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działanie i wybierz **utworzyć SendReply** i wklej go po ostatniej <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="f401d-181">Kliknij przycisk **zdefiniuj...**  łącze w `SendReplyToReceive` działania i wprowadź następujące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f401d-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     <span data-ttu-id="f401d-182">![Ustawienia wiadomości odpowiedzi](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="f401d-182">![Reply message settings](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")</span></span>  
  
13. <span data-ttu-id="f401d-183">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działania i zestaw składa się z <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "Usługa: Wysłano odpowiedź."</span><span class="sxs-lookup"><span data-stu-id="f401d-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="f401d-184">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania w dolnej części przepływu pracy i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "usługi: kończy się przepływu pracy, naciśnij klawisz ENTER, aby wyjść."</span><span class="sxs-lookup"><span data-stu-id="f401d-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="f401d-185">Ukończono usługi przepływu pracy powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-185">The completed service workflow should look like this:</span></span>  
  
     <span data-ttu-id="f401d-186">![Ukończ przepływ pracy usługi](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span><span class="sxs-lookup"><span data-stu-id="f401d-186">![Complete Service Workflow](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")</span></span>  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="f401d-187">Wdrożenie klienta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f401d-187">Implement the workflow client</span></span>  
  
1.  <span data-ttu-id="f401d-188">Dodaj nową aplikację przepływu pracy WCF, o nazwie `WorkflowClient` do `Common` projektu.</span><span class="sxs-lookup"><span data-stu-id="f401d-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="f401d-189">Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, zaznacz **Dodaj**, **nowy element...** , Wybierz pozycję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **działania**.</span><span class="sxs-lookup"><span data-stu-id="f401d-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     <span data-ttu-id="f401d-190">![Dodaj projekt działania](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span><span class="sxs-lookup"><span data-stu-id="f401d-190">![Add an Activity project](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")</span></span>  
  
2.  <span data-ttu-id="f401d-191">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="f401d-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3.  <span data-ttu-id="f401d-192">W ramach <xref:System.Activities.Statements.Sequence> działania przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="f401d-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="f401d-193">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-193">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="f401d-194">![Dodaj działanie WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span><span class="sxs-lookup"><span data-stu-id="f401d-194">![Add a WriteLine activity](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")</span></span>  
  
4.  <span data-ttu-id="f401d-195">Przeciągnij i upuść <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="f401d-196">Wybierz <xref:System.Activities.Statements.TransactionScope> działania, kliknij przycisk Zmienne i dodaj następujące zmienne.</span><span class="sxs-lookup"><span data-stu-id="f401d-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     <span data-ttu-id="f401d-197">![Zmienne można dodawać do elementu TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span><span class="sxs-lookup"><span data-stu-id="f401d-197">![Add variables to the TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")</span></span>  
  
5.  <span data-ttu-id="f401d-198">Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania w treści <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6.  <span data-ttu-id="f401d-199">Przeciągnij i upuść `PrintTransactionInfo` działanie w<xref:System.Activities.Statements.Sequence></span><span class="sxs-lookup"><span data-stu-id="f401d-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7.  <span data-ttu-id="f401d-200">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> "Klienta: początku wysyłania" dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="f401d-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="f401d-201">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-201">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="f401d-202">![Dodawanie działań](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span><span class="sxs-lookup"><span data-stu-id="f401d-202">![Adding activities](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")</span></span>  
  
8.  <span data-ttu-id="f401d-203">Przeciągnij i upuść <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f401d-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="f401d-204">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f401d-204">Property</span></span>|<span data-ttu-id="f401d-205">Wartość</span><span class="sxs-lookup"><span data-stu-id="f401d-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f401d-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="f401d-206">EndpointConfigurationName</span></span>|<span data-ttu-id="f401d-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="f401d-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="f401d-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="f401d-208">OperationName</span></span>|<span data-ttu-id="f401d-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="f401d-209">StartSample</span></span>|  
    |<span data-ttu-id="f401d-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="f401d-210">ServiceContractName</span></span>|<span data-ttu-id="f401d-211">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="f401d-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="f401d-212">Przepływ pracy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f401d-212">The workflow should now look like this:</span></span>  
  
     <span data-ttu-id="f401d-213">![Ustawianie właściwości działania Send](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span><span class="sxs-lookup"><span data-stu-id="f401d-213">![Setting the Send activity properties](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")</span></span>  
  
9. <span data-ttu-id="f401d-214">Kliknij przycisk **zdefiniuj...**  łącze i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="f401d-214">Click the **Define...** link and make the following settings:</span></span>  
  
     <span data-ttu-id="f401d-215">![Wyślij działania ustawienia wiadomości](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="f401d-215">![Send activity message settings](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")</span></span>  
  
10. <span data-ttu-id="f401d-216">Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działanie i wybierz **utworzyć ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="f401d-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="f401d-217"><xref:System.ServiceModel.Activities.ReceiveReply> Działania zostaną automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="f401d-218">Kliknij przycisk Definiuj... link w działaniu ReceiveReplyForSend i wprowadź następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="f401d-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     <span data-ttu-id="f401d-219">![Konfigurowanie ustawień wiadomości ReceiveForSend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span><span class="sxs-lookup"><span data-stu-id="f401d-219">![Setting the ReceiveForSend message settings](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")</span></span>  
  
12. <span data-ttu-id="f401d-220">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania między <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "klienta: wysyłanie pełną."</span><span class="sxs-lookup"><span data-stu-id="f401d-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="f401d-221">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "po stronie klienta: odebrano odpowiedzi =" + replyMessage</span><span class="sxs-lookup"><span data-stu-id="f401d-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="f401d-222">Przeciągnij i upuść `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="f401d-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="f401d-223">Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania na końcu przepływu pracy i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "Kończy się przepływu pracy klienta".</span><span class="sxs-lookup"><span data-stu-id="f401d-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="f401d-224">Przepływ pracy ukończonych klienta powinien wyglądać w poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="f401d-224">The completed client workflow should look like the following diagram.</span></span>  
  
     <span data-ttu-id="f401d-225">![Workfliow klienta zakończonych](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span><span class="sxs-lookup"><span data-stu-id="f401d-225">![The completed client workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")</span></span>  
  
16. <span data-ttu-id="f401d-226">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f401d-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="f401d-227">Tworzenie aplikacji usługi</span><span class="sxs-lookup"><span data-stu-id="f401d-227">Create the Service application</span></span>  
  
1.  <span data-ttu-id="f401d-228">Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f401d-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="f401d-229">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="f401d-229">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="f401d-230">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-230">System.Activities.dll</span></span>  
  
    2.  <span data-ttu-id="f401d-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-231">System.ServiceModel.dll</span></span>  
  
    3.  <span data-ttu-id="f401d-232">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="f401d-232">System.ServiceModel.Activities.dll</span></span>  
  
2.  <span data-ttu-id="f401d-233">Otwórz wygenerowany plik Program.cs i następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f401d-233">Open the generated Program.cs file and the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="f401d-234">Dodaj następujący plik app.config do projektu.</span><span class="sxs-lookup"><span data-stu-id="f401d-234">Add the following app.config file to the project.</span></span>  
  
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
  
### <a name="create-the-client-application"></a><span data-ttu-id="f401d-235">Tworzenie aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="f401d-235">Create the client application</span></span>  
  
1.  <span data-ttu-id="f401d-236">Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f401d-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="f401d-237">Dodaj odwołanie do System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="f401d-237">Add a reference to System.Activities.dll.</span></span>  
  
2.  <span data-ttu-id="f401d-238">Otwórz plik program.cs i Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f401d-238">Open the program.cs file and add the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f401d-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f401d-239">See Also</span></span>  
 [<span data-ttu-id="f401d-240">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f401d-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="f401d-241">Omówienie transakcji programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f401d-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [<span data-ttu-id="f401d-242">Użyj TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="f401d-242">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
