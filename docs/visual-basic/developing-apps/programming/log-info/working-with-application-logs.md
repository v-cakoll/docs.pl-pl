---
title: Praca z dziennikami aplikacji w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40cad53cd9283a99a93cde79616151e77489e7bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="working-with-application-logs-in-visual-basic"></a>Praca z dziennikami aplikacji w Visual Basic
`My.Applicaton.Log` i `My.Log` obiektów ułatwiają zapisywane do dzienników rejestrowanie i informacje o śledzeniu.  
  
## <a name="how-messages-are-logged"></a>Jak komunikaty są rejestrowane.  
 Po raz pierwszy, ważność komunikatu jest wyewidencjonowany z <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości dziennika <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości. Przez domyślne tylko komunikaty o ważności "Informacje" i wyższe są przekazywane do obiektów nasłuchujących śledzenia, określona w dzienniku `TraceListener` kolekcji. Następnie każdego odbiornika porównuje ważność komunikatu do obiektu nasłuchującego <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości. Jeśli ważność komunikatu jest wystarczająco duża, odbiornika zapisuje wychodzących wiadomości.  
  
 Na poniższym diagramie przedstawiono, jak komunikat zapisane `WriteEntry` metody jest przekazywane do `WriteLine` obiekty nasłuchujące śledzenia metody dziennika:  
  
 ![Wywołanie Mój dzienniku](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 Zachowanie dziennika oraz obiekty nasłuchujące śledzenia można zmienić, zmieniając pliku konfiguracji aplikacji. Na poniższym diagramie przedstawiono związek między częściami dziennika i pliku konfiguracji.  
  
 ![Mój dzienniku konfiguracji](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>Gdzie komunikaty są rejestrowane.  
 Jeśli zestaw nie ma konfiguracji pliku, `My.Application.Log` i `My.Log` obiektów zapisywania danych wyjściowych debugowania aplikacji (za pośrednictwem <xref:System.Diagnostics.DefaultTraceListener> klasy). Ponadto `My.Application.Log` obiekt zapisuje do pliku dziennika zestawu (za pośrednictwem <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy), podczas `My.Log` obiektu zapisuje dane wyjściowe strony sieci Web platformy ASP.NET (za pośrednictwem <xref:System.Web.WebPageTraceListener> klasy).  
  
 Można wyświetlić danych wyjściowych debugowania w programie Visual Studio **dane wyjściowe** okno podczas uruchamiania aplikacji w trybie debugowania. Można otworzyć **dane wyjściowe** okna, kliknij przycisk **debugowania** element menu, wskaż **systemu Windows**, a następnie kliknij przycisk **dane wyjściowe**. W **dane wyjściowe** wybierz **debugowania** z **Pokaż dane wyjściowe z** pole.  
  
 Domyślnie `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika. Można uzyskać ścieżki z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> właściwość <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu. Format tej ścieżki jest następujący:  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 Typowa wartość dla `BasePath` ma następującą składnię.  
  
 C:\Documents and Settings\\`username`\Application danych  
  
 Wartości `CompanyName`, `ProductName`, i `ProductVersion` pochodzą z informacji o zestawie aplikacji. Nazwa pliku dziennika jest *AssemblyName*.log, gdzie *AssemblyName* to nazwa pliku zestawu bez rozszerzenia. Jeśli wymagane jest więcej niż jeden plik dziennika, takich jak, gdy oryginalny dziennik jest niedostępny podczas aplikacji podejmuje próbę zapisu w dzienniku, formularz dla nazwy pliku dziennika jest *AssemblyName*-*iteracji* log, gdzie `iteration` jest dodatnią `Integer`.  
  
 Zachowanie domyślne można przesłonić, dodawanie lub zmienianie plików konfiguracji komputera i aplikacji. Aby uzyskać więcej informacji, zobacz [wskazówki: zmiana gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).  
  
## <a name="configuring-log-settings"></a>Konfigurowanie ustawień dziennika  
 `Log` Obiekt ma domyślną implementację, która działa bez pliku konfiguracji aplikacji app.config. Aby zmienić ustawienia domyślne, należy dodać plik konfiguracji przy użyciu nowych ustawień. Aby uzyskać więcej informacji, zobacz [wskazówki: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 W sekcjach konfiguracji dziennika znajdują się w `<system.diagnostics>` węzła w głównym `<configuration>` węzła pliku app.config. Informacje w dzienniku jest zdefiniowany w kilka węzłów:  
  
-   Detektory `Log` obiektu są zdefiniowane w `<sources>` węzła o nazwie DefaultSource.  
  
-   Filtr ważność `Log` obiektu jest zdefiniowana w `<switches>` węzła o nazwie DefaultSwitch.  
  
-   Odbiorniki logu są zdefiniowane w `<sharedListeners>` węzła.  
  
 Przykłady `<sources>`, `<switches>`, i `<sharedListeners>` węzły są wyświetlane w następującym kodzie:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="DefaultSource" switchName="DefaultSwitch">  
        <listeners>  
          <add name="FileLog"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="DefaultSwitch" value="Information" />  
    </switches>  
    <sharedListeners>  
      <add name="FileLog"  
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,  
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"  
        initializeData="FileLogWriter"  
      />  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="changing-log-settings-after-deployment"></a>Zmiana ustawień dziennika po wdrożeniu  
 Podczas opracowywania aplikacji jego ustawienia konfiguracji są przechowywane w pliku app.config, jak pokazano w powyższych przykładach. Po wdrożeniu aplikacji, nadal można skonfigurować dziennika, edytując plik konfiguracji. W aplikacji systemu Windows, nazwa tego pliku jest *applicationName*. exe.config który musi znajdować się w tym samym folderze co plik wykonywalny. Dla aplikacji sieci Web jest to plik Web.config skojarzony z projektem.  
  
 Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji dla informacji o obiekcie. Aby uzyskać `Log` obiekt dzieje się to przy pierwszym `Log` uzyskać dostępu do obiektu. System sprawdza, czy plik konfiguracji tylko raz dla każdego określonego obiektu — aplikacja tworzy obiekt po raz pierwszy. Dlatego może być konieczne ponowne uruchomienie aplikacji, aby zmiany zaczęły obowiązywać.  
  
 We wdrożonej aplikacji Włącz opcję śledzenia kod przy ponownej konfiguracji przełącznika obiektów przed uruchomieniem aplikacji. Zazwyczaj wiąże się to Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponowne uruchomienie aplikacji.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Należy rozważyć podczas zapisywania danych w dzienniku:  
  
-   **Unikaj przeciek informacje o użytkowniku.** Upewnij się, że wpisy z aplikacji tylko zatwierdzone informacji w dzienniku. Na przykład może być możliwa do dziennika aplikacji, które zawierają nazwy użytkowników, ale nie hasło użytkownika.  
  
-   **Zabezpieczyć lokalizacje dziennika.** Wszelkie dziennika, który zawiera potencjalnie wrażliwe informacje powinny być przechowywane w bezpiecznej lokalizacji.  
  
-   **Należy unikać mylących informacji.** Ogólnie rzecz biorąc aplikacji należy zweryfikować wszystkie dane wprowadzane przez użytkownika przed użyciem tych danych. Obejmuje to zapisywanie danych w dzienniku aplikacji.  
  
-   **Unikaj "odmowa usługi".** Jeśli aplikacja zapisuje zbyt dużej ilości informacji w dzienniku, może to wypełnienie dziennika lub ułatwić znajdowanie trudne ważne informacje.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
