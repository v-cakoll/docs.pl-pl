---
title: Konfigurowanie śledzenia dla przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 5ec94d6b8e58012d0c5c8ca8593c3cef81cd9ec3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248215"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurowanie śledzenia dla przepływu pracy

Przepływ pracy można wykonać na trzy sposoby:

- Hostowane w<xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Wykonywane jako<xref:System.Activities.WorkflowApplication>

- Wykonywane bezpośrednio za pomocą<xref:System.Activities.WorkflowInvoker>

W zależności od opcji hostingu przepływu pracy uczestnik śledzenia można dodać za pomocą kodu lub pliku konfiguracyjnego. W tym temacie opisano sposób konfigurowania śledzenia <xref:System.Activities.WorkflowApplication> przez dodanie <xref:System.ServiceModel.Activities.WorkflowServiceHost>uczestnika śledzenia do <xref:System.Activities.WorkflowInvoker>a i do , oraz jak włączyć śledzenie podczas korzystania .

## <a name="configuring-workflow-application-tracking"></a>Konfigurowanie śledzenia aplikacji przepływu pracy

Przepływ pracy można uruchomić <xref:System.Activities.WorkflowApplication> przy użyciu klasy. W tym temacie pokazano, jak [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] śledzenie jest skonfigurowane dla aplikacji <xref:System.Activities.WorkflowApplication> przepływu pracy przez dodanie uczestnika śledzenia do hosta przepływu pracy. W takim przypadku przepływ pracy działa jako aplikacja przepływu pracy. Aplikację przepływu pracy można skonfigurować za pomocą kodu (a nie przy użyciu pliku konfiguracyjnego), który jest samodzielnie hostowanym plikiem exe przy użyciu <xref:System.Activities.WorkflowApplication> klasy. Uczestnik śledzenia jest dodawany jako <xref:System.Activities.WorkflowApplication> rozszerzenie do wystąpienia. Odbywa się to <xref:System.Activities.Tracking.TrackingParticipant> przez dodanie do kolekcji rozszerzeń dla Wystąpienia Aplikacji Przepływu Pracy.

Dla aplikacji przepływu pracy można <xref:System.Activities.Tracking.EtwTrackingParticipant> dodać rozszerzenie zachowania, jak pokazano w poniższym kodzie.

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

Przepływ pracy może być narażony jako usługa WCF, gdy jest hostowany w hoście <xref:System.ServiceModel.Activities.WorkflowServiceHost> usługi. <xref:System.ServiceModel.Activities.WorkflowServiceHost>jest wyspecjalizowaną implementacją usługi .NET ServiceHost dla usługi opartej na przepływie pracy. W tej sekcji wyjaśniono, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jak skonfigurować <xref:System.ServiceModel.Activities.WorkflowServiceHost>śledzenie dla usługi przepływu pracy uruchomionej w pliku . Jest on konfigurowany za pośrednictwem pliku Web.config (dla usługi hostowanego w sieci Web) lub pliku App.config (dla usługi hostowanej w aplikacji autonomicznej, takiej jak <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> aplikacja konsoli), określając zachowanie usługi lub za pomocą kodu, dodając zachowanie specyficzne dla śledzenia do kolekcji dla hosta usługi.

W przypadku usługi przepływu <xref:System.ServiceModel.WorkflowServiceHost>pracy hostowanej <xref:System.Activities.Tracking.EtwTrackingParticipant> w programie można `behavior` dodać element <> w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

Alternatywnie dla usługi przepływu pracy <xref:System.ServiceModel.WorkflowServiceHost>hostowane w <xref:System.Activities.Tracking.EtwTrackingParticipant> programie , można dodać rozszerzenie zachowania za pomocą kodu. Aby dodać niestandardowego uczestnika śledzenia, utwórz nowe <xref:System.ServiceModel.ServiceHost> rozszerzenie zachowania i dodaj je do jak pokazano w poniższym przykładowym kodzie.

> [!NOTE]
> Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć niestandardowy element zachowania, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się z [przykładami śledzenia.](./samples/tracking.md)

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

Uczestnik śledzenia jest dodawany do hosta usługi przepływu pracy jako rozszerzenie zachowania.

Ten przykładowy kod poniżej pokazuje, jak odczytać profil śledzenia z pliku konfiguracji.

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

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

Ten przykładowy kod pokazuje, jak dodać profil śledzenia do hosta przepływu pracy.

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
> Więcej informacji na temat profili śledzenia można znaleźć [w 1.](tracking-profiles.md)

### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurowanie śledzenia przy użyciu narzędzia WorkflowInvoker

