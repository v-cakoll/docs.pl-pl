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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest pakiet redystrybucyjny środowiska wykonawczego. W przypadku tworzenia aplikacji dla tej wersji programu .NET Framework, można dołączyć (łańcucha) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator w ramach wymagań wstępnych instalacji aplikacji. Do prezentowania dostosowane lub ujednoliconego konfiguracji systemu, można uruchomić w trybie dyskretnym [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji i śledzić postęp podczas pokazywania postępu instalacji aplikacji. Aby włączyć śledzenie dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora (mogą być obserwowane) definiuje protokół za pomocą mapowanych na pamięć segment rozwiązanie we/wy (MMIO) do komunikacji z ustawień (obserwatora lub moduł łańcucha). Protokół ten definiuje sposób moduł łańcucha uzyskać informacje o postępie, uzyskiwać szczegółowe wyniki, odpowiada na komunikaty i anulować [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora.  
  
-   **Wywołanie** .  Aby wywołać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora i odbierać informacje o postępie z sekcji Rozwiązanie MMIO, program Instalator musi wykonać następujące czynności:  
  
    1.  Wywołanie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]pakietu redystrybucyjnego programu:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         gdzie *nazwę sekcji* jest dowolną nazwę, które ma być używany do identyfikowania Twojej aplikacji. Instalator .NET framework odczytuje i zapisuje w sekcji Rozwiązanie MMIO asynchronicznie, dlatego może być bardzo łatwe w użyciu zdarzeń i komunikatów w tym czasie. W tym przykładzie proces Instalator .NET Framework został utworzony przez konstruktora że oba przydziela sekcji Rozwiązanie MMIO (`TheSectionName`) i definiuje zdarzenia (`TheEventName`):  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Zamień tych nazw z nazwami, które są unikatowe dla programu Instalatora.  
  
    2.  Przeczytaj rozwiązanie MMIO sekcji. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], są jednoczesnych operacji pobierania i instalacji: jedną część programu .NET Framework może być instalowany podczas pobierania innej części. W związku z tym postępu są wysyłane z powrotem (który zapisany) w sekcji Rozwiązanie MMIO jako dwóch liczb (`m_downloadSoFar` i `m_installSoFar`) który zwiększyć z zakresu od 0 do 255. Gdy 255 są zapisywane i zamyka .NET Framework, instalacja jest zakończona.  
  
-   **Kody zakończenia**. Następujące kody zakończenia z polecenia do wywołania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pakietu redystrybucyjnego programu wskazują, czy Instalator zakończyło się pomyślnie lub nie powiodło się:  
  
    -   0 — instalacja została ukończona pomyślnie.  
  
    -   3010 — instalacja zakończyła się pomyślnie; wymagane jest ponowne uruchomienie systemu.  
  
    -   1602 — Instalator zostało anulowane.  
  
    -   Wszystkie pozostałe kody — Instalator napotkał błędy; Przejrzyj pliki dziennika utworzone w % temp %, aby uzyskać szczegółowe informacje.  
  
-   **Anulowanie instalacji**. W dowolnej chwili można anulować instalacji przy użyciu `Abort` metodę, aby ustawić `m_downloadAbort` i `m_ installAbort` flagi w sekcji Rozwiązanie MMIO.  
  
## <a name="chainer-sample"></a>Przykładowy moduł łańcucha  
 Przykładowy moduł łańcucha dyskretnie uruchamia i śledzi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora podczas pokazywania postępu. Ten przykład jest podobny do przykładu moduł łańcucha dostępnego dla programu .NET Framework 4. Jednak Ponadto go uniknąć ponownego uruchomienia systemu przez przetwarzanie komunikat zamknięcia aplikacji .NET Framework 4. Informacje dla tego pola wiadomości, zobacz [zmniejszenie uruchamia ponownie podczas .NET Framework 4.5 instalacji systemów](../../../docs/framework/deployment/reducing-system-restarts.md). Można użyć tego przykładu z Instalatora .NET Framework 4; w tym scenariuszu komunikat po prostu nie są wysyłane.  
  
