---
title: 'Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990477"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="71488-102">Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="71488-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="71488-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="71488-103">Applies To</span></span>  
  
- <span data-ttu-id="71488-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="71488-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="71488-105">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="71488-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
- <span data-ttu-id="71488-106">Rozwiązywanie problemów i debugowanie aplikacji WIF</span><span class="sxs-lookup"><span data-stu-id="71488-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="71488-107">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="71488-107">Summary</span></span>  
 <span data-ttu-id="71488-108">W tym temacie opisano czynności wymagane do skonfigurowania śledzenia WIF, zbierania dzienników śledzenia i analizowania dzienników śledzenia za pomocą narzędzia Podgląd śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="71488-109">Zapewnia ogólne mapowanie dla wpisów śledzenia do akcji wymaganych do rozwiązywania problemów związanych z WIF.</span><span class="sxs-lookup"><span data-stu-id="71488-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="71488-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="71488-110">Contents</span></span>  
  
- <span data-ttu-id="71488-111">Cele</span><span class="sxs-lookup"><span data-stu-id="71488-111">Objectives</span></span>  
  
- <span data-ttu-id="71488-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="71488-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="71488-113">Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config</span><span class="sxs-lookup"><span data-stu-id="71488-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="71488-114">Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia</span><span class="sxs-lookup"><span data-stu-id="71488-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="71488-115">Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF</span><span class="sxs-lookup"><span data-stu-id="71488-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
- <span data-ttu-id="71488-116">Elementy pokrewne</span><span class="sxs-lookup"><span data-stu-id="71488-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="71488-117">Cele</span><span class="sxs-lookup"><span data-stu-id="71488-117">Objectives</span></span>  
  
- <span data-ttu-id="71488-118">Skonfiguruj śledzenie WIF.</span><span class="sxs-lookup"><span data-stu-id="71488-118">Configure WIF tracing.</span></span>  
  
- <span data-ttu-id="71488-119">Wyświetlanie dzienników śledzenia w narzędziu Podgląd śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-119">View trace logs in the Trace Viewer tool.</span></span>  
  
- <span data-ttu-id="71488-120">Identyfikuj problemy związane z WIF w dziennikach śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-120">Identify WIF related issues in the trace logs.</span></span>  
  
- <span data-ttu-id="71488-121">Stosuj akcje naprawcze do WIF związanych z nimi problemów znalezionych w dziennikach śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="71488-122">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="71488-122">Summary of Steps</span></span>  
  
