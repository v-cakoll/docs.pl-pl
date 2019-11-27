---
title: filtrowanie danych wyjściowych elementu My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353592"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Wskazówki: filtrowanie danych wyjściowych My.Application.Log (Visual Basic)

W tym instruktażu pokazano, jak zmienić domyślne filtrowanie dzienników dla obiektu `My.Application.Log`, aby kontrolować, jakie informacje są przesyłane z obiektu `Log` do detektorów i jakie informacje są zapisywane przez odbiorniki. Zachowanie rejestrowania można zmienić nawet po skompilowaniu aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.

## <a name="getting-started"></a>Wprowadzenie

Każdy komunikat, który `My.Application.Log` zapisuje, ma skojarzony poziom ważności, którego mechanizmy filtrowania używają do kontrolowania danych wyjściowych dziennika. Ta przykładowa aplikacja używa metod `My.Application.Log`, aby napisać kilka komunikatów dziennika z różnymi poziomami ważności.

#### <a name="to-build-the-sample-application"></a>Aby skompilować aplikację przykładową

1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows.

2. Dodaj przycisk o nazwie Button1 do formularza Form1.

3. W obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> dla Button1 Dodaj następujący kod:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Uruchom aplikację w debugerze.

5. Naciśnij pozycję **Button1**.

     Aplikacja zapisuje następujące informacje w danych wyjściowych debugowania i pliku dziennika aplikacji.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Zamknij aplikację.

     Aby uzyskać informacje na temat sposobu wyświetlania okna danych wyjściowych debugowania aplikacji, zobacz [okno dane wyjściowe](/visualstudio/ide/reference/output-window). Aby uzyskać informacje na temat lokalizacji pliku dziennika aplikacji, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Domyślnie aplikacja opróżnia plik dziennika danych wyjściowych po zamknięciu aplikacji.

     W powyższym przykładzie drugie wywołanie metody <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> i wywołanie metody <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> generuje dane wyjściowe dziennika, podczas gdy pierwsze i ostatnie wywołania metody `WriteEntry`. Wynika to z faktu, że poziomy ważności `WriteEntry` i `WriteException` to "informacje" i "błąd", które są dozwolone przez domyślne filtrowanie dzienników obiektu `My.Application.Log`. Jednak zdarzenia z poziomami ważności "Start" i "Stop" uniemożliwiają tworzenie danych wyjściowych dziennika.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrowanie dla wszystkich odbiorników my. Application. log

Obiekt `My.Application.Log` używa <xref:System.Diagnostics.SourceSwitch> o nazwie `DefaultSwitch` do kontrolowania, które komunikaty są przekazywane z metod `WriteEntry` i `WriteException` do detektorów dzienników. `DefaultSwitch` można skonfigurować w pliku konfiguracyjnym aplikacji, ustawiając jego wartość na jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia. Wartością domyślną jest "informacje".

W tej tabeli przedstawiono poziom ważności wymagany dla dziennika w celu zapisania komunikatu do odbiorników z uwzględnieniem konkretnego ustawienia `DefaultSwitch`.

|DefaultSwitch wartość|Ważność komunikatu jest wymagana dla danych wyjściowych|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` lub `Error`|
|`Warning`|`Critical`, `Error`lub `Warning`|
|`Information`|`Critical`, `Error`, `Warning`lub `Information`|
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`lub `Verbose`|
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`lub `Transfer`|
|`All`|Dozwolone są wszystkie komunikaty.|
|`Off`|Wszystkie komunikaty są blokowane.|

> [!NOTE]
> Metody `WriteEntry` i `WriteException` mają Przeciążenie, które nie określają poziomu ważności. Niejawny poziom ważności dla przeciążenia `WriteEntry` to "informacje" i niejawny poziom ważności dla przeciążenia `WriteException` to "Error".

W tej tabeli objaśniono dane wyjściowe dziennika pokazane w poprzednim przykładzie: z domyślnym ustawieniem `DefaultSwitch` "informacje", tylko drugie wywołanie metody `WriteEntry` i wywołanie metody `WriteException` powoduje wygenerowanie danych wyjściowych dziennika.

#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia aktywności

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     —lub—

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź sekcję `<switches>`, która znajduje się w sekcji `<system.diagnostics>`, która znajduje się w sekcji `<configuration>` najwyższego poziomu.

3. Znajdź element, który dodaje `DefaultSwitch` do kolekcji przełączników. Powinien wyglądać podobnie do tego elementu:

     `<add name="DefaultSwitch" value="Information" />`

4. Zmień wartość atrybutu `value` na "ActivityTracing".

5. Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:

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

7. Naciśnij pozycję **Button1**.

     Aplikacja zapisuje następujące informacje w danych wyjściowych debugowania aplikacji i pliku dziennika:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Zamknij aplikację.

9. Zmień wartość atrybutu `value` z powrotem na "informacje".

    > [!NOTE]
    > Ustawienie przełącznika `DefaultSwitch` kontroluje tylko `My.Application.Log`. Nie zmienia to sposobu działania klas .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType>.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Indywidualne filtrowanie dla odbiorników my. Application. log

W poprzednim przykładzie pokazano, jak zmienić filtrowanie dla wszystkich `My.Application.Log` danych wyjściowych. Ten przykład ilustruje sposób filtrowania poszczególnych odbiorników dziennika. Domyślnie aplikacja ma dwa detektory, które zapisują w danych wyjściowych debugowania aplikacji i pliku dziennika.

Plik konfiguracji steruje zachowaniem detektorów dzienników, umożliwiając każdemu z nich filtr, który jest podobny do przełącznika dla `My.Application.Log`. Odbiornik dziennika będzie wyprowadzał komunikat tylko wtedy, gdy ważność komunikatu jest dozwolona zarówno przez `DefaultSwitch` dziennika, jak i filtr odbiornika dzienników.

W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego odbiornika debugowania i dodać go do obiektu `Log`. Domyślny odbiornik debugowania powinien zostać usunięty z obiektu `Log`, więc jest jasne, że komunikaty debugowania pochodzą z nowego odbiornika debugowania.

#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia działania

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \-lub-

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań**. Wybierz pozycję **Otwórz**.

3. Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource", który znajduje się w sekcji `<sources>`. Sekcja `<sources>` znajduje się poniżej sekcji `<system.diagnostics>`, w sekcji `<configuration>` najwyższego poziomu.

4. Dodaj ten element do sekcji `<listeners>`:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Znajdź sekcję `<sharedListeners>` w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.

6. Dodaj ten element do `<sharedListeners>` sekcji:

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

     Filtr <xref:System.Diagnostics.EventTypeFilter> przyjmuje jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia jako atrybut `initializeData`.

7. Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:

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

9. Naciśnij pozycję **Button1**.

     Aplikacja zapisuje następujące informacje w pliku dziennika aplikacji:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Aplikacja zapisuje mniej informacji do danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowanie.

     `Default Error   2   Error`

10. Zamknij aplikację.

Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: tworzenie odbiorców dzienników niestandardowych](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przełączniki śledzenia](../../../../framework/debug-trace-profile/trace-switches.md)
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
