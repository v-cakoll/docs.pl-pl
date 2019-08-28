---
title: Proces zatwierdzania dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 20167cd1c06c2ae57dfe48fd07ab3a0e2adf9927
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038225"
---
# <a name="document-approval-process"></a><span data-ttu-id="03265-102">Proces zatwierdzania dokumentu</span><span class="sxs-lookup"><span data-stu-id="03265-102">Document Approval Process</span></span>

<span data-ttu-id="03265-103">W tym przykładzie pokazano, jak używać wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="03265-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="03265-104">Razem implementują one scenariusz procesu zatwierdzania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="03265-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="03265-105">Aplikacja kliencka może przesyłać dokumenty do zatwierdzenia i zatwierdzania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="03265-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="03265-106">Istnieje aplikacja Menedżera zatwierdzania ułatwiająca komunikację między klientami i Wymuszanie reguł procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="03265-107">Proces zatwierdzania jest przepływem pracy, który może wykonać kilka typów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="03265-108">Istnieją działania mające na celu uzyskanie pojedynczego zatwierdzenia, zatwierdzenie kworum (procent zestawu osób zatwierdzających) oraz złożony proces zatwierdzania, który składa się z kworum i pojedynczej zgody w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="03265-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03265-109">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="03265-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03265-110">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="03265-110">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="03265-111">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="03265-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03265-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="03265-112">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="03265-113">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="03265-113">Sample Details</span></span>

<span data-ttu-id="03265-114">Na poniższej ilustracji przedstawiono przepływ pracy procesu zatwierdzania dokumentów:</span><span class="sxs-lookup"><span data-stu-id="03265-114">The following graphic demonstrates the document approval process workflow:</span></span>

