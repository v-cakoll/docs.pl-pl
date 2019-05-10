---
title: 'Instrukcje: pobieranie danych o postępie z Instalatora .NET Framework 4.5'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdb74259d7b034511722b1d2992b4ec16adb551e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750429"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Instrukcje: pobieranie danych o postępie z Instalatora .NET Framework 4.5

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest redystrybucyjnego środowiska uruchomieniowego. W przypadku tworzenia aplikacji dla tej wersji programu .NET Framework, można dołączyć (łańcuch) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator w ramach wymagań wstępnych instalacji aplikacji. Obecne środowisko dostosowany lub ujednoliconego Instalatora, może chcesz uruchomić w trybie dyskretnym [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i śledzić postęp podczas wyświetlania postępu instalacji aplikacji. Aby włączyć śledzenie dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora (mogą być odtwarzane) definiuje protokół, za pomocą mapowanych na pamięć segment operacji We/Wy (rozwiązanie MMIO) do komunikowania się z ustawień (obserwatora lub chainer). Protokół ten definiuje sposób chainer uzyskać informacje o postępie, Uzyskaj szczegółowe wyniki, odpowiadanie na wiadomości i anulować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora.

- **Wywołania**. Aby wywołać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i otrzymywać informacje o postępie w sekcji Rozwiązanie MMIO, program instalacyjny, należy wykonać następujące czynności:

    1. Wywołaj [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]pakiet redystrybucyjny programu:

        ```
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name
        ```

        gdzie *nazwa sekcji* jest dowolną nazwę, którego chcesz użyć do identyfikacji danej aplikacji. Instalator .NET framework wykonującej Odczyt i zapis w sekcji Rozwiązanie MMIO asynchronicznie, dzięki czemu użytkownik może okazać się przydatna do użycia w tym czasie zdarzenia i komunikaty. W tym przykładzie proces instalacji programu .NET Framework jest tworzony przez konstruktora, przydziela zarówno w sekcji Rozwiązanie MMIO (`TheSectionName`) i definiuje zdarzenia (`TheEventName`):

        ```
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Zamień tych nazw z nazwami, które są unikatowe dla programu instalacyjnego.

    2. Przeczytaj, w sekcji Rozwiązanie MMIO. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], operacje pobierania i instalacji są jednocześnie: Jedną z części pakietu programu .NET Framework może być instalowany podczas pobierania innej części. W rezultacie postępu są wysyłane z powrotem (zapisywanych) w sekcji Rozwiązanie MMIO jako dwóch liczb (`m_downloadSoFar` i `m_installSoFar`), zwiększyć z zakresu od 0 do 255. Po zapisaniu 255 i umożliwia zamknięcie systemu .NET Framework, instalacja została zakończona.

- **Kody zakończenia**. Następujące kody zakończenia z polecenia do wywołania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] program do dystrybucji wskazuje, czy Instalator ma zakończonych powodzeniem lub niepowodzeniem:

  - 0 — instalacja została ukończona pomyślnie.

  - 3010 — instalacja została ukończona pomyślnie; wymagane jest ponowne uruchomienie systemu.

  - 1602 — Instalatora zostało anulowane.

  - Wszystkie pozostałe kody — Instalator napotkał błędy; Sprawdź pliki dziennika utworzone w % temp %, aby uzyskać szczegółowe informacje.

- **Trwa anulowanie instalacji**. Ustawienia można anulować w dowolnym momencie za pomocą `Abort` metodę, aby ustawić `m_downloadAbort` i `m_ installAbort` flagi w sekcji Rozwiązanie MMIO.

## <a name="chainer-sample"></a>Przykładowe chainer

Przykładowe Chainer dyskretnie uruchamia i śledzi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora podczas wyświetlania postępu. Ten przykład jest podobny do przykładu Chainer dostępnego dla programu .NET Framework 4. Jednak dodatkowo go można uniknąć ponownych uruchomień systemu przez przetwarzanie okno komunikatu do zamykania aplikacji .NET Framework 4. Aby dowiedzieć się, to okno komunikatu, zobacz [zmniejszenie uruchamia ponownie podczas .NET Framework 4.5 instalacji systemów](../../../docs/framework/deployment/reducing-system-restarts.md). Możesz użyć tego przykładu z Instalatorem .NET Framework 4; w tym scenariuszu komunikat po prostu nie są wysyłane.

> [!WARNING]
> Należy uruchomić przykład jako administrator.

Możesz pobrać kompletne rozwiązanie programu Visual Studio dla [przykład Chainer programu .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkId=231345) z galerii przykładów MSDN.

W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h ChainingdotNet4.cpp i IProgressObserver.h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- Plik MMIOChainer.h (zobacz [uzupełnianie kodu](https://go.microsoft.com/fwlink/?LinkId=231369)) zawiera definicję struktury danych i klasa bazowa, z której powinna pochodzić klasy chainer. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozszerza rozwiązanie MMIO struktury danych do obsługi danych, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatorowi. Zmian w strukturze rozwiązanie MMIO są zgodne wstecz, aby chainer .NET Framework 4 można pracować z Instalatora .NET Framework 4.5, bez konieczności ponownej kompilacji. Jednak ten scenariusz nie obsługuje tę funkcję w celi zmniejszenia ponownego uruchomienia systemu.

    Pole wersji zapewnia sposób identyfikacji poprawki do formatu struktury i komunikatu. Instalator .NET Framework Określa wersję interfejsu chainer przez wywołanie metody `VirtualQuery` funkcję, aby określić rozmiar mapowania pliku. Jeśli rozmiar jest wystarczająco duża, aby uwzględnić pole wersji, Instalatora .NET Framework używa określonej wartości. W przypadku mapowania pliku jest zbyt mała, aby zawierać pole wersji, która jest w przypadku programu .NET Framework 4, proces instalacji zakłada wersja 0 (4). W przypadku chainer nie obsługuje wersji komunikat, który chce wysłać Instalatora .NET Framework, .NET Framework setup zakłada odpowiedź Ignoruj.

    Rozwiązanie MMIO struktura danych zostaje zdefiniowana w następujący sposób:

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

- `MmioDataStructure` Strukturę danych nie powinny być używane bezpośrednio; użyj `MmioChainer` zamiast klasy do zaimplementowania swoje chainer. Pochodzi od `MmioChainer` klasa do tworzenia łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- Plik IProgressObserver.h implementuje obserwatora postępu ([Zobacz kompletny kod](https://go.microsoft.com/fwlink/?LinkId=231370)). Obserwator pobiera powiadomienia o postępu pobierania i instalacji (określony jako typ unsigned `char`, 0-255, wskazującą, 1 – 100% ukończone). Obserwator jest również otrzymywać chainee wysyła komunikat, gdy obserwatora ma wysyłać odpowiedzi.

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

- [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) pliku implementuje `Server` klasy, która jest pochodną `MmioChainer` klasy i zastępuje odpowiedniej metody, aby wyświetlić informacje o postępie. MmioChainer tworzy sekcję o nazwie określonej sekcji i inicjuje chainer o nazwie określonego zdarzenia. Nazwa zdarzenia są zapisywane w strukturze zmapowanych danych. Nazwy sekcji i zdarzeń należy upewnić się unikatowy. `Server` Klasy poniższy kod uruchamia program instalacyjny określonego monitoruje postęp i zwraca kod zakończenia.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Instalacja jest uruchomiona w metody Main.

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

- Przed uruchomieniem instalacji, chainer sprawdza, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jest już zainstalowany przez wywołanie metody `IsNetFx4Present`:

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

- Ścieżka pliku wykonywalnego (Setup.exe w przykładzie) można zmienić w `Launch` metoda wskaż jego prawidłową lokalizację lub dostosować program code w celu określenia lokalizacji. `MmioChainer` Udostępnia klasę bazową, blokuje `Run()` metodę, która wywołuje klasy pochodnej.

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

- `Send` Metoda przechwytuje i przetwarza komunikaty. W tej wersji programu .NET Framework, tylko obsługiwane komunikat jest zamykanie aplikacji.

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

- Postęp danych jest niepodpisany `char` przedziału od 0 (0%) do 255 (100%).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT jest przekazywany do `Finished` metody.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Pakiet redystrybucyjny zwykle zapisuje komunikaty o postępie wielu i jednego komunikat, który wskazuje ukończenie (po stronie chainer). Odczytuje również asynchronicznie, wyszukiwanie `Abort` rekordów. Jeśli odbierze `Abort` rekordu, go anuluje instalację i zapisuje Zakończono rekord z E_ABORT jako jego dane po instalacji zostało przerwane i operacje instalacji ma została wycofana.

Typowy serwer tworzy losowe rozwiązanie MMIO nazwę pliku, tworzy plik (jak pokazano w poprzednim przykładzie kodu na `Server::CreateSection`) i uruchamia pakiet redystrybucyjny programu za pomocą `CreateProcess` nazw przy użyciu metody i przekazywania potoku `-pipe someFileSectionName` opcji. Serwer powinien implementować `OnProgress`, `Send`, i `Finished` metody z kodu specyficznego dla interfejsu użytkownika aplikacji.

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Wdrażanie](../../../docs/framework/deployment/index.md)
