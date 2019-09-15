---
title: 'Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990477"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Instrukcje: Debugowanie aplikacji obsługujących oświadczenia i usług za pomocą śledzenia programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)  
  
- Rozwiązywanie problemów i debugowanie aplikacji WIF  
  
## <a name="summary"></a>Podsumowanie  
 W tym temacie opisano czynności wymagane do skonfigurowania śledzenia WIF, zbierania dzienników śledzenia i analizowania dzienników śledzenia za pomocą narzędzia Podgląd śledzenia. Zapewnia ogólne mapowanie dla wpisów śledzenia do akcji wymaganych do rozwiązywania problemów związanych z WIF.  
  
## <a name="contents"></a>Spis treści  
  
- Cele  
  
- Zestawienie czynności  
  
- Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config  
  
- Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia  
  
- Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF  
  
- Elementy pokrewne  
  
## <a name="objectives"></a>Cele  
  
- Skonfiguruj śledzenie WIF.  
  
- Wyświetlanie dzienników śledzenia w narzędziu Podgląd śledzenia.  
  
- Identyfikuj problemy związane z WIF w dziennikach śledzenia.  
  
- Stosuj akcje naprawcze do WIF związanych z nimi problemów znalezionych w dziennikach śledzenia.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config  
  
- Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia  
  
- Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1 — Konfigurowanie śledzenia WIF przy użyciu pliku konfiguracyjnego Web. config  
 W tym kroku dodasz zmiany do sekcji konfiguracyjnych w pliku *Web. config* , który umożliwi WIF śledzenie zdarzeń i przechowywanie ich w dzienniku śledzenia.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Aby skonfigurować śledzenie WIF przy użyciu pliku konfiguracyjnego Web. config  
  
1. Otwórz plik konfiguracyjny root **Web. config** lub **App. config** w edytorze programu Visual Studio, klikając go dwukrotnie w **Eksplorator rozwiązań**. Jeśli Twoje rozwiązanie nie ma pliku konfiguracyjnego **Web. config** lub **App. config** , Dodaj go, klikając rozwiązanie w **Eksplorator rozwiązań** i klikając pozycję **Dodaj**, a następnie klikając pozycję **nowy element.** ... W oknie dialogowym **nowy element** wybierz pozycję **plik konfiguracyjny aplikacji pliku** **App. config** lub **plik konfiguracji sieci Web dla pliku** **Web. config** z listy i kliknij przycisk **OK**.  
  
2. Dodaj wpisy konfiguracji podobne do poniższego do pliku  **\<** konfiguracji w węźle Configuration > Node na końcu pliku konfiguracji:  
  
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
  
3. Powyższa konfiguracja nakazuje WIF wygenerowanie pełnych zdarzeń śledzenia i zarejestrowanie ich w pliku *WIFTrace. e2e* . Aby uzyskać pełną listę wartości przełącznika **switchValue** , zapoznaj się z tabelą poziomów śledzenia znajdującą się w następującym temacie: [Konfigurowanie śledzenia](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2 — analizowanie plików śledzenia WIF za pomocą narzędzia Podgląd śledzenia  
 W tym kroku użyjesz narzędzia do przeglądania śledzenia (SvcTraceViewer. exe) do analizowania dzienników śledzenia WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Aby analizować dzienniki śledzenia WIF za pomocą narzędzia Podgląd śledzenia (SvcTraceViewer. exe)  
  
1. Narzędzie Podgląd śledzenia (SvcTraceViewer. exe) jest dostarczane jako część Windows SDK. Jeśli nie zainstalowano jeszcze Windows SDK, możesz pobrać go tutaj: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2. Uruchom narzędzie Podgląd śledzenia (SvcTraceViewer. exe). Jest ona zazwyczaj dostępna w folderze **bin** ścieżki instalacji.  
  
3. Otwórz plik dziennika śledzenia WIF, na przykład WIFTrace. E2E, wybierając **plik**, **Otwórz...** opcji w menu lub przy użyciu skrótu **Ctrl + O** . Plik dziennika śledzenia zostanie otwarty w narzędziu Podgląd śledzenia.  
  
4. Przejrzyj pozycje na karcie **działanie** . Każdy wpis powinien zawierać numer działania, liczbę zarejestrowanych śladów, czas trwania działania oraz jego początkową i końcową sygnaturę czasową.  
  
5. Kliknij kartę **działanie** . W obszarze głównym narzędzia powinny być widoczne szczegółowe wpisy śledzenia. Użyj listy rozwijanej **poziom** w menu, aby odfiltrować określony poziom śladów, na przykład: **Wszystkie**, **Ostrzeżenie**, **Błędy**, **informacje**itd.  
  
6. Kliknij określone wpisy śledzenia, aby przejrzeć szczegóły w dolnym obszarze narzędzia. Szczegóły można wyświetlać przy użyciu **sformatowanego** i **XML** widoku, wybierając odpowiednie karty.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3 — identyfikowanie rozwiązań do rozwiązywania problemów związanych z WIF  
 W tym kroku można zidentyfikować rozwiązania dla problemów związanych z WIF, które zostały zidentyfikowane przy użyciu dziennika śledzenia WIF i narzędzia Podgląd śledzenia. Przedstawia ogólne mapowanie wyjątków związanych z WIF na potencjalne rozwiązania lub wymagane działania w celu rozwiązania problemu.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>Aby zidentyfikować rozwiązania do rozwiązywania problemów związanych z WIF  
  
1. Zapoznaj się z poniższą tabelą wyjątków WIF i wymaganych akcji, aby rozwiązać problemy.  
  
|**Identyfikator błędu**|**Komunikat o błędzie**|**Akcja wymagana do usunięcia błędu**|  
|-|-|-|  
|ID4175|Wystawca tokenu zabezpieczającego nie został rozpoznany przez IssuerNameRegistry.  Aby zaakceptować tokeny zabezpieczające z tego wystawcy, należy skonfigurować IssuerNameRegistry do zwrócenia prawidłowej nazwy dla tego wystawcy.|Ten błąd może być spowodowany przez skopiowanie odcisku palca z przystawki programu MMC i wklejenie go do pliku *Web. config* . W tym celu można uzyskać dodatkowy znak niedrukowalny w ciągu tekstowym podczas kopiowania z okna właściwości certyfikatu. Ten dodatkowy znak powoduje niepowodzenie dopasowania odcisku palca. Procedurę prawidłowego kopiowania odcisku palca można znaleźć na stronie Logowanie jednokrotne [oparte na oświadczeniach dla sieci Web i Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).|  
  
## <a name="related-items"></a>Elementy pokrewne  
  
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
