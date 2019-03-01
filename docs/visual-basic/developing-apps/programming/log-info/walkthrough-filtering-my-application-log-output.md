---
title: Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 9f1f0efd6190ac0ced0f83db747e3c4eb81c4975
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978322"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Przewodnik: Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)
W tym instruktażu pokazano, jak zmienić domyślny dziennik filtrowanie `My.Application.Log` obiektu, aby kontrolować, jakie informacje są przekazywane z `Log` obiekt do odbiorników i jakie informacje są zapisywane przez odbiorniki. Możesz zmienić sposób rejestrowania, nawet po zakończeniu tworzenia aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Każdy komunikat, który `My.Application.Log` zapisów ma poziom ważności skojarzone, który mechanizmy filtrowania użyć, aby kontrolować dane wyjściowe dziennika. Ta przykładowa aplikacja używa `My.Application.Log` metod można zapisać kilka rejestrowania komunikatów za pomocą różne poziomy ważności.  
  
#### <a name="to-build-the-sample-application"></a>Do tworzenia przykładowej aplikacji  
  
1.  Otwórz nowy projekt aplikacji Windows Visual Basic.  
  
2.  Dodaj przycisk o nazwie Button1 do formularza Form1.  
  
3.  W <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla Button1, Dodaj następujący kod:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4.  Uruchom aplikację w debugerze.  
  
5.  Naciśnij klawisz **Button1**.  
  
     Aplikacja zapisuje następujące informacje do pliku danych wyjściowych i dzienników debugowania aplikacji.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Zamknij aplikację.  
  
     Aby uzyskać informacje o sposobie wyświetlania okna danych wyjściowych debugowania aplikacji, zobacz [okno danych wyjściowych](/visualstudio/ide/reference/output-window). Aby uzyskać informacje o lokalizacji pliku dziennika aplikacji, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Domyślnie aplikacja czyści dane wyjściowe pliku dziennika, po zamknięciu aplikacji.  
  
     W przykładzie powyżej, drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> metody i wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> generuje dane wyjściowe dziennika podczas wywołania imię i nazwisko `WriteEntry` metody nie obsługują. Jest to spowodowane poziomy ważności `WriteEntry` i `WriteException` "Informacje" i "Error", które są dozwolone przez `My.Application.Log` obiektu domyślne filtrowanie dziennika. Jednak zdarzeń za pomocą "Start" i "Zatrzymaj" poziomy ważności nie generuje danych wyjściowych dzienników.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrowanie wszystkich odbiorników My.Application.Log  
 `My.Application.Log` Obiektu używa <xref:System.Diagnostics.SourceSwitch> o nazwie `DefaultSwitch` kontrolowanie komunikaty go — dostęp próbny od `WriteEntry` i `WriteException` metody odbiorniki logu. Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji, ustawiając jej wartość na jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia. Domyślna wartość to "Informacje".  
  
 W poniższej tabeli przedstawiono poziom ważności, wymaganych do dziennika zapisać komunikat do odbiorników, biorąc pod uwagę określonego `DefaultSwitch` ustawienie.  
  
|Wartość DefaultSwitch|Ważność wiadomości wymagane dla danych wyjściowych|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` lub `Error`|  
|`Warning`|`Critical`, `Error`, lub `Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, lub `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, lub `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, lub `Transfer`|  
|`All`|Wszystkie komunikaty są dozwolone.|  
|`Off`|Wszystkie komunikaty są blokowane.|  
  
> [!NOTE]
>  `WriteEntry` i `WriteException` metody mają przeciążenia, które nie określa poziom ważności. Poziom ważności niejawne `WriteEntry` przeciążenie jest "Informacje", a poziom ważności niejawne `WriteException` przeciążenie to "Error".  
  
 W następującej tabeli opisano w poprzednim przykładzie dane wyjściowe dziennika: przy użyciu domyślnego `DefaultSwitch` ustawienie "Informacje", tylko drugie wywołanie `WriteEntry` metody i wywołanie `WriteException` dane wyjściowe dziennika produktu metody.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować zdarzenia śledzenia tylko działania  
  
1.  Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz **Otwórz**.  
  
     —lub—  
  
     Jeśli nie ma żadnego pliku app.config:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Znajdź `<switches>` sekcji, która znajduje się w `<system.diagnostics>` sekcji, która znajduje się w najwyższego poziomu `<configuration>` sekcji.  
  
3.  Znajdź element, który dodaje `DefaultSwitch` w kolekcji parametrów. Powinny one wyglądać podobnie do tego elementu:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Zmień wartość właściwości `value` atrybutu "ActivityTracing".  
  
5.  Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:  
  
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
  
6.  Uruchom aplikację w debugerze.  
  
7.  Naciśnij klawisz **Button1**.  
  
     Aplikacja zapisuje następujące informacje do pliku danych wyjściowych i dzienników debugowania aplikacji:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Zamknij aplikację.  
  
9. Zmień wartość właściwości `value` atrybutu "Informacje".  
  
    > [!NOTE]
    >  `DefaultSwitch` Przełącz ustawienie określa `My.Application.Log`. Nie zmienia sposób, w jaki [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> zachowują się klasy.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Osoba filtrowanie odbiorników My.Application.Log  
 Poprzedni przykład pokazuje, jak zmienić ustawienia filtrowania dla wszystkich `My.Application.Log` danych wyjściowych. W tym przykładzie pokazano, jak filtrować odbiornik osobny dziennik. Domyślnie aplikacja ma dwa odbiorniki ten zapis w danych wyjściowych debugowania aplikacji i plik dziennika.  
  
 Plik konfiguracyjny steruje zachowaniem odbiorniki logu, umożliwiając każdej z nich ma filtr, który jest podobny do przełącznika dla `My.Application.Log`. Odbiornik dziennika wiadomość wyjściową, tylko wtedy, gdy ważność komunikatu jest dozwolony w obu dziennika `DefaultSwitch` i Filtruj odbiornika dziennika.  
  
 W tym przykładzie pokazano, jak skonfigurować filtrowanie, aby uzyskać nowy odbiornik debugowania i dodać go do `Log` obiektu. Odbiornik debugowania domyślne powinny zostać usunięte z `Log` obiektu, dzięki czemu jest jasne, że komunikaty debugowania pochodzą z nowy odbiornik debugowania.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować tylko zdarzenia śledzenie aktywności  
  
1.  Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     Jeśli nie ma żadnego pliku app.config:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań**. Wybierz **Otwórz**.  
  
3.  Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource", która jest w trakcie `<sources>` sekcji. `<sources>` Znajduje się w sekcji `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
4.  Dodaj ten element, aby `<listeners>` sekcji:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
6.  Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
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
  
     <xref:System.Diagnostics.EventTypeFilter> Filtr ma jedną z <xref:System.Diagnostics.SourceLevels> wyliczenia wartości zgodnie z jego `initializeData` atrybutu.  
  
7.  Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:  
  
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
  
8.  Uruchom aplikację w debugerze.  
  
9. Naciśnij klawisz **Button1**.  
  
     Aplikacja zapisuje następujące informacje w pliku dziennika aplikacji:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     Aplikacja zapisuje mniej informacji debugowania aplikacji w danych wyjściowych ze względu na bardziej restrykcyjne filtrowania.  
  
     `Default Error   2   Error`  
  
10. Zamknij aplikację.  
  
 Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Zobacz także
- [Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: Tworzenie odbiorników logu niestandardowego](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Instrukcje: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przełączniki śledzenia](../../../../framework/debug-trace-profile/trace-switches.md)
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
