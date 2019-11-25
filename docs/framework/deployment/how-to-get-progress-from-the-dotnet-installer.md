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
ms.openlocfilehash: e07bb3443fb9461fa707d66e74350a39980c60c0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975550"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5

.NET Framework 4,5 to środowisko uruchomieniowe redystrybucyjne. W przypadku tworzenia aplikacji dla tej wersji .NET Framework można uwzględnić konfigurację (łańcuch) .NET Framework 4,5 jako część wymagań wstępnych konfiguracji aplikacji. Aby zaprezentować dostosowane lub ujednolicone środowisko konfiguracji, możesz chcieć dyskretnie uruchomić Instalatora .NET Framework 4,5 i śledzić jego postęp, pokazując postęp instalacji aplikacji. Aby włączyć śledzenie dyskretne, .NET Framework konfigurację 4,5 (którą można obejrzeć) definiuje protokół, używając segmentu we/wy mapowanego na pamięć (MMIO) w celu komunikacji z konfiguracją (obserwatorem lub łańcuchem). Ten protokół definiuje sposób uzyskiwania przez moduł łańcucha informacji o postępie, uzyskiwanie szczegółowych wyników, reagowanie na komunikaty i anulowanie konfiguracji .NET Framework 4,5.

- **Wywołanie**. Aby wywołać konfigurację .NET Framework 4,5 i uzyskać informacje o postępie z sekcji MMIO, program instalacyjny musi wykonać następujące czynności:

    1. Wywołaj program redystrybucyjny .NET Framework 4,5:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        *Nazwa sekcji* , która ma być używana do identyfikowania aplikacji. .NET Framework Instalator odczytuje i zapisuje dane w sekcji MMIO asynchronicznie, dzięki czemu może być przydatne użycie zdarzeń i komunikatów w tym czasie. W przykładzie proces instalacji .NET Framework jest tworzony przez konstruktora, który alokuje sekcję MMIO (`TheSectionName`) i definiuje zdarzenie (`TheEventName`):

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Zastąp te nazwy nazwami unikatowymi dla programu instalacyjnego.

    2. Zapoznaj się z sekcją MMIO. W .NET Framework 4,5 operacje pobierania i instalacji są jednoczesne: jedna część .NET Framework może być instalowana podczas pobierania innej części. W związku z tym postęp jest wysyłany z powrotem (czyli zapisany) do sekcji MMIO jako dwie liczby (`m_downloadSoFar` i `m_installSoFar`), które zwiększają się od 0 do 255. Po zapisaniu 255 i zakończeniu .NET Framework instalacja zostanie zakończona.

- **Kody zakończenia**. Następujące kody zakończenia z polecenia do wywołania programu redystrybucyjnego .NET Framework 4,5 wskazują, czy instalacja zakończyła się powodzeniem, czy niepowodzeniem:

  - 0 — Instalacja została ukończona pomyślnie.

  - 3010 — instalacja została ukończona pomyślnie; wymagane jest ponowne uruchomienie systemu.

  - 1602 — konfiguracja została anulowana.

  - Wszystkie inne kody — Instalator napotkał błędy; Aby uzyskać szczegółowe informacje, Przejrzyj pliki dziennika utworzone w% temp%.

- **Anulowanie instalacji**. Instalację można anulować w dowolnym momencie za pomocą metody `Abort`, aby ustawić flagi `m_downloadAbort` i `m_ installAbort` w sekcji MMIO.

## <a name="chainer-sample"></a>Przykład łańcucha

Przykładowy moduł łańcucha uruchamia dyskretnie i śledzi konfigurację .NET Framework 4,5 podczas wyświetlania postępu. Ten przykład jest podobny do przykładu łańcucha dostarczonego dla .NET Framework 4. Ponadto może to uniemożliwić ponowne uruchomienie systemu przez przetworzenie okna komunikatu do zamykania aplikacji .NET Framework 4. Aby uzyskać informacje na temat tego okna komunikatu, zobacz [ograniczanie ponownych uruchomień systemu podczas instalacji .NET Framework 4,5](reducing-system-restarts.md). Tego przykładu można użyć w Instalatorze programu .NET Framework 4. w tym scenariuszu wiadomość jest po prostu niewysłana.

> [!WARNING]
> Należy uruchomić przykład jako administrator.

Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [przykładu łańcucha .NET Framework 4,5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) z galerii przykładów MSDN.

W poniższych sekcjach opisano znaczące pliki w tym przykładzie: MMIOChainer. h, ChainingdotNet4. cpp i IProgressObserver. h.

#### <a name="mmiochainerh"></a>MMIOChainer. h

