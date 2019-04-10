---
title: 'Instrukcje: Włączanie śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 83382a8375538acc04d293ee938a4e845d5e8820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310268"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="ff6d1-102">Instrukcje: Włączanie śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="ff6d1-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="ff6d1-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="ff6d1-103">Applies To</span></span>  
  
-   <span data-ttu-id="ff6d1-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ff6d1-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ff6d1-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="ff6d1-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ff6d1-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-106">Summary</span></span>  
 <span data-ttu-id="ff6d1-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące włączania śledzenia programu WIF w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="ff6d1-108">Tu również instrukcje testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dzienników są poprawne.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="ff6d1-109">Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="ff6d1-110">Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="ff6d1-111">Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="ff6d1-112">Można go pobrać z następującej lokalizacji: [Narzędzie tożsamość i dostęp](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="ff6d1-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff6d1-113">Włączanie śledzenia programu WIF pasywne aplikacje, oznacza to, aplikacje, które używają protokołu WS-Federation potencjalnie uwidocznić aplikacji złośliwa strona atakom typu odmowa usługi (DoS) lub ujawnienie informacji.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="ff6d1-114">Obejmuje to zarówno pasywnym RPs i STSes pasywnym.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="ff6d1-115">Z tego powodu zaleca się, że możesz nie umożliwiają śledzenia programu WIF pasywnym RPs lub STSes w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="ff6d1-116">Spis treści</span><span class="sxs-lookup"><span data-stu-id="ff6d1-116">Contents</span></span>  
  
-   <span data-ttu-id="ff6d1-117">Cele</span><span class="sxs-lookup"><span data-stu-id="ff6d1-117">Objectives</span></span>  
  
-   <span data-ttu-id="ff6d1-118">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-118">Overview</span></span>  
  
-   <span data-ttu-id="ff6d1-119">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="ff6d1-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ff6d1-120">Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="ff6d1-121">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ff6d1-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="ff6d1-122">Cele</span><span class="sxs-lookup"><span data-stu-id="ff6d1-122">Objectives</span></span>  
  
-   <span data-ttu-id="ff6d1-123">Utwórz prostą aplikację platformy ASP.NET, który używa programu WIF i deweloperskiej usługi STS z narzędzie tożsamość i dostęp</span><span class="sxs-lookup"><span data-stu-id="ff6d1-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="ff6d1-124">Włącz śledzenie i sprawdź, czy działa ona</span><span class="sxs-lookup"><span data-stu-id="ff6d1-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ff6d1-125">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-125">Overview</span></span>  
 <span data-ttu-id="ff6d1-126">Śledzenie umożliwia debugowanie i rozwiązywanie problemów z wielu typów problemów za pomocą programu WIF, łącznie z tokenów, plików cookie, oświadczeń i komunikaty protokołu.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="ff6d1-127">Śledzenia programu WIF jest podobny do śledzenia WCF; na przykład można wybrać poziom szczegółowości śledzenia, aby wyświetlić wszystko — od krytycznych wiadomości o wszystkie komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="ff6d1-128">Dane śledzenia programu WIF, mogą być generowane w **.xml** plików lub **.svclog** pliki, które można przeglądać przy użyciu narzędzia podglądu śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="ff6d1-129">To narzędzie znajduje się w **bin** katalogu zestawu Windows SDK ścieżka instalacji na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="ff6d1-130">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="ff6d1-130">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ff6d1-131">Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="ff6d1-132">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ff6d1-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="ff6d1-133">Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie</span><span class="sxs-lookup"><span data-stu-id="ff6d1-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="ff6d1-134">W tym kroku utworzysz nowej aplikacji ASP.NET Web Forms i zmodyfikować *Web.config* plik, aby umożliwić śledzenie.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="ff6d1-135">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff6d1-135">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="ff6d1-136">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="ff6d1-137">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="ff6d1-138">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="ff6d1-139">Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="ff6d1-140">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="ff6d1-141">W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="ff6d1-142">Utwórz nowy folder w nazwie **dzienniki** w katalogu głównym **C:** dysku, jak pokazano: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="ff6d1-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7. <span data-ttu-id="ff6d1-143">Dodaj następujący kod  **\<system.diagnostics >** elementu *Web.config* pliku konfiguracji, natychmiast po zamykającym  **\</configSections >** elementu, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="ff6d1-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
            ...
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ff6d1-144">Lokalizacja katalogu określonego w **initializeData** atrybut musi istnieć przed rozpoczęciem rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="ff6d1-145">Jeśli lokalizacja nie istnieje, zostanie utworzony żadnych dzienników.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="ff6d1-146">Powyższe ustawienia konfiguracji spowoduje włączenie **pełne** śledzenia dla programu WIF i zapisać wynikowy dziennik, aby **C:logsWIF.xml** pliku.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="ff6d1-147">Krok 2 — przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ff6d1-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="ff6d1-148">W tym kroku przetestujesz aplikację ASP.NET z włączoną obsługą programu WIF, aby sprawdzić, czy dzienniki są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="ff6d1-149">Aby przetestować aplikację ASP.NET z włączoną obsługą programu WIF do śledzenia pomyślnych</span><span class="sxs-lookup"><span data-stu-id="ff6d1-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1. <span data-ttu-id="ff6d1-150">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="ff6d1-151">Użytkownik powinien być prezentowane z domyślną stronę główną struktury ASP.NET i automatycznie uwierzytelniana przy użyciu nazwy użytkownika *Terry*, która jest domyślny użytkownik, który jest zwracany za pomocą deweloperskiej usługi STS.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="ff6d1-152">Zamknij okno przeglądarki, a następnie przejdź do **C:\logs** folderu.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="ff6d1-153">Otwórz **C:\logs\WIF.xml** plików za pomocą edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3. <span data-ttu-id="ff6d1-154">Sprawdzanie **WIF.xml** i sprawdzić, czy zawiera on zapisów, poczynając od  **\<E2ETraceEvent >**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="ff6d1-155">Ślady te będą zawierać  **\<TraceRecord >** elementy z opisami do śledzenia działania, takie jak **sprawdzania poprawności SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="ff6d1-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
