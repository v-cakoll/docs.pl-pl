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
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)  
  
-   Rozwiązywanie problemów i debugowanie aplikacji programu WIF  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera opis czynności, jak skonfigurować śledzenia programu WIF, gromadzić dzienniki śledzenia i jak można analizować śledzenia loguje się przy użyciu narzędzia podglądu śledzenia. Umożliwia mapowanie ogólnych dla wpisów śledzenia akcje niezbędne do rozwiązywania problemów związanych z programu WIF.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Zestawienie czynności  
  
-   Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF  
  
-   Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF  
  
-   Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą  
  
-   Powiązane elementy  
  
## <a name="objectives"></a>Cele  
  
-   Konfigurowanie śledzenia programu WIF.  
  
-   Wyświetl dzienniki śledzenia w narzędziu przeglądarki danych śledzenia.  
  
-   Identyfikowanie WIF powiązane problemy w dziennikach śledzenia.  
  
-   Zastosuj działania naprawcze, aby program WIF powiązane problemy znalezione w dziennikach śledzenia.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF  
  
-   Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF  
  
-   Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1: Konfigurowanie śledzenia za pomocą Web.config — plik konfiguracji programu WIF  
 W tym kroku dodasz zmiany do sekcji konfiguracyjnych w *Web.config* pliku, pozwalających na korzystanie z programu WIF do śledzenia jego zdarzeń i przechowywania ich w dzienniku śledzenia.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Aby skonfigurować śledzenia programu WIF, przy użyciu pliku konfiguracji Web.config  
  
1.  Otwórz katalog główny **Web.config** lub **App.config** plik konfiguracji w edytorze programu Visual Studio przez dwukrotne kliknięcie go w **Eksploratora rozwiązań**. Jeśli rozwiązanie nie ma **Web.config** lub **App.config** konfiguracji pliku, dodaj ją, klikając prawym przyciskiem rozwiązania w **Eksploratora rozwiązań** i klikając  **Dodaj**, klikając **nowy element...** . Na **nowy element** okno dialogowe, wybierz **pliku konfiguracji aplikacji** dla **App.config** lub **pliku konfiguracji sieci Web** dla **Web.config** z listy i kliknij przycisk **OK**.  
  
2.  Dodania wpisów konfiguracji, które podobny do następującego pliku konfiguracji wewnątrz  **\<konfiguracji >** węzła w końcu pliku konfiguracji:  
  
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
  
3.  Powyższa konfiguracja powoduje, że program WIF generowanie zdarzeń śledzenia pełne i zaloguj się do *WIFTrace.e2e* pliku. Aby uzyskać pełną listę wartości **switchValue** przełącznika, można znaleźć w tabeli Poziom śledzenia w następującym temacie: [Konfigurowanie śledzenia](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2: analizowanie za pomocą narzędzia podglądu śledzenia plików śledzenia programu WIF  
 W tym kroku użyjesz Trace Viewer Tool (SvcTraceViewer.exe) do analizowania dzienników śledzenia programu WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Aby analizować dzienniki śledzenia programu WIF, za pomocą narzędzia podglądu śledzenia (SvcTraceViewer.exe)  
  
1.  Narzędzie do śledzenia (SvcTraceViewer.exe) jest dostarczany jako część zestawu Windows SDK. Jeśli jeszcze nie zainstalowano zestawu Windows SDK, możesz ją pobrać tutaj: [zestawu Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  Uruchom narzędzie przeglądarki danych śledzenia (SvcTraceViewer.exe). Jest ona zazwyczaj dostępna w **Bin** folderze ścieżka instalacji.  
  
3.  Otwórz plik dziennika śledzenia programu WIF, na przykład WIFTrace.e2e, wybierając **pliku**, **Otwórz...** Opcja menu lub za pomocą **Ctrl + O** skrótów. Plik dziennika śledzenia zostanie otwarty w narzędziu przeglądarki danych śledzenia.  
  
4.  Przejrzyj wpisy w **działania** kartę. Każdy wpis powinien zawierać numer działania, Liczba śladów, które zostały zarejestrowane, czas trwania działania i jego znaczniki czasu rozpoczęcia i zakończenia.  
  
5.  Kliknij pozycję **działania** kartę. Powinny być widoczne wpisy szczegółowe śledzenie, w obszarze głównym narzędzia. Użyj **poziom** listy rozwijanej w menu, aby filtrować określony poziom ślady, na przykład: **wszystkich**, **ostrzeżenie**, **błędy**, **Informacji**itp.  
  
6.  Polecenie śledzenia określonych wpisów, aby zapoznać się z informacjami w dolnym obszarze narzędzia. Szczegółowe informacje można wyświetlić przy użyciu **sformatowany** i **XML** widoku przez wybranie odpowiednich kart.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3: określenie rozwiązań, aby naprawić program WIF problemy związane z usługą  
 W tym kroku możesz zidentyfikować rozwiązania problemów dotyczących programu WIF, identyfikowane za pomocą programu WIF w dzienniku śledzenia i narzędzie do śledzenia. Zawiera opis ogólnego mapowania środowiska WIF powiązane wyjątki potencjalnych rozwiązań lub wymagane akcje, aby rozwiązać ten problem.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>Aby zidentyfikować rozwiązania, aby naprawić program WIF problemy związane z usługą  
  
1.  Przejrzyj poniższą tabelę wyjątków programu WIF i wymaganych działań do rozwiązania problemów.  
  
|**Identyfikator błędu**|**Komunikat o błędzie**|**Wymagana akcja naprawić błąd**|  
|-|-|-|  
|ID4175|Wystawca tokenu zabezpieczającego nie został rozpoznany przez IssuerNameRegistry.  Aby zaakceptować tokeny zabezpieczające z tym wystawcą, skonfiguruj IssuerNameRegistry zwrócić prawidłową nazwę tego wystawcy.|Ten błąd może być spowodowany przez skopiowanie odcisku palca z przystawki programu MMC i wklejenie go do *Web.config* pliku. W szczególności można uzyskać dodatkowych niedrukowalne znaki w ciągu tekstowym, podczas kopiowania z okna właściwości certyfikatu. Ten dodatkowy znak powoduje, że dopasowanie odcisku palca, aby zakończyć się niepowodzeniem. Procedurę poprawnie kopiowania odcisk palca znajduje się w temacie [logowania jednokrotnego opartego na oświadczeniach — na sieci Web i Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).|  
  
## <a name="related-items"></a>Powiązane elementy  
  
-   [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
