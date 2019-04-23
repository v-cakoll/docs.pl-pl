---
title: 'Instrukcje: Włączanie śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 83382a8375538acc04d293ee938a4e845d5e8820
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769037"
---
# <a name="how-to-enable-wif-tracing"></a>Instrukcje: Włączanie śledzenia programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące włączania śledzenia programu WIF w aplikacji ASP.NET. Tu również instrukcje testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dzienników są poprawne. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [Narzędzie tożsamość i dostęp](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Włączanie śledzenia programu WIF pasywne aplikacje, oznacza to, aplikacje, które używają protokołu WS-Federation potencjalnie uwidocznić aplikacji złośliwa strona atakom typu odmowa usługi (DoS) lub ujawnienie informacji. Obejmuje to zarówno pasywnym RPs i STSes pasywnym. Z tego powodu zaleca się, że możesz nie umożliwiają śledzenia programu WIF pasywnym RPs lub STSes w środowisku produkcyjnym.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie  
  
-   Krok 2 — przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Utwórz prostą aplikację platformy ASP.NET, który używa programu WIF i deweloperskiej usługi STS z narzędzie tożsamość i dostęp  
  
-   Włącz śledzenie i sprawdź, czy działa ona  
  
## <a name="overview"></a>Omówienie  
 Śledzenie umożliwia debugowanie i rozwiązywanie problemów z wielu typów problemów za pomocą programu WIF, łącznie z tokenów, plików cookie, oświadczeń i komunikaty protokołu. Śledzenia programu WIF jest podobny do śledzenia WCF; na przykład można wybrać poziom szczegółowości śledzenia, aby wyświetlić wszystko — od krytycznych wiadomości o wszystkie komunikaty. Dane śledzenia programu WIF, mogą być generowane w **.xml** plików lub **.svclog** pliki, które można przeglądać przy użyciu narzędzia podglądu śledzenia usługi. To narzędzie znajduje się w **bin** katalogu zestawu Windows SDK ścieżka instalacji na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie  
  
-   Krok 2 — przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 — Tworzenie prostych aplikacji ASP.NET Web Forms i włączyć śledzenie  
 W tym kroku utworzysz nowej aplikacji ASP.NET Web Forms i zmodyfikować *Web.config* plik, aby umożliwić śledzenie.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1. Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2. W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3. W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4. Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.  
  
5. **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.  
  
6. Utwórz nowy folder w nazwie **dzienniki** w katalogu głównym **C:** dysku, jak pokazano: **C:\logs**  
  
7. Dodaj następujący kod  **\<system.diagnostics >** elementu *Web.config* pliku konfiguracji, natychmiast po zamykającym  **\</configSections >** elementu, jak pokazano:  
  
    ```xml  
    <configuration>  
        <configSections>  
            ...
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  Lokalizacja katalogu określonego w **initializeData** atrybut musi istnieć przed rozpoczęciem rejestrowania. Jeśli lokalizacja nie istnieje, zostanie utworzony żadnych dzienników.  
  
     Powyższe ustawienia konfiguracji spowoduje włączenie **pełne** śledzenia dla programu WIF i zapisać wynikowy dziennik, aby **C:logsWIF.xml** pliku.  
  
## <a name="step-2--test-your-solution"></a>Krok 2 — przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację ASP.NET z włączoną obsługą programu WIF, aby sprawdzić, czy dzienniki są rejestrowane.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Aby przetestować aplikację ASP.NET z włączoną obsługą programu WIF do śledzenia pomyślnych  
  
1. Uruchom rozwiązanie, naciskając klawisz **F5** klucza. Użytkownik powinien być prezentowane z domyślną stronę główną struktury ASP.NET i automatycznie uwierzytelniana przy użyciu nazwy użytkownika *Terry*, która jest domyślny użytkownik, który jest zwracany za pomocą deweloperskiej usługi STS.  
  
2. Zamknij okno przeglądarki, a następnie przejdź do **C:\logs** folderu. Otwórz **C:\logs\WIF.xml** plików za pomocą edytora tekstów.  
  
3. Sprawdzanie **WIF.xml** i sprawdzić, czy zawiera on zapisów, poczynając od  **\<E2ETraceEvent >**. Ślady te będą zawierać  **\<TraceRecord >** elementy z opisami do śledzenia działania, takie jak **sprawdzania poprawności SecurityToken**.
