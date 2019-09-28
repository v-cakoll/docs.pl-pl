---
title: Konfigurowanie śledzenia dla przepływu pracy
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 889efc804bb45b384dfde5b4deb520a81d1e5486
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353053"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="b3c4d-102">Konfigurowanie śledzenia dla przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b3c4d-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="b3c4d-103">Przepływ pracy można wykonać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="b3c4d-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="b3c4d-104">Hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="b3c4d-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="b3c4d-105">Wykonane jako <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="b3c4d-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="b3c4d-106">Wykonywane bezpośrednio przy użyciu <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="b3c4d-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="b3c4d-107">W zależności od opcji hostingu przepływu pracy można dodać uczestnika śledzenia za pomocą kodu lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="b3c4d-108">W tym temacie opisano sposób skonfigurowania śledzenia przez dodanie uczestnika śledzenia do <xref:System.Activities.WorkflowApplication> i do <xref:System.ServiceModel.Activities.WorkflowServiceHost> oraz sposób włączania śledzenia podczas korzystania z <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="b3c4d-109">Konfigurowanie śledzenia aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b3c4d-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="b3c4d-110">Przepływ pracy można uruchomić za pomocą klasy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b3c4d-111">W tym temacie przedstawiono sposób skonfigurowania śledzenia dla aplikacji przepływu pracy [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] przez dodanie uczestnika śledzenia do hosta przepływów pracy @no__t 1.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="b3c4d-112">W takim przypadku przepływ pracy jest uruchamiany jako aplikacja przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="b3c4d-113">Aplikację przepływu pracy konfiguruje się za pomocą kodu (a nie przy użyciu pliku konfiguracji), który jest nieobsługiwanym plikiem exe przy użyciu klasy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b3c4d-114">Uczestnik śledzenia jest dodawany jako rozszerzenie wystąpienia <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="b3c4d-115">W tym celu należy dodać <xref:System.Activities.Tracking.TrackingParticipant> do kolekcji rozszerzeń dla wystąpienia obiektu WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="b3c4d-116">W przypadku aplikacji przepływu pracy można dodać rozszerzenie zachowanie <xref:System.Activities.Tracking.EtwTrackingParticipant>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="b3c4d-117">Konfigurowanie śledzenia usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b3c4d-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="b3c4d-118">Przepływ pracy może być ujawniony jako usługa WCF, gdy jest hostowany na hoście usługi <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="b3c4d-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> to wyspecjalizowana implementacja ServiceHost platformy .NET dla usługi opartej na przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="b3c4d-120">W tej sekcji wyjaśniono, jak skonfigurować śledzenie dla usługi przepływu pracy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działającej w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b3c4d-121">Jest ona konfigurowana za pośrednictwem pliku Web. config (dla usługi hostowanej w sieci Web) lub pliku App. config (dla usługi hostowanej w aplikacji autonomicznej, takiej jak Aplikacja konsolowa) przez określenie zachowania usługi lub za pośrednictwem kodu przez dodanie zachowania specyficznego dla śledzenia Kolekcja <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="b3c4d-122">W przypadku usługi przepływu pracy hostowanej w <xref:System.ServiceModel.WorkflowServiceHost> można dodać <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu elementu < `behavior` > w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

