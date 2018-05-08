---
title: Śledzenie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: f4ce25efae0e42fa7c95ce5dffe8da8e31db05a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-tracing"></a>Śledzenie przepływu pracy
Śledzenie przepływu pracy daje możliwość przechwytywania informacji diagnostycznych za pomocą obiektów nasłuchujących śledzenia .NET Framework. Śledzenie można włączone, jeśli zostanie wykryty problem z aplikacją i następnie wyłączone ponownie po usunięciu problemu. Istnieją dwa sposoby można włączyć śledzenie debugowania dla przepływów pracy. Można skonfigurować przy użyciu przeglądarki śledzenia zdarzeń lub użyć <xref:System.Diagnostics> do wysyłania zdarzeń śledzenia w pliku.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Włączanie debugowania śledzenia w funkcji ETW  
 Aby włączyć śledzenie za pomocą funkcji ETW, Włącz kanału debugowania w Podglądzie zdarzeń:  
  
1.  Przejdź do analityczne i debugowania węzła Dzienniki w Podglądzie zdarzeń.  
  
2.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **aplikacji -> Podgląd zdarzeń i dzienników usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **aplikacji serwerowych aplikacji** i wybierz **Widok -> Pokaż analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**.  
  
3.  Podczas debugowania działania przepływu pracy i ślady są emitowane do kanału debugowania ETW, można można wyświetlić w Podglądzie zdarzeń. Przejdź do **aplikacji -> Podgląd zdarzeń i dzienników usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Odśwież**.  
  
4.  Domyślny rozmiar buforu śledzenia analitycznego jest tylko 4 kilobajtów (KB); Zaleca się zwiększenie rozmiaru 32 KB. Aby to zrobić, wykonaj następujące czynności.  
  
    1.  Uruchom następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Zmień \<bufferSize > wartość w pliku Windows.ApplicationServer.Applications.man 32 znaków.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  Uruchom następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Jeśli używasz platformy .NET Framework 4 Client Profile, najpierw należy zarejestrować ETW manifest, uruchamiając następujące polecenie z katalogu programu .NET Framework 4: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Włączanie debugowania śledzenia przy użyciu System.Diagnostics  
 Te odbiorniki można skonfigurować w pliku App.config aplikacji przepływu pracy lub w pliku Web.config dla usługi przepływu pracy. W tym przykładzie [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) jest skonfigurowany, aby zapisać informacje śledzenia do pliku MyTraceLog.txt w bieżącym katalogu.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
