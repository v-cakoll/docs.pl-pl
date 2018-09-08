---
title: 'Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c27bdb75ef9950d0b2b32f742b38e141cf4981b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200527"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="a1e22-102">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a1e22-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="a1e22-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest redystrybucyjnego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a1e22-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="a1e22-104">W przypadku tworzenia aplikacji dla tej wersji programu .NET Framework, można dołączyć (łańcuch) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator w ramach wymagań wstępnych instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="a1e22-105">Obecne środowisko dostosowany lub ujednoliconego Instalatora, może chcesz uruchomić w trybie dyskretnym [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i śledzić postęp podczas wyświetlania postępu instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="a1e22-106">Aby włączyć śledzenie dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora (mogą być odtwarzane) definiuje protokół, za pomocą mapowanych na pamięć segment operacji We/Wy (rozwiązanie MMIO) do komunikowania się z ustawień (obserwatora lub chainer).</span><span class="sxs-lookup"><span data-stu-id="a1e22-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="a1e22-107">Protokół ten definiuje sposób chainer uzyskać informacje o postępie, Uzyskaj szczegółowe wyniki, odpowiadanie na wiadomości i anulować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora.</span><span class="sxs-lookup"><span data-stu-id="a1e22-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="a1e22-108">**Wywołania** .</span><span class="sxs-lookup"><span data-stu-id="a1e22-108">**Invocation** .</span></span>  <span data-ttu-id="a1e22-109">Aby wywołać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i otrzymywać informacje o postępie w sekcji Rozwiązanie MMIO, program instalacyjny, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a1e22-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="a1e22-110">Wywołaj [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]pakiet redystrybucyjny programu:</span><span class="sxs-lookup"><span data-stu-id="a1e22-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="a1e22-111">gdzie *nazwa sekcji* jest dowolną nazwę, którego chcesz użyć do identyfikacji danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="a1e22-112">Instalator .NET framework wykonującej Odczyt i zapis w sekcji Rozwiązanie MMIO asynchronicznie, dzięki czemu użytkownik może okazać się przydatna do użycia w tym czasie zdarzenia i komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a1e22-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="a1e22-113">W tym przykładzie proces instalacji programu .NET Framework jest tworzony przez konstruktora, przydziela zarówno w sekcji Rozwiązanie MMIO (`TheSectionName`) i definiuje zdarzenia (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="a1e22-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="a1e22-114">Zamień tych nazw z nazwami, które są unikatowe dla programu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a1e22-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="a1e22-115">Przeczytaj, w sekcji Rozwiązanie MMIO.</span><span class="sxs-lookup"><span data-stu-id="a1e22-115">Read from the MMIO section.</span></span> <span data-ttu-id="a1e22-116">W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], operacji pobierania i instalacji jest jednoczesne: jednej części programu .NET Framework może być instalowany podczas pobierania innej części.</span><span class="sxs-lookup"><span data-stu-id="a1e22-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="a1e22-117">W rezultacie postępu są wysyłane z powrotem (zapisywanych) w sekcji Rozwiązanie MMIO jako dwóch liczb (`m_downloadSoFar` i `m_installSoFar`), zwiększyć z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="a1e22-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="a1e22-118">Po zapisaniu 255 i umożliwia zamknięcie systemu .NET Framework, instalacja została zakończona.</span><span class="sxs-lookup"><span data-stu-id="a1e22-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="a1e22-119">**Kody zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="a1e22-119">**Exit codes**.</span></span> <span data-ttu-id="a1e22-120">Następujące kody zakończenia z polecenia do wywołania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] program do dystrybucji wskazuje, czy Instalator ma zakończonych powodzeniem lub niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="a1e22-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="a1e22-121">0 — instalacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1e22-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="a1e22-122">3010 — instalacja została ukończona pomyślnie; wymagane jest ponowne uruchomienie systemu.</span><span class="sxs-lookup"><span data-stu-id="a1e22-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="a1e22-123">1602 — Instalatora zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="a1e22-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="a1e22-124">Wszystkie pozostałe kody — Instalator napotkał błędy; Sprawdź pliki dziennika utworzone w % temp %, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="a1e22-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="a1e22-125">**Trwa anulowanie instalacji**.</span><span class="sxs-lookup"><span data-stu-id="a1e22-125">**Canceling setup**.</span></span> <span data-ttu-id="a1e22-126">Ustawienia można anulować w dowolnym momencie za pomocą `Abort` metodę, aby ustawić `m_downloadAbort` i `m_ installAbort` flagi w sekcji Rozwiązanie MMIO.</span><span class="sxs-lookup"><span data-stu-id="a1e22-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="a1e22-127">Przykładowe chainer</span><span class="sxs-lookup"><span data-stu-id="a1e22-127">Chainer Sample</span></span>  
 <span data-ttu-id="a1e22-128">Przykładowe Chainer dyskretnie uruchamia i śledzi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora podczas wyświetlania postępu.</span><span class="sxs-lookup"><span data-stu-id="a1e22-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="a1e22-129">Ten przykład jest podobny do przykładu Chainer dostępnego dla programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a1e22-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="a1e22-130">Jednak dodatkowo go można uniknąć ponownych uruchomień systemu przez przetwarzanie okno komunikatu do zamykania aplikacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a1e22-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="a1e22-131">Aby dowiedzieć się, to okno komunikatu, zobacz [zmniejszenie uruchamia ponownie podczas .NET Framework 4.5 instalacji systemów](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="a1e22-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="a1e22-132">Możesz użyć tego przykładu z Instalatorem .NET Framework 4; w tym scenariuszu komunikat po prostu nie są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="a1e22-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a1e22-133">Należy uruchomić przykład jako administrator.</span><span class="sxs-lookup"><span data-stu-id="a1e22-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="a1e22-134">Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [przykład Chainer programu .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkId=231345) z galerii przykładów MSDN.</span><span class="sxs-lookup"><span data-stu-id="a1e22-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="a1e22-135">W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h ChainingdotNet4.cpp i IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="a1e22-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="a1e22-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="a1e22-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="a1e22-137">Plik MMIOChainer.h (zobacz [uzupełnianie kodu](https://go.microsoft.com/fwlink/?LinkId=231369)) zawiera definicję struktury danych i klasa bazowa, z której powinna pochodzić klasy chainer.</span><span class="sxs-lookup"><span data-stu-id="a1e22-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="a1e22-138">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozszerza rozwiązanie MMIO struktury danych do obsługi danych, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatorowi.</span><span class="sxs-lookup"><span data-stu-id="a1e22-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="a1e22-139">Zmian w strukturze rozwiązanie MMIO są zgodne wstecz, aby chainer .NET Framework 4 można pracować z Instalatora .NET Framework 4.5, bez konieczności ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="a1e22-140">Jednak ten scenariusz nie obsługuje tę funkcję w celi zmniejszenia ponownego uruchomienia systemu.</span><span class="sxs-lookup"><span data-stu-id="a1e22-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="a1e22-141">Pole wersji zapewnia sposób identyfikacji poprawki do formatu struktury i komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a1e22-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="a1e22-142">Instalator .NET Framework Określa wersję interfejsu chainer przez wywołanie metody `VirtualQuery` funkcję, aby określić rozmiar mapowania pliku.</span><span class="sxs-lookup"><span data-stu-id="a1e22-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="a1e22-143">Jeśli rozmiar jest wystarczająco duża, aby uwzględnić pole wersji, Instalatora .NET Framework używa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="a1e22-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="a1e22-144">W przypadku mapowania pliku jest zbyt mała, aby zawierać pole wersji, która jest w przypadku programu .NET Framework 4, proces instalacji zakłada wersja 0 (4).</span><span class="sxs-lookup"><span data-stu-id="a1e22-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="a1e22-145">W przypadku chainer nie obsługuje wersji komunikat, który chce wysłać Instalatora .NET Framework, .NET Framework setup zakłada odpowiedź Ignoruj.</span><span class="sxs-lookup"><span data-stu-id="a1e22-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="a1e22-146">Rozwiązanie MMIO struktura danych zostaje zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a1e22-146">The MMIO data structure is defined as follows:</span></span>  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
    ```  
  
-   <span data-ttu-id="a1e22-147">`MmioDataStructure` Strukturę danych nie powinny być używane bezpośrednio; użyj `MmioChainer` zamiast klasy do zaimplementowania swoje chainer.</span><span class="sxs-lookup"><span data-stu-id="a1e22-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="a1e22-148">Pochodzi od `MmioChainer` klasa do tworzenia łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="a1e22-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="a1e22-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="a1e22-150">Plik IProgressObserver.h implementuje obserwatora postępu ([Zobacz kompletny kod](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="a1e22-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="a1e22-151">Obserwator pobiera powiadomienia o postępu pobierania i instalacji (określony jako typ unsigned `char`, 0-255, wskazującą, 1 – 100% ukończone).</span><span class="sxs-lookup"><span data-stu-id="a1e22-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="a1e22-152">Obserwator jest również otrzymywać chainee wysyła komunikat, gdy obserwatora ma wysyłać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a1e22-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="a1e22-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="a1e22-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="a1e22-154">[ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) pliku implementuje `Server` klasy, która jest pochodną `MmioChainer` klasy i zastępuje odpowiedniej metody, aby wyświetlić informacje o postępie.</span><span class="sxs-lookup"><span data-stu-id="a1e22-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="a1e22-155">MmioChainer tworzy sekcję o nazwie określonej sekcji i inicjuje chainer o nazwie określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a1e22-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="a1e22-156">Nazwa zdarzenia są zapisywane w strukturze zmapowanych danych.</span><span class="sxs-lookup"><span data-stu-id="a1e22-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="a1e22-157">Nazwy sekcji i zdarzeń należy upewnić się unikatowy.</span><span class="sxs-lookup"><span data-stu-id="a1e22-157">You should make the section and event names unique.</span></span> <span data-ttu-id="a1e22-158">`Server` Klasy poniższy kod uruchamia program instalacyjny określonego monitoruje postęp i zwraca kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="a1e22-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="a1e22-159">Instalacja jest uruchomiona w metody Main.</span><span class="sxs-lookup"><span data-stu-id="a1e22-159">The installation is started in the Main method.</span></span>  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
    ```  
  
