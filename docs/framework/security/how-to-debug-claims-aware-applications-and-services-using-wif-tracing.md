---
title: 'Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 38e168fff9bc351b6239c41197348d24129a4747
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453396"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="77046-102">Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="77046-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="77046-103">Applies To</span></span>  
  
-   <span data-ttu-id="77046-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="77046-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="77046-105">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="77046-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="77046-106">Rozwiązywanie problemów i debugowanie aplikacji programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="77046-107">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="77046-107">Summary</span></span>  
 <span data-ttu-id="77046-108">Niniejszy instruktaż zawiera opis czynności, jak skonfigurować śledzenia programu WIF, gromadzić dzienniki śledzenia i jak można analizować śledzenia loguje się przy użyciu narzędzia podglądu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="77046-109">Umożliwia mapowanie ogólnych dla wpisów śledzenia akcje niezbędne do rozwiązywania problemów związanych z programu WIF.</span><span class="sxs-lookup"><span data-stu-id="77046-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="77046-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="77046-110">Contents</span></span>  
  
-   <span data-ttu-id="77046-111">Cele</span><span class="sxs-lookup"><span data-stu-id="77046-111">Objectives</span></span>  
  
-   <span data-ttu-id="77046-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="77046-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="77046-113">Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="77046-114">Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="77046-115">Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą</span><span class="sxs-lookup"><span data-stu-id="77046-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="77046-116">Powiązane elementy</span><span class="sxs-lookup"><span data-stu-id="77046-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="77046-117">Cele</span><span class="sxs-lookup"><span data-stu-id="77046-117">Objectives</span></span>  
  
-   <span data-ttu-id="77046-118">Konfigurowanie śledzenia programu WIF.</span><span class="sxs-lookup"><span data-stu-id="77046-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="77046-119">Wyświetl dzienniki śledzenia w narzędziu przeglądarki danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="77046-120">Identyfikowanie WIF powiązane problemy w dziennikach śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="77046-121">Zastosuj działania naprawcze, aby program WIF powiązane problemy znalezione w dziennikach śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="77046-122">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="77046-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="77046-123">Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="77046-124">Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="77046-125">Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą</span><span class="sxs-lookup"><span data-stu-id="77046-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="77046-126">Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="77046-127">W tym kroku dodasz zmiany do sekcji konfiguracyjnych w *Web.config* pliku, pozwalających na korzystanie z programu WIF do śledzenia jego zdarzeń i przechowywania ich w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="77046-128">Aby skonfigurować śledzenia programu WIF, przy użyciu pliku konfiguracji Web.config</span><span class="sxs-lookup"><span data-stu-id="77046-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1.  <span data-ttu-id="77046-129">Otwórz katalog główny **Web.config** lub **App.config** plik konfiguracji w edytorze programu Visual Studio przez dwukrotne kliknięcie go w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="77046-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="77046-130">Jeśli rozwiązanie nie ma **Web.config** lub **App.config** konfiguracji pliku, dodaj ją, klikając prawym przyciskiem rozwiązania w **Eksploratora rozwiązań** i klikając  **Dodaj**, klikając **nowy element...** .</span><span class="sxs-lookup"><span data-stu-id="77046-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="77046-131">Na **nowy element** okno dialogowe, wybierz **pliku konfiguracji aplikacji** dla **App.config** lub **pliku konfiguracji sieci Web** dla **Web.config** z listy i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="77046-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2.  <span data-ttu-id="77046-132">Dodania wpisów konfiguracji, które podobny do następującego pliku konfiguracji wewnątrz  **\<konfiguracji >** węzła w końcu pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="77046-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
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
  
