---
title: Konfigurowanie śledzenia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: c9d38533d11497bd4404e4f8795d8a1ce9b17df9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491259"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurowanie śledzenia przepływu pracy

Przepływ pracy można wykonać na trzy sposoby:

- Hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Wykonywane jako <xref:System.Activities.WorkflowApplication>

- Posługując się bezpośrednio <xref:System.Activities.WorkflowInvoker>

W zależności od opcji obsługi przepływu pracy można dodać uczestnika śledzenia za pomocą kodu lub za pomocą pliku konfiguracji. W tym temacie opisano sposób śledzenia jest skonfigurowany, dodając uczestnikiem śledzenia do <xref:System.Activities.WorkflowApplication> i <xref:System.ServiceModel.Activities.WorkflowServiceHost>oraz jak włączyć śledzenie, korzystając z <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Skonfigurowanie aplikacji przepływu pracy śledzenia

Przepływ pracy można uruchomić przy użyciu <xref:System.Activities.WorkflowApplication> klasy. W tym temacie przedstawiono sposób śledzenia jest skonfigurowany dla [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikacji przepływu pracy, dodając uczestnikiem śledzenia do <xref:System.Activities.WorkflowApplication> hosta przepływu pracy. W takim przypadku przepływ pracy działa jako aplikacja przepływu pracy. Konfigurowanie poziomu aplikacji przepływu pracy za pomocą kodu (zamiast przy użyciu pliku konfiguracji), czyli Self-Hosted .exe plików przy użyciu <xref:System.Activities.WorkflowApplication> klasy. Śledzenia uczestnika zostanie dodany jako rozszerzenie <xref:System.Activities.WorkflowApplication> wystąpienia. Jest to realizowane przez dodanie <xref:System.Activities.Tracking.TrackingParticipant> kolekcji rozszerzeń dla tego wystąpienia WorkflowApplication.

W przypadku aplikacji przepływu pracy, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania, jak pokazano w poniższym kodzie.

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

### <a name="configuring-workflow-service-tracking"></a>Konfigurowanie usługi przepływu pracy śledzenia

Przepływ pracy może być udostępniany jako usługi WCF w przypadku hostowania w <xref:System.ServiceModel.Activities.WorkflowServiceHost> hosta usługi. <xref:System.ServiceModel.Activities.WorkflowServiceHost> to Wyspecjalizowana implementacja .NET ServiceHost dla usługi opartej na przepływie pracy. W tej sekcji opisano sposób konfigurowania śledzenia [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usługi przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Jest skonfigurowany za pomocą pliku Web.config (usługi hostowane w sieci Web) lub plik App.config (dla usługi hostowanej w aplikacji autonomicznej, np. aplikację konsolową w języku), określając zachowanie usługi, lub za pomocą kodu przez dodanie zachowania specyficzny dla śledzenia do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji dla hosta usługi.

Dla usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> element pliku konfiguracji, jak pokazano w poniższym przykładzie.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

Alternatywnie przepływu pracy usługi hostowanej w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania za pomocą kodu. Aby dodać uczestnikiem niestandardowe śledzenia, Utwórz nowe rozszerzenie zachowanie i dodaj go do <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym przykładowym kodzie.

> [!NOTE]
> Aby wyświetlić przykładowy kod, który pokazuje, jak można utworzyć elementu niestandardowe zachowanie, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się [śledzenia](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) przykładów.

```csharp
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

Śledzenia uczestnika zostanie dodany do hosta usługi przepływu pracy jako rozszerzenie do zachowania.

Ten przykładowy kod poniżej pokazano, jak odczytać profil śledzenia w pliku konfiguracji.

```csharp
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

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> Aby uzyskać więcej informacji na temat śledzenia profilów, dotyczą [profile śledzenia](https://go.microsoft.com/fwlink/?LinkId=201310).

### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurowanie śledzenia za pomocą obiektu WorkflowInvoker

Do konfigurowania śledzenia dla przepływu pracy, posługując się <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie <xref:System.Activities.WorkflowInvoker> wystąpienia. Poniższy przykładowy kod pochodzi z [niestandardowe śledzenia](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) próbki.

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Wyświetlanie śledzenia rekordów w Podglądzie zdarzeń

Istnieją dwa dzienniki Podglądu zdarzeń szczególne znaczenie w odniesieniu do wyświetlenia podczas śledzenia wykonywanie WF — dziennik analityczny i dziennik debugowania. Znajdują się zarówno w ramach programu Microsoft&#124;Windows&#124;węzła aplikacje serwera aplikacji. Dzienniki w tej sekcji zawierają zdarzenia z pojedynczą aplikacją, a nie zdarzenia, które mają wpływ na cały system.

Debugowanie śledzenia są zapisywane w dzienniku debugowania. Aby zbierać zdarzenia śledzenia debugowania WF w Podglądzie zdarzeń, włączyć dziennik debugowania.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **uruchomienia.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.

2. W oknie dialogowym podglądu zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.

3. Rozwiń **Microsoft**, **Windows**, i **aplikacje serwera aplikacji** węzłów.

4. Kliknij prawym przyciskiem myszy **debugowania** węźle **aplikacje serwera aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.

5. Wykonaj włączone śledzenie aplikacji generowanie zdarzeń śledzenia.

6. Kliknij prawym przyciskiem myszy **debugowania** a następnie wybierz węzeł **odświeżania.** Śledzenie zdarzeń powinny być widoczne w środkowym okienku.

WF 4 udostępnia śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW (Event Tracing for Windows). Uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany z profil śledzenia do subskrybowania śledzenie rekordów. Po włączeniu śledzenia błędów, śledzenia rekordów są emitowane zdarzeń systemu Windows. Dziennik analityczny odpowiadający zdarzenia śledzenia emitowane przez uczestnika śledzenia zdarzeń systemu Windows są zapisywane ETW śledzenia zdarzeń (między zakres 100 113).

Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **uruchomienia.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.

2. W oknie dialogowym podglądu zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.

3. Rozwiń **Microsoft**, **Windows**, i **aplikacje serwera aplikacji** węzłów.

4. Kliknij prawym przyciskiem myszy **analityczne** węźle **aplikacje serwera aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.

5. Wykonywanie aplikacji z obsługą śledzenia do generowania rekordów śledzenia.

6. Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **odświeżania.** Rekordy śledzenia powinny być widoczne w środkowym okienku.

Na poniższej ilustracji przedstawiono zdarzeń śledzenia w Podglądzie zdarzeń.

![Wyświetlanie podglądu zdarzeń śledzenia rekordów](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")

### <a name="registering-an-application-specific-provider-id"></a>Rejestrowanie identyfikator dostawcy specyficzne dla aplikacji

Jeśli zdarzenia muszą być zapisywane w dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.

1. Zadeklaruj identyfikator dostawcy w pliku konfiguracyjnym aplikacji.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\< najnowszą wersję [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do tymczasowej lokalizacji i zmień jej nazwę na Microsoft.Windows.ApplicationServer.Applications_Provider1.man

3. Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. Jeśli nie chcesz odinstalować domyślnego dostawcę, należy zmienić nazwę dostawcy.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. Jeśli zmienisz nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanałów w pliku manifestu na nową nazwę dostawcy.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Generowanie biblioteki DLL zasobu, wykonaj następujące czynności.

    1. Zainstaluj Windows SDK. Zestaw Windows SDK zawiera kompilator komunikat ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) i kompilator zasobów ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).

    2. W wierszu polecenia zestawu Windows SDK należy uruchomić mc.exe nowego pliku manifestu.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Uruchom rc.exe plik resource wygenerowany w poprzednim kroku.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Utwórz plik pusty cs o nazwie NewProviderReg.cs.

    5. Utwórz zasób biblioteki DLL za pomocą kompilatora C#.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Zmień nazwę biblioteki dll zasobu i komunikatów w pliku manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę biblioteki dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. Użyj [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) można zarejestrować w manifeście.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Zobacz także

- [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
