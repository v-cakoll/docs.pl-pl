---
title: 'Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: cd81ad83aee80341d0334cfa8caa165b25ee0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716489"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="f1281-102">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f1281-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="f1281-103">.NET Framework 4.5 jest redystrybucyjnym czasem wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f1281-103">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="f1281-104">Jeśli programujesz aplikacje dla tej wersji programu .NET Framework, możesz dołączyć (łańcuch) .NET Framework 4.5 konfiguracji jako część wstępną konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-104">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="f1281-105">Aby zaprezentować niestandardowe lub ujednolicone środowisko konfiguracji, można po cichu uruchomić konfigurację programu .NET Framework 4.5 i śledzić jej postęp, pokazując jednocześnie postęp konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-105">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="f1281-106">Aby włączyć ciche śledzenie, instalator programu .NET Framework 4.5 (który można obserwować) definiuje protokół przy użyciu segmentu MMIO (MMIO) mapowanej pamięcią do komunikowania się z konfiguracją (obserwatorem lub łańcuchem).</span><span class="sxs-lookup"><span data-stu-id="f1281-106">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="f1281-107">Ten protokół definiuje sposób, w jaki chainer może uzyskać informacje o postępie, uzyskać szczegółowe wyniki, odpowiedzieć na wiadomości i anulować konfigurację programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f1281-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="f1281-108">**Wywołanie**.</span><span class="sxs-lookup"><span data-stu-id="f1281-108">**Invocation**.</span></span> <span data-ttu-id="f1281-109">Aby wywołać konfigurację programu .NET Framework 4.5 i otrzymywać informacje o postępie z sekcji MMIO, program instalacyjny musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f1281-109">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="f1281-110">Wywołanie programu redystrybucyjnego .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="f1281-110">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="f1281-111">Gdzie *nazwa sekcji* to dowolna nazwa, której chcesz użyć do zidentyfikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-111">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="f1281-112">Instalator programu .NET Framework odczytuje i zapisuje w sekcji MMIO asynchronicznie, więc może okazać się wygodne użycie zdarzeń i wiadomości w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="f1281-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="f1281-113">W tym przykładzie proces konfiguracji programu .NET Framework jest tworzony przez konstruktora, który przydziela sekcję MMIO (`TheSectionName`) i definiuje zdarzenie (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="f1281-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="f1281-114">Należy zastąpić te nazwy nazwami, które są unikatowe dla programu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f1281-114">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="f1281-115">Przeczytaj z sekcji MMIO.</span><span class="sxs-lookup"><span data-stu-id="f1281-115">Read from the MMIO section.</span></span> <span data-ttu-id="f1281-116">W programie .NET Framework 4.5 operacje pobierania i instalacji są jednoczesne: jedna część programu .NET Framework może być instalowana podczas pobierania innej części.</span><span class="sxs-lookup"><span data-stu-id="f1281-116">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="f1281-117">W rezultacie postęp jest odsyłany (czyli zapisywany) do sekcji`m_downloadSoFar` MMIO jako dwie liczby ( i `m_installSoFar`), które zwiększają się z 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="f1281-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="f1281-118">Po zapisaniu 255 i zakończy się działanie programu .NET Framework, instalacja została zakończona.</span><span class="sxs-lookup"><span data-stu-id="f1281-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="f1281-119">**Kody zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="f1281-119">**Exit codes**.</span></span> <span data-ttu-id="f1281-120">Następujące kody zakończenia z polecenia do wywołania programu redystrybucyjnego .NET Framework 4.5 wskazują, czy instalacja powiodła się, czy nie:</span><span class="sxs-lookup"><span data-stu-id="f1281-120">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="f1281-121">0 - Instalacja została pomyślnie zakończona.</span><span class="sxs-lookup"><span data-stu-id="f1281-121">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="f1281-122">3010 – Instalacja została pomyślnie zakończona; wymagane jest ponowne uruchomienie systemu.</span><span class="sxs-lookup"><span data-stu-id="f1281-122">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="f1281-123">1602 – Instalator został anulowany.</span><span class="sxs-lookup"><span data-stu-id="f1281-123">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="f1281-124">Wszystkie inne kody - Instalator napotkał błędy; sprawdź szczegóły plików dziennika utworzonych w %temp%.</span><span class="sxs-lookup"><span data-stu-id="f1281-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="f1281-125">**Anulowanie konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="f1281-125">**Canceling setup**.</span></span> <span data-ttu-id="f1281-126">Konfigurację można anulować w `Abort` dowolnym momencie, używając metody do ustawiania `m_downloadAbort` i `m_ installAbort` flag w sekcji MMIO.</span><span class="sxs-lookup"><span data-stu-id="f1281-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="f1281-127">Próbka łańcucha</span><span class="sxs-lookup"><span data-stu-id="f1281-127">Chainer Sample</span></span>

