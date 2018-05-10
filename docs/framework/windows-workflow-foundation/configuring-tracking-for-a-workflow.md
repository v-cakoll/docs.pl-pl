---
title: Konfigurowanie śledzenia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 23a20b014962b74b6408c8b3c9ac6764d4a42d56
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurowanie śledzenia przepływu pracy
Przepływ pracy można wykonać na trzy sposoby:  
  
-   Obsługiwane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
-   Wykonane jako <xref:System.Activities.WorkflowApplication>  
  
-   Posługując się bezpośrednio <xref:System.Activities.WorkflowInvoker>  
  
 W zależności od opcji obsługi przepływu pracy można dodać uczestnika śledzenia za pośrednictwem kodu lub pliku konfiguracji. W tym temacie opisano konfiguracji śledzenia, dodając śledzenie uczestnika do <xref:System.Activities.WorkflowApplication> i <xref:System.ServiceModel.Activities.WorkflowServiceHost>i jak włączyć śledzenie, korzystając z <xref:System.Activities.WorkflowInvoker>.  
  
## <a name="configuring-workflow-application-tracking"></a>Konfigurowanie śledzenia aplikacji przepływu pracy  
 Przepływ pracy można uruchomić przy użyciu <xref:System.Activities.WorkflowApplication> klasy. W tym temacie przedstawiono sposób śledzenia jest skonfigurowany dla [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikacji przepływu pracy, dodając śledzenie uczestnika do <xref:System.Activities.WorkflowApplication> hosta przepływu pracy. W takim przypadku przepływ pracy jest uruchamiany jako aplikacja przepływu pracy. Skonfigurować aplikację przepływu pracy za pomocą kodu (a nie przy użyciu pliku konfiguracji), który jest samodzielnie hostowana .exe plik za pomocą <xref:System.Activities.WorkflowApplication> klasy. Uczestnik śledzenia jest dodawana jako rozszerzenie <xref:System.Activities.WorkflowApplication> wystąpienia. Jest to realizowane przez dodanie <xref:System.Activities.Tracking.TrackingParticipant> do kolekcji rozszerzeń dla tego wystąpienia obiektu WorkflowApplication.  
  
 W przypadku aplikacji przepływu pracy, można dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania, jak pokazano w poniższym kodzie.  
  
```csharp  
LogActivity activity = new LogActivity();  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
EtwTrackingParticipant trackingParticipant =  
    new EtwTrackingParticipant  
{  
  
        TrackingProfile = new TrackingProfile  
           {  
               Name = "SampleTrackingProfile",  
               ActivityDefinitionId = "ProcessOrder",  
               Queries = new WorkflowInstanceQuery  
               {  
                  States = { "*" }  
              }  
          }  
       };  
instance.Extensions.Add(trackingParticipant);  
```  
  
### <a name="configuring-workflow-service-tracking"></a>Konfigurowanie śledzenia usługi przepływu pracy  
 Przepływ pracy może być udostępniany jako usługi WCF w przypadku hostowania w <xref:System.ServiceModel.Activities.WorkflowServiceHost> hosta usługi. <xref:System.ServiceModel.Activities.WorkflowServiceHost> to specjalne implementacja .NET ServiceHost dla usługi opartej na przepływie pracy. W tej sekcji opisano sposób konfigurowania śledzenia dla [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usługi przepływu pracy uruchomionych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Jest skonfigurowany za pomocą pliku Web.config (dla usługi sieci Web hostowanych) lub plik App.config (dla usługi hostowanej w autonomicznej aplikacji, na przykład aplikacji konsoli), określając zachowanie usługi lub za pomocą kodu dodając zachowanie specyficzne dla śledzenia w celu <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji hosta usługi.  
  
 Dla usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> w pliku konfiguracji, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 Alternatywnie usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania za pomocą kodu. Aby dodać niestandardowe śledzenia uczestnika, Utwórz nowe rozszerzenia zachowania i dodaj go do <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym przykładzie kodzie.  
  
> [!NOTE]
>  Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć element zachowania niestandardowego, który dodaje uczestnika śledzenia niestandardowych, można skorzystać z [śledzenia](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) próbek.  
  
```  
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new   
                                 Uri("http://localhost:8001/Sample"));  
EtwTrackingBehavior trackingBehavior =   
    new EtwTrackingBehavior  
    {  
        ProfileName = "Sample Tracking Profile"  
    };  
svcHost.Description.Behaviors.Add(trackingBehavior);  
svcHost.Open();  
```  
  
 Uczestnik śledzenia jest dodawany do hosta usługi przepływu pracy jako rozszerzenie do zachowania.  
  
 Ten przykładowy kod poniżej pokazano, jak można odczytać z pliku konfiguracji profilu śledzenia.  
  
```  
TrackingProfile GetProfile(string profileName, string displayName)  
        {  
            TrackingProfile trackingProfile = null;  
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");  
            if (trackingSection == null)   
            {  
                return null;  
            }  
  
            if (profileName == null)   
            {  
                profileName = "";  
            }  
  
            //Find the profile with the specified profile name in the list of profile found in config  
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)  
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))  
                        select p;  
  
            if (match.Count() == 0)  
            {  
                //return an empty profile  
                trackingProfile = new TrackingProfile()  
                {  
                    ActivityDefinitionId = displayName  
                };  
  
            }  
            else  
            {  
                trackingProfile = match.First();  
            }  
  
            return trackingProfile;  
```  
  
 Ten przykładowy kod przedstawia sposób dodawania profilu śledzenia do hosta przepływu pracy.  
  
```  
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;  
if (null != workflowServiceHost)  
{  
              string workflowDisplayName = workflowServiceHost.Activity.DisplayName;  
               TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);  
                workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant  {  
               TrackingProfile = trackingProfile  
                        });  
 }  
```  
  
> [!NOTE]
>  Więcej informacji o śledzeniu profile, można znaleźć w [śledzenia profile](http://go.microsoft.com/fwlink/?LinkId=201310).  
  
### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurowanie śledzenia przy użyciu WorkflowInvoker  
 Aby skonfigurować śledzenia dla przepływu pracy wykonywane przy użyciu <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie <xref:System.Activities.WorkflowInvoker> wystąpienia. Poniższy przykładowy kod jest z [śledzenia niestandardowe](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) próbki.  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a>Wyświetlanie rekordów w Podglądzie zdarzeń śledzenia  
 Istnieją dwa dzienniki Podglądu zdarzeń szczególne znaczenie widoku, gdy śledzenie wykonywanie WF — analityczne dziennika i dzienników debugowania. Znajdują się zarówno w obszarze Microsoft&#124;Windows&#124;węzła aplikacje serwera aplikacji.  Dzienniki w tej sekcji zawierają zdarzenia z jednej aplikacji zamiast zdarzenia, które mają wpływ na cały system.  
  
 Debugowanie śledzenia są zapisywane w dzienniku debugowania. Aby zbierać WF debugowania śledzenia zdarzeń w Podglądzie zdarzeń, włączyć dziennik debugowania.  
  
1.  Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.  
  
2.  W oknie dialogowym Podgląd zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.  
  
3.  Rozwiń węzeł **Microsoft**, **Windows**, i **aplikacji serwerowych aplikacji** węzłów.  
  
4.  Kliknij prawym przyciskiem myszy **debugowania** węźle **aplikacji serwerowych aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.  
  
5.  Wykonanie włączone śledzenie aplikacji generowanie zdarzeń śledzenia.  
  
6.  Kliknij prawym przyciskiem myszy **debugowania** a następnie wybierz węzeł **odświeżania.** Śledzenie zdarzeń powinny być widoczne w środkowym okienku.  
  
 WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia w sesji usługi ETW (zdarzenia śledzenia dla systemu Windows). Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany przy użyciu profilu śledzenia, aby subskrybować śledzenie rekordów.  Gdy śledzenie jest włączone, śledzenie rejestruje błędy są emitowane do funkcji ETW. ETW śledzenia zdarzeń (między zakres 100 113) odpowiadający emitowane przez uczestnika śledzenia funkcji ETW zdarzenia śledzenia są zapisywane w dzienniku analitycznych.  
  
 Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.  
  
1.  Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.  
  
2.  W oknie dialogowym Podgląd zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.  
  
3.  Rozwiń węzeł **Microsoft**, **Windows**, i **aplikacji serwerowych aplikacji** węzłów.  
  
4.  Kliknij prawym przyciskiem myszy **analityczne** węźle **aplikacji serwerowych aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.  
  
5.  Wykonanie włączone śledzenie aplikacji do wygenerowania rekordów śledzenia.  
  
6.  Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **odświeżania.** Śledzenie rekordów powinny być widoczne w środkowym okienku.  
  
 Na poniższej ilustracji przedstawiono śledzenia zdarzeń w Podglądzie zdarzeń.  
  
 ![Wyświetlanie podglądu zdarzeń śledzenia rekordów](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")  
  
### <a name="registering-an-application-specific-provider-id"></a>Rejestrowanie identyfikator dostawcy specyficzne dla aplikacji  
 Jeśli zdarzeń muszą być zapisywane w dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowe manifestu dostawcy.  
  
1.  Deklarowanie identyfikator dostawcy w pliku konfiguracyjnym aplikacji.  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\< najnowszą wersję [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do tymczasowej lokalizacji i zmień jego nazwę Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
  
3.  Zmień identyfikator GUID w pliku manifestu nowego identyfikatora GUID.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  Zmień nazwę dostawcy, jeśli nie chcesz odinstalować domyślnego dostawcy.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  Jeśli zmienisz nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanału w pliku manifestu na nową nazwę dostawcy.  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  Generowanie biblioteki DLL zasobu, wykonaj następujące czynności.  
  
    1.  Zainstaluj zestaw Windows SDK. Zestaw SDK systemu Windows zawiera komunikat kompilatora ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) i kompilatora zasobów ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).  
  
    2.  W wierszu polecenia systemu Windows SDK należy uruchomić mc.exe na nowym pliku manifestu.  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  Uruchom rc.exe na plik zasobów wygenerowany w poprzednim kroku.  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  Utwórz cs pusty plik o nazwie NewProviderReg.cs.  
  
    5.  Utwórz zasób biblioteki DLL przy użyciu kompilatora C#.  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  Zmień namel dl zasobów i komunikatów w pliku manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę biblioteki dll.  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  Użyj [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) zarejestrować manifestu.  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
