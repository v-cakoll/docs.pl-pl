---
title: Śledzenie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 27e56933043c9eb955500cdd1c5bbd06cb33bde8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210896"
---
# <a name="workflow-tracing"></a>Śledzenie przepływu pracy
Śledzenie przepływu pracy pozwala do przechwytywania informacji diagnostycznych za pomocą obiektów nasłuchujących śledzenia .NET Framework. Śledzenie można włączone, jeśli zostanie wykryty problem z aplikacją i następnie ponownie wyłączona po problem został rozwiązany. Istnieją dwa sposoby, można włączyć śledzenie debugowania dla przepływów pracy. Możesz skonfigurować używanie przeglądarki danych śledzenia zdarzeń lub użyć <xref:System.Diagnostics> do wysyłania zdarzeń śledzenia w pliku.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Włączanie debugowania, śledzenie zdarzeń systemu Windows  
 Aby włączyć śledzenie za pomocą funkcji ETW, Włącz kanał debugowania w Podglądzie zdarzeń:  
  
1.  Przejdź do analityczne i debugowania dzienniki węzła w Podglądzie zdarzeń.  
  
2.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **aplikacje serwera aplikacji** i wybierz **Widok -> Pokaż analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**.  
  
3.  Podczas działania przepływu pracy debugowania i śledzenia są emitowane do kanału debugowania funkcji ETW, mogą być wyświetlane w Podglądzie zdarzeń. Przejdź do **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Odśwież**.  
  
4.  Domyślny rozmiar buforu śledzenia analitycznego jest tylko 4 kilobajtów (KB); zalecane jest, aby zwiększyć rozmiar na 32 KB. Aby to zrobić, wykonaj następujące czynności.  
  
    1.  Wykonaj następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Zmiana \<bufferSize > wartość w pliku Windows.ApplicationServer.Applications.man do 32.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  Wykonaj następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Jeśli używasz platformy .NET Framework 4 Client Profile, najpierw musisz się zarejestrować manifestu ETW, uruchamiając następujące polecenie z katalogu .NET Framework 4: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Włączanie debugowania śledzenia przy użyciu System.Diagnostics  
 Te detektorów można skonfigurować w pliku App.config aplikacji przepływu pracy lub w pliku Web.config dla usługi przepływu pracy. W tym przykładzie [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) jest skonfigurowany, aby zapisać informacje śledzenia do pliku MyTraceLog.txt w bieżącym katalogu.  
  
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
 [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
