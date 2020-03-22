---
title: filtrowanie danych wyjściowych elementu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353592"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Wskazówki: filtrowanie danych wyjściowych My.Application.Log (Visual Basic)

W tym przewodniku pokazano, jak zmienić domyślne `My.Application.Log` filtrowanie dziennika dla obiektu, `Log` aby kontrolować, jakie informacje są przekazywane z obiektu do odbiorników i jakie informacje są zapisywane przez detektory. Zachowanie rejestrowania można zmienić nawet po zbudowaniu aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracyjnym aplikacji.

## <a name="getting-started"></a>Wprowadzenie

Każdy komunikat, który `My.Application.Log` pisze ma skojarzony poziom ważności, który mechanizmy filtrowania używać do kontrolowania danych wyjściowych dziennika. Ta przykładowa `My.Application.Log` aplikacja używa metod do zapisu kilku komunikatów dziennika o różnych poziomach ważności.

#### <a name="to-build-the-sample-application"></a>Aby utworzyć przykładową aplikację

1. Otwórz nowy projekt aplikacji systemu Windows visual basic.

2. Dodaj przycisk o nazwie Button1 do formularza1.

3. W <xref:System.Windows.Forms.Control.Click> programie obsługi zdarzeń dla Button1 dodaj następujący kod:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Uruchom aplikację w debugerze.

5. Naciśnij **przycisk1**.

     Aplikacja zapisuje następujące informacje do pliku wyjściowego debugowania i dziennika aplikacji.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Zamknij aplikację.

     Aby uzyskać informacje dotyczące sposobu wyświetlania okna wyjściowego debugowania aplikacji, zobacz [Okno wyjściowe](/visualstudio/ide/reference/output-window). Aby uzyskać informacje na temat lokalizacji pliku dziennika aplikacji, zobacz [Instruktaż: Określanie, gdzie my.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Domyślnie aplikacja opróżnia dane wyjściowe pliku dziennika po zamknięciu aplikacji.

     W powyższym przykładzie drugie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> wywołanie metody i <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> wywołanie metody daje dane wyjściowe dziennika, podczas gdy pierwsze i ostatnie wywołania `WriteEntry` metody nie. Jest to spowodowane poziom `WriteEntry` ważności `WriteException` i są "Informacje" i "Błąd", z `My.Application.Log` których oba są dozwolone przez domyślne filtrowanie dziennika obiektu. Jednak zdarzenia z poziomami ważności "Start" i "Stop" nie mogą wytwarzania danych wyjściowych dziennika.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrowanie dla wszystkich detektorów My.Application.Log

Obiekt `My.Application.Log` <xref:System.Diagnostics.SourceSwitch> używa `DefaultSwitch` nazwany do kontrolowania, które komunikaty przechodzi z `WriteEntry` i `WriteException` metody do detektorów dziennika. Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jego wartość na jedną z wartości wyliczenia. <xref:System.Diagnostics.SourceLevels> Domyślnie jego wartość to "Informacje".

W tej tabeli przedstawiono poziom ważności wymagany dla dziennika do zapisu wiadomości do odbiorników, biorąc pod uwagę określone `DefaultSwitch` ustawienie.

|Domyślna wartość przełącznika|Ważność wiadomości wymagana dla danych wyjściowych|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` lub `Error`|
|`Warning`|`Critical`, `Error`, lub`Warning`|
|`Information`|`Critical`, `Error` `Warning`, , lub`Information`|
|`Verbose`|`Critical`, `Error` `Warning`, `Information`, , lub`Verbose`|
|`ActivityTracing`|`Start`, `Stop` `Suspend`, `Resume`, , lub`Transfer`|
|`All`|Wszystkie wiadomości są dozwolone.|
|`Off`|Wszystkie wiadomości są zablokowane.|

> [!NOTE]
> I `WriteEntry` `WriteException` metody każdy ma przeciążenie, które nie określa poziomu ważności. Niejawny poziom ważności `WriteEntry` przeciążenia jest "Informacje", a poziom niejawnego ważności `WriteException` przeciążenia jest "Błąd".

W tej tabeli wyjaśniono dane wyjściowe `DefaultSwitch` dziennika pokazane w poprzednim przykładzie: `WriteEntry` z domyślnym `WriteException` ustawieniem "Informacje", tylko drugie wywołanie metody i wywołanie metody produkcji danych wyjściowych dziennika.

#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia aktywności

1. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.

     — lub —

     Jeśli nie ma pliku app.config:

    1. W menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Zlokalizuj sekcję, `<switches>` która znajduje się `<system.diagnostics>` w `<configuration>` sekcji najwyższego poziomu.

3. Znajdź element, `DefaultSwitch` który dodaje do kolekcji przełączników. Powinien wyglądać podobnie do tego elementu:

     `<add name="DefaultSwitch" value="Information" />`

4. Zmień wartość atrybutu na `value` "ActivityTracing".

5. Zawartość pliku app.config powinna być podobna do następującej opcji XML:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. Uruchom aplikację w debugerze.

7. Naciśnij **przycisk1**.

     Aplikacja zapisuje następujące informacje do pliku wyjściowego i dziennika debugowania aplikacji:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Zamknij aplikację.

9. Zmień wartość atrybutu `value` z powrotem na "Informacje".

    > [!NOTE]
    > Ustawienie `DefaultSwitch` przełącznika `My.Application.Log`steruje tylko . Nie zmienia zachowania .NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> Framework <xref:System.Diagnostics.Debug?displayProperty=nameWithType> i klas.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Indywidualne filtrowanie dla detektorów My.Application.Log

W poprzednim przykładzie pokazano, jak `My.Application.Log` zmienić filtrowanie dla wszystkich danych wyjściowych. W tym przykładzie pokazano, jak filtrować odbiornika dziennika poszczególnych. Domyślnie aplikacja ma dwa odbiorniki, które zapisują do danych wyjściowych debugowania aplikacji i pliku dziennika.

Plik konfiguracyjny steruje zachowaniem detektorów dziennika, zezwalając każdemu z nich `My.Application.Log`na filtr, który jest podobny do przełącznika dla . Odbiornik dziennika będzie wysyłać komunikat tylko wtedy, gdy ważność wiadomości jest `DefaultSwitch` dozwolone zarówno przez dziennik i filtr odbiornika dziennika.

W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego `Log` odbiornika debugowania i dodać go do obiektu. Domyślny odbiornik debugowania powinny `Log` zostać usunięte z obiektu, więc jest jasne, że komunikaty debugowania pochodzą z nowego odbiornika debugowania.

#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia aktywności

1. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.

     \-lub-

     Jeśli nie ma pliku app.config:

    1. W menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań**. Wybierz **pozycję Otwórz**.

3. Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource", `<sources>` który znajduje się w sekcji. Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.

4. Dodaj ten element `<listeners>` do sekcji:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.

6. Dodaj ten element `<sharedListeners>` do tej sekcji:

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     Filtr <xref:System.Diagnostics.EventTypeFilter> przyjmuje jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia jako jego `initializeData` atrybut.

7. Zawartość pliku app.config powinna być podobna do następującej opcji XML:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. Uruchom aplikację w debugerze.

9. Naciśnij **przycisk1**.

     Aplikacja zapisuje następujące informacje do pliku dziennika aplikacji:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Aplikacja zapisuje mniej informacji do danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowanie.

     `Default Error   2   Error`

10. Zamknij aplikację.

Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Zobacz też

- [Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: tworzenie odbiorców dzienników niestandardowych](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przełączniki śledzenia](../../../../framework/debug-trace-profile/trace-switches.md)
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
