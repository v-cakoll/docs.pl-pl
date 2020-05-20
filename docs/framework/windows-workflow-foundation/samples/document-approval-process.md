---
title: Proces zatwierdzania dokumentu
description: Ten przykład pokazuje wiele funkcji Windows Workflow Foundation i Windows Communication Foundation w scenariuszu procesu zatwierdzania dokumentów.
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421413"
---
# <a name="document-approval-process"></a><span data-ttu-id="9a641-103">Proces zatwierdzania dokumentu</span><span class="sxs-lookup"><span data-stu-id="9a641-103">Document Approval Process</span></span>

<span data-ttu-id="9a641-104">W tym przykładzie pokazano, jak używać wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9a641-104">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="9a641-105">Razem implementują one scenariusz procesu zatwierdzania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="9a641-105">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="9a641-106">Aplikacja kliencka może przesyłać dokumenty do zatwierdzenia i zatwierdzania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="9a641-106">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="9a641-107">Istnieje aplikacja Menedżera zatwierdzania ułatwiająca komunikację między klientami i Wymuszanie reguł procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-107">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="9a641-108">Proces zatwierdzania jest przepływem pracy, który może wykonać kilka typów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-108">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="9a641-109">Istnieją działania mające na celu uzyskanie pojedynczego zatwierdzenia, zatwierdzenie kworum (procent zestawu osób zatwierdzających) oraz złożony proces zatwierdzania, który składa się z kworum i pojedynczej zgody w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9a641-109">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a641-110">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9a641-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9a641-111">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="9a641-111">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9a641-112">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="9a641-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a641-113">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9a641-113">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a><span data-ttu-id="9a641-114">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="9a641-114">Sample Details</span></span>

<span data-ttu-id="9a641-115">Na poniższej ilustracji przedstawiono przepływ pracy procesu zatwierdzania dokumentów:</span><span class="sxs-lookup"><span data-stu-id="9a641-115">The following graphic demonstrates the document approval process workflow:</span></span>

![Przepływ pracy procesu zatwierdzania dokumentów](./media/document-approval-process/document-approval-process.jpg)

<span data-ttu-id="9a641-117">Z punktu widzenia klienta proces zatwierdzania działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9a641-117">From the client's perspective, the approval process functions as follows:</span></span>

1. <span data-ttu-id="9a641-118">Klient subskrybuje użytkownika w systemie procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-118">A client subscribes to be a user in the approval process system.</span></span>

2. <span data-ttu-id="9a641-119">Klient programu WCF wysyła do usługi WCF hostowanej przez aplikację Menedżer zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-119">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>

3. <span data-ttu-id="9a641-120">Do klienta jest zwracany unikatowy identyfikator użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a641-120">A unique user ID is returned to the client.</span></span> <span data-ttu-id="9a641-121">Klient może teraz uczestniczyć w procesach zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-121">The client can now participate in approval processes.</span></span>

4. <span data-ttu-id="9a641-122">Po dołączeniu klient może wysłać dokument do zatwierdzenia przy użyciu jednego, kworum lub złożonych procesów zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-122">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>

5. <span data-ttu-id="9a641-123">Kliknięto przycisk w interfejsie klienta, co spowoduje uruchomienie wystąpienia przepływu pracy na hoście usługi przepływu pracy klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-123">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>

6. <span data-ttu-id="9a641-124">Przepływ pracy wysyła żądanie zatwierdzenia do aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-124">The workflow sends an approval request to the approval manager application.</span></span>

7. <span data-ttu-id="9a641-125">Menedżer przepływów pracy uruchamia przepływ pracy na własną stronę, aby reprezentować proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-125">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>

8. <span data-ttu-id="9a641-126">Po zakończeniu przepływu pracy zatwierdzania w Menedżerze wyniki są odsyłane do klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-126">Once the manager approval workflow executes, the results are sent back to the client.</span></span>

9. <span data-ttu-id="9a641-127">Klient wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="9a641-127">The client displays the results.</span></span>

10. <span data-ttu-id="9a641-128">Klient może otrzymać żądanie zatwierdzenia i odpowiedzieć na żądanie w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="9a641-128">A client may receive an approval request and respond to the request at any point in time.</span></span>

11. <span data-ttu-id="9a641-129">Usługa WCF hostowana na kliencie może odebrać żądanie zatwierdzenia od aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-129">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>

12. <span data-ttu-id="9a641-130">Informacje o dokumencie są prezentowane na kliencie do przeglądu.</span><span class="sxs-lookup"><span data-stu-id="9a641-130">The document information is presented on the client for review.</span></span>

13. <span data-ttu-id="9a641-131">Użytkownik może zatwierdzić lub odrzucić dokument.</span><span class="sxs-lookup"><span data-stu-id="9a641-131">The user can approve or reject the document.</span></span>

14. <span data-ttu-id="9a641-132">Klient WCF jest używany do wysyłania odpowiedzi zatwierdzenia z powrotem do aplikacji Menedżera zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-132">A WCF client is used to send an approval response back to the approval manager application.</span></span>

