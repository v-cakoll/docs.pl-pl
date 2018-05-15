---
title: Proces zatwierdzania dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: c28dafd3b0a1cb6dbee37fed2b3df8923ccd82c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="document-approval-process"></a><span data-ttu-id="bce8a-102">Proces zatwierdzania dokumentu</span><span class="sxs-lookup"><span data-stu-id="bce8a-102">Document Approval Process</span></span>
<span data-ttu-id="bce8a-103">W przykładzie pokazano korzystanie z wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF) ze sobą.</span><span class="sxs-lookup"><span data-stu-id="bce8a-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="bce8a-104">Razem wdrażają scenariusza proces zatwierdzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="bce8a-105">Aplikacja kliencka można przesyłać dokumenty do zatwierdzenia i zatwierdzić dokumenty.</span><span class="sxs-lookup"><span data-stu-id="bce8a-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="bce8a-106">Aplikacja menedżera zatwierdzenia istnieje ułatwiających komunikację między klientami i do wymuszania reguł procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="bce8a-107">Proces zatwierdzania jest przepływ pracy, który można wykonać kilka typów zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="bce8a-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="bce8a-108">Działania istnieje pobieranie jednego zatwierdzenia, zatwierdzenia kworum (procent zbiór osób zatwierdzających) i proces zatwierdzania złożonych, który składa się z kworum i jednego zatwierdzenia w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bce8a-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bce8a-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bce8a-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bce8a-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bce8a-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bce8a-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="bce8a-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bce8a-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="bce8a-113">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="bce8a-113">Sample Details</span></span>  
 <span data-ttu-id="bce8a-114">Na poniższym rysunku przedstawiono proces zatwierdzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="bce8a-115">![Proces zatwierdzania dokumentu](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="bce8a-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="bce8a-116">Z perspektywy klienta zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bce8a-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="bce8a-117">Jako użytkownik w systemie proces zatwierdzania zasubskrybowaniem przez klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="bce8a-118">Klient WCF wysyła do usługi WCF hostowanej przez aplikację menedżera zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="bce8a-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="bce8a-119">Identyfikator unikatowy użytkownika jest zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="bce8a-120">Klient może teraz uczestniczyć w procesów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="bce8a-121">Po połączone, klient może wysyłać dokumentu do zatwierdzenia przy użyciu pojedynczego kworum lub procesów zatwierdzania złożonych.</span><span class="sxs-lookup"><span data-stu-id="bce8a-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="bce8a-122">Kliknięto przycisk w interfejsie klienta, uruchamia wystąpienie przepływu pracy w kliencie hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bce8a-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="bce8a-123">Przepływ pracy wysyła żądanie zatwierdzenia do zatwierdzenia aplikacji menedżera.</span><span class="sxs-lookup"><span data-stu-id="bce8a-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="bce8a-124">Menedżer przepływu pracy jest uruchamiany przepływ pracy w bok do reprezentowania procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="bce8a-125">Gdy przepływ pracy zatwierdzania manager wykonuje, wyniki są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="bce8a-126">Klient wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="bce8a-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="bce8a-127">Klient może odbierać żądania zatwierdzenia i odpowiedzi na żądanie w dowolnym momencie w czasie.</span><span class="sxs-lookup"><span data-stu-id="bce8a-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="bce8a-128">Usługi WCF hostowanych na komputerze klienckim może odbierać żądania zatwierdzenia z aplikacji Menedżera zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="bce8a-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="bce8a-129">Informacje dokumentu są przedstawione na kliencie do przeglądu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="bce8a-130">Użytkownika można zatwierdzić lub odrzucić dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="bce8a-131">Klienta programu WCF służy do wysyłania odpowiedzi zatwierdzenia z powrotem do aplikacji Menedżera zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="bce8a-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="bce8a-132">Z punktu widzenia aplikacji Menedżera zatwierdzenia zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bce8a-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="bce8a-133">Klient żąda brać udziału w systemie procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="bce8a-134">Usługi WCF w Menedżerze zatwierdzania odbiera żądanie, jako część systemu procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="bce8a-135">Unikatowy identyfikator jest generowany dla klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="bce8a-136">Informacje użytkownika są przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="bce8a-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="bce8a-137">Unikatowy identyfikator jest wysyłany do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bce8a-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="bce8a-138">Żądania zatwierdzenia jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="bce8a-138">An approval request is receive.</span></span> <span data-ttu-id="bce8a-139">Menedżer zatwierdzeń wykonuje proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="bce8a-140">Żądania zatwierdzenia jest odbierany przez Menedżera zatwierdzeń uruchamianie nowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bce8a-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="bce8a-141">W zależności od typu żądania (prosty, kworum lub złożonych) innej aktywności jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="bce8a-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="bce8a-142">Wyślij i Odbierz działania z korelacją są używane do wysyłania żądań zatwierdzenia do klienta do przeglądu i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bce8a-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="bce8a-143">Wynik procesu zatwierdzania są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="bce8a-144">Przy użyciu próbki</span><span class="sxs-lookup"><span data-stu-id="bce8a-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="bce8a-145">Aby skonfigurować bazę danych</span><span class="sxs-lookup"><span data-stu-id="bce8a-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="bce8a-146">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora, przejdź do tego folderu DocumentApprovalProcess i uruchom Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="bce8a-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="bce8a-147">Aby skonfigurować aplikację</span><span class="sxs-lookup"><span data-stu-id="bce8a-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="bce8a-148">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="bce8a-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="bce8a-149">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="bce8a-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="bce8a-150">Aby uruchomić rozwiązanie, uruchom aplikację menedżera zatwierdzeń, klikając prawym przyciskiem myszy projekt ApprovalManager w **Eksploratora rozwiązań** i klikając **debugowania**->**Start**  nowe wystąpienie w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="bce8a-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="bce8a-151">Poczekaj na Menedżerze wyjścia z informacją, że jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="bce8a-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="bce8a-152">Aby uruchomić scenariusz jednego zatwierdzenia</span><span class="sxs-lookup"><span data-stu-id="bce8a-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="bce8a-153">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bce8a-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="bce8a-154">Przejdź do katalogu, który zawiera rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="bce8a-155">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj dwa wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bce8a-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="bce8a-156">Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="bce8a-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="bce8a-157">Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="bce8a-158">Dla jednego klienta, użyj `UserType1` i inny typ `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="bce8a-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="bce8a-159">W `UserType1` klienta, wybierz jednego zatwierdzenia typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="bce8a-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="bce8a-160">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="bce8a-161">W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="bce8a-162">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="bce8a-163">Wyniki powinny pojawiać się w `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="bce8a-164">Aby uruchomić scenariusza zatwierdzania kworum</span><span class="sxs-lookup"><span data-stu-id="bce8a-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="bce8a-165">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bce8a-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="bce8a-166">Przejdź do katalogu, który zawiera rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="bce8a-167">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj trzy wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bce8a-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="bce8a-168">Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="bce8a-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="bce8a-169">Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="bce8a-170">Dla jednego klienta, użyj `UserType1` i inny typ `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="bce8a-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="bce8a-171">W `UserType1` klienta, wybierz opcję zatwierdzania kworum typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="bce8a-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="bce8a-172">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-172">Click **Request Approval**.</span></span> <span data-ttu-id="bce8a-173">To żądania wysyłane przez dwa `UserType2` klientów zatwierdzanie lub odrzucanie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bce8a-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="bce8a-174">Zarówno podczas `UserType2` klienci muszą odpowiadać tylko jeden klient musi zatwierdzić dokumentu do zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="bce8a-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="bce8a-175">W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="bce8a-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="bce8a-176">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="bce8a-177">Wyniki powinny pojawiać się w `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="bce8a-178">Aby uruchomić scenariusza zatwierdzania złożonych</span><span class="sxs-lookup"><span data-stu-id="bce8a-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="bce8a-179">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bce8a-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="bce8a-180">Przejdź do katalogu, który zawiera rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bce8a-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="bce8a-181">Przejdź do folderu ApprovalClient\Bin\Debug i wykonać cztery wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bce8a-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="bce8a-182">Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="bce8a-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="bce8a-183">Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="bce8a-184">Dla jednego klienta, użyj `UserType1`w dwóch używa typu `UserType2`i w przypadku ostatniego użycia `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="bce8a-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="bce8a-185">W `UserType1` klienta, wybierz jednego zatwierdzenia typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="bce8a-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="bce8a-186">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="bce8a-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="bce8a-187">W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="bce8a-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="bce8a-188">Zaznacz go i naciśnij klawisz **zatwierdzić**, dokument jest przekazywana do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="bce8a-189">Jeśli dokument zostanie zaakceptowane przez pierwszy `UserType2` kworum, dokument jest przekazywana do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="bce8a-190">Zatwierdzanie lub odrzucanie dokumentu z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="bce8a-191">Wyniki powinny pojawiać się w `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="bce8a-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="bce8a-192">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="bce8a-192">To clean up</span></span>  
  
1.  <span data-ttu-id="bce8a-193">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, przejdź do folderu DocumentApprovalProcess i uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="bce8a-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>