![Przepływ pracy procesu zatwierdzania dokumentów](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="03265-116">Z punktu widzenia klienta proces zatwierdzania działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03265-116">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="03265-117">Klient subskrybuje użytkownika w systemie procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-117">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="03265-118">Klient programu WCF wysyła do usługi WCF hostowanej przez aplikację Menedżer zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="03265-119">Do klienta jest zwracany unikatowy identyfikator użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03265-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="03265-120">Klient może teraz uczestniczyć w procesach zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-120">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="03265-121">Po dołączeniu klient może wysłać dokument do zatwierdzenia przy użyciu jednego, kworum lub złożonych procesów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="03265-122">Kliknięto przycisk w interfejsie klienta, co spowoduje uruchomienie wystąpienia przepływu pracy na hoście usługi przepływu pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="03265-123">Przepływ pracy wysyła żądanie zatwierdzenia do aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-123">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="03265-124">Menedżer przepływów pracy uruchamia przepływ pracy na własną stronę, aby reprezentować proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="03265-125">Po zakończeniu przepływu pracy zatwierdzania w Menedżerze wyniki są odsyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="03265-126">Klient wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="03265-126">The client displays the results.</span></span>

10. <span data-ttu-id="03265-127">Klient może otrzymać żądanie zatwierdzenia i odpowiedzieć na żądanie w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="03265-127">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="03265-128">Usługa WCF hostowana na kliencie może odebrać żądanie zatwierdzenia od aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="03265-129">Informacje o dokumencie są prezentowane na kliencie do przeglądu.</span><span class="sxs-lookup"><span data-stu-id="03265-129">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="03265-130">Użytkownik może zatwierdzić lub odrzucić dokument.</span><span class="sxs-lookup"><span data-stu-id="03265-130">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="03265-131">Klient WCF jest używany do wysyłania odpowiedzi zatwierdzenia z powrotem do aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="03265-132">Z punktu widzenia aplikacji Menedżera zatwierdzania proces zatwierdzania działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03265-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="03265-133">Klient wnioskuje o uczestnictwo w systemie przetwarzania zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="03265-133">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="03265-134">Usługa WCF w Menedżerze zatwierdzania odbiera żądanie, które jest częścią systemu procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="03265-135">Dla klienta jest generowany unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="03265-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="03265-136">Informacje o użytkowniku są przechowywane w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="03265-136">The user information is stored in a database.</span></span>

4. <span data-ttu-id="03265-137">Unikatowy identyfikator jest odsyłany do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03265-137">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="03265-138">Odbierane jest żądanie zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="03265-138">An approval request is receive.</span></span> <span data-ttu-id="03265-139">Menedżer zatwierdzania wykonuje proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="03265-139">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="03265-140">Menedżer zatwierdzania odbiera żądanie zatwierdzenia, rozpoczynając nowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="03265-140">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="03265-141">W zależności od typu żądania (prostego, kworum lub złożone) wykonywane jest inne działanie.</span><span class="sxs-lookup"><span data-stu-id="03265-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="03265-142">Działania wysyłania i odbierania z korelacją są używane do wysyłania żądania zatwierdzenia do klienta w celu przejrzenia i odebrania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="03265-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="03265-143">Wynik przepływu pracy procesu zatwierdzania jest wysyłany do klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-143">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="03265-144">Korzystanie z przykładu</span><span class="sxs-lookup"><span data-stu-id="03265-144">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="03265-145">Aby skonfigurować bazę danych</span><span class="sxs-lookup"><span data-stu-id="03265-145">To set up the database</span></span>

1. <span data-ttu-id="03265-146">W wierszu polecenia programu Visual Studio 2010 otwartym z uprawnieniami administratora przejdź do tego folderu DocumentApprovalProcess i uruchom polecenie Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="03265-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="03265-147">Aby skonfigurować aplikację</span><span class="sxs-lookup"><span data-stu-id="03265-147">To set up the application</span></span>

1. <span data-ttu-id="03265-148">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="03265-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="03265-149">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="03265-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="03265-150">Aby uruchomić rozwiązanie, uruchom aplikację Menedżer zatwierdzania, klikając prawym przyciskiem myszy projekt zatwierdzania w **Eksplorator rozwiązań** a następnie klikając polecenie **Debuguj**->**Uruchom** nowe wystąpienie w menu rozwijanym.</span><span class="sxs-lookup"><span data-stu-id="03265-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="03265-151">Poczekaj na dane wyjściowe menedżera, aby poinformować, że jest to gotowe.</span><span class="sxs-lookup"><span data-stu-id="03265-151">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="03265-152">Aby uruchomić scenariusz o pojedynczej zatwierdzeniu</span><span class="sxs-lookup"><span data-stu-id="03265-152">To run the single approval scenario</span></span>

1. <span data-ttu-id="03265-153">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="03265-153">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="03265-154">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="03265-154">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="03265-155">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj dwa wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="03265-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="03265-156">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="03265-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="03265-157">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="03265-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="03265-158">Dla jednego klienta Użyj `UserType1` i innego typu. `UserType2`</span><span class="sxs-lookup"><span data-stu-id="03265-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="03265-159">`UserType1` W kliencie wybierz typ pojedynczego zatwierdzenia z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="03265-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="03265-160">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="03265-160">Click **Request Approval**.</span></span>

7. <span data-ttu-id="03265-161">`UserType2` W kliencie zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="03265-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="03265-162">Zaznacz go i naciśnij przycisk Zatwierdź lub Odrzuć.</span><span class="sxs-lookup"><span data-stu-id="03265-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="03265-163">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="03265-163">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="03265-164">Aby uruchomić Scenariusz zatwierdzania kworum</span><span class="sxs-lookup"><span data-stu-id="03265-164">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="03265-165">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="03265-165">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="03265-166">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="03265-166">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="03265-167">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj trzy wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="03265-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="03265-168">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="03265-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="03265-169">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="03265-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="03265-170">Dla jednego klienta `UserType1` i drugiego typu `UserType2`.</span><span class="sxs-lookup"><span data-stu-id="03265-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="03265-171">`UserType1` W kliencie wybierz typ zatwierdzenia kworum z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="03265-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="03265-172">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="03265-172">Click **Request Approval**.</span></span> <span data-ttu-id="03265-173">Ta prośba o zaakceptowanie lub odrzucenie dokumentu przez dwóch `UserType2` klientów.</span><span class="sxs-lookup"><span data-stu-id="03265-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="03265-174">Chociaż obydwie `UserType2` klienci muszą reagować, tylko jeden klient musi zatwierdzić dokument do zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="03265-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="03265-175">`UserType2` Na klientach zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="03265-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="03265-176">Zaznacz go i naciśnij przycisk Zatwierdź lub Odrzuć.</span><span class="sxs-lookup"><span data-stu-id="03265-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="03265-177">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="03265-177">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="03265-178">Aby uruchomić złożony Scenariusz zatwierdzania</span><span class="sxs-lookup"><span data-stu-id="03265-178">To run the complex approval scenario</span></span>

1. <span data-ttu-id="03265-179">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="03265-179">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="03265-180">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="03265-180">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="03265-181">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj cztery wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="03265-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="03265-182">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="03265-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="03265-183">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="03265-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="03265-184">Do użycia `UserType1`w przypadku jednego klienta w przypadku dwóch `UserType2`typów użycia i w ostatnim użyciu `UserType3`.</span><span class="sxs-lookup"><span data-stu-id="03265-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="03265-185">`UserType1` W kliencie wybierz typ pojedynczego zatwierdzenia z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="03265-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="03265-186">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="03265-186">Click **Request Approval**.</span></span>

7. <span data-ttu-id="03265-187">`UserType2` Na klientach zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="03265-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="03265-188">Zaznacz go i naciśnijprzycisk Zatwierdź, dokument jest przesyłany `UserType3` do klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="03265-189">Jeśli dokument zostanie zatwierdzony przez pierwsze `UserType2` kworum, dokument jest przesyłany `UserType3` do klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="03265-190">Zatwierdź lub Odrzuć dokument z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="03265-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="03265-191">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="03265-191">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="03265-192">Aby oczyścić</span><span class="sxs-lookup"><span data-stu-id="03265-192">To clean up</span></span>

1. <span data-ttu-id="03265-193">W wierszu polecenia programu Visual Studio 2010 przejdź do folderu DocumentApprovalProcess i uruchom polecenie Oczyść. cmd.</span><span class="sxs-lookup"><span data-stu-id="03265-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
