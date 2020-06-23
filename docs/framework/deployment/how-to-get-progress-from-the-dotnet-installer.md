---
title: 'Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5'
description: Dowiedz się, jak uzyskać postęp z Instalatora programu .NET 4,5. Jeśli tworzysz aplikacje dla tej wersji platformy .NET, możesz dołączyć Instalatora programu .NET 4,5 (łańcucha) do konfiguracji aplikacji.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 501fcaa7636d586ddfff8606768d4639fdc010d7
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904263"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="de853-104">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="de853-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="de853-105">.NET Framework 4,5 to środowisko uruchomieniowe redystrybucyjne.</span><span class="sxs-lookup"><span data-stu-id="de853-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="de853-106">W przypadku tworzenia aplikacji dla tej wersji .NET Framework można uwzględnić konfigurację (łańcuch) .NET Framework 4,5 jako część wymagań wstępnych konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de853-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="de853-107">Aby zaprezentować dostosowane lub ujednolicone środowisko konfiguracji, możesz chcieć dyskretnie uruchomić Instalatora .NET Framework 4,5 i śledzić jego postęp, pokazując postęp instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de853-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="de853-108">Aby włączyć śledzenie dyskretne, .NET Framework konfigurację 4,5 (którą można obejrzeć) definiuje protokół, używając segmentu we/wy mapowanego na pamięć (MMIO) w celu komunikacji z konfiguracją (obserwatorem lub łańcuchem).</span><span class="sxs-lookup"><span data-stu-id="de853-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="de853-109">Ten protokół definiuje sposób uzyskiwania przez moduł łańcucha informacji o postępie, uzyskiwanie szczegółowych wyników, reagowanie na komunikaty i anulowanie konfiguracji .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="de853-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="de853-110">**Wywołanie**.</span><span class="sxs-lookup"><span data-stu-id="de853-110">**Invocation**.</span></span> <span data-ttu-id="de853-111">Aby wywołać konfigurację .NET Framework 4,5 i uzyskać informacje o postępie z sekcji MMIO, program instalacyjny musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="de853-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="de853-112">Wywołaj program redystrybucyjny .NET Framework 4,5:</span><span class="sxs-lookup"><span data-stu-id="de853-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="de853-113">*Nazwa sekcji* , która ma być używana do identyfikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de853-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="de853-114">.NET Framework Instalator odczytuje i zapisuje dane w sekcji MMIO asynchronicznie, dzięki czemu może być przydatne użycie zdarzeń i komunikatów w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="de853-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="de853-115">W przykładzie proces instalacji .NET Framework jest tworzony przez konstruktora, który alokuje sekcję MMIO ( `TheSectionName` ) i definiuje zdarzenie ( `TheEventName` ):</span><span class="sxs-lookup"><span data-stu-id="de853-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="de853-116">Zastąp te nazwy nazwami unikatowymi dla programu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="de853-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="de853-117">Zapoznaj się z sekcją MMIO.</span><span class="sxs-lookup"><span data-stu-id="de853-117">Read from the MMIO section.</span></span> <span data-ttu-id="de853-118">W .NET Framework 4,5 operacje pobierania i instalacji są jednoczesne: jedna część .NET Framework może być instalowana podczas pobierania innej części.</span><span class="sxs-lookup"><span data-stu-id="de853-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="de853-119">W związku z tym postęp jest wysyłany z powrotem (czyli zapisany) do sekcji MMIO jako dwie liczby ( `m_downloadSoFar` i `m_installSoFar` ), które zwiększają się od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="de853-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="de853-120">Po zapisaniu 255 i zakończeniu .NET Framework instalacja zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="de853-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="de853-121">**Kody zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="de853-121">**Exit codes**.</span></span> <span data-ttu-id="de853-122">Następujące kody zakończenia z polecenia do wywołania programu redystrybucyjnego .NET Framework 4,5 wskazują, czy instalacja zakończyła się powodzeniem, czy niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="de853-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="de853-123">0 — Instalacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="de853-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="de853-124">3010 — instalacja została ukończona pomyślnie; wymagane jest ponowne uruchomienie systemu.</span><span class="sxs-lookup"><span data-stu-id="de853-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="de853-125">1602 — konfiguracja została anulowana.</span><span class="sxs-lookup"><span data-stu-id="de853-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="de853-126">Wszystkie inne kody — Instalator napotkał błędy; Aby uzyskać szczegółowe informacje, Przejrzyj pliki dziennika utworzone w% temp%.</span><span class="sxs-lookup"><span data-stu-id="de853-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="de853-127">**Anulowanie instalacji**.</span><span class="sxs-lookup"><span data-stu-id="de853-127">**Canceling setup**.</span></span> <span data-ttu-id="de853-128">Instalację można anulować w dowolnym momencie przy użyciu metody, `Abort` Aby ustawić `m_downloadAbort` `m_ installAbort` flagi i w sekcji MMIO.</span><span class="sxs-lookup"><span data-stu-id="de853-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="de853-129">Przykład łańcucha</span><span class="sxs-lookup"><span data-stu-id="de853-129">Chainer Sample</span></span>