-   <span data-ttu-id="a1e22-160">Przed uruchomieniem instalacji, chainer sprawdza, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jest już zainstalowany przez wywołanie metody `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="a1e22-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
    ```  
  
-   <span data-ttu-id="a1e22-161">Ścieżka pliku wykonywalnego (Setup.exe w przykładzie) można zmienić w `Launch` metoda wskaż jego prawidłową lokalizację lub dostosować program code w celu określenia lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="a1e22-162">`MmioChainer` Udostępnia klasę bazową, blokuje `Run()` metodę, która wywołuje klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="a1e22-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
    ```cpp  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
    ```  
  
-   <span data-ttu-id="a1e22-163">`Send` Metoda przechwytuje i przetwarza komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a1e22-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="a1e22-164">W tej wersji programu .NET Framework, tylko obsługiwane komunikat jest zamykanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
    ```  
  
-   <span data-ttu-id="a1e22-165">Postęp danych jest niepodpisany `char` od 0 (0%) do 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="a1e22-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="a1e22-166">HRESULT jest przekazywany do `Finished` metody.</span><span class="sxs-lookup"><span data-stu-id="a1e22-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a1e22-167">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Pakiet redystrybucyjny zwykle zapisuje komunikaty o postępie wielu i jednego komunikat, który wskazuje ukończenie (po stronie chainer).</span><span class="sxs-lookup"><span data-stu-id="a1e22-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="a1e22-168">Odczytuje również asynchronicznie, wyszukiwanie `Abort` rekordów.</span><span class="sxs-lookup"><span data-stu-id="a1e22-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="a1e22-169">Jeśli odbierze `Abort` rekordu, go anuluje instalację i zapisuje Zakończono rekord z E_ABORT jako jego dane po instalacji zostało przerwane i operacje instalacji ma została wycofana.</span><span class="sxs-lookup"><span data-stu-id="a1e22-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="a1e22-170">Typowy serwer tworzy losowe rozwiązanie MMIO nazwę pliku, tworzy plik (jak pokazano w poprzednim przykładzie kodu na `Server::CreateSection`) i uruchamia pakiet redystrybucyjny programu za pomocą `CreateProcess` nazw przy użyciu metody i przekazywania potoku `-pipe someFileSectionName` opcji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="a1e22-171">Serwer powinien implementować `OnProgress`, `Send`, i `Finished` metody z kodu specyficznego dla interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1e22-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e22-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1e22-172">See Also</span></span>  
 [<span data-ttu-id="a1e22-173">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="a1e22-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="a1e22-174">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="a1e22-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
