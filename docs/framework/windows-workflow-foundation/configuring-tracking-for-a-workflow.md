---
title: Konfigurowanie śledzenia dla przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: d8d3293fd2b271c0e1a00a1fca30d5ecd166df12
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690565"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="dacb2-102">Konfigurowanie śledzenia dla przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dacb2-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="dacb2-103">Przepływ pracy można wykonać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="dacb2-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="dacb2-104">Hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="dacb2-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="dacb2-105">Wykonywane jako <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="dacb2-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="dacb2-106">Posługując się bezpośrednio <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="dacb2-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="dacb2-107">W zależności od opcji obsługi przepływu pracy można dodać uczestnika śledzenia za pomocą kodu lub za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dacb2-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="dacb2-108">W tym temacie opisano sposób śledzenia jest skonfigurowany, dodając uczestnikiem śledzenia do <xref:System.Activities.WorkflowApplication> i <xref:System.ServiceModel.Activities.WorkflowServiceHost>oraz jak włączyć śledzenie, korzystając z <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="dacb2-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="dacb2-109">Skonfigurowanie aplikacji przepływu pracy śledzenia</span><span class="sxs-lookup"><span data-stu-id="dacb2-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="dacb2-110">Przepływ pracy można uruchomić przy użyciu <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="dacb2-111">W tym temacie przedstawiono sposób śledzenia jest skonfigurowany dla [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikacji przepływu pracy, dodając uczestnikiem śledzenia do <xref:System.Activities.WorkflowApplication> hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="dacb2-112">W takim przypadku przepływ pracy działa jako aplikacja przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="dacb2-113">Konfigurowanie poziomu aplikacji przepływu pracy za pomocą kodu (zamiast przy użyciu pliku konfiguracji), czyli Self-Hosted .exe plików przy użyciu <xref:System.Activities.WorkflowApplication> klasy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="dacb2-114">Śledzenia uczestnika zostanie dodany jako rozszerzenie <xref:System.Activities.WorkflowApplication> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dacb2-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="dacb2-115">Jest to realizowane przez dodanie <xref:System.Activities.Tracking.TrackingParticipant> kolekcji rozszerzeń dla tego wystąpienia WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="dacb2-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="dacb2-116">W przypadku aplikacji przepływu pracy, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dacb2-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="dacb2-117">Konfigurowanie usługi przepływu pracy śledzenia</span><span class="sxs-lookup"><span data-stu-id="dacb2-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="dacb2-118">Przepływ pracy może być udostępniany jako usługi WCF w przypadku hostowania w <xref:System.ServiceModel.Activities.WorkflowServiceHost> hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="dacb2-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="dacb2-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> to Wyspecjalizowana implementacja .NET ServiceHost dla usługi opartej na przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="dacb2-120">W tej sekcji opisano sposób konfigurowania śledzenia [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usługi przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="dacb2-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="dacb2-121">Jest skonfigurowany za pomocą pliku Web.config (usługi hostowane w sieci Web) lub plik App.config (dla usługi hostowanej w aplikacji autonomicznej, np. aplikację konsolową w języku), określając zachowanie usługi, lub za pomocą kodu przez dodanie zachowania specyficzny dla śledzenia do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="dacb2-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="dacb2-122">Dla usługi przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> element pliku konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dacb2-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

