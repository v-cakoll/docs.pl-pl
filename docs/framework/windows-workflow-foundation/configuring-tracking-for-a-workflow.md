---
title: Konfigurowanie śledzenia dla przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 97b25873e9f20d5d390b7a59531b3a5af32296df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802677"
---
# <a name="configuring-tracking-for-a-workflow"></a>Konfigurowanie śledzenia dla przepływu pracy

Przepływ pracy można wykonać na trzy sposoby:

- Hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Wykonane jako <xref:System.Activities.WorkflowApplication>

- Wykonywane bezpośrednio przy użyciu <xref:System.Activities.WorkflowInvoker>

W zależności od opcji hostingu przepływu pracy można dodać uczestnika śledzenia za pomocą kodu lub pliku konfiguracji. W tym temacie opisano sposób skonfigurowania śledzenia przez dodanie uczestnika śledzenia do <xref:System.Activities.WorkflowApplication> i <xref:System.ServiceModel.Activities.WorkflowServiceHost>i sposobu włączania śledzenia przy użyciu <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Konfigurowanie śledzenia aplikacji przepływu pracy

Przepływ pracy można uruchomić za pomocą klasy <xref:System.Activities.WorkflowApplication>. W tym temacie przedstawiono sposób skonfigurowania śledzenia dla aplikacji przepływu pracy [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] przez dodanie uczestnika śledzenia do <xref:System.Activities.WorkflowApplication> hosta przepływu pracy. W takim przypadku przepływ pracy jest uruchamiany jako aplikacja przepływu pracy. Aplikację przepływu pracy konfiguruje się za pomocą kodu (a nie przy użyciu pliku konfiguracji), który jest nieobsługiwanym plikiem exe przy użyciu klasy <xref:System.Activities.WorkflowApplication>. Uczestnik śledzenia jest dodawany jako rozszerzenie do wystąpienia <xref:System.Activities.WorkflowApplication>. Można to zrobić, dodając <xref:System.Activities.Tracking.TrackingParticipant> do kolekcji rozszerzeń dla wystąpienia obiektu WorkflowApplication.

W przypadku aplikacji przepływu pracy można dodać rozszerzenie zachowanie <xref:System.Activities.Tracking.EtwTrackingParticipant>, jak pokazano w poniższym kodzie.

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

Przepływ pracy może być ujawniony jako usługa WCF, gdy jest hostowany na hoście usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowServiceHost> to wyspecjalizowana implementacja ServiceHost platformy .NET dla usługi opartej na przepływie pracy. W tej sekcji wyjaśniono, jak skonfigurować śledzenie dla usługi przepływu pracy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działającej w programie <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Jest ona konfigurowana za pośrednictwem pliku Web. config (dla usługi hostowanej w sieci Web) lub pliku App. config (dla usługi hostowanej w aplikacji autonomicznej, takiej jak Aplikacja konsolowa) przez określenie zachowania usługi lub za pośrednictwem kodu przez dodanie zachowania specyficznego dla śledzenia do kolekcji <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> dla hosta usługi.

W przypadku usługi przepływu pracy hostowanej w <xref:System.ServiceModel.WorkflowServiceHost>można dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu elementu <`behavior`> w pliku konfiguracji, jak pokazano w poniższym przykładzie.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

Alternatywnie, w przypadku usługi przepływu pracy hostowanej w <xref:System.ServiceModel.WorkflowServiceHost>można dodać rozszerzenie zachowania <xref:System.Activities.Tracking.EtwTrackingParticipant> za pomocą kodu. Aby dodać uczestnika śledzenia niestandardowego, Utwórz nowe rozszerzenie zachowania i Dodaj je do <xref:System.ServiceModel.ServiceHost>, jak pokazano w poniższym przykładowym kodzie.

> [!NOTE]
> Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć niestandardowy element zachowania, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się z przykładami [śledzenia](./samples/tracking.md) .

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

Poniższy przykładowy kod pokazuje, jak odczytać profil śledzenia z pliku konfiguracyjnego.

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
> Więcej informacji o profilach śledzenia można znaleźć w tematach [śledzenie profilów](tracking-profiles.md).

### <a name="configuring-tracking-using-workflowinvoker"></a>Konfigurowanie śledzenia przy użyciu WorkflowInvoker