<span data-ttu-id="de853-130">Przykładowy moduł łańcucha uruchamia dyskretnie i śledzi konfigurację .NET Framework 4,5 podczas wyświetlania postępu.</span><span class="sxs-lookup"><span data-stu-id="de853-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="de853-131">Ten przykład jest podobny do przykładu łańcucha dostarczonego dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="de853-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="de853-132">Ponadto może to uniemożliwić ponowne uruchomienie systemu przez przetworzenie okna komunikatu do zamykania aplikacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="de853-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="de853-133">Aby uzyskać informacje na temat tego okna komunikatu, zobacz [ograniczanie ponownych uruchomień systemu podczas instalacji .NET Framework 4,5](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="de853-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="de853-134">Tego przykładu można użyć w Instalatorze programu .NET Framework 4. w tym scenariuszu wiadomość jest po prostu niewysłana.</span><span class="sxs-lookup"><span data-stu-id="de853-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="de853-135">Należy uruchomić przykład jako administrator.</span><span class="sxs-lookup"><span data-stu-id="de853-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="de853-136">Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [przykładu łańcucha .NET Framework 4,5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) z galerii przykładów MSDN.</span><span class="sxs-lookup"><span data-stu-id="de853-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="de853-137">W poniższych sekcjach opisano znaczące pliki w tym przykładzie: MMIOChainer. h, ChainingdotNet4. cpp i IProgressObserver. h.</span><span class="sxs-lookup"><span data-stu-id="de853-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="de853-138">MMIOChainer. h</span><span class="sxs-lookup"><span data-stu-id="de853-138">MMIOChainer.h</span></span>

