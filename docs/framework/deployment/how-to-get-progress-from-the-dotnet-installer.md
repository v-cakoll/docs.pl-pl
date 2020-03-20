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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5

.NET Framework 4.5 jest redystrybucyjnym czasem wykonywania. Jeśli programujesz aplikacje dla tej wersji programu .NET Framework, możesz dołączyć (łańcuch) .NET Framework 4.5 konfiguracji jako część wstępną konfiguracji aplikacji. Aby zaprezentować niestandardowe lub ujednolicone środowisko konfiguracji, można po cichu uruchomić konfigurację programu .NET Framework 4.5 i śledzić jej postęp, pokazując jednocześnie postęp konfiguracji aplikacji. Aby włączyć ciche śledzenie, instalator programu .NET Framework 4.5 (który można obserwować) definiuje protokół przy użyciu segmentu MMIO (MMIO) mapowanej pamięcią do komunikowania się z konfiguracją (obserwatorem lub łańcuchem). Ten protokół definiuje sposób, w jaki chainer może uzyskać informacje o postępie, uzyskać szczegółowe wyniki, odpowiedzieć na wiadomości i anulować konfigurację programu .NET Framework 4.5.

- **Wywołanie**. Aby wywołać konfigurację programu .NET Framework 4.5 i otrzymywać informacje o postępie z sekcji MMIO, program instalacyjny musi wykonać następujące czynności:

    1. Wywołanie programu redystrybucyjnego .NET Framework 4.5:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        Gdzie *nazwa sekcji* to dowolna nazwa, której chcesz użyć do zidentyfikowania aplikacji. Instalator programu .NET Framework odczytuje i zapisuje w sekcji MMIO asynchronicznie, więc może okazać się wygodne użycie zdarzeń i wiadomości w tym czasie. W tym przykładzie proces konfiguracji programu .NET Framework jest tworzony przez konstruktora, który przydziela sekcję MMIO (`TheSectionName`) i definiuje zdarzenie (`TheEventName`):

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Należy zastąpić te nazwy nazwami, które są unikatowe dla programu instalacyjnego.

    2. Przeczytaj z sekcji MMIO. W programie .NET Framework 4.5 operacje pobierania i instalacji są jednoczesne: jedna część programu .NET Framework może być instalowana podczas pobierania innej części. W rezultacie postęp jest odsyłany (czyli zapisywany) do sekcji`m_downloadSoFar` MMIO jako dwie liczby ( i `m_installSoFar`), które zwiększają się z 0 do 255. Po zapisaniu 255 i zakończy się działanie programu .NET Framework, instalacja została zakończona.

- **Kody zakończenia**. Następujące kody zakończenia z polecenia do wywołania programu redystrybucyjnego .NET Framework 4.5 wskazują, czy instalacja powiodła się, czy nie:

  - 0 - Instalacja została pomyślnie zakończona.

  - 3010 – Instalacja została pomyślnie zakończona; wymagane jest ponowne uruchomienie systemu.

  - 1602 – Instalator został anulowany.

  - Wszystkie inne kody - Instalator napotkał błędy; sprawdź szczegóły plików dziennika utworzonych w %temp%.

- **Anulowanie konfiguracji**. Konfigurację można anulować w `Abort` dowolnym momencie, używając metody do ustawiania `m_downloadAbort` i `m_ installAbort` flag w sekcji MMIO.

## <a name="chainer-sample"></a>Próbka łańcucha

Próbka Chainer dyskretnie uruchamia i śledzi konfigurację programu .NET Framework 4.5, pokazując jednocześnie postęp. Ten przykład jest podobny do próbki Chainer przewidziane dla .NET Framework 4. Jednak ponadto można uniknąć ponownego uruchomienia systemu, przetwarzając okno komunikatu do zamykania aplikacji .NET Framework 4. Aby uzyskać informacje na temat tego okna komunikatu, zobacz [Zmniejszanie liczby ponownych uruchomień systemu podczas instalacji programu .NET Framework 4.5](reducing-system-restarts.md). Tego przykładu można użyć za pomocą instalatora .NET Framework 4; w tym scenariuszu wiadomość po prostu nie jest wysyłana.

> [!WARNING]
> Należy uruchomić przykład jako administrator.

Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [próbki .NET Framework 4.5 Chainer](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) z galerii przykładów MSDN.

