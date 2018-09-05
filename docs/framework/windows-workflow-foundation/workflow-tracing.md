---
title: Śledzenie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 27e56933043c9eb955500cdd1c5bbd06cb33bde8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558286"
---
# <a name="workflow-tracing"></a><span data-ttu-id="4e5f1-102">Śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4e5f1-102">Workflow Tracing</span></span>
<span data-ttu-id="4e5f1-103">Śledzenie przepływu pracy pozwala do przechwytywania informacji diagnostycznych za pomocą obiektów nasłuchujących śledzenia .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="4e5f1-104">Śledzenie można włączone, jeśli zostanie wykryty problem z aplikacją i następnie ponownie wyłączona po problem został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="4e5f1-105">Istnieją dwa sposoby, można włączyć śledzenie debugowania dla przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="4e5f1-106">Możesz skonfigurować używanie przeglądarki danych śledzenia zdarzeń lub użyć <xref:System.Diagnostics> do wysyłania zdarzeń śledzenia w pliku.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="4e5f1-107">Włączanie debugowania, śledzenie zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4e5f1-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="4e5f1-108">Aby włączyć śledzenie za pomocą funkcji ETW, Włącz kanał debugowania w Podglądzie zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="4e5f1-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1.  <span data-ttu-id="4e5f1-109">Przejdź do analityczne i debugowania dzienniki węzła w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2.  <span data-ttu-id="4e5f1-110">W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="4e5f1-111">Kliknij prawym przyciskiem myszy **aplikacje serwera aplikacji** i wybierz **Widok -> Pokaż analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="4e5f1-112">Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3.  <span data-ttu-id="4e5f1-113">Podczas działania przepływu pracy debugowania i śledzenia są emitowane do kanału debugowania funkcji ETW, mogą być wyświetlane w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="4e5f1-114">Przejdź do **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="4e5f1-115">Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Odśwież**.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4.  <span data-ttu-id="4e5f1-116">Domyślny rozmiar buforu śledzenia analitycznego jest tylko 4 kilobajtów (KB); zalecane jest, aby zwiększyć rozmiar na 32 KB.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="4e5f1-117">Aby to zrobić, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-117">To do this, perform the following steps.</span></span>  
  
    1.  <span data-ttu-id="4e5f1-118">Wykonaj następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="4e5f1-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2.  <span data-ttu-id="4e5f1-119">Zmiana \<bufferSize > wartość w pliku Windows.ApplicationServer.Applications.man do 32.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  <span data-ttu-id="4e5f1-120">Wykonaj następujące polecenie w bieżącym katalogu framework (na przykład C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="4e5f1-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e5f1-121">Jeśli używasz platformy .NET Framework 4 Client Profile, najpierw musisz się zarejestrować manifestu ETW, uruchamiając następujące polecenie z katalogu .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="4e5f1-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="4e5f1-122">Włączanie debugowania śledzenia przy użyciu System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="4e5f1-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="4e5f1-123">Te detektorów można skonfigurować w pliku App.config aplikacji przepływu pracy lub w pliku Web.config dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="4e5f1-124">W tym przykładzie [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) jest skonfigurowany, aby zapisać informacje śledzenia do pliku MyTraceLog.txt w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4e5f1-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e5f1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e5f1-125">See Also</span></span>  
 [<span data-ttu-id="4e5f1-126">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="4e5f1-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="4e5f1-127">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="4e5f1-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