<span data-ttu-id="dacb2-123">Alternatywnie przepływu pracy usługi hostowanej w <xref:System.ServiceModel.WorkflowServiceHost>, możesz dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> rozszerzenia zachowania za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="dacb2-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="dacb2-124">Aby dodać uczestnikiem niestandardowe śledzenia, Utwórz nowe rozszerzenie zachowanie i dodaj go do <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dacb2-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="dacb2-125">Aby wyświetlić przykładowy kod, który pokazuje, jak można utworzyć elementu niestandardowe zachowanie, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się [śledzenia](./samples/tracking.md) przykładów.</span><span class="sxs-lookup"><span data-stu-id="dacb2-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="dacb2-126">Śledzenia uczestnika zostanie dodany do hosta usługi przepływu pracy jako rozszerzenie do zachowania.</span><span class="sxs-lookup"><span data-stu-id="dacb2-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="dacb2-127">Ten przykładowy kod poniżej pokazano, jak odczytać profil śledzenia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dacb2-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="dacb2-128">Ten przykładowy kod przedstawia sposób dodawania profilu śledzenia do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="dacb2-129">Aby uzyskać więcej informacji na temat śledzenia profilów, dotyczą [profile śledzenia](https://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="dacb2-129">For more information on tracking profiles, refer to [Tracking Profiles](https://go.microsoft.com/fwlink/?LinkId=201310).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="dacb2-130">Konfigurowanie śledzenia za pomocą obiektu WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="dacb2-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="dacb2-131">Do konfigurowania śledzenia dla przepływu pracy, posługując się <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie <xref:System.Activities.WorkflowInvoker> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dacb2-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="dacb2-132">Poniższy przykładowy kod pochodzi z [niestandardowe śledzenia](./samples/custom-tracking.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="dacb2-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="dacb2-133">Wyświetlanie śledzenia rekordów w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dacb2-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="dacb2-134">Istnieją dwa dzienniki Podglądu zdarzeń szczególne znaczenie w odniesieniu do wyświetlenia podczas śledzenia wykonywanie WF — dziennik analityczny i dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="dacb2-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="dacb2-135">Znajdują się zarówno w ramach programu Microsoft&#124;Windows&#124;węzła aplikacje serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dacb2-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="dacb2-136">Dzienniki w tej sekcji zawierają zdarzenia z pojedynczą aplikacją, a nie zdarzenia, które mają wpływ na cały system.</span><span class="sxs-lookup"><span data-stu-id="dacb2-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="dacb2-137">Debugowanie śledzenia są zapisywane w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="dacb2-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="dacb2-138">Aby zbierać zdarzenia śledzenia debugowania WF w Podglądzie zdarzeń, włączyć dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="dacb2-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="dacb2-139">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **uruchomienia.**</span><span class="sxs-lookup"><span data-stu-id="dacb2-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="dacb2-140">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="dacb2-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="dacb2-141">W oknie dialogowym podglądu zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="dacb2-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="dacb2-142">Rozwiń **Microsoft**, **Windows**, i **aplikacje serwera aplikacji** węzłów.</span><span class="sxs-lookup"><span data-stu-id="dacb2-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="dacb2-143">Kliknij prawym przyciskiem myszy **debugowania** węźle **aplikacje serwera aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="dacb2-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="dacb2-144">Wykonaj włączone śledzenie aplikacji generowanie zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="dacb2-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="dacb2-145">Kliknij prawym przyciskiem myszy **debugowania** a następnie wybierz węzeł **odświeżania.**</span><span class="sxs-lookup"><span data-stu-id="dacb2-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="dacb2-146">Śledzenie zdarzeń powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="dacb2-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="dacb2-147">WF 4 udostępnia śledzenia uczestnika, który zapisuje rekordy śledzenia sesji funkcji ETW (Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="dacb2-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="dacb2-148">Uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany z profil śledzenia do subskrybowania śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="dacb2-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="dacb2-149">Po włączeniu śledzenia błędów, śledzenia rekordów są emitowane zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dacb2-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="dacb2-150">Dziennik analityczny odpowiadający zdarzenia śledzenia emitowane przez uczestnika śledzenia zdarzeń systemu Windows są zapisywane ETW śledzenia zdarzeń (między zakres 100 113).</span><span class="sxs-lookup"><span data-stu-id="dacb2-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="dacb2-151">Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="dacb2-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="dacb2-152">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **uruchomienia.**</span><span class="sxs-lookup"><span data-stu-id="dacb2-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="dacb2-153">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="dacb2-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="dacb2-154">W oknie dialogowym podglądu zdarzeń, rozwiń węzeł **Dzienniki aplikacji i usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="dacb2-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="dacb2-155">Rozwiń **Microsoft**, **Windows**, i **aplikacje serwera aplikacji** węzłów.</span><span class="sxs-lookup"><span data-stu-id="dacb2-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="dacb2-156">Kliknij prawym przyciskiem myszy **analityczne** węźle **aplikacje serwera aplikacji** , a następnie wybierz węzeł **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="dacb2-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="dacb2-157">Wykonywanie aplikacji z obsługą śledzenia do generowania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="dacb2-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="dacb2-158">Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **odświeżania.**</span><span class="sxs-lookup"><span data-stu-id="dacb2-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="dacb2-159">Rekordy śledzenia powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="dacb2-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="dacb2-160">Na poniższej ilustracji przedstawiono zdarzeń śledzenia w Podglądzie zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="dacb2-160">The following image shows tracking events in the event viewer:</span></span>

![Zrzut ekranu przedstawiający Podgląd zdarzeń, śledzenia rekordów.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="dacb2-162">Rejestrowanie identyfikator dostawcy specyficzne dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="dacb2-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="dacb2-163">Jeśli zdarzenia muszą być zapisywane w dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="dacb2-164">Zadeklaruj identyfikator dostawcy w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dacb2-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="dacb2-165">Skopiuj plik manifestu z %windir%\Microsoft.NET\Framework\\\<najnowszą wersję [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do tymczasowej lokalizacji i zmień jej nazwę na Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="dacb2-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="dacb2-166">Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.</span><span class="sxs-lookup"><span data-stu-id="dacb2-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="dacb2-167">Jeśli nie chcesz odinstalować domyślnego dostawcę, należy zmienić nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="dacb2-168">Jeśli zmienisz nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanałów w pliku manifestu na nową nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="dacb2-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="dacb2-169">Generowanie biblioteki DLL zasobu, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="dacb2-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="dacb2-170">Zainstaluj Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="dacb2-170">Install the Windows SDK.</span></span> <span data-ttu-id="dacb2-171">Zestaw Windows SDK zawiera kompilator komunikat ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) i kompilator zasobów ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="dacb2-171">The Windows SDK includes the message compiler ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>

    2. <span data-ttu-id="dacb2-172">W wierszu polecenia zestawu Windows SDK należy uruchomić mc.exe nowego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="dacb2-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="dacb2-173">Uruchom rc.exe plik resource wygenerowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="dacb2-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="dacb2-174">Utwórz plik pusty cs o nazwie NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="dacb2-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="dacb2-175">Utwórz zasób biblioteki DLL za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="dacb2-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="dacb2-176">Zmień nazwę biblioteki dll zasobu i komunikatów w pliku manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="dacb2-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="dacb2-177">Użyj [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) można zarejestrować w manifeście.</span><span class="sxs-lookup"><span data-stu-id="dacb2-177">Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="dacb2-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dacb2-178">See also</span></span>

- [<span data-ttu-id="dacb2-179">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="dacb2-179">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="dacb2-180">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="dacb2-180">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
