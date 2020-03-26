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
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="8cc06-102">Konfigurowanie śledzenia dla przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8cc06-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="8cc06-103">Przepływ pracy można wykonać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="8cc06-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="8cc06-104">Hostowane w<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="8cc06-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="8cc06-105">Wykonywane jako<xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="8cc06-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="8cc06-106">Wykonywane bezpośrednio za pomocą<xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="8cc06-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="8cc06-107">W zależności od opcji hostingu przepływu pracy uczestnik śledzenia można dodać za pomocą kodu lub pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="8cc06-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="8cc06-108">W tym temacie opisano sposób konfigurowania śledzenia <xref:System.Activities.WorkflowApplication> przez dodanie <xref:System.ServiceModel.Activities.WorkflowServiceHost>uczestnika śledzenia do <xref:System.Activities.WorkflowInvoker>a i do , oraz jak włączyć śledzenie podczas korzystania .</span><span class="sxs-lookup"><span data-stu-id="8cc06-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="8cc06-109">Konfigurowanie śledzenia aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8cc06-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="8cc06-110">Przepływ pracy można uruchomić <xref:System.Activities.WorkflowApplication> przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="8cc06-111">W tym temacie pokazano, jak [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] śledzenie jest skonfigurowane dla aplikacji <xref:System.Activities.WorkflowApplication> przepływu pracy przez dodanie uczestnika śledzenia do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="8cc06-112">W takim przypadku przepływ pracy działa jako aplikacja przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="8cc06-113">Aplikację przepływu pracy można skonfigurować za pomocą kodu (a nie przy użyciu pliku konfiguracyjnego), który jest samodzielnie hostowanym plikiem exe przy użyciu <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="8cc06-114">Uczestnik śledzenia jest dodawany jako <xref:System.Activities.WorkflowApplication> rozszerzenie do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cc06-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="8cc06-115">Odbywa się to <xref:System.Activities.Tracking.TrackingParticipant> przez dodanie do kolekcji rozszerzeń dla Wystąpienia Aplikacji Przepływu Pracy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="8cc06-116">Dla aplikacji przepływu pracy można <xref:System.Activities.Tracking.EtwTrackingParticipant> dodać rozszerzenie zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8cc06-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="8cc06-117">Konfigurowanie śledzenia usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8cc06-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="8cc06-118">Przepływ pracy może być narażony jako usługa WCF, gdy jest hostowany w hoście <xref:System.ServiceModel.Activities.WorkflowServiceHost> usługi.</span><span class="sxs-lookup"><span data-stu-id="8cc06-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="8cc06-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>jest wyspecjalizowaną implementacją usługi .NET ServiceHost dla usługi opartej na przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="8cc06-120">W tej sekcji wyjaśniono, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jak skonfigurować <xref:System.ServiceModel.Activities.WorkflowServiceHost>śledzenie dla usługi przepływu pracy uruchomionej w pliku .</span><span class="sxs-lookup"><span data-stu-id="8cc06-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8cc06-121">Jest on konfigurowany za pośrednictwem pliku Web.config (dla usługi hostowanego w sieci Web) lub pliku App.config (dla usługi hostowanej w aplikacji autonomicznej, takiej jak <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> aplikacja konsoli), określając zachowanie usługi lub za pomocą kodu, dodając zachowanie specyficzne dla śledzenia do kolekcji dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="8cc06-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="8cc06-122">W przypadku usługi przepływu <xref:System.ServiceModel.WorkflowServiceHost>pracy hostowanej <xref:System.Activities.Tracking.EtwTrackingParticipant> w programie można `behavior` dodać element <> w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8cc06-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="8cc06-123">Alternatywnie dla usługi przepływu pracy <xref:System.ServiceModel.WorkflowServiceHost>hostowane w <xref:System.Activities.Tracking.EtwTrackingParticipant> programie , można dodać rozszerzenie zachowania za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="8cc06-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="8cc06-124">Aby dodać niestandardowego uczestnika śledzenia, utwórz nowe <xref:System.ServiceModel.ServiceHost> rozszerzenie zachowania i dodaj je do jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8cc06-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="8cc06-125">Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć niestandardowy element zachowania, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się z [przykładami śledzenia.](./samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="8cc06-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="8cc06-126">Uczestnik śledzenia jest dodawany do hosta usługi przepływu pracy jako rozszerzenie zachowania.</span><span class="sxs-lookup"><span data-stu-id="8cc06-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="8cc06-127">Ten przykładowy kod poniżej pokazuje, jak odczytać profil śledzenia z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8cc06-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="8cc06-128">Ten przykładowy kod pokazuje, jak dodać profil śledzenia do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="8cc06-129">Więcej informacji na temat profili śledzenia można znaleźć [w 1.](tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8cc06-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="8cc06-130">Konfigurowanie śledzenia przy użyciu narzędzia WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="8cc06-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="8cc06-131">Aby skonfigurować śledzenie dla przepływu <xref:System.Activities.WorkflowInvoker>pracy wykonywanego przy użyciu <xref:System.Activities.WorkflowInvoker> , dodaj dostawcę śledzenia jako rozszerzenie do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8cc06-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="8cc06-132">Poniższy przykład kodu pochodzi z przykładu [śledzenia niestandardowego.](./samples/custom-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="8cc06-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="8cc06-133">Wyświetlanie rekordów śledzenia w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8cc06-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="8cc06-134">Istnieją dwa dzienniki Podglądu zdarzeń o szczególnym znaczeniu do wyświetlenia podczas śledzenia wykonywania WF — dziennika analitycznego i dziennika debugowania.</span><span class="sxs-lookup"><span data-stu-id="8cc06-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="8cc06-135">Oba znajdują się w węźle Microsoft&#124;Windows&#124;Application Server-Applications.</span><span class="sxs-lookup"><span data-stu-id="8cc06-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="8cc06-136">Dzienniki w tej sekcji zawierają zdarzenia z jednej aplikacji, a nie zdarzenia, które mają wpływ na cały system.</span><span class="sxs-lookup"><span data-stu-id="8cc06-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="8cc06-137">Zdarzenia śledzenia debugowania są zapisywane w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="8cc06-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="8cc06-138">Aby zebrać zdarzenia śledzenia debugowania WF w Podglądzie zdarzeń, włącz dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="8cc06-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="8cc06-139">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="8cc06-140">W oknie dialogowym `eventvwr`Uruchom wpisz .</span><span class="sxs-lookup"><span data-stu-id="8cc06-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="8cc06-141">W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="8cc06-142">Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="8cc06-143">Kliknij prawym przyciskiem myszy węzeł **Debugowanie** w węźle **Aplikacje serwera aplikacji,** a następnie wybierz polecenie **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="8cc06-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="8cc06-144">Wykonaj aplikację z włączoną funkcją śledzenia, aby wygenerować zdarzenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8cc06-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="8cc06-145">Kliknij prawym przyciskiem myszy węzeł **debugowania** i wybierz polecenie **Odśwież.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="8cc06-146">Śledzenie zdarzeń powinno być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="8cc06-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="8cc06-147">WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia do sesji ETW (Śledzenie zdarzeń dla systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="8cc06-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="8cc06-148">Uczestnik śledzenia ETW jest skonfigurowany z profilem śledzenia, aby subskrybować rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8cc06-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="8cc06-149">Gdy śledzenie jest włączone, rekordy śledzenia błędów są emitowane do ETW.</span><span class="sxs-lookup"><span data-stu-id="8cc06-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="8cc06-150">Zdarzenia śledzenia ETW (między zakresem 100-113) odpowiadające zdarzeń śledzenia emitowanych przez uczestnika śledzenia ETW są zapisywane w dzienniku analitycznym.</span><span class="sxs-lookup"><span data-stu-id="8cc06-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="8cc06-151">Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="8cc06-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="8cc06-152">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="8cc06-153">W oknie dialogowym `eventvwr`Uruchom wpisz .</span><span class="sxs-lookup"><span data-stu-id="8cc06-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="8cc06-154">W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="8cc06-155">Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="8cc06-156">Kliknij prawym przyciskiem myszy węzeł **analityczny** w węźle **Aplikacje serwera aplikacji,** a następnie wybierz polecenie **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="8cc06-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="8cc06-157">Wykonaj aplikację z włączoną funkcją śledzenia, aby wygenerować rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8cc06-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="8cc06-158">Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież.**</span><span class="sxs-lookup"><span data-stu-id="8cc06-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="8cc06-159">Rekordy śledzenia powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="8cc06-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="8cc06-160">Na poniższej ilustracji przedstawiono zdarzenia śledzące w podglądzie zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="8cc06-160">The following image shows tracking events in the event viewer:</span></span>

![Zrzut ekranu przedstawiający Podgląd zdarzeń przedstawiający rekordy śledzenia.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="8cc06-162">Rejestrowanie identyfikatora dostawcy specyficznego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="8cc06-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="8cc06-163">Jeśli zdarzenia muszą być zapisywane w dzienniku określonej aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="8cc06-164">Zadeklaruj identyfikator dostawcy w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cc06-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="8cc06-165">Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\\<najnowszej [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wersji>\Microsoft.Windows.ApplicationServer.Applications.man do lokalizacji tymczasowej i zmień jego nazwę na Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="8cc06-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="8cc06-166">Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.</span><span class="sxs-lookup"><span data-stu-id="8cc06-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="8cc06-167">Zmień nazwę dostawcy, jeśli nie chcesz odinstalowywać domyślnego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="8cc06-168">Jeśli zmieniono nazwę dostawcy w poprzednim kroku, zmień nazwy kanałów w pliku manifestu na nową nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8cc06-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="8cc06-169">Wygeneruj bibliotekę DLL zasobu, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="8cc06-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="8cc06-170">Zainstaluj pakiet Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8cc06-170">Install the Windows SDK.</span></span> <span data-ttu-id="8cc06-171">Zestaw Windows SDK zawiera kompilator komunikatów[(mc.exe)](/windows/win32/wes/message-compiler--mc-exe-)i kompilator zasobów ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span><span class="sxs-lookup"><span data-stu-id="8cc06-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="8cc06-172">W wierszu polecenia Windows SDK uruchom program mc.exe w nowym pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="8cc06-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="8cc06-173">Uruchom program rc.exe w pliku zasobu wygenerowanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="8cc06-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="8cc06-174">Utwórz pusty plik cs o nazwie NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="8cc06-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="8cc06-175">Utwórz bibliotekę DLL zasobów przy użyciu kompilatora języka C#.</span><span class="sxs-lookup"><span data-stu-id="8cc06-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="8cc06-176">Zmień nazwę dll zasobu i wiadomości `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` w pliku manifestu z nowej nazwy biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="8cc06-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="8cc06-177">Użyj [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) zarejestrować manifest.</span><span class="sxs-lookup"><span data-stu-id="8cc06-177">Use [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="8cc06-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cc06-178">See also</span></span>

- <span data-ttu-id="8cc06-179">[Monitorowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8cc06-179">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="8cc06-180">[Monitorowanie aplikacji za pomocą sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8cc06-180">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
