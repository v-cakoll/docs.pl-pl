---
title: 'Instrukcje: Włączanie śledzenia programu WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971515"
---
# <a name="how-to-enable-wif-tracing"></a>Instrukcje: Włączanie śledzenia programu WIF

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Podsumowanie

Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące włączania śledzenia WIF w aplikacji ASP.NET. Zawiera również instrukcje testowania aplikacji, aby sprawdzić, czy odbiornik śledzenia i dziennik działają prawidłowo. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [Narzędzie tożsamości i dostępu](https://go.microsoft.com/fwlink/?LinkID=245849)

> [!IMPORTANT]
> Włączenie śledzenia WIF dla pasywnych aplikacji, czyli aplikacji korzystających z protokołu WS-Federation, może potencjalnie uwidocznić aplikację w oddziałach ataków typu "odmowa usługi" (DoS) lub ujawnienie informacji złośliwej stronie. Obejmuje to zarówno pasywne RPS pliku, jak i pasywne STSes. Z tego powodu zalecamy, aby nie włączać śledzenia WIF dla pasywnego RPS pliku lub STSes w środowisku produkcyjnym.

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia

- Krok 2 — testowanie rozwiązania

## <a name="objectives"></a>Cele

- Utwórz prostą aplikację ASP.NET, która używa WIF i usługi STS do tworzenia oprogramowania w ramach narzędzia do identyfikacji i uzyskiwania dostępu

- Włącz śledzenie i sprawdź, czy działa

## <a name="overview"></a>Omówienie

Funkcja śledzenia umożliwia debugowanie i rozwiązywanie problemów z wieloma typami problemów z usługą WIF, w tym z tokenami, plikami cookie, oświadczeniami, komunikatami protokołu itd. Śledzenie WIF jest podobne do śledzenia WCF; na przykład można wybrać poziom szczegółowości śladów, aby wyświetlić wszystkie informacje od krytycznych komunikatów do wszystkich komunikatów. Ślady WIF można generować w plikach **XML** lub w plikach **. svclog** , które są widoczne przy użyciu narzędzia Podgląd śledzenia usługi. To narzędzie znajduje się w katalogu **bin** ścieżki instalacji Windows SDK na komputerze, na przykład: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia

- Krok 2 — testowanie rozwiązania

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms i Włączanie śledzenia

W tym kroku utworzysz nową aplikację ASP.NET Web Forms i zmodyfikujesz plik *Web. config* w celu włączenia śledzenia.

### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET

1. Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.

2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.

3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.

5. Zostanie wyświetlone okno **tożsamość i dostęp** . W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.

6. Utwórz nowy folder w nazwanych **dziennikach** w katalogu głównym dysku **C:** , tak jak pokazano: **C:\LOGS**

7. Dodaj następujący  **\<element System. Diagnostics >** do pliku konfiguracyjnego *Web. config* bezpośrednio po zamykającym  **\<elemencie/configSections >** , jak pokazano poniżej:

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
    > Lokalizacja katalogu określona w atrybucie **initializeData** musi istnieć przed rozpoczęciem rejestrowania. Jeśli lokalizacja nie istnieje, dzienniki nie zostaną utworzone.

     Powyższe ustawienia konfiguracji umożliwią **pełne** śledzenie WIF i zapisywanie wynikowego dziennika w pliku **C:logsWIF.XML** .

## <a name="step-2--test-your-solution"></a>Krok 2 — testowanie rozwiązania

W tym kroku nastąpi przetestowanie aplikacji ASP.NET z obsługą WIF, aby sprawdzić, czy dzienniki są rejestrowane.

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Aby przetestować aplikację ASP.NET z obsługą usługi WIF w celu pomyślnego śledzenia

1. Uruchom rozwiązanie, naciskając klawisz **F5** . Powinna zostać wyświetlona domyślna Strona główna ASP.NET i automatycznie uwierzytelniona przy użyciu nazwy użytkownika *Terry*, który jest domyślnym użytkownikiem zwracanym przez program Development STS.

2. Zamknij okno przeglądarki, a następnie przejdź do folderu **C:\LOGS** . Otwórz plik **C:\logs\WIF.XML** za pomocą edytora tekstów.

3. Zbadaj plik **WIF. XML** i sprawdź, czy zawiera on wpisy zaczynające się  **\<od E2ETraceEvent >** . Te ślady będą zawierać  **\<TraceRecord >** elementy z opisami działań śledzonych, takich jak **Walidacja obiektu SecurityToken**.
