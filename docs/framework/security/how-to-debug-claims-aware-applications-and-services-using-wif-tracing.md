---
title: 'Porady: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0f2126a83e6a5638eb492bb2a529dbf4cdab1714
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Porady: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)  
  
-   Rozwiązywanie problemów i debugowanie aplikacji WIF  
  
## <a name="summary"></a>Podsumowanie  
 Ten instrukcje w tym artykule opisano czynności, jak skonfigurować śledzenie WIF, zbieranie dzienników śledzenia i sposobu analizowania śledzenia loguje się przy użyciu narzędzia podglądu śledzenia. Udostępnia ogólne mapowania dla śledzenia pozycje, aby rozwiązywać problemy związane z WIF akcje.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Zestawienie czynności  
  
-   Krok 1: Konfigurowanie śledzenia przy użyciu pliku konfiguracji Web.config WIF  
  
-   Krok 2: analizowanie plików śledzenia WIF za pomocą narzędzia podglądu śledzenia  
  
-   Krok 3: określenie rozwiązań, aby naprawić WIF problemy związane z  
  
-   Elementy pokrewne  
  
## <a name="objectives"></a>Cele  
  
-   Konfiguruj śledzenie WIF.  
  
-   Wyświetl ślad Dzienniki narzędzia podglądu śledzenia.  
  
-   Zidentyfikuj WIF związane problemy w dziennikach śledzenia.  
  
-   Zastosuj do WIF działania naprawcze związane problemy znalezione w dziennikach śledzenia.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: Konfigurowanie śledzenia przy użyciu pliku konfiguracji Web.config WIF  
  
-   Krok 2: analizowanie plików śledzenia WIF za pomocą narzędzia podglądu śledzenia  
  
-   Krok 3: określenie rozwiązań, aby naprawić WIF problemy związane z  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1: Konfigurowanie śledzenia przy użyciu pliku konfiguracji Web.config WIF  
 Zmiany w tym kroku zostaną dodane do sekcji konfiguracyjnych w *Web.config* pliku, które umożliwiają WIF do śledzenia jego zdarzeń i przechowywania ich w dzienniku śledzenia.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Aby skonfigurować śledzenie WIF przy użyciu pliku konfiguracji Web.config  
  
1.  Otwórz katalog główny **Web.config** lub **App.config** pliku konfiguracji w edytorze programu Visual Studio przez dwukrotne kliknięcie w **Eksploratora rozwiązań**. Jeśli nie ma rozwiązania **Web.config** lub **App.config** konfiguracji pliku, dodaj ją, klikając prawym przyciskiem myszy w ramach rozwiązania w **Eksploratora rozwiązań** i klikając  **Dodaj**, klikając **nowy element...** . Na **nowy element** zaznacz pozycję **pliku konfiguracji aplikacji** dla **App.config** lub **pliku konfiguracji sieci Web** dla **Web.config** na liście i kliknij przycisk **OK**.  
  
2.  Dodania wpisów konfiguracji, podobny do następującego pliku konfiguracji wewnątrz  **\<konfiguracji >** węzeł w końcu pliku konfiguracji:  
  
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
  
3.  Powyższej konfiguracji powoduje, że WIF generowanie zdarzeń śledzenia pełne i zaloguj się do *WIFTrace.e2e* pliku. Aby uzyskać pełną listę wartości **switchValue** , zobacz tabelę poziom śledzenia w następującym temacie: [Konfigurowanie śledzenia](http://msdn.microsoft.com/library/ms733025.aspx).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2: analizowanie plików śledzenia WIF za pomocą narzędzia podglądu śledzenia  
 W tym kroku użyjesz Trace Viewer Tool (SvcTraceViewer.exe) do analizowania dzienników śledzenia WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Do analizowania dzienników śledzenia WIF za pomocą narzędzia podglądu śledzenia (SvcTraceViewer.exe)  
  
1.  Narzędzia podglądu śledzenia (SvcTraceViewer.exe) jest dostarczany jako część zestawu Windows SDK. Jeśli nie został już zainstalowany zestaw Windows SDK, można go pobrać tutaj: [zestaw Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  Uruchom narzędzie przeglądarki śledzenia (SvcTraceViewer.exe). Jest ona zazwyczaj dostępna w **Bin** folderu ścieżki instalacji.  
  
3.  Otwórz plik dziennika śledzenia WIF, na przykład WIFTrace.e2e wybierając **pliku**, **Otwórz...** Opcja menu lub przy użyciu **Ctrl + O** skrótów. Otwiera plik dziennika śledzenia w narzędziu Podgląd śledzenia.  
  
4.  Przejrzyj wpisy w **działania** kartę. Każdy wpis powinien zawierać numer działania, Liczba śladów, które zostały zarejestrowane, czas trwania działania i jego znaczniki czasu rozpoczęcia i zakończenia.  
  
5.  Polecenie **działania** kartę. Należy również wyświetlić szczegółowe śledzenia wpisy w obszarze głównym narzędzia. Użyj **poziom** listy rozwijanej w menu, aby filtrować określony poziom śledzenia, na przykład: **wszystkie**, **ostrzeżenie**, **błędy**, **Informacji**itp.  
  
6.  Polecenie wpisów śledzenia określonych szczegółowych informacji w dolnym obszarze narzędzia. Szczegółowe informacje można wyświetlać przy użyciu **sformatowany** i **XML** widoku, wybierając odpowiednie karty.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3: określenie rozwiązań, aby naprawić WIF problemy związane z  
 W tym kroku należy zidentyfikować rozwiązania problemów związanych z WIF oznaczona przy użyciu narzędzia podglądu śledzenia i WIF w dzienniku śledzenia. Zawiera opis ogólnego mapowania WIF powiązane wyjątki potencjalne rozwiązania lub wymagane akcje w celu rozwiązania problemu.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>Aby zidentyfikować rozwiązania, aby naprawić WIF problemy związane z  
  
1.  Należy przejrzeć poniższą tabelę WIF wyjątków i wymagane akcje do rozwiązania problemów.  
  
|**Identyfikator błędu**|**Komunikat o błędzie**|**Czynności, aby naprawić błąd**|  
|-|-|-|  
|ID4175|Wystawca tokenu zabezpieczającego nie został rozpoznany przez IssuerNameRegistry.  Aby zaakceptować tokeny zabezpieczające z tym wystawcą, skonfiguruj IssuerNameRegistry, aby zwrócić prawidłową nazwę tego wystawcy.|Ten błąd może być spowodowany przez skopiowanie odcisk palca z przystawki programu MMC i wklejenie go do *Web.config* pliku. W szczególności podczas kopiowania z okna właściwości certyfikatu można uzyskać bardzo niedrukowalne znaki w ciągu tekstowym. Ten dodatkowy znak powoduje niepowodzenie dopasowania odcisk palca. Procedurę poprawnie kopiowania odcisk palca można znaleźć tutaj: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)|  
  
## <a name="related-items"></a>Elementy pokrewne  
  
-   [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](http://msdn.microsoft.com/library/aa751795.aspx)
