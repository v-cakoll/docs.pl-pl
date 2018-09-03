---
title: 'Instrukcje: Włączanie wykrywania powtarzania tokenu'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd5adf39c37fce92d4caf1d85e2a6a12e9e6b59b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486519"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="4adbb-102">Instrukcje: Włączanie wykrywania powtarzania tokenu</span><span class="sxs-lookup"><span data-stu-id="4adbb-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="4adbb-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="4adbb-103">Applies To</span></span>  
  
-   <span data-ttu-id="4adbb-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4adbb-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="4adbb-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="4adbb-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4adbb-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="4adbb-106">Summary</span></span>  
 <span data-ttu-id="4adbb-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące włączania wykrywania powtarzania tokenu w aplikacji ASP.NET, który używa programu WIF.</span><span class="sxs-lookup"><span data-stu-id="4adbb-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="4adbb-108">On również instrukcje testowania aplikacji pozwalające sprawdzić, czy jest włączone wykrywanie powtórzeń tokenów.</span><span class="sxs-lookup"><span data-stu-id="4adbb-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="4adbb-109">Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp.</span><span class="sxs-lookup"><span data-stu-id="4adbb-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="4adbb-110">Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="4adbb-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="4adbb-111">Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="4adbb-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="4adbb-112">Można go pobrać z następującej lokalizacji: [narzędzie tożsamość i dostęp](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="4adbb-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="4adbb-113">Spis treści</span><span class="sxs-lookup"><span data-stu-id="4adbb-113">Contents</span></span>  
  
-   <span data-ttu-id="4adbb-114">Cele</span><span class="sxs-lookup"><span data-stu-id="4adbb-114">Objectives</span></span>  
  
-   <span data-ttu-id="4adbb-115">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4adbb-115">Overview</span></span>  
  
-   <span data-ttu-id="4adbb-116">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4adbb-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4adbb-117">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania</span><span class="sxs-lookup"><span data-stu-id="4adbb-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="4adbb-118">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4adbb-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="4adbb-119">Cele</span><span class="sxs-lookup"><span data-stu-id="4adbb-119">Objectives</span></span>  
  
-   <span data-ttu-id="4adbb-120">Utwórz prostą aplikację platformy ASP.NET, który używa programu WIF i deweloperskiej usługi STS z narzędzie tożsamość i dostęp</span><span class="sxs-lookup"><span data-stu-id="4adbb-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="4adbb-121">Włączanie wykrywania powtarzania tokenu i sprawdź, czy działa ona</span><span class="sxs-lookup"><span data-stu-id="4adbb-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4adbb-122">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4adbb-122">Overview</span></span>  
 <span data-ttu-id="4adbb-123">Atak przez powtarzanie występuje, gdy klienci podejmują próbę uwierzytelnienia do jednostki uzależnionej przy użyciu tokenu usługi STS, została już użyta przez klienta.</span><span class="sxs-lookup"><span data-stu-id="4adbb-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="4adbb-124">Aby uniknąć tego ataku, program WIF zawiera pamięci podręcznej wykrywania powtórzeń tokenów usługi STS, poprzednio używanych.</span><span class="sxs-lookup"><span data-stu-id="4adbb-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="4adbb-125">Po włączeniu wykrywania powtarzania sprawdza token żądania przychodzącego i sprawdza, czy token został wcześniej użyty.</span><span class="sxs-lookup"><span data-stu-id="4adbb-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="4adbb-126">Jeśli token został już użyty, żądanie zostało odrzucone i <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4adbb-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="4adbb-127">Poniższe kroki pokazują zmiany konfiguracji wymagane do włączenia wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="4adbb-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="4adbb-128">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4adbb-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4adbb-129">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania</span><span class="sxs-lookup"><span data-stu-id="4adbb-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="4adbb-130">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4adbb-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="4adbb-131">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania</span><span class="sxs-lookup"><span data-stu-id="4adbb-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="4adbb-132">W tym kroku utworzysz nowej aplikacji ASP.NET Web Forms i zmodyfikować *Web.config* plik w celu włączenia wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="4adbb-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="4adbb-133">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4adbb-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="4adbb-134">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4adbb-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="4adbb-135">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="4adbb-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="4adbb-136">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="4adbb-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="4adbb-137">Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="4adbb-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="4adbb-138">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="4adbb-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="4adbb-139">W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="4adbb-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="4adbb-140">Dodaj następujący kod  **\<tokenReplayDetection >** elementu *Web.config* pliku konfiguracji, natychmiast po  **\<system.identityModel >** i  **\<identityConfiguration >** elementów, takich jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="4adbb-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="4adbb-141">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4adbb-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="4adbb-142">W tym kroku przetestujesz aplikację ASP.NET z włączoną obsługą programu WIF, aby sprawdzić, czy włączono wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="4adbb-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="4adbb-143">Aby przetestować aplikację ASP.NET z włączoną obsługą programu WIF do wykrywania powtórzeń</span><span class="sxs-lookup"><span data-stu-id="4adbb-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="4adbb-144">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="4adbb-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="4adbb-145">Użytkownik powinien być prezentowane z domyślną stronę główną struktury ASP.NET i automatycznie uwierzytelniana przy użyciu nazwy użytkownika *Terry*, która jest domyślny użytkownik, który jest zwracany za pomocą deweloperskiej usługi STS.</span><span class="sxs-lookup"><span data-stu-id="4adbb-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="4adbb-146">Naciśnij w przeglądarce **ponownie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4adbb-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="4adbb-147">Powinna pojawić się **błąd serwera w aplikacji» /»** strony na następujący opis: *ID1062: wykryto powtarzania: Token: "System.IdentityModel.Tokens.SamlSecurityToken"* , a następnie *identyfikator potwierdzenia* i *wystawcy*.</span><span class="sxs-lookup"><span data-stu-id="4adbb-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="4adbb-148">Ta strona błędu jest wyświetlana, ponieważ wystąpił wyjątek typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> był zgłaszany, gdy wykryto powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="4adbb-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="4adbb-149">Ten błąd występuje, ponieważ próbujesz ponownie wysłać żądanie POST początkowej, najpierw umieszczeniem tokenu.</span><span class="sxs-lookup"><span data-stu-id="4adbb-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="4adbb-150">**Ponownie** przycisku nie spowoduje to zachowanie dla kolejnych żądań do serwera.</span><span class="sxs-lookup"><span data-stu-id="4adbb-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