<span data-ttu-id="9a641-133">Z punktu widzenia aplikacji Menedżera zatwierdzania proces zatwierdzania działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9a641-133">From the approval manager application’s point of view, the approval process functions as follows:</span></span>

1. <span data-ttu-id="9a641-134">Klient wnioskuje o uczestnictwo w systemie przetwarzania zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="9a641-134">A client requests to participate to the approval process system.</span></span>

2. <span data-ttu-id="9a641-135">Usługa WCF w Menedżerze zatwierdzania odbiera żądanie, które jest częścią systemu procesu zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-135">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>

3. <span data-ttu-id="9a641-136">Dla klienta jest generowany unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="9a641-136">A unique ID is generated for the client.</span></span> <span data-ttu-id="9a641-137">Informacje o użytkowniku są przechowywane w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="9a641-137">The user information is stored in a database.</span></span>

4. <span data-ttu-id="9a641-138">Unikatowy identyfikator jest odsyłany do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a641-138">The unique ID is sent back to the user.</span></span>

5. <span data-ttu-id="9a641-139">Odbierane jest żądanie zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="9a641-139">An approval request is receive.</span></span> <span data-ttu-id="9a641-140">Menedżer zatwierdzania wykonuje proces zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="9a641-140">The approval manager executes an approval process.</span></span>

6. <span data-ttu-id="9a641-141">Menedżer zatwierdzania odbiera żądanie zatwierdzenia, rozpoczynając nowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="9a641-141">An approval request is received by the approval manager, starting a new workflow.</span></span>

7. <span data-ttu-id="9a641-142">W zależności od typu żądania (prostego, kworum lub złożone) wykonywane jest inne działanie.</span><span class="sxs-lookup"><span data-stu-id="9a641-142">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>

8. <span data-ttu-id="9a641-143">Działania wysyłania i odbierania z korelacją są używane do wysyłania żądania zatwierdzenia do klienta w celu przejrzenia i odebrania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a641-143">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>

9. <span data-ttu-id="9a641-144">Wynik przepływu pracy procesu zatwierdzania jest wysyłany do klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-144">The result of the approval process workflow is sent to the client.</span></span>

## <a name="using-the-sample"></a><span data-ttu-id="9a641-145">Korzystanie z przykładu</span><span class="sxs-lookup"><span data-stu-id="9a641-145">Using the Sample</span></span>

##### <a name="to-set-up-the-database"></a><span data-ttu-id="9a641-146">Aby skonfigurować bazę danych</span><span class="sxs-lookup"><span data-stu-id="9a641-146">To set up the database</span></span>

1. <span data-ttu-id="9a641-147">W wierszu polecenia programu Visual Studio 2010 otwartym z uprawnieniami administratora przejdź do tego folderu DocumentApprovalProcess i uruchom polecenie Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="9a641-147">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>

##### <a name="to-set-up-the-application"></a><span data-ttu-id="9a641-148">Aby skonfigurować aplikację</span><span class="sxs-lookup"><span data-stu-id="9a641-148">To set up the application</span></span>

1. <span data-ttu-id="9a641-149">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania DocumentApprovalProcess. sln.</span><span class="sxs-lookup"><span data-stu-id="9a641-149">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>

2. <span data-ttu-id="9a641-150">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="9a641-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="9a641-151">Aby uruchomić rozwiązanie, uruchom aplikację Menedżer zatwierdzania, klikając prawym przyciskiem myszy projekt zatwierdzania w **Eksplorator rozwiązań** a następnie klikając polecenie **Debuguj** -> **Uruchom** nowe wystąpienie w menu rozwijanym.</span><span class="sxs-lookup"><span data-stu-id="9a641-151">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>

    <span data-ttu-id="9a641-152">Poczekaj na dane wyjściowe menedżera, aby poinformować, że jest to gotowe.</span><span class="sxs-lookup"><span data-stu-id="9a641-152">Wait for the manager’s output to let you know that it is ready.</span></span>

##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="9a641-153">Aby uruchomić scenariusz o pojedynczej zatwierdzeniu</span><span class="sxs-lookup"><span data-stu-id="9a641-153">To run the single approval scenario</span></span>

1. <span data-ttu-id="9a641-154">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9a641-154">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="9a641-155">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9a641-155">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="9a641-156">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj dwa wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="9a641-156">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="9a641-157">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="9a641-157">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="9a641-158">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="9a641-158">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9a641-159">Dla jednego klienta Użyj `UserType1` i innego typu `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="9a641-159">For one client, use `UserType1` and the other type `UserType2`.</span></span>

6. <span data-ttu-id="9a641-160">W `UserType1` kliencie wybierz typ pojedynczego zatwierdzenia z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="9a641-160">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9a641-161">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="9a641-161">Click **Request Approval**.</span></span>

