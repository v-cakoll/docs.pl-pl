---
title: Filtrowanie danych wyjściowych my. Application. log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: af1dc3e1ce22112d76ad566873f40c1c2ac05c9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968687"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Przewodnik: Filtrowanie danych wyjściowych my. Application. log (Visual Basic)
W tym instruktażu pokazano, jak zmienić domyślne filtrowanie dzienników dla `My.Application.Log` obiektu, aby kontrolować, jakie informacje są przesyłane `Log` z obiektu do odbiorników i jakie informacje są zapisywane przez odbiorniki. Zachowanie rejestrowania można zmienić nawet po skompilowaniu aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Każdy komunikat, `My.Application.Log` który zapisuje, ma skojarzony poziom ważności, którego mechanizmy filtrowania używają do kontrolowania danych wyjściowych dziennika. Ta przykładowa aplikacja `My.Application.Log` używa metod do pisania kilku komunikatów dziennika z różnymi poziomami ważności.  
  
#### <a name="to-build-the-sample-application"></a>Aby skompilować aplikację przykładową  
  
1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows.  
  
2. Dodaj przycisk o nazwie Button1 do formularza Form1.  
  
3. W programie obsługi zdarzeń dla Button1 Dodaj następujący kod: <xref:System.Windows.Forms.Control.Click>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4. Uruchom aplikację w debugerze.  
  
5. Naciśnij pozycję **Button1**.  
  
     Aplikacja zapisuje następujące informacje w danych wyjściowych debugowania i pliku dziennika aplikacji.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6. Zamknij aplikację.  
  
     Aby uzyskać informacje na temat sposobu wyświetlania okna danych wyjściowych debugowania aplikacji, zobacz [okno dane wyjściowe](/visualstudio/ide/reference/output-window). Aby uzyskać informacje na temat lokalizacji pliku dziennika aplikacji, zobacz [Przewodnik: Ustalanie, gdzie my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)zapisuje informacje.  
  
    > [!NOTE]
    > Domyślnie aplikacja opróżnia plik dziennika danych wyjściowych po zamknięciu aplikacji.  
  
     W powyższym przykładzie drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metody i wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> metody generuje dane wyjściowe dziennika, podczas gdy pierwsze `WriteEntry` i ostatnie wywołania metody nie. Wynika to z faktu, że `WriteEntry` poziomy `WriteException` ważności i są "informacje" i "błąd", `My.Application.Log` które są dozwolone przez domyślne filtrowanie dzienników obiektu. Jednak zdarzenia z poziomami ważności "Start" i "Stop" uniemożliwiają tworzenie danych wyjściowych dziennika.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrowanie dla wszystkich odbiorników my. Application. log  
 `WriteException` `WriteEntry` Obiekt używa nazwy do`DefaultSwitch` kontrolowania, które wiadomości są przekazywane z i metod do odbiorników dziennika. <xref:System.Diagnostics.SourceSwitch> `My.Application.Log` Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jego wartość na jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia. Wartością domyślną jest "informacje".  
  
 W tej tabeli przedstawiono poziom ważności wymagany dla dziennika w celu zapisania komunikatu do odbiorników z uwzględnieniem konkretnego `DefaultSwitch` ustawienia.  
  
|DefaultSwitch wartość|Ważność komunikatu jest wymagana dla danych wyjściowych|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` lub `Error`|  
|`Warning`|`Critical`, `Error`lub`Warning`|  
|`Information`|`Critical`, `Error`, `Warning`lub`Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, lub`Information``Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, lub`Resume``Transfer`|  
|`All`|Dozwolone są wszystkie komunikaty.|  
|`Off`|Wszystkie komunikaty są blokowane.|  
  
> [!NOTE]
> Metody `WriteEntry` i`WriteException` każdy mają Przeciążenie, które nie określają poziomu ważności. Niejawny poziom `WriteEntry` ważności przeciążenia to "informacje" i niejawny poziom `WriteException` ważności przeciążenia to "Error".  
  
 W tej tabeli objaśniono dane wyjściowe dziennika pokazane w poprzednim przykładzie: z `DefaultSwitch` domyślnym ustawieniem "informacje", tylko drugie wywołanie `WriteEntry` metody `WriteException` i wywołanie metody generowanie danych wyjściowych dziennika.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia aktywności  
  
1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     Jeśli nie ma pliku App. config:  
  
    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.  
  
    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.  
  
    3. Kliknij przycisk **Dodaj**.  
  
2. Znajdź sekcję znajdującą się `<system.diagnostics>` w sekcji, która znajduje się w sekcji najwyższego poziomu `<configuration>`. `<switches>`  
  
3. Znajdź element, który dodaje `DefaultSwitch` do kolekcji przełączników. Powinien wyglądać podobnie do tego elementu:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4. Zmień wartość `value` atrybutu na "ActivityTracing".  
  
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
  
9. Zmień wartość `value` atrybutu z powrotem na "informacje".  
  
    > [!NOTE]
    > `DefaultSwitch` Ustawienia`My.Application.Log`przełącznika. Nie zmienia to sposobu zachowania .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> klas.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Indywidualne filtrowanie dla odbiorników my. Application. log  
 W poprzednim przykładzie pokazano, jak zmienić filtrowanie dla wszystkich `My.Application.Log` danych wyjściowych. Ten przykład ilustruje sposób filtrowania poszczególnych odbiorników dziennika. Domyślnie aplikacja ma dwa detektory, które zapisują w danych wyjściowych debugowania aplikacji i pliku dziennika.  
  
 Plik konfiguracji steruje zachowaniem detektorów dzienników, umożliwiając każdemu z nich filtr, który jest podobny do przełącznika `My.Application.Log`. Odbiornik dziennika będzie wyprowadzał komunikat tylko wtedy, gdy ważność komunikatu jest dozwolona zarówno w przypadku filtru, `DefaultSwitch` jak i dla filtra odbiornika dzienników.  
  
 W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego odbiornika debugowania i dodać go do `Log` obiektu. Domyślny odbiornik debugowania powinien zostać usunięty z `Log` obiektu, dlatego jest jasne, że komunikaty debugowania pochodzą z nowego odbiornika debugowania.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenia działania  
  
1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     Jeśli nie ma pliku App. config:  
  
    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.  
  
    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.  
  
    3. Kliknij przycisk **Dodaj**.  
  
2. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań**. Wybierz pozycję **Otwórz**.  
  
3. Znajdź sekcję w sekcji z `name` atrybutem `<sources>` "DefaultSource", który znajduje się poniżej sekcji. `<source>` `<listeners>` Sekcja znajduje się `<system.diagnostics>` poniżej sekcji w sekcji najwyższego poziomu `<configuration>`. `<sources>`  
  
4. Dodaj ten element do `<listeners>` sekcji:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5. `<sharedListeners>` Znajdź sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .  
  
6. Dodaj ten element do tej `<sharedListeners>` sekcji:  
  
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
  
     Filtr przyjmuje jedną <xref:System.Diagnostics.SourceLevels> z wartości wyliczenia jako `initializeData` atrybut. <xref:System.Diagnostics.EventTypeFilter>  
  
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

- [Przewodnik: Ustalanie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: Tworzenie niestandardowych odbiorników dziennika](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Instrukcje: Zapisuj komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przełączniki śledzenia](../../../../framework/debug-trace-profile/trace-switches.md)
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