W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h, ChainingdotNet4.cpp i IProgressObserver.h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- Plik MMIOChainer.h (zobacz [pełny kod)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)zawiera definicję struktury danych i klasę podstawową, z której powinna pochodzić klasa chainer. Program .NET Framework 4.5 rozszerza strukturę danych MMIO w celu obsługi danych wymaganych przez instalatora programu .NET Framework 4.5. Zmiany w strukturze MMIO są zgodne z powrotem, więc .NET Framework 4 chainer może pracować z .NET Framework 4.5 konfiguracji bez konieczności ponownej kompilacji. Jednak ten scenariusz nie obsługuje funkcji zmniejszania ponownego uruchamiania systemu.

    Pole wersji umożliwia identyfikację poprawek do struktury i formatu wiadomości. Instalator programu .NET Framework określa wersję interfejsu łańcucha, `VirtualQuery` wywołując funkcję w celu określenia rozmiaru mapowania plików. Jeśli rozmiar jest wystarczająco duży, aby pomieścić pole wersji, instalator programu .NET Framework używa określonej wartości. Jeśli mapowanie pliku jest zbyt małe, aby zawierało pole wersji, co ma miejsce w przypadku programu .NET Framework 4, proces instalacji zakłada wersję 0 (4). Jeśli chainer nie obsługuje wersji wiadomości, którą instalator programu .NET Framework chce wysłać, instalator programu .NET Framework zakłada, że odpowiedź ignoruje.

    Struktura danych MMIO jest zdefiniowana w następujący sposób:

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

- Struktura `MmioDataStructure` danych nie powinna być używana bezpośrednio; użyj `MmioChainer` klasy zamiast do zaimplementowania chainer. Wynik z `MmioChainer` klasy do łańcucha .NET Framework 4.5 redystrybucyjne.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- Plik IProgressObserver.h implementuje obserwatora postępu[(zobacz pełny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)). Ten obserwator otrzymuje powiadomienie o postępie pobierania i `char`instalacji (określonym jako niepodpisany , 0-255, wskazujący 1%-100% ukończony). Obserwator jest również powiadamiany, gdy chainee wysyła wiadomość, a obserwator powinien wysłać odpowiedź.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ChainingdotNet4.5.cpp

- [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) plik implementuje `Server` klasy, która pochodzi `MmioChainer` z klasy i zastępuje odpowiednie metody wyświetlania informacji o postępie. MmioChainer tworzy sekcję o określonej nazwie sekcji i inicjuje chainer o określonej nazwie zdarzenia. Nazwa zdarzenia jest zapisywana w zamapowanym strukturze danych. Nazwy sekcji i zdarzeń powinny być unikatowe. Klasa `Server` w poniższym kodzie uruchamia określony program instalacyjny, monitoruje jego postęp i zwraca kod zakończenia.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Instalacja jest uruchamiana w Main metody.

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

- Przed uruchomieniem instalacji, chainer sprawdza, czy .NET Framework 4.5 jest już zainstalowany przez wywołanie: `IsNetFx4Present`

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

- Można zmienić ścieżkę pliku wykonywalnego (Setup.exe w przykładzie) w `Launch` metodzie, aby wskazać jego poprawną lokalizację lub dostosować kod, aby określić lokalizację. Klasa `MmioChainer` podstawowa zawiera `Run()` metodę blokowania, która wywołuje klasę pochodną.

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

- Metoda `Send` przechwytuje i przetwarza wiadomości. W tej wersji programu .NET Framework jedyną obsługiwana wiadomością jest komunikat bliskiej aplikacji.

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

- Dane postępu to niepodpisany `char` od 0 (0%) i 255 (100%).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT jest przekazywana do `Finished` metody.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > .NET Framework 4.5 redystrybucyjne zazwyczaj zapisuje wiele komunikatów postępu i pojedynczy komunikat, który wskazuje zakończenie (po stronie łańcucha). Odczytuje również asynchronicznie, `Abort` szukając rekordów. Jeśli otrzyma `Abort` rekord, anuluje instalację i zapisuje gotowy rekord z E_ABORT jako jego dane po przerwaniu instalacji i cofnięciu operacji instalacyjnych.

Typowy serwer tworzy losową nazwę pliku MMIO, tworzy plik (jak `Server::CreateSection`pokazano w poprzednim przykładzie `CreateProcess` kodu, w ), i `-pipe someFileSectionName` uruchamia redystrybucyjny przy użyciu metody i przekazując nazwę potoku z opcją. Serwer powinien `OnProgress`implementować `Send` `Finished` , i metody z kodu specyficznego dla interfejsu użytkownika aplikacji.

## <a name="see-also"></a>Zobacz też

- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Wdrożenie](index.md)
