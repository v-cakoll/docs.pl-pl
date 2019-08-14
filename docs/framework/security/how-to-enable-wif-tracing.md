---
title: 'Instrukcje: Włączanie śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971515"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="db1e0-102">Instrukcje: Włączanie śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="db1e0-102">How To: Enable WIF Tracing</span></span>

## <a name="applies-to"></a><span data-ttu-id="db1e0-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="db1e0-103">Applies To</span></span>

- <span data-ttu-id="db1e0-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="db1e0-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="db1e0-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="db1e0-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="db1e0-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="db1e0-106">Summary</span></span>

<span data-ttu-id="db1e0-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące włączania śledzenia WIF w aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="db1e0-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="db1e0-108">Zawiera również instrukcje testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dziennik działają prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="db1e0-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="db1e0-109">Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp.</span><span class="sxs-lookup"><span data-stu-id="db1e0-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="db1e0-110">Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="db1e0-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="db1e0-111">Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="db1e0-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="db1e0-112">Można go pobrać z następującej lokalizacji: [Narzędzie tożsamości i dostępu](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="db1e0-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db1e0-113">Włączenie śledzenia WIF dla pasywnych aplikacji, czyli aplikacji korzystających z protokołu WS-Federation, może potencjalnie uwidocznić aplikację w oddziałach ataków typu "odmowa usługi" (DoS) lub ujawnienie informacji złośliwej stronie.</span><span class="sxs-lookup"><span data-stu-id="db1e0-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="db1e0-114">Obejmuje to zarówno pasywne RPS pliku, jak i pasywne STSes.</span><span class="sxs-lookup"><span data-stu-id="db1e0-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="db1e0-115">Z tego powodu zalecamy, aby nie włączać śledzenia WIF dla pasywnego RPS pliku lub STSes w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="db1e0-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>

## <a name="contents"></a><span data-ttu-id="db1e0-116">Spis treści</span><span class="sxs-lookup"><span data-stu-id="db1e0-116">Contents</span></span>

- <span data-ttu-id="db1e0-117">Cele</span><span class="sxs-lookup"><span data-stu-id="db1e0-117">Objectives</span></span>

- <span data-ttu-id="db1e0-118">Omówienie</span><span class="sxs-lookup"><span data-stu-id="db1e0-118">Overview</span></span>

- <span data-ttu-id="db1e0-119">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="db1e0-119">Summary of Steps</span></span>

- <span data-ttu-id="db1e0-120">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="db1e0-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="db1e0-121">Krok 2 — testowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="db1e0-121">Step 2 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="db1e0-122">Cele</span><span class="sxs-lookup"><span data-stu-id="db1e0-122">Objectives</span></span>

- <span data-ttu-id="db1e0-123">Utwórz prostą aplikację ASP.NET, która używa WIF i usługi STS do tworzenia oprogramowania w ramach narzędzia do identyfikacji i uzyskiwania dostępu</span><span class="sxs-lookup"><span data-stu-id="db1e0-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>

- <span data-ttu-id="db1e0-124">Włącz śledzenie i sprawdź, czy działa</span><span class="sxs-lookup"><span data-stu-id="db1e0-124">Enable tracing and verify that it is working</span></span>

## <a name="overview"></a><span data-ttu-id="db1e0-125">Omówienie</span><span class="sxs-lookup"><span data-stu-id="db1e0-125">Overview</span></span>

<span data-ttu-id="db1e0-126">Funkcja śledzenia umożliwia debugowanie i rozwiązywanie problemów z wieloma typami problemów z usługą WIF, w tym z tokenami, plikami cookie, oświadczeniami, komunikatami protokołu itd.</span><span class="sxs-lookup"><span data-stu-id="db1e0-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="db1e0-127">Śledzenie WIF jest podobne do śledzenia WCF; na przykład można wybrać poziom szczegółowości śladów, aby wyświetlić wszystkie informacje od krytycznych komunikatów do wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="db1e0-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="db1e0-128">Ślady WIF można generować w plikach **XML** lub w plikach **. svclog** , które są widoczne przy użyciu narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="db1e0-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="db1e0-129">To narzędzie znajduje się w katalogu **bin** ścieżki instalacji Windows SDK na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="db1e0-130">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="db1e0-130">Summary of Steps</span></span>

- <span data-ttu-id="db1e0-131">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="db1e0-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="db1e0-132">Krok 2 — testowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="db1e0-132">Step 2 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="db1e0-133">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="db1e0-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

<span data-ttu-id="db1e0-134">W tym kroku utworzysz nową aplikację ASP.NET Web Forms i zmodyfikujesz plik *Web. config* w celu włączenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="db1e0-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="db1e0-135">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="db1e0-135">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="db1e0-136">Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="db1e0-137">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="db1e0-138">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-138">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="db1e0-139">Kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

5. <span data-ttu-id="db1e0-140">Zostanie wyświetlone okno **tożsamość i dostęp** .</span><span class="sxs-lookup"><span data-stu-id="db1e0-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="db1e0-141">W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

6. <span data-ttu-id="db1e0-142">Utwórz nowy folder w nazwanych **dziennikach** w katalogu głównym dysku **C:** , tak jak pokazano: **C:\LOGS**</span><span class="sxs-lookup"><span data-stu-id="db1e0-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>

7. <span data-ttu-id="db1e0-143">Dodaj następujący  **\<element System. Diagnostics >** do pliku konfiguracyjnego *Web. config* bezpośrednio po zamykającym  **\<elemencie/configSections >** , jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="db1e0-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>

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
    > <span data-ttu-id="db1e0-144">Lokalizacja katalogu określona w atrybucie **initializeData** musi istnieć przed rozpoczęciem rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="db1e0-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="db1e0-145">Jeśli lokalizacja nie istnieje, dzienniki nie zostaną utworzone.</span><span class="sxs-lookup"><span data-stu-id="db1e0-145">If the location does not exist, no logs will be created.</span></span>

     <span data-ttu-id="db1e0-146">Powyższe ustawienia konfiguracji umożliwią **pełne** śledzenie WIF i zapisywanie wynikowego dziennika w pliku **C:logsWIF.XML** .</span><span class="sxs-lookup"><span data-stu-id="db1e0-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>

## <a name="step-2--test-your-solution"></a><span data-ttu-id="db1e0-147">Krok 2 — testowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="db1e0-147">Step 2 – Test Your Solution</span></span>

<span data-ttu-id="db1e0-148">W tym kroku nastąpi przetestowanie aplikacji ASP.NET z obsługą WIF, aby sprawdzić, czy dzienniki są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="db1e0-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="db1e0-149">Aby przetestować aplikację ASP.NET z obsługą usługi WIF w celu pomyślnego śledzenia</span><span class="sxs-lookup"><span data-stu-id="db1e0-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>

1. <span data-ttu-id="db1e0-150">Uruchom rozwiązanie, naciskając klawisz **F5** .</span><span class="sxs-lookup"><span data-stu-id="db1e0-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="db1e0-151">Powinna zostać wyświetlona domyślna Strona główna ASP.NET i automatycznie uwierzytelniona przy użyciu nazwy użytkownika *Terry*, który jest domyślnym użytkownikiem zwracanym przez program Development STS.</span><span class="sxs-lookup"><span data-stu-id="db1e0-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>

2. <span data-ttu-id="db1e0-152">Zamknij okno przeglądarki, a następnie przejdź do folderu **C:\LOGS** .</span><span class="sxs-lookup"><span data-stu-id="db1e0-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="db1e0-153">Otwórz plik **C:\logs\WIF.XML** za pomocą edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="db1e0-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>

3. <span data-ttu-id="db1e0-154">Zbadaj plik **WIF. XML** i sprawdź, czy zawiera on wpisy zaczynające się  **\<od E2ETraceEvent >** .</span><span class="sxs-lookup"><span data-stu-id="db1e0-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="db1e0-155">Te ślady będą zawierać  **\<TraceRecord >** elementy z opisami działań śledzonych, takich jak **Walidacja obiektu SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="db1e0-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