3.  <span data-ttu-id="77046-133">Powyższa konfiguracja powoduje, że program WIF generowanie zdarzeń śledzenia pełne i zaloguj się do *WIFTrace.e2e* pliku.</span><span class="sxs-lookup"><span data-stu-id="77046-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="77046-134">Aby uzyskać pełną listę wartości **switchValue** przełącznika, można znaleźć w tabeli Poziom śledzenia w następującym temacie: [Konfigurowanie śledzenia](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="77046-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="77046-135">Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF</span><span class="sxs-lookup"><span data-stu-id="77046-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="77046-136">W tym kroku użyjesz Trace Viewer Tool (SvcTraceViewer.exe) do analizowania dzienników śledzenia programu WIF.</span><span class="sxs-lookup"><span data-stu-id="77046-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="77046-137">Aby analizować dzienniki śledzenia programu WIF, za pomocą narzędzia podglądu śledzenia (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="77046-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1.  <span data-ttu-id="77046-138">Narzędzie do śledzenia (SvcTraceViewer.exe) jest dostarczany jako część zestawu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="77046-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="77046-139">Jeśli jeszcze nie zainstalowano zestawu Windows SDK, możesz ją pobrać tutaj: [zestawu Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="77046-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2.  <span data-ttu-id="77046-140">Uruchom narzędzie przeglądarki danych śledzenia (SvcTraceViewer.exe).</span><span class="sxs-lookup"><span data-stu-id="77046-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="77046-141">Jest ona zazwyczaj dostępna w **Bin** folderze ścieżka instalacji.</span><span class="sxs-lookup"><span data-stu-id="77046-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3.  <span data-ttu-id="77046-142">Otwórz plik dziennika śledzenia programu WIF, na przykład WIFTrace.e2e, wybierając **pliku**, **Otwórz...**</span><span class="sxs-lookup"><span data-stu-id="77046-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="77046-143">Opcja menu lub za pomocą **Ctrl + O** skrótów.</span><span class="sxs-lookup"><span data-stu-id="77046-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="77046-144">Plik dziennika śledzenia zostanie otwarty w narzędziu przeglądarki danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4.  <span data-ttu-id="77046-145">Przejrzyj wpisy w **działania** kartę. Każdy wpis powinien zawierać numer działania, Liczba śladów, które zostały zarejestrowane, czas trwania działania i jego znaczniki czasu rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="77046-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5.  <span data-ttu-id="77046-146">Kliknij pozycję **działania** kartę. Powinny być widoczne wpisy szczegółowe śledzenie, w obszarze głównym narzędzia.</span><span class="sxs-lookup"><span data-stu-id="77046-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="77046-147">Użyj **poziom** listy rozwijanej w menu, aby filtrować określony poziom ślady, na przykład: **wszystkich**, **ostrzeżenie**, **błędy**, **Informacji**itp.</span><span class="sxs-lookup"><span data-stu-id="77046-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6.  <span data-ttu-id="77046-148">Polecenie śledzenia określonych wpisów, aby zapoznać się z informacjami w dolnym obszarze narzędzia.</span><span class="sxs-lookup"><span data-stu-id="77046-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="77046-149">Szczegółowe informacje można wyświetlić przy użyciu **sformatowany** i **XML** widoku przez wybranie odpowiednich kart.</span><span class="sxs-lookup"><span data-stu-id="77046-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="77046-150">Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą</span><span class="sxs-lookup"><span data-stu-id="77046-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="77046-151">W tym kroku możesz zidentyfikować rozwiązania problemów dotyczących programu WIF, identyfikowane za pomocą programu WIF w dzienniku śledzenia i narzędzie do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77046-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="77046-152">Zawiera opis ogólnego mapowania środowiska WIF powiązane wyjątki potencjalnych rozwiązań lub wymagane akcje, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="77046-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="77046-153">Aby zidentyfikować rozwiązania, aby naprawić program WIF problemy związane z usługą</span><span class="sxs-lookup"><span data-stu-id="77046-153">To identify solutions to fix WIF related issues</span></span>  
  
1.  <span data-ttu-id="77046-154">Przejrzyj poniższą tabelę wyjątków programu WIF i wymaganych działań do rozwiązania problemów.</span><span class="sxs-lookup"><span data-stu-id="77046-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="77046-155">**Identyfikator błędu**</span><span class="sxs-lookup"><span data-stu-id="77046-155">**Error ID**</span></span>|<span data-ttu-id="77046-156">**Komunikat o błędzie**</span><span class="sxs-lookup"><span data-stu-id="77046-156">**Error Message**</span></span>|<span data-ttu-id="77046-157">**Wymagana akcja naprawić błąd**</span><span class="sxs-lookup"><span data-stu-id="77046-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="77046-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="77046-158">ID4175</span></span>|<span data-ttu-id="77046-159">Wystawca tokenu zabezpieczającego nie został rozpoznany przez IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="77046-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="77046-160">Aby zaakceptować tokeny zabezpieczające z tym wystawcą, skonfiguruj IssuerNameRegistry zwrócić prawidłową nazwę tego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="77046-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="77046-161">Ten błąd może być spowodowany przez skopiowanie odcisku palca z przystawki programu MMC i wklejenie go do *Web.config* pliku.</span><span class="sxs-lookup"><span data-stu-id="77046-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="77046-162">W szczególności można uzyskać dodatkowych niedrukowalne znaki w ciągu tekstowym, podczas kopiowania z okna właściwości certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="77046-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="77046-163">Ten dodatkowy znak powoduje, że dopasowanie odcisku palca, aby zakończyć się niepowodzeniem. Procedurę poprawnie kopiowania odcisk palca znajduje się w temacie [logowania jednokrotnego opartego na oświadczeniach — na sieci Web i Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="77046-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="77046-164">Powiązane elementy</span><span class="sxs-lookup"><span data-stu-id="77046-164">Related Items</span></span>  
  
-   [<span data-ttu-id="77046-165">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="77046-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
