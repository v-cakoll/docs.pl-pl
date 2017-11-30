---
title: "Filtrowanie danych wyjściowych My.Application.Log (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fd445227e0c8290ad63fccf807d6d7bdf43ccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>Wskazówki: filtrowanie danych wyjściowych My.Application.Log (Visual Basic)
W tym przewodniku przedstawiono sposób zmiany domyślnego dziennika filtrowania `My.Application.Log` obiekt, aby kontrolować, jakie informacje są przekazywane z `Log` obiektu odbiorniki i jakie informacje są zapisywane przez odbiorniki. Zachowanie rejestrowania można zmienić nawet po tworzenia aplikacji, ponieważ informacje o konfiguracji są przechowywane w pliku konfiguracji aplikacji.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Każdy komunikat, który `My.Application.Log` zapisy ma poziom ważności skojarzony, w których mechanizmy filtrowania umożliwia sterowanie wpisu w dzienniku. Ta przykładowa aplikacja korzysta `My.Application.Log` metod można zapisać kilka komunikaty dziennika z różne poziomy ważności.  
  
#### <a name="to-build-the-sample-application"></a>Do tworzenia przykładowej aplikacji  
  
1.  Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikacji systemu Windows.  
  
2.  Dodawanie przycisku o nazwie Button1 do Form1.  
  
3.  W <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla Button1, Dodaj następujący kod:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  Uruchom aplikację w debugerze.  
  
