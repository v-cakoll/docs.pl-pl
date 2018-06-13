---
title: 'Porady: Włączanie śledzenia WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 459d74f3faf9fab4cba047a87ccff77d193e9026
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399568"
---
# <a name="how-to-enable-wif-tracing"></a>Porady: Włączanie śledzenia WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Instrukcje ten zawiera szczegółowe procedury krok po kroku włączania śledzenia WIF w aplikacji ASP.NET. Dostępne są także instrukcje dotyczące testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dziennika są poprawne. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [tożsamości i dostępu do narzędzia](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Włączanie śledzenia WIF pasywne aplikacje, oznacza to, aplikacje, które korzystają z protokołu WS-Federation można narażając aplikacji strony złośliwych ataki (DoS) lub ujawnienie informacji. Obejmuje to zarówno pasywnym RPs i STSes pasywnych. Z tego powodu zalecamy nie włączenie śledzenia WIF pasywnym RPs lub STSes w środowisku produkcyjnym.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie  
  
-   Krok 2 – Sprawdź swoje rozwiązanie  
  
## <a name="objectives"></a>Cele  
  
-   Utwórz prostą aplikację ASP.NET, która używa WIF i STS programowanie z tożsamości i dostępu do narzędzia  
  
-   Włącz śledzenie i sprawdź, czy działa ona  
  
## <a name="overview"></a>Omówienie  
 Śledzenie umożliwia debugowania i rozwiązywania problemów z wielu rodzajów problemy z WIF, łącznie z tokenów, plików cookie, oświadczeń i komunikaty protokołu. Śledzenie WIF jest podobny do śledzenia WCF; na przykład można wybrać poziom szczegółowości śledzenia do wyświetlenia wszystkich elementów krytycznych wiadomości o wszystkie komunikaty. Ślady WIF mogą być generowane w **.xml** plików lub w **.svclog** plików, które są widoczne za pomocą narzędzia podglądu śledzenia usługi. To narzędzie znajduje się w **bin** katalogu zestawu Windows SDK ścieżka instalacji na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie  
  
-   Krok 2 – Sprawdź swoje rozwiązanie  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 — Tworzenie aplikacji formularzy sieci Web ASP.NET proste i Włącz śledzenie  
 W tym kroku zostanie utworzenie nowej aplikacji formularzy sieci Web ASP.NET i zmodyfikować *Web.config* plik w celu włączenia śledzenia.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.  
  
5.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.  
  
6.  Utwórz nowy folder w nazwie **dzienniki** w folderze głównym **C:** dysków, tak samo, jak pokazano: **C:\logs**  
  
7.  Dodaj następujące  **\<system.diagnostics >** elementu *Web.config* pliku konfiguracji bezpośrednio po upływie  **\</configSections >** elementu, tak samo, jak pokazano:  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
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
    >  Lokalizacja katalogu określonego w **initializeData —** atrybutu musi istnieć przed rozpoczęciem rejestrowania. Jeśli lokalizacja nie istnieje, zostanie utworzone żadne dzienniki.  
  
     Ustawienia konfiguracji powyżej spowoduje włączenie **pełne** śledzenia dla WIF i Zapisz dziennik wynikowy na **C:logsWIF.xml** pliku.  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – Sprawdź swoje rozwiązanie  
 W tym kroku zostanie przetestować aplikację ASP.NET włączone WIF, aby sprawdzić, czy dzienniki są rejestrowane.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Aby przetestować aplikację ASP.NET włączoną WIF pomyślne śledzenia  
  
1.  Uruchom rozwiązanie, naciskając klawisz **F5** klucza. Powinna być wyświetlana domyślna strona główna programu ASP.NET i automatycznie uwierzytelniony nazwy użytkownika *Jakub*, która jest zwracana przez usługę STS programowanie domyślny użytkownik.  
  
2.  Zamknij okno przeglądarki, a następnie przejdź do **C:\logs** folderu. Otwórz **C:\logs\WIF.xml** plików za pomocą edytora tekstu.  
  
3.  Sprawdź **WIF.xml** i sprawdzić, czy zawiera on wpisów, począwszy od  **\<E2ETraceEvent >**. Te operacje śledzenia będą zawierać  **\<TraceRecord >** elementy z opisami śledzonych działania, takie jak **sprawdzania poprawności obiektu SecurityToken**.