<span data-ttu-id="b3c4d-123">Alternatywnie w przypadku usługi przepływu pracy hostowanej w <xref:System.ServiceModel.WorkflowServiceHost> można dodać rozszerzenie zachowania <xref:System.Activities.Tracking.EtwTrackingParticipant> za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="b3c4d-124">Aby dodać uczestnika śledzenia niestandardowego, Utwórz nowe rozszerzenie zachowania i Dodaj je do <xref:System.ServiceModel.ServiceHost>, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="b3c4d-125">Jeśli chcesz wyświetlić przykładowy kod, który pokazuje, jak utworzyć niestandardowy element zachowania, który dodaje niestandardowego uczestnika śledzenia, zapoznaj się z przykładami [śledzenia](./samples/tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="b3c4d-126">Uczestnik śledzenia jest dodawany do hosta usługi przepływu pracy jako rozszerzenie zachowania.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="b3c4d-127">Poniższy przykładowy kod pokazuje, jak odczytać profil śledzenia z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="b3c4d-128">Ten przykładowy kod pokazuje, jak dodać profil śledzenia do hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="b3c4d-129">Więcej informacji o profilach śledzenia można znaleźć w tematach [śledzenie profilów](https://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="b3c4d-129">For more information on tracking profiles, refer to [Tracking Profiles](https://go.microsoft.com/fwlink/?LinkId=201310).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="b3c4d-130">Konfigurowanie śledzenia przy użyciu WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="b3c4d-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="b3c4d-131">Aby skonfigurować śledzenie dla przepływu pracy wykonywanego przy użyciu <xref:System.Activities.WorkflowInvoker>, Dodaj dostawcę śledzenia jako rozszerzenie do wystąpienia <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="b3c4d-132">Poniższy przykład kodu pochodzi z niestandardowego przykładu [śledzenia](./samples/custom-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="b3c4d-133">Wyświetlanie rekordów śledzenia w Podgląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b3c4d-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="b3c4d-134">Istnieją dwa Podgląd zdarzeń Dzienniki o szczególnym znaczeniu do wyświetlenia podczas śledzenia wykonywania funkcji WF — dziennik analityczny i Dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="b3c4d-135">Oba znajdują się w węźle&#124;serwer&#124;aplikacji systemu Microsoft Windows — aplikacje.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="b3c4d-136">Dzienniki w tej sekcji zawierają zdarzenia z pojedynczej aplikacji, a nie zdarzenia mające wpływ na cały system.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="b3c4d-137">Zdarzenia śledzenia debugowania są zapisywane w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="b3c4d-138">Aby zbierać zdarzenia śledzenia debugowania WF w Podgląd zdarzeń, Włącz Dziennik debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="b3c4d-139">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="b3c4d-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="b3c4d-140">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="b3c4d-141">W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług** .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="b3c4d-142">Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications** .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="b3c4d-143">Kliknij prawym przyciskiem myszy węzeł **debugowanie** w węźle **serwer aplikacji — aplikacje** , a następnie wybierz pozycję **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="b3c4d-144">Uruchom aplikację obsługującą śledzenie, aby wygenerować zdarzenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="b3c4d-145">Kliknij prawym przyciskiem myszy węzeł **debugowanie** i wybierz polecenie **Odśwież.**</span><span class="sxs-lookup"><span data-stu-id="b3c4d-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="b3c4d-146">Zdarzenia śledzenia powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="b3c4d-147">WF 4 udostępnia uczestnika śledzenia, który zapisuje rekordy śledzenia do sesji ETW (śledzenie zdarzeń systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="b3c4d-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="b3c4d-148">Uczestnik śledzenia ETW jest skonfigurowany przy użyciu profilu śledzenia w celu subskrybowania śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="b3c4d-149">Po włączeniu śledzenia błędy śledzenia rekordów są emitowane do funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="b3c4d-150">Zdarzenia śledzenia funkcji ETW (między zakresem 100-113) odpowiadające zdarzeniom śledzenia emitowanym przez uczestnika śledzenia ETW są zapisywane w dzienniku analitycznym.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="b3c4d-151">Aby wyświetlić rekordy śledzenia, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="b3c4d-152">Aby otworzyć Podgląd zdarzeń, kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom.**</span><span class="sxs-lookup"><span data-stu-id="b3c4d-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="b3c4d-153">W oknie dialogowym Uruchamianie wpisz `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="b3c4d-154">W oknie dialogowym Podgląd zdarzeń rozwiń węzeł **Dzienniki aplikacji i usług** .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="b3c4d-155">Rozwiń węzły **Microsoft**, **Windows**i **Application Server-Applications** .</span><span class="sxs-lookup"><span data-stu-id="b3c4d-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="b3c4d-156">Kliknij prawym przyciskiem myszy węzeł **analityczny** w węźle **serwer aplikacji — aplikacje** , a następnie wybierz pozycję **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="b3c4d-157">Wykonaj swoją aplikację obsługującą śledzenie, aby generować rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="b3c4d-158">Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież.**</span><span class="sxs-lookup"><span data-stu-id="b3c4d-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="b3c4d-159">Rekordy śledzenia powinny być widoczne w środkowym okienku.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="b3c4d-160">Na poniższej ilustracji przedstawiono śledzenie zdarzeń w Podglądzie zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b3c4d-160">The following image shows tracking events in the event viewer:</span></span>

![Zrzut ekranu przedstawiający Podgląd zdarzeń pokazujący śledzone rekordy.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="b3c4d-162">Rejestrowanie identyfikatora dostawcy specyficznego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="b3c4d-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="b3c4d-163">Jeśli zdarzenia muszą być zapisywane w określonym dzienniku aplikacji, wykonaj następujące kroki, aby zarejestrować nowy manifest dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="b3c4d-164">Zadeklaruj identyfikator dostawcy w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="b3c4d-165">Skopiuj plik manifestu z%windir%\Microsoft.NET\Framework @ no__t-0 @ no__t-1latest wersja [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] > \Microsoft.Windows.ApplicationServer.Applications.man do lokalizacji tymczasowej, a następnie zmień jej nazwę na Microsoft. Windows. ApplicationServer. Applications_Provider1. Man</span><span class="sxs-lookup"><span data-stu-id="b3c4d-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="b3c4d-166">Zmień identyfikator GUID w pliku manifestu na nowy identyfikator GUID.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="b3c4d-167">Zmień nazwę dostawcy, jeśli nie chcesz odinstalować domyślnego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="b3c4d-168">Jeśli zmieniono nazwę dostawcy w poprzednim kroku, należy zmienić nazwy kanałów w pliku manifestu na nazwę nowego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="b3c4d-169">Wygeneruj bibliotekę DLL zasobów, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="b3c4d-170">Zainstaluj Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-170">Install the Windows SDK.</span></span> <span data-ttu-id="b3c4d-171">Windows SDK obejmuje kompilator komunikatów ([mc. exe](https://go.microsoft.com/fwlink/?LinkId=184606)) i kompilator zasobów ([RC. exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="b3c4d-171">The Windows SDK includes the message compiler ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>

    2. <span data-ttu-id="b3c4d-172">W Windows SDK wierszu polecenia Uruchom polecenie mc. exe w nowym pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="b3c4d-173">Uruchom RC. exe w pliku zasobów wygenerowanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="b3c4d-174">Utwórz pusty plik CS o nazwie NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="b3c4d-175">Utwórz bibliotekę DLL zasobów przy użyciu C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="b3c4d-176">Zmień nazwę biblioteki DLL zasobu i komunikatu w pliku manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nową nazwę dll.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="b3c4d-177">Użyj [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) , aby zarejestrować manifest.</span><span class="sxs-lookup"><span data-stu-id="b3c4d-177">Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="b3c4d-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3c4d-178">See also</span></span>

- [<span data-ttu-id="b3c4d-179">Monitorowanie aplikacji sieci szkieletowej systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="b3c4d-179">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="b3c4d-180">Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="b3c4d-180">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