> [!WARNING]
>  Przykład musi działać jako administrator.  
  
 Możesz pobrać kompletne rozwiązanie Visual Studio dla [.NET Framework 4.5 moduł łańcucha próbki](http://go.microsoft.com/fwlink/?LinkId=231345) z galerii przykładów MSDN.  
  
 W poniższych sekcjach opisano istotne pliki w tym przykładzie: MMIOChainer.h, ChainingdotNet4.cpp i IProgressObserver.h.  
  
#### <a name="mmiochainerh"></a>MMIOChainer.h  
  
-   Plik MMIOChainer.h (zobacz [uzupełnianie kodu](http://go.microsoft.com/fwlink/?LinkId=231369)) zawiera definicji danych struktury i klasy podstawowej, z którego powinien pochodzić klasy moduł łańcucha. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozszerza rozwiązanie MMIO struktury danych do obsługi danych który [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatorowi. Zmiany w strukturze rozwiązanie MMIO są zapewniającej, dzięki użyciu modułu łańcucha .NET Framework 4 można pracować z Instalatora .NET Framework 4.5 bez konieczności ponownej kompilacji. Jednak ten scenariusz nie obsługuje funkcji zmniejszenia ponownego uruchomienia systemu.  
  
     Pole wersji udostępnia sposób identyfikacji zmian w formacie struktury i komunikatu.  Instalator .NET Framework Określa wersję interfejsu moduł łańcucha wywołując `VirtualQuery` funkcji do określenia rozmiaru mapowania pliku.  Jeśli rozmiar jest wystarczająco duży, aby zmieścił się w polu wersji, Instalator .NET Framework używa określonej wartości. Jeśli mapowanie pliku jest zbyt mały, aby pomieścił pole wersji, która jest w przypadku programu .NET Framework 4, proces instalacji zakłada wersji 0 (4). Jeśli moduł łańcucha nie obsługuje wersji komunikat, który chce wysłać Instalator .NET Framework, Instalator .NET Framework zakłada Ignoruj odpowiedzi.  
  
     Struktura danych rozwiązanie MMIO jest zdefiniowane w następujący sposób:  
  
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
  
-   `MmioDataStructure` Struktury danych nie powinna być używana bezpośrednio; użyj `MmioChainer` zamiast klasy do zaimplementowania programu moduł łańcucha. Pochodzić od `MmioChainer` klasy łańcucha [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji.  
  
#### <a name="iprogressobserverh"></a>IProgressObserver.h  
  
-   Plik IProgressObserver.h implementuje obserwatora postępu ([, zobacz pełny kod](http://go.microsoft.com/fwlink/?LinkId=231370)). Obserwator pobiera powiadomienie postępu pobierania i instalacji (określony jako niepodpisany `char`, 0 – 255, wskazującą 1 100% pełną). Obserwator jest również powiadomienie, gdy chainee wysyła komunikat i obserwatora należy wysłać odpowiedzi.  
  
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
  
-   [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) pliku implementuje `Server` klasy, która jest pochodną `MmioChainer` klasy i zastępuje odpowiedniej metody, aby wyświetlić informacje o postępie. MmioChainer tworzy sekcję o nazwie określonej sekcji i inicjuje moduł łańcucha o nazwie określone zdarzenie. Nazwa zdarzenia są zapisywane w strukturze zmapowanych danych. Nazwy sekcji i zdarzenia powinien zapewnić unikatowy. `Server` Klasy w poniższym kodzie uruchamia określony Instalatora, monitoruje postęp i zwraca kod zakończenia.  
  
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
  
-   Przed uruchomieniem instalacji, moduł łańcucha sprawdza, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jest już zainstalowana przez wywołanie metody `IsNetFx4Present`:  
  
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
  
-   Można zmienić ścieżkę do pliku wykonywalnego (Setup.exe w przykładzie) w `Launch` metodę, aby wskazać jej poprawnej lokalizacji lub Dostosuj kod, aby określić lokalizację. `MmioChainer` Udostępnia klasę podstawową blokujący `Run()` metodę, która wywołuje klasy pochodnej.  
  
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
  
-   `Send` Metody przechwytuje i przetwarza wiadomości.  W tej wersji programu .NET Framework tylko komunikatów obsługiwanych jest komunikat zamknięcia aplikacji.  
  
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
  
-   Postęp danych jest niepodpisany `char` od 0 (0%) do 255 (100%).  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   HRESULT jest przekazywana do `Finished` metody.  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Pakietu redystrybucyjnego zwykle zapisuje komunikaty o postępie wielu i jednego komunikatu informującego zakończenia (po stronie moduł łańcucha). Odczytuje również asynchronicznie, wyszukiwanie `Abort` rekordów. Po otrzymaniu `Abort` rekordów, jego anuluje instalację i zapisuje Zakończono rekord z E_ABORT jako jego danych po instalacji zostało przerwane i operacje instalacji mają została wycofana.  
  
 Typowy serwer tworzy losowe rozwiązanie MMIO nazwę pliku, tworzy plik (jak pokazano w poprzednim przykładzie kodu `Server::CreateSection`) i uruchamia pakiet redystrybucyjny programu przy użyciu `CreateProcess` — metoda i przekazywanie potoku nazw z `-pipe someFileSectionName` opcji. Serwer powinien implementować `OnProgress`, `Send`, i `Finished` metody z kodu specyficzne dla interfejsu użytkownika aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Wdrażanie](../../../docs/framework/deployment/index.md)