- <span data-ttu-id="71488-123">Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config</span><span class="sxs-lookup"><span data-stu-id="71488-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="71488-124">Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia</span><span class="sxs-lookup"><span data-stu-id="71488-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="71488-125">Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF</span><span class="sxs-lookup"><span data-stu-id="71488-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="71488-126">Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config</span><span class="sxs-lookup"><span data-stu-id="71488-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="71488-127">W tym kroku dodasz zmiany do sekcji konfiguracyjnych w pliku *Web. config* , który umożliwi WIF śledzenie zdarzeń i przechowywanie ich w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="71488-128">Aby skonfigurować śledzenie WIF przy użyciu pliku konfiguracyjnego Web. config</span><span class="sxs-lookup"><span data-stu-id="71488-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="71488-129">Otwórz plik konfiguracyjny root **Web. config** lub **App. config** w edytorze programu Visual Studio, klikając go dwukrotnie w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="71488-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="71488-130">Jeśli Twoje rozwiązanie nie ma pliku konfiguracyjnego **Web. config** lub **App. config** , Dodaj go, klikając rozwiązanie w **Eksplorator rozwiązań** i klikając pozycję **Dodaj**, a następnie klikając pozycję **nowy element.** ...</span><span class="sxs-lookup"><span data-stu-id="71488-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="71488-131">W oknie dialogowym **nowy element** wybierz pozycję **plik konfiguracyjny aplikacji pliku** **App. config** lub **plik konfiguracji sieci Web dla pliku** **Web. config** z listy i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="71488-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="71488-132">Dodaj wpisy konfiguracji podobne do poniższego do pliku  **\<** konfiguracji w węźle Configuration > Node na końcu pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="71488-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3. <span data-ttu-id="71488-133">Powyższa konfiguracja nakazuje WIF wygenerowanie pełnych zdarzeń śledzenia i zarejestrowanie ich w pliku *WIFTrace. e2e* .</span><span class="sxs-lookup"><span data-stu-id="71488-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="71488-134">Aby uzyskać pełną listę wartości przełącznika **switchValue** , zapoznaj się z tabelą poziomów śledzenia znajdującą się w następującym temacie: [Konfigurowanie śledzenia](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="71488-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="71488-135">Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia</span><span class="sxs-lookup"><span data-stu-id="71488-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="71488-136">W tym kroku użyjesz narzędzia do przeglądania śledzenia (SvcTraceViewer. exe) do analizowania dzienników śledzenia WIF.</span><span class="sxs-lookup"><span data-stu-id="71488-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="71488-137">Aby analizować dzienniki śledzenia WIF za pomocą narzędzia Podgląd śledzenia (SvcTraceViewer. exe)</span><span class="sxs-lookup"><span data-stu-id="71488-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="71488-138">Narzędzie Podgląd śledzenia (SvcTraceViewer. exe) jest dostarczane jako część Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="71488-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="71488-139">Jeśli nie zainstalowano jeszcze Windows SDK, możesz pobrać go tutaj: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="71488-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="71488-140">Uruchom narzędzie Podgląd śledzenia (SvcTraceViewer. exe).</span><span class="sxs-lookup"><span data-stu-id="71488-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="71488-141">Jest ona zazwyczaj dostępna w folderze **bin** ścieżki instalacji.</span><span class="sxs-lookup"><span data-stu-id="71488-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="71488-142">Otwórz plik dziennika śledzenia WIF, na przykład WIFTrace. E2E, wybierając **plik**, **Otwórz...**</span><span class="sxs-lookup"><span data-stu-id="71488-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="71488-143">opcji w menu lub przy użyciu skrótu **Ctrl + O** .</span><span class="sxs-lookup"><span data-stu-id="71488-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="71488-144">Plik dziennika śledzenia zostanie otwarty w narzędziu Podgląd śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="71488-145">Przejrzyj pozycje na karcie **działanie** . Każdy wpis powinien zawierać numer działania, liczbę zarejestrowanych śladów, czas trwania działania oraz jego początkową i końcową sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="71488-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="71488-146">Kliknij kartę **działanie** . W obszarze głównym narzędzia powinny być widoczne szczegółowe wpisy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="71488-147">Użyj listy rozwijanej **poziom** w menu, aby odfiltrować określony poziom śladów, na przykład: **Wszystkie**, **Ostrzeżenie**, **Błędy**, **informacje**itd.</span><span class="sxs-lookup"><span data-stu-id="71488-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="71488-148">Kliknij określone wpisy śledzenia, aby przejrzeć szczegóły w dolnym obszarze narzędzia.</span><span class="sxs-lookup"><span data-stu-id="71488-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="71488-149">Szczegóły można wyświetlać przy użyciu **sformatowanego** i **XML** widoku, wybierając odpowiednie karty.</span><span class="sxs-lookup"><span data-stu-id="71488-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="71488-150">Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF</span><span class="sxs-lookup"><span data-stu-id="71488-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="71488-151">W tym kroku można zidentyfikować rozwiązania dla problemów związanych z WIF, które zostały zidentyfikowane przy użyciu dziennika śledzenia WIF i narzędzia Podgląd śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71488-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="71488-152">Przedstawia ogólne mapowanie wyjątków związanych z WIF na potencjalne rozwiązania lub wymagane działania w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="71488-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="71488-153">Aby zidentyfikować rozwiązania do rozwiązywania problemów związanych z WIF</span><span class="sxs-lookup"><span data-stu-id="71488-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="71488-154">Zapoznaj się z poniższą tabelą wyjątków WIF i wymaganych akcji, aby rozwiązać problemy.</span><span class="sxs-lookup"><span data-stu-id="71488-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="71488-155">**Identyfikator błędu**</span><span class="sxs-lookup"><span data-stu-id="71488-155">**Error ID**</span></span>|<span data-ttu-id="71488-156">**Komunikat o błędzie**</span><span class="sxs-lookup"><span data-stu-id="71488-156">**Error Message**</span></span>|<span data-ttu-id="71488-157">**Akcja wymagana do usunięcia błędu**</span><span class="sxs-lookup"><span data-stu-id="71488-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="71488-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="71488-158">ID4175</span></span>|<span data-ttu-id="71488-159">Wystawca tokenu zabezpieczającego nie został rozpoznany przez IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="71488-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="71488-160">Aby zaakceptować tokeny zabezpieczające z tego wystawcy, należy skonfigurować IssuerNameRegistry do zwrócenia prawidłowej nazwy dla tego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="71488-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="71488-161">Ten błąd może być spowodowany przez skopiowanie odcisku palca z przystawki programu MMC i wklejenie go do pliku *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="71488-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="71488-162">W tym celu można uzyskać dodatkowy znak niedrukowalny w ciągu tekstowym podczas kopiowania z okna właściwości certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="71488-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="71488-163">Ten dodatkowy znak powoduje niepowodzenie dopasowania odcisku palca.</span><span class="sxs-lookup"><span data-stu-id="71488-163">This extra character causes the thumbprint match to fail.</span></span> <span data-ttu-id="71488-164">Procedurę prawidłowego kopiowania odcisku palca można znaleźć na stronie Logowanie jednokrotne [oparte na oświadczeniach dla sieci Web i Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="71488-164">The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="71488-165">Elementy pokrewne</span><span class="sxs-lookup"><span data-stu-id="71488-165">Related Items</span></span>  
  
- [<span data-ttu-id="71488-166">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="71488-166">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
