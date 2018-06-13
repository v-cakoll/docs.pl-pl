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
ms.openlocfilehash: 84bd96f27e8276546bef0dd9994163ccd843ac20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393312"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="288bb-102">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="288bb-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="288bb-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest pakiet redystrybucyjny środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="288bb-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="288bb-104">W przypadku tworzenia aplikacji dla tej wersji programu .NET Framework, można dołączyć (łańcucha) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator w ramach wymagań wstępnych instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="288bb-105">Do prezentowania dostosowane lub ujednoliconego konfiguracji systemu, można uruchomić w trybie dyskretnym [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i śledzić postęp podczas pokazywania postępu instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="288bb-106">Aby włączyć śledzenie dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora (mogą być obserwowane) definiuje protokół za pomocą mapowanych na pamięć segment rozwiązanie we/wy (MMIO) do komunikacji z ustawień (obserwatora lub moduł łańcucha).</span><span class="sxs-lookup"><span data-stu-id="288bb-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="288bb-107">Protokół ten definiuje sposób moduł łańcucha uzyskać informacje o postępie, uzyskiwać szczegółowe wyniki, odpowiada na komunikaty i anulować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora.</span><span class="sxs-lookup"><span data-stu-id="288bb-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="288bb-108">**Wywołanie** .</span><span class="sxs-lookup"><span data-stu-id="288bb-108">**Invocation** .</span></span>  <span data-ttu-id="288bb-109">Aby wywołać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora i odbierać informacje o postępie z sekcji Rozwiązanie MMIO, program Instalator musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="288bb-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="288bb-110">Wywołanie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]pakietu redystrybucyjnego programu:</span><span class="sxs-lookup"><span data-stu-id="288bb-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="288bb-111">gdzie *nazwę sekcji* jest dowolną nazwę, które ma być używany do identyfikowania Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="288bb-112">Instalator .NET framework odczytuje i zapisuje w sekcji Rozwiązanie MMIO asynchronicznie, dlatego może być bardzo łatwe w użyciu zdarzeń i komunikatów w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="288bb-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="288bb-113">W tym przykładzie proces Instalator .NET Framework został utworzony przez konstruktora że oba przydziela sekcji Rozwiązanie MMIO (`TheSectionName`) i definiuje zdarzenia (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="288bb-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="288bb-114">Zamień tych nazw z nazwami, które są unikatowe dla programu Instalatora.</span><span class="sxs-lookup"><span data-stu-id="288bb-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="288bb-115">Przeczytaj rozwiązanie MMIO sekcji.</span><span class="sxs-lookup"><span data-stu-id="288bb-115">Read from the MMIO section.</span></span> <span data-ttu-id="288bb-116">W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], są jednoczesnych operacji pobierania i instalacji: jedną część programu .NET Framework może być instalowany podczas pobierania innej części.</span><span class="sxs-lookup"><span data-stu-id="288bb-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="288bb-117">W związku z tym postępu są wysyłane z powrotem (który zapisany) w sekcji Rozwiązanie MMIO jako dwóch liczb (`m_downloadSoFar` i `m_installSoFar`) który zwiększyć z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="288bb-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="288bb-118">Gdy 255 są zapisywane i zamyka .NET Framework, instalacja jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="288bb-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="288bb-119">**Kody zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="288bb-119">**Exit codes**.</span></span> <span data-ttu-id="288bb-120">Następujące kody zakończenia z polecenia do wywołania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakietu redystrybucyjnego programu wskazują, czy Instalator zakończyło się pomyślnie lub nie powiodło się:</span><span class="sxs-lookup"><span data-stu-id="288bb-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="288bb-121">0 — instalacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="288bb-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="288bb-122">3010 — instalacja zakończyła się pomyślnie; wymagane jest ponowne uruchomienie systemu.</span><span class="sxs-lookup"><span data-stu-id="288bb-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="288bb-123">1602 — Instalator zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="288bb-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="288bb-124">Wszystkie pozostałe kody — Instalator napotkał błędy; Przejrzyj pliki dziennika utworzone w % temp %, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="288bb-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="288bb-125">**Anulowanie instalacji**.</span><span class="sxs-lookup"><span data-stu-id="288bb-125">**Canceling setup**.</span></span> <span data-ttu-id="288bb-126">W dowolnej chwili można anulować instalacji przy użyciu `Abort` metodę, aby ustawić `m_downloadAbort` i `m_ installAbort` flagi w sekcji Rozwiązanie MMIO.</span><span class="sxs-lookup"><span data-stu-id="288bb-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="288bb-127">Przykładowy moduł łańcucha</span><span class="sxs-lookup"><span data-stu-id="288bb-127">Chainer Sample</span></span>  
 <span data-ttu-id="288bb-128">Przykładowy moduł łańcucha dyskretnie uruchamia i śledzi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora podczas pokazywania postępu.</span><span class="sxs-lookup"><span data-stu-id="288bb-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="288bb-129">Ten przykład jest podobny do przykładu moduł łańcucha dostępnego dla programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="288bb-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="288bb-130">Jednak Ponadto go uniknąć ponownego uruchomienia systemu przez przetwarzanie komunikat zamknięcia aplikacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="288bb-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="288bb-131">Informacje dla tego pola wiadomości, zobacz [zmniejszenie uruchamia ponownie podczas .NET Framework 4.5 instalacji systemów](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="288bb-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="288bb-132">Można użyć tego przykładu z Instalatora .NET Framework 4; w tym scenariuszu komunikat po prostu nie są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="288bb-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="288bb-133">Przykład musi działać jako administrator.</span><span class="sxs-lookup"><span data-stu-id="288bb-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="288bb-134">Możesz pobrać kompletne rozwiązanie Visual Studio dla [.NET Framework 4.5 moduł łańcucha próbki](http://go.microsoft.com/fwlink/?LinkId=231345) z galerii przykładów MSDN.</span><span class="sxs-lookup"><span data-stu-id="288bb-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](http://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="288bb-135">W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h, ChainingdotNet4.cpp i IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="288bb-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="288bb-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="288bb-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="288bb-137">Plik MMIOChainer.h (zobacz [uzupełnianie kodu](http://go.microsoft.com/fwlink/?LinkId=231369)) zawiera definicji danych struktury i klasy podstawowej, z którego powinien pochodzić klasy moduł łańcucha.</span><span class="sxs-lookup"><span data-stu-id="288bb-137">The MMIOChainer.h file (see [complete code](http://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="288bb-138">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozszerza rozwiązanie MMIO struktury danych do obsługi danych który [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatorowi.</span><span class="sxs-lookup"><span data-stu-id="288bb-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="288bb-139">Zmiany w strukturze rozwiązanie MMIO są zapewniającej, dzięki użyciu modułu łańcucha .NET Framework 4 można pracować z Instalatora .NET Framework 4.5 bez konieczności ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="288bb-140">Jednak ten scenariusz nie obsługuje funkcji zmniejszenia ponownego uruchomienia systemu.</span><span class="sxs-lookup"><span data-stu-id="288bb-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="288bb-141">Pole wersji udostępnia sposób identyfikacji zmian w formacie struktury i komunikatu.</span><span class="sxs-lookup"><span data-stu-id="288bb-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="288bb-142">Instalator .NET Framework Określa wersję interfejsu moduł łańcucha wywołując `VirtualQuery` funkcji do określenia rozmiaru mapowania pliku.</span><span class="sxs-lookup"><span data-stu-id="288bb-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="288bb-143">Jeśli rozmiar jest wystarczająco duży, aby zmieścił się w polu wersji, Instalator .NET Framework używa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="288bb-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="288bb-144">Jeśli mapowanie pliku jest zbyt mały, aby pomieścił pole wersji, która jest w przypadku programu .NET Framework 4, proces instalacji zakłada wersji 0 (4).</span><span class="sxs-lookup"><span data-stu-id="288bb-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="288bb-145">Jeśli moduł łańcucha nie obsługuje wersji komunikat, który chce wysłać Instalator .NET Framework, Instalator .NET Framework zakłada Ignoruj odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="288bb-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="288bb-146">Struktura danych rozwiązanie MMIO jest zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="288bb-146">The MMIO data structure is defined as follows:</span></span>  
  
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
  
-   <span data-ttu-id="288bb-147">`MmioDataStructure` Struktury danych nie powinna być używana bezpośrednio; użyj `MmioChainer` zamiast klasy do zaimplementowania programu moduł łańcucha.</span><span class="sxs-lookup"><span data-stu-id="288bb-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="288bb-148">Pochodzić od `MmioChainer` klasy łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="288bb-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="288bb-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="288bb-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="288bb-150">Plik IProgressObserver.h implementuje obserwatora postępu ([, zobacz pełny kod](http://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="288bb-150">The IProgressObserver.h file implements a progress observer ([see complete code](http://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="288bb-151">Obserwator pobiera powiadomienie postępu pobierania i instalacji (określony jako niepodpisany `char`, 0 – 255, wskazującą 1 100% pełną).</span><span class="sxs-lookup"><span data-stu-id="288bb-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="288bb-152">Obserwator jest również powiadomienie, gdy chainee wysyła komunikat i obserwatora należy wysłać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="288bb-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="288bb-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="288bb-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="288bb-154">[ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) pliku implementuje `Server` klasy, która jest pochodną `MmioChainer` klasy i zastępuje odpowiedniej metody, aby wyświetlić informacje o postępie.</span><span class="sxs-lookup"><span data-stu-id="288bb-154">The [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="288bb-155">MmioChainer tworzy sekcję o nazwie określonej sekcji i inicjuje moduł łańcucha o nazwie określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="288bb-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="288bb-156">Nazwa zdarzenia są zapisywane w strukturze zmapowanych danych.</span><span class="sxs-lookup"><span data-stu-id="288bb-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="288bb-157">Nazwy sekcji i zdarzenia powinien zapewnić unikatowy.</span><span class="sxs-lookup"><span data-stu-id="288bb-157">You should make the section and event names unique.</span></span> <span data-ttu-id="288bb-158">`Server` Klasy w poniższym kodzie uruchamia określony Instalatora, monitoruje postęp i zwraca kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="288bb-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="288bb-159">Instalacja jest uruchomiona w metody Main.</span><span class="sxs-lookup"><span data-stu-id="288bb-159">The installation is started in the Main method.</span></span>  
  
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
  
-   <span data-ttu-id="288bb-160">Przed uruchomieniem instalacji, moduł łańcucha sprawdza, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jest już zainstalowana przez wywołanie metody `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="288bb-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
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
  
-   <span data-ttu-id="288bb-161">Można zmienić ścieżkę do pliku wykonywalnego (Setup.exe w przykładzie) w `Launch` metodę, aby wskazać jej poprawnej lokalizacji lub Dostosuj kod, aby określić lokalizację.</span><span class="sxs-lookup"><span data-stu-id="288bb-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="288bb-162">`MmioChainer` Udostępnia klasę podstawową blokujący `Run()` metodę, która wywołuje klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="288bb-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
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
  
-   <span data-ttu-id="288bb-163">`Send` Metody przechwytuje i przetwarza wiadomości.</span><span class="sxs-lookup"><span data-stu-id="288bb-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="288bb-164">W tej wersji programu .NET Framework tylko komunikatów obsługiwanych jest komunikat zamknięcia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
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
  
-   <span data-ttu-id="288bb-165">Postęp danych jest niepodpisany `char` od 0 (0%) do 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="288bb-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="288bb-166">HRESULT jest przekazywana do `Finished` metody.</span><span class="sxs-lookup"><span data-stu-id="288bb-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="288bb-167">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Pakietu redystrybucyjnego zwykle zapisuje komunikaty o postępie wielu i jednego komunikatu informującego zakończenia (po stronie moduł łańcucha).</span><span class="sxs-lookup"><span data-stu-id="288bb-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="288bb-168">Odczytuje również asynchronicznie, wyszukiwanie `Abort` rekordów.</span><span class="sxs-lookup"><span data-stu-id="288bb-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="288bb-169">Po otrzymaniu `Abort` rekordów, jego anuluje instalację i zapisuje Zakończono rekord z E_ABORT jako jego danych po instalacji zostało przerwane i operacje instalacji mają została wycofana.</span><span class="sxs-lookup"><span data-stu-id="288bb-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="288bb-170">Typowy serwer tworzy losowe rozwiązanie MMIO nazwę pliku, tworzy plik (jak pokazano w poprzednim przykładzie kodu `Server::CreateSection`) i uruchamia pakiet redystrybucyjny programu przy użyciu `CreateProcess` — metoda i przekazywanie potoku nazw z `-pipe someFileSectionName` opcji.</span><span class="sxs-lookup"><span data-stu-id="288bb-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="288bb-171">Serwer powinien implementować `OnProgress`, `Send`, i `Finished` metody z kodu specyficzne dla interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="288bb-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="288bb-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="288bb-172">See Also</span></span>  
 [<span data-ttu-id="288bb-173">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="288bb-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="288bb-174">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="288bb-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