5.  Naciśnij klawisz **Button1**.  
  
     Aplikacja zapisuje następujące informacje do pliku wyjściowego i dziennika debugowania aplikacji.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Zamknij aplikację.  
  
     Aby uzyskać informacje o sposobie wyświetlania okno danych wyjściowych debugowania aplikacji, zobacz [okno danych wyjściowych](/visualstudio/ide/reference/output-window). Aby uzyskać informacje o lokalizacji pliku dziennika aplikacji, zobacz [wskazówki: Ustalanie gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Domyślnie aplikacja Opróżnia dane wyjściowe pliku dziennika, po zamknięciu aplikacji.  
  
     W przykładzie powyżej, drugie wywołanie <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> — metoda i wywołania w celu <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> generuje danych wyjściowych dziennika podczas wywołania imię i nazwisko `WriteEntry` — metoda nie. Jest to spowodowane poziomy ważności `WriteEntry` i `WriteException` "Informacje" i "Błąd", które są dozwolone w `My.Application.Log` obiektu domyślne dziennika filtrowania. Jednak zdarzenia z poziomami ważności "Start" i "Stop" nie generuje danych wyjściowych dziennika.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtrowanie w przypadku wszystkich odbiorników My.Application.Log  
 `My.Application.Log` Obiekt używa <xref:System.Diagnostics.SourceSwitch> o nazwie `DefaultSwitch` kontrolowanie, które komunikaty go przekazuje z `WriteEntry` i `WriteException` metody odbiorniki dzienników. Można skonfigurować `DefaultSwitch` w pliku konfiguracyjnym aplikacji przez ustawienie jej wartość na jedną z <xref:System.Diagnostics.SourceLevels> wartości wyliczenia. Domyślna wartość to "Informacje".  
  
 W poniższej tabeli przedstawiono poziom ważności wymagane dla dziennika do zapisu komunikatu odbiorników, podane określonego `DefaultSwitch` ustawienie.  
  
|Wartość DefaultSwitch|Ważność komunikatu wymagane dla danych wyjściowych|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical`lub`Error`|  
|`Warning`|`Critical`, `Error`, lub`Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, lub`Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, lub`Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, lub`Transfer`|  
|`All`|Wszystkie komunikaty są dozwolone.|  
|`Off`|Wszystkie komunikaty są zablokowane.|  
  
> [!NOTE]
>  `WriteEntry` i `WriteException` metody mają przeciążenia, która nie określa poziom ważności. Poziom ważności niejawne `WriteEntry` jest przeciążenie "Informacje", a poziom ważności niejawne `WriteException` jest przeciążenie "Error".  
  
 W następującej tabeli opisano w poprzednim przykładzie wpisu w dzienniku: przy użyciu domyślnego `DefaultSwitch` ustawienie "Informacje", tylko drugie wywołanie `WriteEntry` — metoda i wywołania w celu `WriteException` danych wyjściowych metody produktu dziennika.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Aby rejestrować zdarzenia śledzenia tylko działania  
  
1.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz **Otwórz**.  
  
     —lub—  
  
     Jeśli plik app.config, nie istnieje:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Zlokalizuj `<switches>` sekcję, co jest `<system.diagnostics>` sekcję, co jest najwyższego poziomu `<configuration>` sekcji.  
  
3.  Znajdź element, który dodaje `DefaultSwitch` do kolekcji parametrów. Powinien być podobny do tego elementu:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Zmień wartość `value` atrybutu "ActivityTracing".  
  
5.  Zawartość pliku app.config powinny być podobne do następującego kodu XML:  
  
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
  
     Aplikacja zapisuje następujące informacje w pliku danych wyjściowych i dziennika debugowania aplikacji:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Zamknij aplikację.  
  
9. Zmień wartość `value` atrybutu "Informacje".  
  
    > [!NOTE]
    >  `DefaultSwitch` Przełącznika tylko formanty ustawienie `My.Application.Log`. Nie zmienia sposób [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> zachowanie klasy.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Poszczególne filtrowanie w przypadku odbiorników My.Application.Log  
 Poprzednim przykładzie pokazano, jak zmienić ustawienia filtrowania dla wszystkich `My.Application.Log` danych wyjściowych. W tym przykładzie przedstawiono sposób filtrowania odbiornik osobny dziennik. Domyślnie aplikacja ma dwa odbiorniki tego zapisu w danych wyjściowych debugowania aplikacji i pliku dziennika.  
  
 Plik konfiguracji steruje zachowaniem odbiorniki logu zezwalając każdej z nich ma filtr, który jest podobny do przełącznika dla `My.Application.Log`. Odbiornik dziennika dane wyjściowe obejmują wiadomości tylko wtedy, gdy ważność komunikatu jest dozwolony w obu dziennika `DefaultSwitch` i odbiornika dziennika filtru.  
  
 W tym przykładzie pokazano, jak skonfigurować filtrowanie dla nowego odbiornika debugowania i dodaj go do `Log` obiektu. Odbiornik debugowania domyślna powinna zostać usunięta z `Log` obiektu, więc jest jasne, czy komunikaty debugowania pochodzą z nowego odbiornika debugowania.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Do rejestrowania tylko działania śledzenia zdarzeń  
  
1.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     Jeśli plik app.config, nie istnieje:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań**. Wybierz **Otwórz**.  
  
3.  Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource", która znajduje się w `<sources>` sekcji. `<sources>` Znajduje się w sekcji `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
4.  Ten element, aby dodać `<listeners>` sekcji:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
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
  
     <xref:System.Diagnostics.EventTypeFilter> Filtru przyjmuje jeden z <xref:System.Diagnostics.SourceLevels> wyliczenia wartości jako jego `initializeData` atrybutu.  
  
7.  Zawartość pliku app.config powinny być podobne do następującego kodu XML:  
  
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
  
     Aplikacja zapisuje mniej informacje w danych wyjściowych debugowania aplikacji ze względu na bardziej restrykcyjne filtrowania.  
  
     `Default Error   2   Error`  
  
10. Zamknij aplikację.  
  
 Aby uzyskać więcej informacji na temat zmiany ustawień dziennika po wdrożeniu, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [Wskazówki: Tworzenie odbiorników logu niestandardowego](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Przełączniki śledzenia](../../../../framework/debug-trace-profile/trace-switches.md)  
 [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