Aby skonfigurować śledzenie dla przepływu pracy wykonywanego przy użyciu <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie do wystąpienia <xref:System.Activities.WorkflowInvoker>. Poniższy przykład kodu pochodzi z niestandardowego przykładu [śledzenia](./samples/custom-tracking.md) .

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Wyświetlanie rekordów śledzenia w Podgląd zdarzeń

Istnieją dwa Podgląd zdarzeń Dzienniki o szczególnym znaczeniu do wyświetlenia podczas śledzenia wykonywania funkcji WF — dziennik analityczny i Dziennik debugowania. Oba znajdują się w węźle&#124;serwer&#124;aplikacji systemu Microsoft Windows — aplikacje. Dzienniki w tej sekcji zawierają zdarzenia z pojedynczej aplikacji, a nie zdarzenia mające wpływ na cały system.

Zdarzenia śledzenia debugowania są zapisywane w dzienniku debugowania. Aby zbierać zdarzenia śledzenia debugowania WF w Podgląd zdarzeń, Włącz Dziennik debugowania.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.

2. W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług** .

3. Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications** .

4. Kliknij prawym przyciskiem myszy węzeł **debugowanie** w węźle **serwer aplikacji — aplikacje** , a następnie wybierz pozycję **Włącz dziennik**.

5. Uruchom aplikację obsługującą śledzenie, aby wygenerować zdarzenia śledzenia.

6. Kliknij prawym przyciskiem myszy węzeł **debugowanie** i wybierz polecenie **Odśwież.** Zdarzenia śledzenia powinny być widoczne w środkowym okienku.

WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia do sesji ETW (śledzenie zdarzeń systemu Windows). Uczestnik śledzenia ETW jest skonfigurowany przy użyciu profilu śledzenia w celu subskrybowania śledzenia rekordów. Po włączeniu śledzenia błędy śledzenia rekordów są emitowane do funkcji ETW. Zdarzenia śledzenia funkcji ETW (między zakresem 100-113) odpowiadające zdarzeniom śledzenia emitowanym przez uczestnika śledzenia ETW są zapisywane w dzienniku analitycznym.

Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.

1. Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.** W oknie dialogowym Uruchamianie wpisz `eventvwr`.

2. W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług** .

3. Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications** .

4. Kliknij prawym przyciskiem myszy węzeł **analityczny** w węźle **serwer aplikacji — aplikacje** , a następnie wybierz pozycję **Włącz dziennik**.

5. Wykonaj swoją aplikację obsługującą śledzenie, aby generować rekordy śledzenia.

6. Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież.** Rekordy śledzenia powinny być widoczne w środkowym okienku.

Na poniższej ilustracji przedstawiono śledzenie zdarzeń w Podglądzie zdarzeń:

![Zrzut ekranu przedstawiający Podgląd zdarzeń pokazujący śledzone rekordy.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Rejestrowanie identyfikatora dostawcy specyficznego dla aplikacji

Jeśli zdarzenia muszą być zapisywane w określonym dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.

1. Zadeklaruj identyfikator dostawcy w pliku konfiguracyjnym aplikacji.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Skopiuj plik manifestu z%windir%\Microsoft.NET\Framework\\\<najnowszej wersji [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do lokalizacji tymczasowej, a następnie zmień jego nazwę na Microsoft. Windows. ApplicationServer. Applications_Provider1. Man

3. Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. Zmień nazwę dostawcy, jeśli nie chcesz odinstalować domyślnego dostawcy.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. Jeśli zmieniono nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanałów w pliku manifestu na nazwę nowego dostawcy.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Wygeneruj bibliotekę DLL zasobów, wykonując następujące kroki.

    1. Zainstaluj Windows SDK. Windows SDK obejmuje kompilator komunikatów ([mc. exe](/windows/win32/wes/message-compiler--mc-exe-)) i kompilator zasobów ([RC. exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).

    2. W Windows SDK wierszu polecenia Uruchom polecenie mc. exe w nowym pliku manifestu.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Uruchom RC. exe w pliku zasobów wygenerowanym w poprzednim kroku.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Utwórz pusty plik CS o nazwie NewProviderReg.cs.

    5. Utwórz bibliotekę DLL zasobów przy użyciu C# kompilatora.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Zmień nazwę biblioteki DLL zasobu i komunikatu w pliku manifestu, `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. Użyj [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) , aby zarejestrować manifest.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Zobacz także

- [Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
