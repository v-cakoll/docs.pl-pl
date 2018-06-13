---
title: 'Porady: Włączanie śledzenia WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 459d74f3faf9fab4cba047a87ccff77d193e9026
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399568"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="716e1-102">Porady: Włączanie śledzenia WIF</span><span class="sxs-lookup"><span data-stu-id="716e1-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="716e1-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="716e1-103">Applies To</span></span>  
  
-   <span data-ttu-id="716e1-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="716e1-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="716e1-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="716e1-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="716e1-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="716e1-106">Summary</span></span>  
 <span data-ttu-id="716e1-107">Instrukcje ten zawiera szczegółowe procedury krok po kroku włączania śledzenia WIF w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="716e1-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="716e1-108">Dostępne są także instrukcje dotyczące testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dziennika są poprawne.</span><span class="sxs-lookup"><span data-stu-id="716e1-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="716e1-109">Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp.</span><span class="sxs-lookup"><span data-stu-id="716e1-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="716e1-110">Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="716e1-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="716e1-111">Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="716e1-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="716e1-112">Można go pobrać z następującej lokalizacji: [tożsamości i dostępu do narzędzia](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="716e1-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="716e1-113">Włączanie śledzenia WIF pasywne aplikacje, oznacza to, aplikacje, które korzystają z protokołu WS-Federation można narażając aplikacji strony złośliwych ataki (DoS) lub ujawnienie informacji.</span><span class="sxs-lookup"><span data-stu-id="716e1-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="716e1-114">Obejmuje to zarówno pasywnym RPs i STSes pasywnych.</span><span class="sxs-lookup"><span data-stu-id="716e1-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="716e1-115">Z tego powodu zalecamy nie włączenie śledzenia WIF pasywnym RPs lub STSes w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="716e1-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="716e1-116">Spis treści</span><span class="sxs-lookup"><span data-stu-id="716e1-116">Contents</span></span>  
  
-   <span data-ttu-id="716e1-117">Cele</span><span class="sxs-lookup"><span data-stu-id="716e1-117">Objectives</span></span>  
  
-   <span data-ttu-id="716e1-118">Omówienie</span><span class="sxs-lookup"><span data-stu-id="716e1-118">Overview</span></span>  
  
-   <span data-ttu-id="716e1-119">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="716e1-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="716e1-120">Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie</span><span class="sxs-lookup"><span data-stu-id="716e1-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="716e1-121">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="716e1-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="716e1-122">Cele</span><span class="sxs-lookup"><span data-stu-id="716e1-122">Objectives</span></span>  
  
-   <span data-ttu-id="716e1-123">Utwórz prostą aplikację ASP.NET, która używa WIF i STS programowanie z tożsamości i dostępu do narzędzia</span><span class="sxs-lookup"><span data-stu-id="716e1-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="716e1-124">Włącz śledzenie i sprawdź, czy działa ona</span><span class="sxs-lookup"><span data-stu-id="716e1-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="716e1-125">Omówienie</span><span class="sxs-lookup"><span data-stu-id="716e1-125">Overview</span></span>  
 <span data-ttu-id="716e1-126">Śledzenie umożliwia debugowania i rozwiązywania problemów z wielu rodzajów problemy z WIF, łącznie z tokenów, plików cookie, oświadczeń i komunikaty protokołu.</span><span class="sxs-lookup"><span data-stu-id="716e1-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="716e1-127">Śledzenie WIF jest podobny do śledzenia WCF; na przykład można wybrać poziom szczegółowości śledzenia do wyświetlenia wszystkich elementów krytycznych wiadomości o wszystkie komunikaty.</span><span class="sxs-lookup"><span data-stu-id="716e1-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="716e1-128">Ślady WIF mogą być generowane w **.xml** plików lub w **.svclog** plików, które są widoczne za pomocą narzędzia podglądu śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="716e1-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="716e1-129">To narzędzie znajduje się w **bin** katalogu zestawu Windows SDK ścieżka instalacji na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="716e1-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="716e1-130">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="716e1-130">Summary of Steps</span></span>  
  
-   <span data-ttu-id="716e1-131">Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie</span><span class="sxs-lookup"><span data-stu-id="716e1-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="716e1-132">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="716e1-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="716e1-133">Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie</span><span class="sxs-lookup"><span data-stu-id="716e1-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="716e1-134">W tym kroku zostanie utworzenie nowej aplikacji formularzy sieci Web ASP.NET i zmodyfikować *Web.config* plik w celu włączenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="716e1-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="716e1-135">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="716e1-135">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="716e1-136">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="716e1-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="716e1-137">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="716e1-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="716e1-138">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="716e1-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="716e1-139">Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="716e1-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="716e1-140">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="716e1-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="716e1-141">W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="716e1-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="716e1-142">Utwórz nowy folder w nazwie **dzienniki** w folderze głównym **C:** dysków, tak samo, jak pokazano: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="716e1-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7.  <span data-ttu-id="716e1-143">Dodaj następujące  **\<system.diagnostics >** elementu *Web.config* pliku konfiguracji bezpośrednio po upływie  **\</configSections >** elementu, tak samo, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="716e1-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
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
    >  <span data-ttu-id="716e1-144">Lokalizacja katalogu określonego w **initializeData —** atrybutu musi istnieć przed rozpoczęciem rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="716e1-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="716e1-145">Jeśli lokalizacja nie istnieje, zostanie utworzone żadne dzienniki.</span><span class="sxs-lookup"><span data-stu-id="716e1-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="716e1-146">Ustawienia konfiguracji powyżej spowoduje włączenie **pełne** śledzenia dla WIF i Zapisz dziennik wynikowy na **C:logsWIF.xml** pliku.</span><span class="sxs-lookup"><span data-stu-id="716e1-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="716e1-147">Krok 2 – Sprawdź swoje rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="716e1-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="716e1-148">W tym kroku zostanie przetestować aplikację ASP.NET włączone WIF, aby sprawdzić, czy dzienniki są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="716e1-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="716e1-149">Aby przetestować aplikację ASP.NET włączoną WIF pomyślne śledzenia</span><span class="sxs-lookup"><span data-stu-id="716e1-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1.  <span data-ttu-id="716e1-150">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="716e1-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="716e1-151">Powinna być wyświetlana domyślna strona główna programu ASP.NET i automatycznie uwierzytelniony nazwy użytkownika *Jakub*, która jest zwracana przez usługę STS programowanie domyślny użytkownik.</span><span class="sxs-lookup"><span data-stu-id="716e1-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="716e1-152">Zamknij okno przeglądarki, a następnie przejdź do **C:\logs** folderu.</span><span class="sxs-lookup"><span data-stu-id="716e1-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="716e1-153">Otwórz **C:\logs\WIF.xml** plików za pomocą edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="716e1-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3.  <span data-ttu-id="716e1-154">Sprawdź **WIF.xml** i sprawdzić, czy zawiera on wpisów, począwszy od  **\<E2ETraceEvent >**.</span><span class="sxs-lookup"><span data-stu-id="716e1-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="716e1-155">Te operacje śledzenia będą zawierać  **\<TraceRecord >** elementy z opisami śledzonych działania, takie jak **sprawdzania poprawności obiektu SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="716e1-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
