---
title: "Porady: Włączanie wykrywania powtórzeń tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a7c72d77b4894376fb6cb8aed2d1c6641a3977da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="85c74-102">Porady: Włączanie wykrywania powtórzeń tokenów</span><span class="sxs-lookup"><span data-stu-id="85c74-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="85c74-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="85c74-103">Applies To</span></span>  
  
-   <span data-ttu-id="85c74-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="85c74-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="85c74-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="85c74-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="85c74-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="85c74-106">Summary</span></span>  
 <span data-ttu-id="85c74-107">Porada ten zawiera szczegółowe procedury krok po kroku umożliwiających wykrywanie powtórzeń tokenów w aplikacji ASP.NET, która używa WIF.</span><span class="sxs-lookup"><span data-stu-id="85c74-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="85c74-108">Umożliwia także instrukcje przetestować aplikację, aby sprawdzić, czy włączono wykrywania powtórzeń tokenów.</span><span class="sxs-lookup"><span data-stu-id="85c74-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="85c74-109">Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp.</span><span class="sxs-lookup"><span data-stu-id="85c74-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="85c74-110">Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="85c74-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="85c74-111">Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="85c74-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="85c74-112">Można go pobrać z następującej lokalizacji: [tożsamości i dostępu do narzędzia](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="85c74-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="85c74-113">Spis treści</span><span class="sxs-lookup"><span data-stu-id="85c74-113">Contents</span></span>  
  
-   <span data-ttu-id="85c74-114">Cele</span><span class="sxs-lookup"><span data-stu-id="85c74-114">Objectives</span></span>  
  
-   <span data-ttu-id="85c74-115">Omówienie</span><span class="sxs-lookup"><span data-stu-id="85c74-115">Overview</span></span>  
  
-   <span data-ttu-id="85c74-116">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="85c74-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="85c74-117">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania</span><span class="sxs-lookup"><span data-stu-id="85c74-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="85c74-118">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="85c74-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="85c74-119">Cele</span><span class="sxs-lookup"><span data-stu-id="85c74-119">Objectives</span></span>  
  
-   <span data-ttu-id="85c74-120">Utwórz prostą aplikację ASP.NET, która używa WIF i STS programowanie z tożsamości i dostępu do narzędzia</span><span class="sxs-lookup"><span data-stu-id="85c74-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="85c74-121">Umożliwia to wykrywanie powtórzeń tokenów i sprawdź, czy działa ona</span><span class="sxs-lookup"><span data-stu-id="85c74-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="85c74-122">Omówienie</span><span class="sxs-lookup"><span data-stu-id="85c74-122">Overview</span></span>  
 <span data-ttu-id="85c74-123">Atak powtarzania występuje, gdy klient podejmie próbę uwierzytelnienia do jednostki uzależnionej z tokenem STS została już użyta przez klienta.</span><span class="sxs-lookup"><span data-stu-id="85c74-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="85c74-124">Aby zapobiec atakom, WIF zawiera pamięci podręcznej wykrywania powtórzeń tokenów STS poprzednio.</span><span class="sxs-lookup"><span data-stu-id="85c74-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="85c74-125">Po włączeniu wykrywania powtórzeń sprawdza token żądania przychodzącego i sprawdza, czy token został wcześniej użyty.</span><span class="sxs-lookup"><span data-stu-id="85c74-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="85c74-126">Jeśli token został już użyty, żądanie jest odrzucane i <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="85c74-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="85c74-127">Następująca procedura przedstawia zmiany w konfiguracji wymagane do włączenia wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="85c74-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="85c74-128">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="85c74-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="85c74-129">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania</span><span class="sxs-lookup"><span data-stu-id="85c74-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="85c74-130">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="85c74-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="85c74-131">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania</span><span class="sxs-lookup"><span data-stu-id="85c74-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="85c74-132">W tym kroku zostanie utworzenie nowej aplikacji formularzy sieci Web ASP.NET i zmodyfikować *Web.config* pliku, aby włączyć wykrywanie powtarzania.</span><span class="sxs-lookup"><span data-stu-id="85c74-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="85c74-133">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="85c74-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="85c74-134">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="85c74-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="85c74-135">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="85c74-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="85c74-136">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="85c74-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="85c74-137">Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="85c74-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="85c74-138">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="85c74-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="85c74-139">W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="85c74-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="85c74-140">Dodaj następujące  **\<tokenReplayDetection >** elementu *Web.config* pliku konfiguracji bezpośrednio po  **\<system.identityModel >** i  **\<identityConfiguration >** elementów, takich jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="85c74-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="85c74-141">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="85c74-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="85c74-142">W tym kroku zostanie przetestować aplikację ASP.NET włączoną WIF, aby sprawdzić, czy włączono wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="85c74-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="85c74-143">Aby przetestować aplikację ASP.NET włączoną WIF do wykrywania powtórzeń</span><span class="sxs-lookup"><span data-stu-id="85c74-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="85c74-144">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="85c74-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="85c74-145">Powinna być wyświetlana domyślna strona główna programu ASP.NET i automatycznie uwierzytelniony nazwy użytkownika *Jakub*, która jest zwracana przez usługę STS programowanie domyślny użytkownik.</span><span class="sxs-lookup"><span data-stu-id="85c74-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="85c74-146">Naciśnij klawisz przeglądarki **ponownie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="85c74-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="85c74-147">Powinna pojawić się **błąd serwera w "/" aplikacja** strona zawierająca następujący opis: *ID1062: wykryto powtarzania: tokenu: "System.IdentityModel.Tokens.SamlSecurityToken"* , a następnie *identyfikator potwierdzenia* i *wystawcy*.</span><span class="sxs-lookup"><span data-stu-id="85c74-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="85c74-148">Ta strona błędu jest wyświetlany, ponieważ wystąpił wyjątek typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> został zgłoszony, gdy wykryto powtórzeń tokenów.</span><span class="sxs-lookup"><span data-stu-id="85c74-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="85c74-149">Ten błąd występuje, ponieważ próbujesz ponownie wysłać początkowe żądanie POST, gdy token najpierw został przedstawiony.</span><span class="sxs-lookup"><span data-stu-id="85c74-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="85c74-150">**Ponownie** przycisku nie spowoduje to zachowanie na kolejnych żądań wysyłanych do serwera.</span><span class="sxs-lookup"><span data-stu-id="85c74-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