Aby skonfigurować śledzenie dla przepływu <xref:System.Activities.WorkflowInvoker>pracy wykonywanego przy użyciu <xref:System.Activities.WorkflowInvoker> , dodaj dostawcę śledzenia jako rozszerzenie do wystąpienia. Poniższy przykład kodu pochodzi z przykładu [śledzenia niestandardowego.](./samples/custom-tracking.md)

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Wyświetlanie rekordów śledzenia w Podglądzie zdarzeń

Istnieją dwa dzienniki Podglądu zdarzeń o szczególnym znaczeniu do wyświetlenia podczas śledzenia wykonywania WF — dziennika analitycznego i dziennika debugowania. Oba znajdują się w węźle Microsoft&#124;Windows&#124;Application Server-Applications. Dzienniki w tej sekcji zawierają zdarzenia z jednej aplikacji, a nie zdarzenia, które mają wpływ na cały system.

Zdarzenia śledzenia debugowania są zapisywane w dzienniku debugowania. Aby zebrać zdarzenia śledzenia debugowania WF w Podglądzie zdarzeń, włącz dziennik debugowania.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym `eventvwr`Uruchom wpisz .

2. W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług.**

3. Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications.**

4. Kliknij prawym przyciskiem myszy węzeł **Debugowanie** w węźle **Aplikacje serwera aplikacji,** a następnie wybierz polecenie **Włącz dziennik**.

5. Wykonaj aplikację z włączoną funkcją śledzenia, aby wygenerować zdarzenia śledzenia.

6. Kliknij prawym przyciskiem myszy węzeł **debugowania** i wybierz polecenie **Odśwież.** Śledzenie zdarzeń powinno być widoczne w środkowym okienku.

WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia do sesji ETW (Śledzenie zdarzeń dla systemu Windows). Uczestnik śledzenia ETW jest skonfigurowany z profilem śledzenia, aby subskrybować rekordy śledzenia. Gdy śledzenie jest włączone, rekordy śledzenia błędów są emitowane do ETW. Zdarzenia śledzenia ETW (między zakresem 100-113) odpowiadające zdarzeń śledzenia emitowanych przez uczestnika śledzenia ETW są zapisywane w dzienniku analitycznym.

Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym `eventvwr`Uruchom wpisz .

2. W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług.**

3. Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications.**

4. Kliknij prawym przyciskiem myszy węzeł **analityczny** w węźle **Aplikacje serwera aplikacji,** a następnie wybierz polecenie **Włącz dziennik**.

5. Wykonaj aplikację z włączoną funkcją śledzenia, aby wygenerować rekordy śledzenia.

6. Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież.** Rekordy śledzenia powinny być widoczne w środkowym okienku.

Na poniższej ilustracji przedstawiono zdarzenia śledzące w podglądzie zdarzeń:

![Zrzut ekranu przedstawiający Podgląd zdarzeń przedstawiający rekordy śledzenia.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Rejestrowanie identyfikatora dostawcy specyficznego dla aplikacji

Jeśli zdarzenia muszą być zapisywane w dzienniku określonej aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.

1. Zadeklaruj identyfikator dostawcy w pliku konfiguracji aplikacji.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\\<najnowszej [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wersji>\Microsoft.Windows.ApplicationServer.Applications.man do lokalizacji tymczasowej i zmień jego nazwę na Microsoft.Windows.ApplicationServer.Applications_Provider1.man

3. Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. Zmień nazwę dostawcy, jeśli nie chcesz odinstalowywać domyślnego dostawcy.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. Jeśli zmieniono nazwę dostawcy w poprzednim kroku, zmień nazwy kanałów w pliku manifestu na nową nazwę dostawcy.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Wygeneruj bibliotekę DLL zasobu, wykonując następujące kroki.

    1. Zainstaluj pakiet Windows SDK. Zestaw Windows SDK zawiera kompilator komunikatów[(mc.exe)](/windows/win32/wes/message-compiler--mc-exe-)i kompilator zasobów ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).

    2. W wierszu polecenia Windows SDK uruchom program mc.exe w nowym pliku manifestu.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Uruchom program rc.exe w pliku zasobu wygenerowanym w poprzednim kroku.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Utwórz pusty plik cs o nazwie NewProviderReg.cs.

    5. Utwórz bibliotekę DLL zasobów przy użyciu kompilatora języka C#.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Zmień nazwę dll zasobu i wiadomości `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` w pliku manifestu z nowej nazwy biblioteki dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. Użyj [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) zarejestrować manifest.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Zobacz też

- [Monitorowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorowanie aplikacji za pomocą sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
