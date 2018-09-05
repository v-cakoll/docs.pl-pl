---
title: Proces zatwierdzania dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 874ee560407c3054b4f270a35e5100eaf9e174b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508933"
---
# <a name="document-approval-process"></a><span data-ttu-id="3240f-102">Proces zatwierdzania dokumentu</span><span class="sxs-lookup"><span data-stu-id="3240f-102">Document Approval Process</span></span>
<span data-ttu-id="3240f-103">Niniejszy przykład pokazuje użycie wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF) ze sobą.</span><span class="sxs-lookup"><span data-stu-id="3240f-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="3240f-104">Razem mogą implementować scenariusza proces zatwierdzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3240f-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="3240f-105">Aplikacja kliencka można przesłać dokumenty do zatwierdzenia i zatwierdzić dokumenty.</span><span class="sxs-lookup"><span data-stu-id="3240f-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="3240f-106">Aplikacja menedżera zatwierdzenia istnieje ułatwienie komunikacji między klientami i wymuszać reguły proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="3240f-107">Proces zatwierdzania jest przepływ pracy, który może wykonać kilka typów zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="3240f-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="3240f-108">Działania ma korzystać z jednego zatwierdzenia, zatwierdzenia kworum (procent zestaw osób zatwierdzających) i proces zatwierdzania złożony, który składa się z kworum i jednego zatwierdzenia w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3240f-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3240f-109">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3240f-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3240f-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3240f-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3240f-111">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3240f-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3240f-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3240f-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="3240f-113">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="3240f-113">Sample Details</span></span>  
 <span data-ttu-id="3240f-114">Na poniższym rysunku przedstawiono proces zatwierdzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3240f-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="3240f-115">![Proces zatwierdzania dokumentu](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="3240f-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="3240f-116">Z perspektywy klienta zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3240f-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="3240f-117">Jako użytkownik w systemie proces zatwierdzania zasubskrybowaniem przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="3240f-118">Klienta programu WCF wysyła do usługi WCF hostowanej przez aplikację Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="3240f-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="3240f-119">Unikatowy identyfikator użytkownika jest zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="3240f-120">Klient może teraz uczestniczyć w procesów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="3240f-121">Po przyłączony, klient może wysyłać dokumentu do zatwierdzenia przy użyciu pojedynczego kworum lub procesów zatwierdzania złożone.</span><span class="sxs-lookup"><span data-stu-id="3240f-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="3240f-122">Po kliknięciu przycisku w interfejsie klienta uruchamia wystąpienie przepływu pracy w kliencie hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3240f-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="3240f-123">Przepływ pracy wysyła żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="3240f-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="3240f-124">Usługa workflow manager uruchamia przepływ pracy na bok do reprezentowania proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="3240f-125">Gdy przepływ pracy zatwierdzania manager wykonuje, wyniki są odsyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="3240f-126">Klient wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="3240f-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="3240f-127">Klient może odbierać żądania zatwierdzenia i odpowiadać na żądania w dowolnym momencie w czasie.</span><span class="sxs-lookup"><span data-stu-id="3240f-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="3240f-128">Usługi WCF hostowane na komputerze klienckim może odbierać żądania zatwierdzenia z aplikacji Menedżera zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="3240f-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="3240f-129">Informacje dokumentu są przedstawione na kliencie do przeglądu.</span><span class="sxs-lookup"><span data-stu-id="3240f-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="3240f-130">Użytkownika można zatwierdzić lub odrzucić dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3240f-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="3240f-131">Klienta programu WCF służy do wysyłania odpowiedzi na żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="3240f-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="3240f-132">Z punktu widzenia aplikacji Menedżera zatwierdzenia zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3240f-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="3240f-133">Klient żąda do wzięcia udziału w systemie proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="3240f-134">Usługi WCF w Menedżerze zatwierdzania odbiera żądanie jako część systemu proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="3240f-135">Unikatowy identyfikator jest generowany dla klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="3240f-136">Informacje użytkownika są przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3240f-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="3240f-137">Unikatowy identyfikator jest wysyłane z powrotem do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3240f-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="3240f-138">Żądanie zatwierdzenia jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="3240f-138">An approval request is receive.</span></span> <span data-ttu-id="3240f-139">Menedżer zatwierdzeń wykonuje proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="3240f-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="3240f-140">Żądanie zatwierdzenia jest odbierane przez Menedżera zatwierdzeń od nowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3240f-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="3240f-141">W zależności od typu żądania (prosty, kworum lub złożonych) jest wykonywana innego działania.</span><span class="sxs-lookup"><span data-stu-id="3240f-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="3240f-142">Wysyłania i odbierania działań z korelacją są używane do wysłania żądania zatwierdzenia do klienta do przeglądu i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3240f-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="3240f-143">Wynik procesu zatwierdzania, są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="3240f-144">Przy użyciu przykładu</span><span class="sxs-lookup"><span data-stu-id="3240f-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="3240f-145">Aby skonfigurować bazę danych</span><span class="sxs-lookup"><span data-stu-id="3240f-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="3240f-146">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] polecenia otwartych z uprawnieniami administratora, przejdź do tego folderu DocumentApprovalProcess i uruchom plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="3240f-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="3240f-147">Aby skonfigurować aplikację</span><span class="sxs-lookup"><span data-stu-id="3240f-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="3240f-148">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="3240f-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="3240f-149">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="3240f-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3240f-150">Aby uruchomić rozwiązanie, uruchamianie aplikacji Menedżer zatwierdzeń, klikając prawym przyciskiem myszy projekt ApprovalManager w **Eksploratora rozwiązań** i klikając **debugowania**->**Start**  nowe wystąpienie z menu podręcznego.</span><span class="sxs-lookup"><span data-stu-id="3240f-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="3240f-151">Poczekaj, aż Menedżer wyjście z informacją, że jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="3240f-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="3240f-152">Aby uruchomić scenariusza z jednego zatwierdzenia</span><span class="sxs-lookup"><span data-stu-id="3240f-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="3240f-153">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="3240f-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="3240f-154">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3240f-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="3240f-155">Przejdź do folderu ApprovalClient\Bin\Debug, a następnie wykonaj dwa wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="3240f-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="3240f-156">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="3240f-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="3240f-157">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="3240f-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="3240f-158">Dla jednego klienta, należy użyć `UserType1` i innych typów `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="3240f-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="3240f-159">W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="3240f-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="3240f-160">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="3240f-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="3240f-161">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="3240f-162">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="3240f-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="3240f-163">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="3240f-164">Aby uruchomić scenariusz zatwierdzania kworum</span><span class="sxs-lookup"><span data-stu-id="3240f-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="3240f-165">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="3240f-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="3240f-166">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3240f-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="3240f-167">Przejdź do folderu ApprovalClient\Bin\Debug oraz wykonania trzech wystąpień ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="3240f-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="3240f-168">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="3240f-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="3240f-169">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="3240f-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="3240f-170">Dla jednego klienta użyj `UserType1` i innego typu `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="3240f-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="3240f-171">W `UserType1` klienta, wybierz opcję zatwierdzenia kworum typ z menu rozwijanego a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="3240f-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="3240f-172">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="3240f-172">Click **Request Approval**.</span></span> <span data-ttu-id="3240f-173">To żądania wysyłane przez dwa `UserType2` klientów zatwierdzenia lub odrzucenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3240f-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="3240f-174">Podczas gdy obie `UserType2` klienci muszą odpowiadać tylko jednego klienta muszą zatwierdzić dokument, aby mogła zostać zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="3240f-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="3240f-175">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="3240f-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="3240f-176">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="3240f-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="3240f-177">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="3240f-178">Aby uruchomić scenariusz zatwierdzania złożonych</span><span class="sxs-lookup"><span data-stu-id="3240f-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="3240f-179">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="3240f-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="3240f-180">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3240f-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="3240f-181">Przejdź do folderu ApprovalClient\Bin\Debug i wykonać cztery wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="3240f-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="3240f-182">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="3240f-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="3240f-183">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="3240f-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="3240f-184">Dla jednego klienta użyj `UserType1`w dwóch używa typu `UserType2`i ostatniego użycia `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="3240f-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="3240f-185">W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="3240f-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="3240f-186">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="3240f-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="3240f-187">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="3240f-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="3240f-188">Zaznacz go i naciśnij klawisz **zatwierdzić**, dokument jest przekazywany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="3240f-189">Jeśli dokument zostanie zatwierdzony przez pierwszy `UserType2` kworum, dokument jest przekazywany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="3240f-190">Zatwierdź lub Odrzuć dokument z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="3240f-191">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="3240f-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="3240f-192">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="3240f-192">To clean up</span></span>  
  
1.  <span data-ttu-id="3240f-193">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, przejdź do folderu DocumentApprovalProcess i uruchomić Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="3240f-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>