7. <span data-ttu-id="9a641-162">W `UserType2` kliencie zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="9a641-162">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="9a641-163">Zaznacz go i naciśnij przycisk **Zatwierdź** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="9a641-163">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="9a641-164">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="9a641-164">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="9a641-165">Aby uruchomić Scenariusz zatwierdzania kworum</span><span class="sxs-lookup"><span data-stu-id="9a641-165">To run the quorum approval scenario</span></span>

1. <span data-ttu-id="9a641-166">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9a641-166">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="9a641-167">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9a641-167">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="9a641-168">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj trzy wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="9a641-168">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="9a641-169">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="9a641-169">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="9a641-170">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="9a641-170">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9a641-171">Dla jednego klienta `UserType1` i drugiego typu `UserType2` .</span><span class="sxs-lookup"><span data-stu-id="9a641-171">For one client use `UserType1` and the other two type `UserType2`.</span></span>

6. <span data-ttu-id="9a641-172">W `UserType1` kliencie wybierz typ zatwierdzenia kworum z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="9a641-172">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9a641-173">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="9a641-173">Click **Request Approval**.</span></span> <span data-ttu-id="9a641-174">Ta prośba o `UserType2` zaakceptowanie lub odrzucenie dokumentu przez dwóch klientów.</span><span class="sxs-lookup"><span data-stu-id="9a641-174">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="9a641-175">Chociaż obydwie `UserType2` klienci muszą reagować, tylko jeden klient musi zatwierdzić dokument do zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="9a641-175">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>

7. <span data-ttu-id="9a641-176">Na `UserType2` klientach zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="9a641-176">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="9a641-177">Zaznacz go i naciśnij przycisk **Zatwierdź** lub **Odrzuć**.</span><span class="sxs-lookup"><span data-stu-id="9a641-177">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="9a641-178">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="9a641-178">The results should show in the `UserType1` client.</span></span>

##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="9a641-179">Aby uruchomić złożony Scenariusz zatwierdzania</span><span class="sxs-lookup"><span data-stu-id="9a641-179">To run the complex approval scenario</span></span>

1. <span data-ttu-id="9a641-180">Otwórz wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9a641-180">Open a command prompt with administrator permission.</span></span>

2. <span data-ttu-id="9a641-181">Przejdź do katalogu, który zawiera rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9a641-181">Navigate to the directory that contains the solution.</span></span>

3. <span data-ttu-id="9a641-182">Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj cztery wystąpienia programu ApprovalClient. exe.</span><span class="sxs-lookup"><span data-stu-id="9a641-182">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>

4. <span data-ttu-id="9a641-183">Kliknij przycisk **odkryj**, poczekaj, aż przycisk **Subskrybuj** zostanie włączony.</span><span class="sxs-lookup"><span data-stu-id="9a641-183">Click **discover**, wait until the **subscribe** button is enabled.</span></span>

5. <span data-ttu-id="9a641-184">Wpisz dowolną nazwę użytkownika i kliknij przycisk **Subskrybuj**.</span><span class="sxs-lookup"><span data-stu-id="9a641-184">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="9a641-185">Do użycia w przypadku jednego klienta `UserType1` w przypadku dwóch typów użycia `UserType2` i w ostatnim użyciu `UserType3` .</span><span class="sxs-lookup"><span data-stu-id="9a641-185">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>

6. <span data-ttu-id="9a641-186">W `UserType1` kliencie wybierz typ pojedynczego zatwierdzenia z menu rozwijanego i wpisz nazwę dokumentu i zawartość.</span><span class="sxs-lookup"><span data-stu-id="9a641-186">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="9a641-187">Kliknij pozycję **Żądaj zatwierdzenia**.</span><span class="sxs-lookup"><span data-stu-id="9a641-187">Click **Request Approval**.</span></span>

7. <span data-ttu-id="9a641-188">Na `UserType2` klientach zostanie wyświetlony dokument oczekujący na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="9a641-188">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="9a641-189">Zaznacz go i naciśnij przycisk **Zatwierdź**, dokument jest przesyłany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-189">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>

    <span data-ttu-id="9a641-190">Jeśli dokument zostanie zatwierdzony przez pierwsze `UserType2` kworum, dokument jest przesyłany do `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-190">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>

8. <span data-ttu-id="9a641-191">Zatwierdź lub Odrzuć dokument z `UserType3` klienta.</span><span class="sxs-lookup"><span data-stu-id="9a641-191">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="9a641-192">Wyniki powinny być wyświetlane na `UserType1` kliencie.</span><span class="sxs-lookup"><span data-stu-id="9a641-192">The results should show in the `UserType1` client.</span></span>

##### <a name="to-clean-up"></a><span data-ttu-id="9a641-193">Aby oczyścić</span><span class="sxs-lookup"><span data-stu-id="9a641-193">To clean up</span></span>

1. <span data-ttu-id="9a641-194">W wierszu polecenia programu Visual Studio 2010 przejdź do folderu DocumentApprovalProcess i uruchom polecenie Oczyść. cmd.</span><span class="sxs-lookup"><span data-stu-id="9a641-194">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
