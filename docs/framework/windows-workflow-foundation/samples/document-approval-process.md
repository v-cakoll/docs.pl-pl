---
title: Proces zatwierdzania dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 4451719bfb1d46a4e0e4dcde19666d1f8b2de427
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409552"
---
# <a name="document-approval-process"></a><span data-ttu-id="8d72a-102">Proces zatwierdzania dokumentu</span><span class="sxs-lookup"><span data-stu-id="8d72a-102">Document Approval Process</span></span>
<span data-ttu-id="8d72a-103">Niniejszy przykład pokazuje użycie wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF) ze sobą.</span><span class="sxs-lookup"><span data-stu-id="8d72a-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="8d72a-104">Razem mogą implementować scenariusza proces zatwierdzania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8d72a-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="8d72a-105">Aplikacja kliencka można przesłać dokumenty do zatwierdzenia i zatwierdzić dokumenty.</span><span class="sxs-lookup"><span data-stu-id="8d72a-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="8d72a-106">Aplikacja menedżera zatwierdzenia istnieje ułatwienie komunikacji między klientami i wymuszać reguły proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="8d72a-107">Proces zatwierdzania jest przepływ pracy, który może wykonać kilka typów zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8d72a-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="8d72a-108">Działania ma korzystać z jednego zatwierdzenia, zatwierdzenia kworum (procent zestaw osób zatwierdzających) i proces zatwierdzania złożony, który składa się z kworum i jednego zatwierdzenia w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8d72a-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="8d72a-109">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8d72a-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d72a-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8d72a-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d72a-111">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="8d72a-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d72a-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d72a-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="8d72a-113">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="8d72a-113">Sample Details</span></span>  
 <span data-ttu-id="8d72a-114">Poniższa ilustracja przedstawia proces zatwierdzania dokumentu:</span><span class="sxs-lookup"><span data-stu-id="8d72a-114">The following graphic demonstrates the document approval process workflow:</span></span>  
  
 ![Proces zatwierdzania dokumentu](./media/document-approval-process/document-approval-process.jpg)  
  
 <span data-ttu-id="8d72a-116">Z perspektywy klienta zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8d72a-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="8d72a-117">Jako użytkownik w systemie proces zatwierdzania zasubskrybowaniem przez klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="8d72a-118">Klienta programu WCF wysyła do usługi WCF hostowanej przez aplikację Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8d72a-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="8d72a-119">Unikatowy identyfikator użytkownika jest zwracana do klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="8d72a-120">Klient może teraz uczestniczyć w procesów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="8d72a-121">Po przyłączony, klient może wysyłać dokumentu do zatwierdzenia przy użyciu pojedynczego kworum lub procesów zatwierdzania złożone.</span><span class="sxs-lookup"><span data-stu-id="8d72a-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="8d72a-122">Po kliknięciu przycisku w interfejsie klienta uruchamia wystąpienie przepływu pracy w kliencie hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d72a-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="8d72a-123">Przepływ pracy wysyła żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8d72a-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="8d72a-124">Usługa workflow manager uruchamia przepływ pracy na bok do reprezentowania proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="8d72a-125">Gdy przepływ pracy zatwierdzania manager wykonuje, wyniki są odsyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="8d72a-126">Klient wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="8d72a-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="8d72a-127">Klient może odbierać żądania zatwierdzenia i odpowiadać na żądania w dowolnym momencie w czasie.</span><span class="sxs-lookup"><span data-stu-id="8d72a-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="8d72a-128">Usługi WCF hostowane na komputerze klienckim może odbierać żądania zatwierdzenia z aplikacji Menedżera zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8d72a-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="8d72a-129">Informacje dokumentu są przedstawione na kliencie do przeglądu.</span><span class="sxs-lookup"><span data-stu-id="8d72a-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="8d72a-130">Użytkownika można zatwierdzić lub odrzucić dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8d72a-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="8d72a-131">Klienta programu WCF służy do wysyłania odpowiedzi na żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8d72a-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="8d72a-132">Z punktu widzenia aplikacji Menedżera zatwierdzenia zatwierdzenia proces funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8d72a-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="8d72a-133">Klient żąda do wzięcia udziału w systemie proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="8d72a-134">Usługi WCF w Menedżerze zatwierdzania odbiera żądanie jako część systemu proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="8d72a-135">Unikatowy identyfikator jest generowany dla klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="8d72a-136">Informacje użytkownika są przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8d72a-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="8d72a-137">Unikatowy identyfikator jest wysyłane z powrotem do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d72a-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="8d72a-138">Żądanie zatwierdzenia jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="8d72a-138">An approval request is receive.</span></span> <span data-ttu-id="8d72a-139">Menedżer zatwierdzeń wykonuje proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="8d72a-140">Żądanie zatwierdzenia jest odbierane przez Menedżera zatwierdzeń od nowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d72a-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="8d72a-141">W zależności od typu żądania (prosty, kworum lub złożonych) jest wykonywana innego działania.</span><span class="sxs-lookup"><span data-stu-id="8d72a-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="8d72a-142">Wysyłania i odbierania działań z korelacją są używane do wysłania żądania zatwierdzenia do klienta do przeglądu i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8d72a-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="8d72a-143">Wynik procesu zatwierdzania, są wysyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="8d72a-144">Przy użyciu przykładu</span><span class="sxs-lookup"><span data-stu-id="8d72a-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="8d72a-145">Aby skonfigurować bazę danych</span><span class="sxs-lookup"><span data-stu-id="8d72a-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="8d72a-146">Z wiersza polecenia programu Visual Studio 2010 otwartych z uprawnieniami administratora przejdź do tego folderu DocumentApprovalProcess i uruchom plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8d72a-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="8d72a-147">Aby skonfigurować aplikację</span><span class="sxs-lookup"><span data-stu-id="8d72a-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="8d72a-148">Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania DocumentApprovalProcess.sln.</span><span class="sxs-lookup"><span data-stu-id="8d72a-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="8d72a-149">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8d72a-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="8d72a-150">Aby uruchomić rozwiązanie, uruchamianie aplikacji Menedżer zatwierdzeń, klikając prawym przyciskiem myszy projekt ApprovalManager w **Eksploratora rozwiązań** i klikając **debugowania**->**Start**  nowe wystąpienie z menu podręcznego.</span><span class="sxs-lookup"><span data-stu-id="8d72a-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="8d72a-151">Poczekaj, aż Menedżer wyjście z informacją, że jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="8d72a-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="8d72a-152">Aby uruchomić scenariusza z jednego zatwierdzenia</span><span class="sxs-lookup"><span data-stu-id="8d72a-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="8d72a-153">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="8d72a-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="8d72a-154">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8d72a-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="8d72a-155">Przejdź do folderu ApprovalClient\Bin\Debug, a następnie wykonaj dwa wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="8d72a-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="8d72a-156">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="8d72a-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="8d72a-157">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="8d72a-158">Dla jednego klienta, należy użyć `UserType1` i innych typów `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="8d72a-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="8d72a-159">W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="8d72a-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="8d72a-160">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="8d72a-161">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="8d72a-162">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="8d72a-163">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="8d72a-164">Aby uruchomić scenariusz zatwierdzania kworum</span><span class="sxs-lookup"><span data-stu-id="8d72a-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="8d72a-165">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="8d72a-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="8d72a-166">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8d72a-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="8d72a-167">Przejdź do folderu ApprovalClient\Bin\Debug oraz wykonania trzech wystąpień ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="8d72a-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="8d72a-168">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="8d72a-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="8d72a-169">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="8d72a-170">Dla jednego klienta użyj `UserType1` i innego typu `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="8d72a-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="8d72a-171">W `UserType1` klienta, wybierz opcję zatwierdzenia kworum typ z menu rozwijanego a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="8d72a-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="8d72a-172">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-172">Click **Request Approval**.</span></span> <span data-ttu-id="8d72a-173">To żądania wysyłane przez dwa `UserType2` klientów zatwierdzenia lub odrzucenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8d72a-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="8d72a-174">Podczas gdy obie `UserType2` klienci muszą odpowiadać tylko jednego klienta muszą zatwierdzić dokument, aby mogła zostać zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="8d72a-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="8d72a-175">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="8d72a-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="8d72a-176">Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="8d72a-177">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="8d72a-178">Aby uruchomić scenariusz zatwierdzania złożonych</span><span class="sxs-lookup"><span data-stu-id="8d72a-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="8d72a-179">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="8d72a-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="8d72a-180">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8d72a-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="8d72a-181">Przejdź do folderu ApprovalClient\Bin\Debug i wykonać cztery wystąpienia ApprovalClient.exe.</span><span class="sxs-lookup"><span data-stu-id="8d72a-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="8d72a-182">Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="8d72a-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="8d72a-183">Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="8d72a-184">Dla jednego klienta użyj `UserType1`w dwóch używa typu `UserType2`i ostatniego użycia `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="8d72a-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="8d72a-185">W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="8d72a-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="8d72a-186">Kliknij przycisk **zażądać zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="8d72a-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="8d72a-187">W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów.</span><span class="sxs-lookup"><span data-stu-id="8d72a-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="8d72a-188">Zaznacz go i naciśnij klawisz **zatwierdzić**, dokument jest przekazywany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="8d72a-189">Jeśli dokument zostanie zatwierdzony przez pierwszy `UserType2` kworum, dokument jest przekazywany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="8d72a-190">Zatwierdź lub Odrzuć dokument z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="8d72a-191">Wyniki powinny pokazywać `UserType1` klienta.</span><span class="sxs-lookup"><span data-stu-id="8d72a-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="8d72a-192">Aby wyczyścić</span><span class="sxs-lookup"><span data-stu-id="8d72a-192">To clean up</span></span>  
  
1.  <span data-ttu-id="8d72a-193">Z wiersza polecenia programu Visual Studio 2010 przejdź do folderu DocumentApprovalProcess i uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8d72a-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