- Plik MMIOChainer. h (zobacz [kompletny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) zawiera definicję struktury danych i klasę bazową, z której Klasa łańcucha powinna być pochodna. .NET Framework 4,5 rozszerza strukturę danych MMIO w celu obsługi danych wymaganych przez Instalatora .NET Framework 4,5. Zmiany struktury MMIO są zgodne z poprzednimi wersjami, dzięki czemu moduł .NET Framework 4 może współpracował z instalacją .NET Framework 4,5, bez konieczności ponownej kompilacji. Jednak ten scenariusz nie obsługuje funkcji ograniczania ponownych uruchomień systemu.

    Pole Version zawiera metodę identyfikowania poprawek w formacie struktury i komunikatu. Konfiguracja .NET Framework określa wersję interfejsu łańcucha przez wywołanie funkcji `VirtualQuery` w celu określenia rozmiaru mapowania pliku. Jeśli rozmiar jest wystarczająco duży, aby zmieścił się w polu wersja, .NET Framework Instalator używa określonej wartości. Jeśli mapowanie pliku jest za małe, aby zawierało pole wersji, czyli w przypadku .NET Framework 4, proces instalacji przyjmuje wersję 0 (4). Jeśli moduł łańcucha nie obsługuje wersji komunikatu, która .NET Framework instalator chce wysłać, .NET Framework instalator zabierze odpowiedź na ignorowanie.

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

- Struktury danych `MmioDataStructure` nie należy używać bezpośrednio; Zamiast tego użyj klasy `MmioChainer`, aby zaimplementować moduł łańcucha. Utwórz z klasy `MmioChainer`, aby utworzyć łańcuch pakietu redystrybucyjnego .NET Framework 4,5.

#### <a name="iprogressobserverh"></a>IProgressObserver. h

- Plik IProgressObserver. h implementuje obserwatora postępu ([Zobacz kompletny kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)). Ten obserwator otrzymuje powiadomienie o postępie pobierania i instalacji (określony jako niepodpisany `char`, 0-255, wskazujący, że zakończono 1%-100%). Obserwator zostanie również powiadomiony, gdy chainee wysyła komunikat, a obserwator powinien wysłać odpowiedź.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ChainingdotNet 4.5. cpp

- Plik [chainingdotnet 4.5. cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) implementuje klasę `Server`, która pochodzi z klasy `MmioChainer` i zastępuje odpowiednie metody wyświetlania informacji o postępie. MmioChainer tworzy sekcję z określoną nazwą sekcji i inicjuje łańcuch z określoną nazwą zdarzenia. Nazwa zdarzenia jest zapisywana w mapowanej strukturze danych. Należy zmienić nazwy sekcji i zdarzeń na unikatowe. Klasa `Server` w poniższym kodzie uruchamia określony program instalacyjny, monitoruje postęp i zwraca kod zakończenia.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Instalacja została uruchomiona w metodzie Main.

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

- Przed uruchomieniem instalacji program łańcucha sprawdza, czy .NET Framework 4,5 jest już zainstalowany przez wywołanie `IsNetFx4Present`:

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

- Można zmienić ścieżkę pliku wykonywalnego (Setup. exe w przykładzie) w metodzie `Launch`, aby wskazać jego poprawną lokalizację, lub dostosować kod w celu określenia lokalizacji. Klasa bazowa `MmioChainer` zapewnia blokującą metodę `Run()`, która wywołuje klasę pochodną.

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

- Metoda `Send` przechwytuje i przetwarza komunikaty. W tej wersji .NET Framework jedynym obsługiwanym komunikatem jest komunikat zamknięcia aplikacji.

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

- Dane postępu są niepodpisane `char` między 0 (0%) i 255 (100%).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- WYNIK HRESULT jest przesyłany do metody `Finished`.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > Pakiet redystrybucyjny .NET Framework 4,5 zazwyczaj zapisuje wiele komunikatów o postępie i pojedynczy komunikat wskazujący na zakończenie (po stronie łańcucha). Odczytuje również asynchronicznie, szukając `Abort` rekordów. Jeśli odbierze rekord `Abort`, anuluje instalację i zapisuje gotowy rekord z E_ABORT jako dane po przerwaniu instalacji i wycofaniu operacji instalacji.

Typowy serwer tworzy losową nazwę pliku MMIO, tworzy plik (jak pokazano w poprzednim przykładzie kodu, w `Server::CreateSection`) i uruchamia pakiet redystrybucyjny przy użyciu metody `CreateProcess` i przekazując nazwę potoku przy użyciu opcji `-pipe someFileSectionName`. Serwer powinien implementować `OnProgress`, `Send`i `Finished` metody przy użyciu kodu specyficznego dla interfejsu użytkownika aplikacji.

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Wdrażanie](index.md)