<span data-ttu-id="f1281-128">Próbka Chainer dyskretnie uruchamia i śledzi konfigurację programu .NET Framework 4.5, pokazując jednocześnie postęp.</span><span class="sxs-lookup"><span data-stu-id="f1281-128">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="f1281-129">Ten przykład jest podobny do próbki Chainer przewidziane dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f1281-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="f1281-130">Jednak ponadto można uniknąć ponownego uruchomienia systemu, przetwarzając okno komunikatu do zamykania aplikacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f1281-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="f1281-131">Aby uzyskać informacje na temat tego okna komunikatu, zobacz [Zmniejszanie liczby ponownych uruchomień systemu podczas instalacji programu .NET Framework 4.5](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="f1281-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="f1281-132">Tego przykładu można użyć za pomocą instalatora .NET Framework 4; w tym scenariuszu wiadomość po prostu nie jest wysyłana.</span><span class="sxs-lookup"><span data-stu-id="f1281-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="f1281-133">Należy uruchomić przykład jako administrator.</span><span class="sxs-lookup"><span data-stu-id="f1281-133">You must run the example as an administrator.</span></span>

<span data-ttu-id="f1281-134">Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [próbki .NET Framework 4.5 Chainer](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) z galerii przykładów MSDN.</span><span class="sxs-lookup"><span data-stu-id="f1281-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="f1281-135">W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h, ChainingdotNet4.cpp i IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="f1281-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="f1281-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="f1281-136">MMIOChainer.h</span></span>

- <span data-ttu-id="f1281-137">Plik MMIOChainer.h (zobacz [pełny kod)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)zawiera definicję struktury danych i klasę podstawową, z której powinna pochodzić klasa chainer.</span><span class="sxs-lookup"><span data-stu-id="f1281-137">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="f1281-138">Program .NET Framework 4.5 rozszerza strukturę danych MMIO w celu obsługi danych wymaganych przez instalatora programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f1281-138">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="f1281-139">Zmiany w strukturze MMIO są zgodne z powrotem, więc .NET Framework 4 chainer może pracować z .NET Framework 4.5 konfiguracji bez konieczności ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="f1281-140">Jednak ten scenariusz nie obsługuje funkcji zmniejszania ponownego uruchamiania systemu.</span><span class="sxs-lookup"><span data-stu-id="f1281-140">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="f1281-141">Pole wersji umożliwia identyfikację poprawek do struktury i formatu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f1281-141">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="f1281-142">Instalator programu .NET Framework określa wersję interfejsu łańcucha, `VirtualQuery` wywołując funkcję w celu określenia rozmiaru mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="f1281-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="f1281-143">Jeśli rozmiar jest wystarczająco duży, aby pomieścić pole wersji, instalator programu .NET Framework używa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="f1281-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="f1281-144">Jeśli mapowanie pliku jest zbyt małe, aby zawierało pole wersji, co ma miejsce w przypadku programu .NET Framework 4, proces instalacji zakłada wersję 0 (4).</span><span class="sxs-lookup"><span data-stu-id="f1281-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="f1281-145">Jeśli chainer nie obsługuje wersji wiadomości, którą instalator programu .NET Framework chce wysłać, instalator programu .NET Framework zakłada, że odpowiedź ignoruje.</span><span class="sxs-lookup"><span data-stu-id="f1281-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="f1281-146">Struktura danych MMIO jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f1281-146">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="f1281-147">Struktura `MmioDataStructure` danych nie powinna być używana bezpośrednio; użyj `MmioChainer` klasy zamiast do zaimplementowania chainer.</span><span class="sxs-lookup"><span data-stu-id="f1281-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="f1281-148">Wynik z `MmioChainer` klasy do łańcucha .NET Framework 4.5 redystrybucyjne.</span><span class="sxs-lookup"><span data-stu-id="f1281-148">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="f1281-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="f1281-149">IProgressObserver.h</span></span>

- <span data-ttu-id="f1281-150">Plik IProgressObserver.h implementuje obserwatora postępu[(zobacz pełny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span><span class="sxs-lookup"><span data-stu-id="f1281-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="f1281-151">Ten obserwator otrzymuje powiadomienie o postępie pobierania i `char`instalacji (określonym jako niepodpisany , 0-255, wskazujący 1%-100% ukończony).</span><span class="sxs-lookup"><span data-stu-id="f1281-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="f1281-152">Obserwator jest również powiadamiany, gdy chainee wysyła wiadomość, a obserwator powinien wysłać odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="f1281-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="f1281-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="f1281-153">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="f1281-154">[ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) plik implementuje `Server` klasy, która pochodzi `MmioChainer` z klasy i zastępuje odpowiednie metody wyświetlania informacji o postępie.</span><span class="sxs-lookup"><span data-stu-id="f1281-154">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="f1281-155">MmioChainer tworzy sekcję o określonej nazwie sekcji i inicjuje chainer o określonej nazwie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f1281-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="f1281-156">Nazwa zdarzenia jest zapisywana w zamapowanym strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="f1281-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="f1281-157">Nazwy sekcji i zdarzeń powinny być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="f1281-157">You should make the section and event names unique.</span></span> <span data-ttu-id="f1281-158">Klasa `Server` w poniższym kodzie uruchamia określony program instalacyjny, monitoruje jego postęp i zwraca kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="f1281-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="f1281-159">Instalacja jest uruchamiana w Main metody.</span><span class="sxs-lookup"><span data-stu-id="f1281-159">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="f1281-160">Przed uruchomieniem instalacji, chainer sprawdza, czy .NET Framework 4.5 jest już zainstalowany przez wywołanie: `IsNetFx4Present`</span><span class="sxs-lookup"><span data-stu-id="f1281-160">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="f1281-161">Można zmienić ścieżkę pliku wykonywalnego (Setup.exe w przykładzie) w `Launch` metodzie, aby wskazać jego poprawną lokalizację lub dostosować kod, aby określić lokalizację.</span><span class="sxs-lookup"><span data-stu-id="f1281-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="f1281-162">Klasa `MmioChainer` podstawowa zawiera `Run()` metodę blokowania, która wywołuje klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="f1281-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="f1281-163">Metoda `Send` przechwytuje i przetwarza wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f1281-163">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="f1281-164">W tej wersji programu .NET Framework jedyną obsługiwana wiadomością jest komunikat bliskiej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

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

- <span data-ttu-id="f1281-165">Dane postępu to niepodpisany `char` od 0 (0%) i 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="f1281-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="f1281-166">HRESULT jest przekazywana do `Finished` metody.</span><span class="sxs-lookup"><span data-stu-id="f1281-166">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f1281-167">.NET Framework 4.5 redystrybucyjne zazwyczaj zapisuje wiele komunikatów postępu i pojedynczy komunikat, który wskazuje zakończenie (po stronie łańcucha).</span><span class="sxs-lookup"><span data-stu-id="f1281-167">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="f1281-168">Odczytuje również asynchronicznie, `Abort` szukając rekordów.</span><span class="sxs-lookup"><span data-stu-id="f1281-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="f1281-169">Jeśli otrzyma `Abort` rekord, anuluje instalację i zapisuje gotowy rekord z E_ABORT jako jego dane po przerwaniu instalacji i cofnięciu operacji instalacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f1281-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="f1281-170">Typowy serwer tworzy losową nazwę pliku MMIO, tworzy plik (jak `Server::CreateSection`pokazano w poprzednim przykładzie `CreateProcess` kodu, w ), i `-pipe someFileSectionName` uruchamia redystrybucyjny przy użyciu metody i przekazując nazwę potoku z opcją.</span><span class="sxs-lookup"><span data-stu-id="f1281-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="f1281-171">Serwer powinien `OnProgress`implementować `Send` `Finished` , i metody z kodu specyficznego dla interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1281-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1281-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1281-172">See also</span></span>

- [<span data-ttu-id="f1281-173">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="f1281-173">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="f1281-174">Wdrożenie</span><span class="sxs-lookup"><span data-stu-id="f1281-174">Deployment</span></span>](index.md)