- <span data-ttu-id="de853-139">Plik MMIOChainer. h (zobacz [kompletny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) zawiera definicję struktury danych i klasę bazową, z której Klasa łańcucha powinna być pochodna.</span><span class="sxs-lookup"><span data-stu-id="de853-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="de853-140">.NET Framework 4,5 rozszerza strukturę danych MMIO w celu obsługi danych wymaganych przez Instalatora .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="de853-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="de853-141">Zmiany struktury MMIO są zgodne z poprzednimi wersjami, dzięki czemu moduł .NET Framework 4 może współpracował z instalacją .NET Framework 4,5, bez konieczności ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="de853-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="de853-142">Jednak ten scenariusz nie obsługuje funkcji ograniczania ponownych uruchomień systemu.</span><span class="sxs-lookup"><span data-stu-id="de853-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="de853-143">Pole Version zawiera metodę identyfikowania poprawek w formacie struktury i komunikatu.</span><span class="sxs-lookup"><span data-stu-id="de853-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="de853-144">Konfiguracja .NET Framework określa wersję interfejsu łańcucha, wywołując `VirtualQuery` funkcję w celu określenia rozmiaru mapowania pliku.</span><span class="sxs-lookup"><span data-stu-id="de853-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="de853-145">Jeśli rozmiar jest wystarczająco duży, aby zmieścił się w polu wersja, .NET Framework Instalator używa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="de853-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="de853-146">Jeśli mapowanie pliku jest za małe, aby zawierało pole wersji, czyli w przypadku .NET Framework 4, proces instalacji przyjmuje wersję 0 (4).</span><span class="sxs-lookup"><span data-stu-id="de853-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="de853-147">Jeśli moduł łańcucha nie obsługuje wersji komunikatu, która .NET Framework instalator chce wysłać, .NET Framework instalator zabierze odpowiedź na ignorowanie.</span><span class="sxs-lookup"><span data-stu-id="de853-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="de853-148">Struktura danych MMIO jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="de853-148">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="de853-149">`MmioDataStructure`Struktury danych nie należy używać bezpośrednio. `MmioChainer` zamiast tego użyj klasy do zaimplementowania łańcucha.</span><span class="sxs-lookup"><span data-stu-id="de853-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="de853-150">Pochodne od `MmioChainer` klasy do łańcucha redystrybucyjnego .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="de853-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="de853-151">IProgressObserver. h</span><span class="sxs-lookup"><span data-stu-id="de853-151">IProgressObserver.h</span></span>

- <span data-ttu-id="de853-152">Plik IProgressObserver. h implementuje obserwatora postępu ([Zobacz kompletny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span><span class="sxs-lookup"><span data-stu-id="de853-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="de853-153">Ten obserwator otrzymuje powiadomienie o postępie pobierania i instalacji (określony jako niepodpisany `char` , 0-255, wskazujący na ukończenie 1%-100%).</span><span class="sxs-lookup"><span data-stu-id="de853-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="de853-154">Obserwator zostanie również powiadomiony, gdy chainee wysyła komunikat, a obserwator powinien wysłać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="de853-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="de853-155">ChainingdotNet 4.5. cpp</span><span class="sxs-lookup"><span data-stu-id="de853-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="de853-156">Plik [chainingdotnet 4.5. cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) implementuje `Server` klasę, która dziedziczy z `MmioChainer` klasy i zastępuje odpowiednie metody wyświetlania informacji o postępie.</span><span class="sxs-lookup"><span data-stu-id="de853-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="de853-157">MmioChainer tworzy sekcję z określoną nazwą sekcji i inicjuje łańcuch z określoną nazwą zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="de853-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="de853-158">Nazwa zdarzenia jest zapisywana w mapowanej strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="de853-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="de853-159">Należy zmienić nazwy sekcji i zdarzeń na unikatowe.</span><span class="sxs-lookup"><span data-stu-id="de853-159">You should make the section and event names unique.</span></span> <span data-ttu-id="de853-160">`Server`Klasa w poniższym kodzie uruchamia określony program instalacyjny, monitoruje postęp i zwraca kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="de853-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="de853-161">Instalacja została uruchomiona w metodzie Main.</span><span class="sxs-lookup"><span data-stu-id="de853-161">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="de853-162">Przed uruchomieniem instalacji program łańcucha sprawdza, czy .NET Framework 4,5 jest już zainstalowany przez wywołanie `IsNetFx4Present` :</span><span class="sxs-lookup"><span data-stu-id="de853-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="de853-163">Można zmienić ścieżkę pliku wykonywalnego (Setup.exe w przykładzie) w `Launch` metodzie, aby wskazywała jego poprawną lokalizację, lub dostosować kod w celu określenia lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="de853-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="de853-164">`MmioChainer`Klasa bazowa zapewnia metodę blokującą `Run()` , która wywołuje klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="de853-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="de853-165">`Send`Metoda przechwytuje i przetwarza komunikaty.</span><span class="sxs-lookup"><span data-stu-id="de853-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="de853-166">W tej wersji .NET Framework jedynym obsługiwanym komunikatem jest komunikat zamknięcia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de853-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
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

- <span data-ttu-id="de853-167">Dane postępu są niepodpisane `char` między 0 (0%) i 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="de853-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="de853-168">WYNIK HRESULT jest przesyłany do `Finished` metody.</span><span class="sxs-lookup"><span data-stu-id="de853-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="de853-169">Pakiet redystrybucyjny .NET Framework 4,5 zazwyczaj zapisuje wiele komunikatów o postępie i pojedynczy komunikat wskazujący na zakończenie (po stronie łańcucha).</span><span class="sxs-lookup"><span data-stu-id="de853-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="de853-170">Odczytuje również asynchronicznie, szukając `Abort` rekordów.</span><span class="sxs-lookup"><span data-stu-id="de853-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="de853-171">Jeśli odbierze `Abort` rekord, anuluje instalację i zapisuje zakończony rekord z E_ABORT jako dane po przerwaniu instalacji i wycofaniu operacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="de853-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="de853-172">Typowy serwer tworzy losową nazwę pliku MMIO, tworzy plik (jak pokazano w poprzednim przykładzie kodu, w `Server::CreateSection` ) i uruchamia pakiet redystrybucyjny przy użyciu `CreateProcess` metody i przekazując nazwę potoku przy użyciu `-pipe someFileSectionName` opcji.</span><span class="sxs-lookup"><span data-stu-id="de853-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="de853-173">Serwer powinien implementować `OnProgress` `Send` metody,, i `Finished` z kodem SPECYFICZNYM dla interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de853-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="de853-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de853-174">See also</span></span>

- [<span data-ttu-id="de853-175">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="de853-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="de853-176">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="de853-176">Deployment</span></span>](index.md)
